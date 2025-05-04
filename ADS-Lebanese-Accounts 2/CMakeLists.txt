cmake_minimum_required(VERSION 3.29)
project(DS_Lebanese_Accounts_2)

set(CMAKE_CXX_STANDARD 14)

include_directories(.)

add_executable(DS_Lebanese_Accounts_2
    accounts/account_1_ee.txt
    accounts/account_68725__Derogator.txt
    accounts/account_890__Opening_b.txt
    accounts/account_892_testing_ac.txt
    resources/accounts.txt
    resources/savedAccounts.text
    resources/savedAccounts.txt
    Account.cpp
    Account.h
    ForestTree.cpp
    ForestTree.h
    main.cpp
        Transaction.cpp
    Transaction.h)
