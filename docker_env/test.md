> -_- coding: utf-8 -_-
> vim:fenc=utf-8
> File name: test.md
> First Edit: 2020-02-13
> Last Change: 13-Feb-2020.

---

I tried to get 2019 year's data.
But the 2019 year's data downloads failed.
Except 2019 year, downlad works well. ( I tested 2013 to 2018 ) 

This is the error message and my code.

> con2019 <- DBI::dbConnect(RPostgreSQL::PostgreSQL(), dbname = "mlb_2019",
+                       host = "172.28.1.2", port = 5432,
+                       user = "postgres", password = "postgres")

> get_payload(start = "2019-04-01", end = "2019-05-01", async = TRUE, db_con=con2019)

Gathering Gameday data, please be patient...
Processing data chunk 1 of 2
Error: `by` can't contain join column `tfs_zulu`, `inning`, `inning_side`, `des` which is missing from LHS
Run `rlang::last_error()` to see where the error occurred.

> rlang::last_error()
<error/rlang_error>
`by` can't contain join column `tfs_zulu`, `inning`, `inning_side`, `des` which is missing from LHS
Backtrace:
 1. mlbgameday::get_payload(...)
 2. mlbgameday::payload.gd_inning_all(urlz)
 4. dplyr:::left_join.tbl_df(...)
 6. dplyr:::common_by.character(by, x, y)
 7. dplyr:::common_by.list(by, x, y)
 8. dplyr:::bad_args(...)
 9. dplyr:::glubort(fmt_args(args), ..., .envir = .envir)
Run `rlang::last_trace()` to see the full context.

> rlang::last_trace()
<error/rlang_error>
`by` can't contain join column `tfs_zulu`, `inning`, `inning_side`, `des` which is missing from LHS
Backtrace:
    █
 1. └─mlbgameday::get_payload(...)
 2.   └─mlbgameday::payload.gd_inning_all(urlz)
 3.     ├─dplyr::left_join(...)
 4.     └─dplyr:::left_join.tbl_df(...)
 5.       ├─dplyr::common_by(by, x, y)
 6.       └─dplyr:::common_by.character(by, x, y)
 7.         └─dplyr:::common_by.list(by, x, y)
 8.           └─dplyr:::bad_args(...)
 9.             └─dplyr:::glubort(fmt_args(args), ..., .envir = .envir)
