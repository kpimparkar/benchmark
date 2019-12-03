# Cloud-Azure Benchmark
* Complete output can be accessed [here](https://github.com/cloudmesh-community/fa19-516-157/tree/master/Benchmark_Output)
## Summary
* test_01 & test_02 passed, some functions are skipped because key functions such as storage, list, delete isn't supported by Azure
* test_04 passed, butthe entire flavor was listed which caused the output file to be almost 46MB and 98% is the flavor result
* test_08 failed likely due to the same error as other clouds, wrong key name lookup, the output shows that all resources such as NIC, Subnet was successfully created but interrupted before vm creation
* test_09 ubuntu image look up fail due to the ubuntu doesn't exist in azure-image collection. I have encountered the same error in my custom test script, the result doesn't seem like official images like Ubuntu, Centos where user can see in AWS data. The Azure images are more like custom images created from snapshots by individual users, following is the azure image output
+---------+----------+---------------+--------------------------+--------------------------+------------------+
| Name    | Location | Publisher     | Plan Name                | Product                  | Operating System |
+---------+----------+---------------+--------------------------+--------------------------+------------------+
| 1.0.0   | eastus   | 128technology | 128t_networking_platform | 128t_networking_platform |                  |
| 1.1.0   | eastus   | 128technology | 128t_networking_platform | 128t_networking_platform |                  |
| 1.1.2   | eastus   | 128technology | 128t_networking_platform | 128t_networking_platform |                  |
| 4.10.11 | eastus   | 1e            | tachyonv4-1              | tachyonv30-0-100         |                  |
| 0.0.2   | eastus   | 2021ai        | grace_vm                 | grace-churn-vm           |                  |
| 16.0.8  | eastus   | 3cx-pbx       | 16                       | 3cx-pbx                  |                  |
| 5.2.5   | eastus   | 4psa          | vpn525-single            | voipnow                  |                  |
+---------+----------+---------------+--------------------------+--------------------------+------------------+


## test_00_sys
PASSED
tests/cloud/test_00_sys.py::Test_Sys::test_benchmark 
+-------------------+-----------------------------------------------------------------------------------+
| Machine Attribute | Value                                                                             |
+-------------------+-----------------------------------------------------------------------------------+
| cpu_count         | 12                                                                                |
| mac_version       |                                                                                   |
| machine           | ('AMD64',)                                                                        |
| mem_available     | 5.8 GiB                                                                           |
| mem_free          | 5.8 GiB                                                                           |
| mem_percent       | 63.8%                                                                             |
| mem_total         | 15.9 GiB                                                                          |
| mem_used          | 10.2 GiB                                                                          |
| node              | ('LAPTOP-0UEFF4CG',)                                                              |
| platform          | Windows-10-10.0.17763-SP0                                                         |
| processor         | ('Intel64 Family 6 Model 158 Stepping 10, GenuineIntel',)                         |
| processors        | Windows                                                                           |
| python            | 3.7.4 (tags/v3.7.4:e09359112e, Jul  8 2019, 20:34:20) [MSC v.1916 64 bit (AMD64)] |
| release           | ('10',)                                                                           |
| sys               | win32                                                                             |
| system            | Windows                                                                           |
| user              |                                                                                   |
| version           | 10.0.17763                                                                        |
| win_version       | ('10', '10.0.17763', 'SP0', '')                                                   |
+-------------------+-----------------------------------------------------------------------------------+
+---------------------------+-------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
| timer                     | time  | start               | tag   | node                 | user | system  | mac_version | win_version                     |
+---------------------------+-------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
| test_00_sys/test_cms_help | 2.538 | 2019-12-02 23:21:32 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| benchmark_start_stop      | 0.0   | 2019-12-02 23:21:34 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
+---------------------------+-------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
## test_01_clean_local_remote
* Azure doesn't support key storage, so key list isn't supported
######################################################################
test_delete_all_keys_from_cloud \tests\cloud\test_01_clean_local_remote.py 42
######################################################################
[0m
[31mERROR: Key list is not supported in Azure!

PASSED
tests/cloud/test_01_clean_local_remote.py::Test_Clean_Local_Remote::test_benchmark 
+-----------------------------------------------------------------+--------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
| timer                                                           | time   | start               | tag   | node                 | user | system  | mac_version | win_version                     |
+-----------------------------------------------------------------+--------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
| test_00_sys/test_cms_help                                       | 2.538  | 2019-12-02 23:21:32 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| benchmark_start_stop                                            | 0.0    | 2019-12-02 23:21:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_cms_init                        | 18.074 | 2019-12-02 23:21:34 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_delete_all_keys_from_cloud      | 0.003  | 2019-12-02 23:21:52 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_delete_all_secgroups_from_cloud | 0.363  | 2019-12-02 23:21:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
+-----------------------------------------------------------------+--------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
## test_02_key
* same as test_01 key list and other functions isn't supported by Azure

tests/cloud/test_02_key.py::Test_Key::test_benchmark 
+-----------------------------------------------------------------+--------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
| timer                                                           | time   | start               | tag   | node                 | user | system  | mac_version | win_version                     |
+-----------------------------------------------------------------+--------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
| test_00_sys/test_cms_help                                       | 2.538  | 2019-12-02 23:21:32 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| benchmark_start_stop                                            | 0.0    | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_cms_init                        | 18.074 | 2019-12-02 23:21:34 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_delete_all_keys_from_cloud      | 0.003  | 2019-12-02 23:21:52 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_delete_all_secgroups_from_cloud | 0.363  | 2019-12-02 23:21:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_upload_key_to_database                         | 0.333  | 2019-12-02 23:21:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_upload_key_to_cloud                            | 0.004  | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_list_key_from_cloud                            | 0.004  | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_delete_key_from_cloud                          | 0.004  | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
+-----------------------------------------------------------------+--------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
## test_03_key_upload
tests/cloud/test_03_key_upload.py::Test_Key::test_cleanup SKIPPED
tests/cloud/test_03_key_upload.py::Test_Key::test_upload_key_to_database SKIPPED
tests/cloud/test_03_key_upload.py::Test_Key::test_upload_key_to_cloud SKIPPED
tests/cloud/test_03_key_upload.py::Test_Key::test_list_key_from_cloud SKIPPED
tests/cloud/test_03_key_upload.py::Test_Key::test_benchmark SKIPPED
## test_04_flavor
* The provider is working and returning correct data, however, the benchmark script only outputted flavor list in azure cloud.
* The huge list of flavor caused the output file to be 46.8MB and 98% of the file is flavor list.
## test_05_image
PASSED
tests/cloud/test_05_image.py::Test_Image::test_benchmark 
+-----------------------------------------------------------------+--------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
| timer                                                           | time   | start               | tag   | node                 | user | system  | mac_version | win_version                     |
+-----------------------------------------------------------------+--------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
| test_00_sys/test_cms_help                                       | 2.538  | 2019-12-02 23:21:32 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| benchmark_start_stop                                            | 0.0    | 2019-12-02 23:23:12 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_cms_init                        | 18.074 | 2019-12-02 23:21:34 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_delete_all_keys_from_cloud      | 0.003  | 2019-12-02 23:21:52 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_delete_all_secgroups_from_cloud | 0.363  | 2019-12-02 23:21:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_upload_key_to_database                         | 0.333  | 2019-12-02 23:21:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_upload_key_to_cloud                            | 0.004  | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_list_key_from_cloud                            | 0.004  | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_delete_key_from_cloud                          | 0.004  | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_empty_database                              | 0.32   | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_provider_flavor                             | 12.0   | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_provider_flavor_update                      | 12.345 | 2019-12-02 23:22:08 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_cms_flavor_refresh                          | 14.981 | 2019-12-02 23:22:21 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_cms_flavor                                  | 5.049  | 2019-12-02 23:22:36 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_empty_database                               | 0.316  | 2019-12-02 23:22:41 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_provider_image                               | 7.704  | 2019-12-02 23:22:41 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_provider_image_update                        | 7.286  | 2019-12-02 23:22:49 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_cms_image_refresh                            | 10.286 | 2019-12-02 23:22:57 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_cms_image                                    | 5.007  | 2019-12-02 23:23:07 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
+-----------------------------------------------------------------+--------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
## test_06_sec_command
PASSED
tests/cloud/test_06_sec_command.py::TestSecCLI::test_benchmark 
+-----------------------------------------------------------------+--------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
| timer                                                           | time   | start               | tag   | node                 | user | system  | mac_version | win_version                     |
+-----------------------------------------------------------------+--------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
| test_00_sys/test_cms_help                                       | 2.538  | 2019-12-02 23:21:32 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| benchmark_start_stop                                            | 0.0    | 2019-12-02 23:23:53 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_cms_init                        | 18.074 | 2019-12-02 23:21:34 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_delete_all_keys_from_cloud      | 0.003  | 2019-12-02 23:21:52 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_delete_all_secgroups_from_cloud | 0.363  | 2019-12-02 23:21:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_upload_key_to_database                         | 0.333  | 2019-12-02 23:21:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_upload_key_to_cloud                            | 0.004  | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_list_key_from_cloud                            | 0.004  | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_delete_key_from_cloud                          | 0.004  | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_empty_database                              | 0.32   | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_provider_flavor                             | 12.0   | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_provider_flavor_update                      | 12.345 | 2019-12-02 23:22:08 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_cms_flavor_refresh                          | 14.981 | 2019-12-02 23:22:21 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_cms_flavor                                  | 5.049  | 2019-12-02 23:22:36 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_empty_database                               | 0.316  | 2019-12-02 23:22:41 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_provider_image                               | 7.704  | 2019-12-02 23:22:41 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_provider_image_update                        | 7.286  | 2019-12-02 23:22:49 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_cms_image_refresh                            | 10.286 | 2019-12-02 23:22:57 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_cms_image                                    | 5.007  | 2019-12-02 23:23:07 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_group_add                              | 3.898  | 2019-12-02 23:23:13 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_group_delete                           | 3.365  | 2019-12-02 23:23:17 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_sec_list                               | 3.447  | 2019-12-02 23:23:39 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_sec_group_list_local                   | 3.465  | 2019-12-02 23:23:43 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_sec_group_list_cloud                   | 5.381  | 2019-12-02 23:23:47 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
+-----------------------------------------------------------------+--------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
## test_07_secgroup_provider
PASSED
tests/cloud/test_07_secgroup_provider.py::Test_secgroup_provider::test_benchmark 
+-----------------------------------------------------------------+--------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
| timer                                                           | time   | start               | tag   | node                 | user | system  | mac_version | win_version                     |
+-----------------------------------------------------------------+--------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
| test_00_sys/test_cms_help                                       | 2.538  | 2019-12-02 23:21:32 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| benchmark_start_stop                                            | 0.0    | 2019-12-02 23:24:16 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_cms_init                        | 18.074 | 2019-12-02 23:21:34 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_delete_all_keys_from_cloud      | 0.003  | 2019-12-02 23:21:52 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_delete_all_secgroups_from_cloud | 0.363  | 2019-12-02 23:21:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_upload_key_to_database                         | 0.333  | 2019-12-02 23:21:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_upload_key_to_cloud                            | 0.004  | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_list_key_from_cloud                            | 0.004  | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_delete_key_from_cloud                          | 0.004  | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_empty_database                              | 0.32   | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_provider_flavor                             | 12.0   | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_provider_flavor_update                      | 12.345 | 2019-12-02 23:22:08 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_cms_flavor_refresh                          | 14.981 | 2019-12-02 23:22:21 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_cms_flavor                                  | 5.049  | 2019-12-02 23:22:36 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_empty_database                               | 0.316  | 2019-12-02 23:22:41 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_provider_image                               | 7.704  | 2019-12-02 23:22:41 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_provider_image_update                        | 7.286  | 2019-12-02 23:22:49 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_cms_image_refresh                            | 10.286 | 2019-12-02 23:22:57 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_cms_image                                    | 5.007  | 2019-12-02 23:23:07 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_group_add                              | 3.898  | 2019-12-02 23:23:13 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_group_delete                           | 3.365  | 2019-12-02 23:23:17 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_sec_list                               | 3.447  | 2019-12-02 23:23:39 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_sec_group_list_local                   | 3.465  | 2019-12-02 23:23:43 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_sec_group_list_cloud                   | 5.381  | 2019-12-02 23:23:47 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_load                             | 0.344  | 2019-12-02 23:23:53 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_list_variables                   | 0.003  | 2019-12-02 23:23:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_list_secgroups                   | 0.537  | 2019-12-02 23:23:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_list_secgroups_rules             | 0.894  | 2019-12-02 23:23:55 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_secgroups_add                    | 0.601  | 2019-12-02 23:23:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_upload_secgroup                  | 5.403  | 2019-12-02 23:23:57 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_secgroups_delete                 | 10.751 | 2019-12-02 23:24:03 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_secgroups_delete_again           | 1.525  | 2019-12-02 23:24:14 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
+-----------------------------------------------------------------+--------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
## test_08_vm_provider
* Creation of resources such as NIC,Subnet was all successful, it failed during vm creation, likely due to the same reason as other clouds, wrong key name lookup 
* VM creation failed and caused chain reaction
 
tests/cloud/test_08_vm_provider.py::Test_provider_vm::test_benchmark 
+-----------------------------------------------------------------+---------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
| timer                                                           | time    | start               | tag   | node                 | user | system  | mac_version | win_version                     |
+-----------------------------------------------------------------+---------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
| test_00_sys/test_cms_help                                       | 2.538   | 2019-12-02 23:21:32 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| benchmark_start_stop                                            | 0.0     | 2019-12-02 23:31:02 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_cms_init                        | 18.074  | 2019-12-02 23:21:34 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_delete_all_keys_from_cloud      | 0.003   | 2019-12-02 23:21:52 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_delete_all_secgroups_from_cloud | 0.363   | 2019-12-02 23:21:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_upload_key_to_database                         | 0.333   | 2019-12-02 23:21:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_upload_key_to_cloud                            | 0.004   | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_list_key_from_cloud                            | 0.004   | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_delete_key_from_cloud                          | 0.004   | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_empty_database                              | 0.32    | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_provider_flavor                             | 12.0    | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_provider_flavor_update                      | 12.345  | 2019-12-02 23:22:08 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_cms_flavor_refresh                          | 14.981  | 2019-12-02 23:22:21 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_cms_flavor                                  | 5.049   | 2019-12-02 23:22:36 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_empty_database                               | 0.316   | 2019-12-02 23:22:41 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_provider_image                               | 7.704   | 2019-12-02 23:22:41 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_provider_image_update                        | 7.286   | 2019-12-02 23:22:49 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_cms_image_refresh                            | 10.286  | 2019-12-02 23:22:57 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_cms_image                                    | 5.007   | 2019-12-02 23:23:07 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_group_add                              | 3.898   | 2019-12-02 23:23:13 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_group_delete                           | 3.365   | 2019-12-02 23:23:17 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_sec_list                               | 3.447   | 2019-12-02 23:23:39 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_sec_group_list_local                   | 3.465   | 2019-12-02 23:23:43 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_sec_group_list_cloud                   | 5.381   | 2019-12-02 23:23:47 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_load                             | 0.344   | 2019-12-02 23:23:53 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_list_variables                   | 0.003   | 2019-12-02 23:23:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_list_secgroups                   | 0.537   | 2019-12-02 23:23:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_list_secgroups_rules             | 0.894   | 2019-12-02 23:23:55 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_secgroups_add                    | 0.601   | 2019-12-02 23:23:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_upload_secgroup                  | 5.403   | 2019-12-02 23:23:57 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_secgroups_delete                 | 10.751  | 2019-12-02 23:24:03 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_secgroups_delete_again           | 1.525   | 2019-12-02 23:24:14 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_provider_vm_create                     |         | 2019-12-02 23:24:16 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| create vm test-wang542-vm-5                                     |         | 2019-12-02 23:24:17 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_provider_vmprovider_vm_list            |         | 2019-12-02 23:25:51 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_provider_vm_wait                       |         | 2019-12-02 23:25:51 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_provider_vm_ssh                        |         | 2019-12-02 23:26:03 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_provider_vm_info                       |         | 2019-12-02 23:26:04 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_vm_status                              |         | 2019-12-02 23:26:04 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_provider_vm_stop                       |         | 2019-12-02 23:26:04 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_provider_vm_start                      |         | 2019-12-02 23:26:05 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_provider_vm_terminate                  | 291.983 | 2019-12-02 23:26:05 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
+-----------------------------------------------------------------+---------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
## test_09_cm_names_find
* Unlike aws, Azure failed because the image collection doesn't have ubuntu. I have encountered this problem in custom test scipt, the image collection doesn't seem to have correct entries such as Ubuntu, Centos. 
* And there are only several entries, unlike aws has hundreds of image options
[35m
######################################################################
test_cm_find_ubuntu_in_images \tests\cloud\test_09_cm_names_find.py 131
######################################################################
[0m

{'name': {'$regex': '.*Ubuntu.*'}}
Number of entries [image 0
FAILED

tests/cloud/test_09_cm_names_find.py::Test_cm_find::test_benchmark 
+-----------------------------------------------------------------+---------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
| timer                                                           | time    | start               | tag   | node                 | user | system  | mac_version | win_version                     |
+-----------------------------------------------------------------+---------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+
| test_00_sys/test_cms_help                                       | 2.538   | 2019-12-02 23:21:32 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| benchmark_start_stop                                            | 0.0     | 2019-12-02 23:31:08 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_cms_init                        | 18.074  | 2019-12-02 23:21:34 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_delete_all_keys_from_cloud      | 0.003   | 2019-12-02 23:21:52 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_01_clean_local_remote/test_delete_all_secgroups_from_cloud | 0.363   | 2019-12-02 23:21:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_upload_key_to_database                         | 0.333   | 2019-12-02 23:21:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_upload_key_to_cloud                            | 0.004   | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_list_key_from_cloud                            | 0.004   | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_02_key/test_delete_key_from_cloud                          | 0.004   | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_empty_database                              | 0.32    | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_provider_flavor                             | 12.0    | 2019-12-02 23:21:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_provider_flavor_update                      | 12.345  | 2019-12-02 23:22:08 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_cms_flavor_refresh                          | 14.981  | 2019-12-02 23:22:21 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_04_flavor/test_cms_flavor                                  | 5.049   | 2019-12-02 23:22:36 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_empty_database                               | 0.316   | 2019-12-02 23:22:41 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_provider_image                               | 7.704   | 2019-12-02 23:22:41 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_provider_image_update                        | 7.286   | 2019-12-02 23:22:49 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_cms_image_refresh                            | 10.286  | 2019-12-02 23:22:57 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_05_image/test_cms_image                                    | 5.007   | 2019-12-02 23:23:07 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_group_add                              | 3.898   | 2019-12-02 23:23:13 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_group_delete                           | 3.365   | 2019-12-02 23:23:17 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_sec_list                               | 3.447   | 2019-12-02 23:23:39 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_sec_group_list_local                   | 3.465   | 2019-12-02 23:23:43 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_06_sec_command/test_sec_group_list_cloud                   | 5.381   | 2019-12-02 23:23:47 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_load                             | 0.344   | 2019-12-02 23:23:53 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_list_variables                   | 0.003   | 2019-12-02 23:23:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_list_secgroups                   | 0.537   | 2019-12-02 23:23:54 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_list_secgroups_rules             | 0.894   | 2019-12-02 23:23:55 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_secgroups_add                    | 0.601   | 2019-12-02 23:23:56 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_upload_secgroup                  | 5.403   | 2019-12-02 23:23:57 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_secgroups_delete                 | 10.751  | 2019-12-02 23:24:03 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_07_secgroup_provider/test_secgroups_delete_again           | 1.525   | 2019-12-02 23:24:14 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_provider_vm_create                     |         | 2019-12-02 23:24:16 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| create vm test-wang542-vm-5                                     |         | 2019-12-02 23:24:17 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_provider_vmprovider_vm_list            |         | 2019-12-02 23:25:51 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_provider_vm_wait                       |         | 2019-12-02 23:25:51 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_provider_vm_ssh                        |         | 2019-12-02 23:26:03 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_provider_vm_info                       |         | 2019-12-02 23:26:04 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_vm_status                              |         | 2019-12-02 23:26:04 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_provider_vm_stop                       |         | 2019-12-02 23:26:04 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_provider_vm_start                      |         | 2019-12-02 23:26:05 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_08_vm_provider/test_provider_vm_terminate                  | 291.983 | 2019-12-02 23:26:05 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_09_cm_names_find/test_cm_find_collection                   | 0.309   | 2019-12-02 23:31:02 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_09_cm_names_find/test_cm_find_loop                         | 0.896   | 2019-12-02 23:31:03 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_09_cm_names_find/test_cm_image_name_cloud                  | 0.306   | 2019-12-02 23:31:04 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_09_cm_names_find/test_cm_image_name_collection             | 0.297   | 2019-12-02 23:31:05 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_09_cm_names_find/test_names_regexp                         | 0.609   | 2019-12-02 23:31:05 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_09_cm_names_find/test_cm_find_vms                          | 0.302   | 2019-12-02 23:31:06 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_09_cm_names_find/test_cm_find_ubuntu_in_images             | 0.311   | 2019-12-02 23:31:06 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_09_cm_names_find/test_cm_find_cloud_name_attributes        | 0.312   | 2019-12-02 23:31:06 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_09_cm_names_find/test_cm_find_vm_collections               | 0.312   | 2019-12-02 23:31:07 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_09_cm_names_find/test_cm_find_vm_collections_vm            | 0.302   | 2019-12-02 23:31:07 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
| test_09_cm_names_find/test_cm_find_vm_collection_form_parameter | 0.299   | 2019-12-02 23:31:07 | azure | ('LAPTOP-0UEFF4CG',) |      | Windows |             | ('10', '10.0.17763', 'SP0', '') |
+-----------------------------------------------------------------+---------+---------------------+-------+----------------------+------+---------+-------------+---------------------------------+

## Failures
================================== FAILURES ===================================
__________________ Test_provider_vm.test_provider_vm_create ___________________

self = <test_08_vm_provider.Test_provider_vm object at 0x0000017D5F499608>

    def test_provider_vm_create(self):
        HEADING()
        name_generator.incr()
        Benchmark.Start()
>       data = provider.create(key=key)

tests\cloud\test_08_vm_provider.py:59: 
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
cloudmesh\mongo\DataBaseDecorator.py:86: in wrapper
    current = f(*args, **kwargs)
cloudmesh\compute\vm\Provider.py:217: in create
    created = self.loop(self._create, **arguments)
cloudmesh\compute\vm\Provider.py:114: in loop
    vm = func(**parameters)
cloudmesh\compute\vm\Provider.py:252: in _create
    data = self.p.create(**arguments)
cloudmesh\compute\azure\Provider.py:977: in create
    vm_parameters = self._create_vm_parameters(name, secgroup, pub_ip, key)
cloudmesh\compute\azure\Provider.py:1069: in _create_vm_parameters
    str(self._get_local_key_content(key)
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

self = <cloudmesh.compute.azure.Provider.Provider object at 0x0000017D5DC46588>
key_name = 'wang542-key'

    def _get_local_key_content(self, key_name):
        query = {'name': key_name}
    
        key = list(self.cmDatabase.collection('local-key').find(query))
    
        if len(key) == 0:
>           raise ValueError(f'Unable to find key: {key_name}')
E           ValueError: Unable to find key: wang542-key

cloudmesh\compute\azure\Provider.py:1038: ValueError
______________ Test_provider_vm.test_provider_vmprovider_vm_list ______________

self = <test_08_vm_provider.Test_provider_vm object at 0x0000017D5F4655C8>

    def test_provider_vmprovider_vm_list(self):
        # list should be after create() since it would return empty and
        # len(data) would be 0
        HEADING()
        Benchmark.Start()
        data = provider.list()
>       assert len(data) > 0
E       assert 0 > 0
E        +  where 0 = len([])

tests\cloud\test_08_vm_provider.py:75: AssertionError
___________________ Test_provider_vm.test_provider_vm_wait ____________________

self = <test_08_vm_provider.Test_provider_vm object at 0x0000017D5F110D88>

    def test_provider_vm_wait(self):
        HEADING()
        name = str(Name())
        Benchmark.Start()
        cm = CmDatabase()
        vm = cm.find_name(name, kind="vm")[0]
>       assert provider.wait(vm=vm), "cms wait timed out ..."
E       AssertionError: cms wait timed out ...
E       assert []
E        +  where [] = <bound method Provider.wait of <cloudmesh.compute.vm.Provider.Provider object at 0x0000017D5F0A1D08>>(vm={'_id': ObjectId('5de59d21fc4d81a9e4638892'), 'cm': {'cloud': 'azure', 'collection': 'azure-vm', 'created': '2019-12-02 23:24:17.380384', 'group': 'cloudmesh', ...}, 'name': 'test-wang542-vm-5'})
E        +    where <bound method Provider.wait of <cloudmesh.compute.vm.Provider.Provider object at 0x0000017D5F0A1D08>> = <cloudmesh.compute.vm.Provider.Provider object at 0x0000017D5F0A1D08>.wait

tests\cloud\test_08_vm_provider.py:85: AssertionError
____________________ Test_provider_vm.test_provider_vm_ssh ____________________

self = <test_08_vm_provider.Test_provider_vm object at 0x0000017D5F465588>

    def test_provider_vm_ssh(self):
        HEADING()
        name = str(Name())
        Benchmark.Start()
        cm = CmDatabase()
        vm = cm.find_name(name, kind="vm")[0]
>       data = provider.ssh(vm=vm, command='\"echo IAmAlive\"')

tests\cloud\test_08_vm_provider.py:94: 
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
cloudmesh\compute\vm\Provider.py:447: in ssh
    return self.p.ssh(vm=vm, command=command)
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

self = <cloudmesh.compute.azure.Provider.Provider object at 0x0000017D5DC46588>
vm = {'_id': ObjectId('5de59d21fc4d81a9e4638892'), 'cm': {'cloud': 'azure', 'collection': 'azure-vm', 'created': '2019-12-02 23:24:17.380384', 'group': 'cloudmesh', ...}, 'name': 'test-wang542-vm-5'}
command = '"echo IAmAlive"'

    def ssh(self, vm=None, command=None):
        if vm is None or command is None:
            raise Exception(f"vm or command can not be null")
    
        if isinstance(vm, dict):
            vm_obj = vm
        else:
            vm_obj = self._get_local_vm(vm)
    
>       nic_id = vm_obj['network_profile']['network_interfaces'][0]['id']
E       KeyError: 'network_profile'

cloudmesh\compute\azure\Provider.py:505: KeyError
___________________ Test_provider_vm.test_provider_vm_info ____________________

self = <test_08_vm_provider.Test_provider_vm object at 0x0000017D5F388308>

    def test_provider_vm_info(self):
        # This is just a dry run, status test actually uses info() in all
        # provider
        HEADING()
        Benchmark.Start()
        name = str(Name())
>       data = provider.info(name=name)

tests\cloud\test_08_vm_provider.py:106: 
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
cloudmesh\compute\vm\Provider.py:303: in info
    return self.loop_name(name, self.p.info)
cloudmesh\compute\vm\Provider.py:96: in loop_name
    vm = func(name=name)
cloudmesh\compute\azure\Provider.py:1313: in info
    node = self.vms.get(group, name, expand='instanceView')
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

self = <azure.mgmt.compute.v2019_03_01.operations.virtual_machines_operations.VirtualMachinesOperations object at 0x0000017D5F153F48>
resource_group_name = 'cloudmesh', vm_name = 'test-wang542-vm-5'
expand = 'instanceView', custom_headers = None, raw = False
operation_config = {}
url = 'https://management.azure.com/subscriptions/1b552345-85f2-4a12-97af-c67f27be817b/resourceGroups/cloudmesh/providers/Microsoft.Compute/virtualMachines/test-wang542-vm-5'
path_format_arguments = {'resourceGroupName': 'cloudmesh', 'subscriptionId': '1b552345-85f2-4a12-97af-c67f27be817b', 'vmName': 'test-wang542-vm-5'}
query_parameters = {'$expand': 'instanceView', 'api-version': '2019-03-01'}
header_parameters = {'Accept': 'application/json', 'accept-language': 'en-US', 'x-ms-client-request-id': '1be6e848-155b-11ea-965b-9078413e7703'}
request = <ClientRequest [GET]>, response = <Response [404]>
exp = CloudError("The Resource 'Microsoft.Compute/virtualMachines/test-wang542-vm-5' under resource group 'cloudmesh' was not found.")

    def get(
            self, resource_group_name, vm_name, expand=None, custom_headers=None, raw=False, **operation_config):
        """Retrieves information about the model view or the instance view of a
        virtual machine.
    
        :param resource_group_name: The name of the resource group.
        :type resource_group_name: str
        :param vm_name: The name of the virtual machine.
        :type vm_name: str
        :param expand: The expand expression to apply on the operation.
         Possible values include: 'instanceView'
        :type expand: str or
         ~azure.mgmt.compute.v2019_03_01.models.InstanceViewTypes
        :param dict custom_headers: headers that will be added to the request
        :param bool raw: returns the direct response alongside the
         deserialized response
        :param operation_config: :ref:`Operation configuration
         overrides<msrest:optionsforoperations>`.
        :return: VirtualMachine or ClientRawResponse if raw=true
        :rtype: ~azure.mgmt.compute.v2019_03_01.models.VirtualMachine or
         ~msrest.pipeline.ClientRawResponse
        :raises: :class:`CloudError<msrestazure.azure_exceptions.CloudError>`
        """
        # Construct URL
        url = self.get.metadata['url']
        path_format_arguments = {
            'resourceGroupName': self._serialize.url("resource_group_name", resource_group_name, 'str'),
            'vmName': self._serialize.url("vm_name", vm_name, 'str'),
            'subscriptionId': self._serialize.url("self.config.subscription_id", self.config.subscription_id, 'str')
        }
        url = self._client.format_url(url, **path_format_arguments)
    
        # Construct parameters
        query_parameters = {}
        if expand is not None:
            query_parameters['$expand'] = self._serialize.query("expand", expand, 'InstanceViewTypes')
        query_parameters['api-version'] = self._serialize.query("self.api_version", self.api_version, 'str')
    
        # Construct headers
        header_parameters = {}
        header_parameters['Accept'] = 'application/json'
        if self.config.generate_client_request_id:
            header_parameters['x-ms-client-request-id'] = str(uuid.uuid1())
        if custom_headers:
            header_parameters.update(custom_headers)
        if self.config.accept_language is not None:
            header_parameters['accept-language'] = self._serialize.header("self.config.accept_language", self.config.accept_language, 'str')
    
        # Construct and send request
        request = self._client.get(url, query_parameters, header_parameters)
        response = self._client.send(request, stream=False, **operation_config)
    
        if response.status_code not in [200]:
            exp = CloudError(response)
            exp.request_id = response.headers.get('x-ms-request-id')
>           raise exp
E           msrestazure.azure_exceptions.CloudError: Azure Error: ResourceNotFound
E           Message: The Resource 'Microsoft.Compute/virtualMachines/test-wang542-vm-5' under resource group 'cloudmesh' was not found.

..\..\lib\site-packages\azure\mgmt\compute\v2019_03_01\operations\virtual_machines_operations.py:557: CloudError
_______________________ Test_provider_vm.test_vm_status _______________________

self = <test_08_vm_provider.Test_provider_vm object at 0x0000017D5F3CFDC8>

    def test_vm_status(self):
        HEADING()
        name = str(Name())
        Benchmark.Start()
>       data = provider.status(name=name)

tests\cloud\test_08_vm_provider.py:115: 
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
cloudmesh\compute\vm\Provider.py:311: in status
    r = self.info(name=name)
cloudmesh\compute\vm\Provider.py:303: in info
    return self.loop_name(name, self.p.info)
cloudmesh\compute\vm\Provider.py:96: in loop_name
    vm = func(name=name)
cloudmesh\compute\azure\Provider.py:1313: in info
    node = self.vms.get(group, name, expand='instanceView')
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

self = <azure.mgmt.compute.v2019_03_01.operations.virtual_machines_operations.VirtualMachinesOperations object at 0x0000017D5F153F48>
resource_group_name = 'cloudmesh', vm_name = 'test-wang542-vm-5'
expand = 'instanceView', custom_headers = None, raw = False
operation_config = {}
url = 'https://management.azure.com/subscriptions/1b552345-85f2-4a12-97af-c67f27be817b/resourceGroups/cloudmesh/providers/Microsoft.Compute/virtualMachines/test-wang542-vm-5'
path_format_arguments = {'resourceGroupName': 'cloudmesh', 'subscriptionId': '1b552345-85f2-4a12-97af-c67f27be817b', 'vmName': 'test-wang542-vm-5'}
query_parameters = {'$expand': 'instanceView', 'api-version': '2019-03-01'}
header_parameters = {'Accept': 'application/json', 'accept-language': 'en-US', 'x-ms-client-request-id': '1c148ef8-155b-11ea-8ed2-9078413e7703'}
request = <ClientRequest [GET]>, response = <Response [404]>
exp = CloudError("The Resource 'Microsoft.Compute/virtualMachines/test-wang542-vm-5' under resource group 'cloudmesh' was not found.")

    def get(
            self, resource_group_name, vm_name, expand=None, custom_headers=None, raw=False, **operation_config):
        """Retrieves information about the model view or the instance view of a
        virtual machine.
    
        :param resource_group_name: The name of the resource group.
        :type resource_group_name: str
        :param vm_name: The name of the virtual machine.
        :type vm_name: str
        :param expand: The expand expression to apply on the operation.
         Possible values include: 'instanceView'
        :type expand: str or
         ~azure.mgmt.compute.v2019_03_01.models.InstanceViewTypes
        :param dict custom_headers: headers that will be added to the request
        :param bool raw: returns the direct response alongside the
         deserialized response
        :param operation_config: :ref:`Operation configuration
         overrides<msrest:optionsforoperations>`.
        :return: VirtualMachine or ClientRawResponse if raw=true
        :rtype: ~azure.mgmt.compute.v2019_03_01.models.VirtualMachine or
         ~msrest.pipeline.ClientRawResponse
        :raises: :class:`CloudError<msrestazure.azure_exceptions.CloudError>`
        """
        # Construct URL
        url = self.get.metadata['url']
        path_format_arguments = {
            'resourceGroupName': self._serialize.url("resource_group_name", resource_group_name, 'str'),
            'vmName': self._serialize.url("vm_name", vm_name, 'str'),
            'subscriptionId': self._serialize.url("self.config.subscription_id", self.config.subscription_id, 'str')
        }
        url = self._client.format_url(url, **path_format_arguments)
    
        # Construct parameters
        query_parameters = {}
        if expand is not None:
            query_parameters['$expand'] = self._serialize.query("expand", expand, 'InstanceViewTypes')
        query_parameters['api-version'] = self._serialize.query("self.api_version", self.api_version, 'str')
    
        # Construct headers
        header_parameters = {}
        header_parameters['Accept'] = 'application/json'
        if self.config.generate_client_request_id:
            header_parameters['x-ms-client-request-id'] = str(uuid.uuid1())
        if custom_headers:
            header_parameters.update(custom_headers)
        if self.config.accept_language is not None:
            header_parameters['accept-language'] = self._serialize.header("self.config.accept_language", self.config.accept_language, 'str')
    
        # Construct and send request
        request = self._client.get(url, query_parameters, header_parameters)
        response = self._client.send(request, stream=False, **operation_config)
    
        if response.status_code not in [200]:
            exp = CloudError(response)
            exp.request_id = response.headers.get('x-ms-request-id')
>           raise exp
E           msrestazure.azure_exceptions.CloudError: Azure Error: ResourceNotFound
E           Message: The Resource 'Microsoft.Compute/virtualMachines/test-wang542-vm-5' under resource group 'cloudmesh' was not found.

..\..\lib\site-packages\azure\mgmt\compute\v2019_03_01\operations\virtual_machines_operations.py:557: CloudError
___________________ Test_provider_vm.test_provider_vm_stop ____________________

self = <test_08_vm_provider.Test_provider_vm object at 0x0000017D5F0C1A88>

    def test_provider_vm_stop(self):
        HEADING()
        name = str(Name())
        Benchmark.Start()
>       data = provider.stop(name=name)

tests\cloud\test_08_vm_provider.py:127: 
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
cloudmesh\mongo\DataBaseDecorator.py:86: in wrapper
    current = f(*args, **kwargs)
cloudmesh\compute\vm\Provider.py:293: in stop
    return self.loop_name(name, self.p.stop)
cloudmesh\compute\vm\Provider.py:96: in loop_name
    vm = func(name=name)
cloudmesh\compute\azure\Provider.py:1262: in stop
    async_vm_stop = self.vms.power_off(group, name)
..\..\lib\site-packages\azure\mgmt\compute\v2019_03_01\operations\virtual_machines_operations.py:1127: in power_off
    **operation_config
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

self = <azure.mgmt.compute.v2019_03_01.operations.virtual_machines_operations.VirtualMachinesOperations object at 0x0000017D5F153F48>
resource_group_name = 'cloudmesh', vm_name = 'test-wang542-vm-5'
skip_shutdown = False, custom_headers = None, raw = True, operation_config = {}
url = 'https://management.azure.com/subscriptions/1b552345-85f2-4a12-97af-c67f27be817b/resourceGroups/cloudmesh/providers/Microsoft.Compute/virtualMachines/test-wang542-vm-5/powerOff'
path_format_arguments = {'resourceGroupName': 'cloudmesh', 'subscriptionId': '1b552345-85f2-4a12-97af-c67f27be817b', 'vmName': 'test-wang542-vm-5'}
query_parameters = {'api-version': '2019-03-01', 'skipShutdown': 'false'}
header_parameters = {'accept-language': 'en-US', 'x-ms-client-request-id': '1c3dbdb6-155b-11ea-a64f-9078413e7703'}
request = <ClientRequest [POST]>, response = <Response [404]>
exp = CloudError("The Resource 'Microsoft.Compute/virtualMachines/test-wang542-vm-5' under resource group 'cloudmesh' was not found.")

    def _power_off_initial(
            self, resource_group_name, vm_name, skip_shutdown=False, custom_headers=None, raw=False, **operation_config):
        # Construct URL
        url = self.power_off.metadata['url']
        path_format_arguments = {
            'resourceGroupName': self._serialize.url("resource_group_name", resource_group_name, 'str'),
            'vmName': self._serialize.url("vm_name", vm_name, 'str'),
            'subscriptionId': self._serialize.url("self.config.subscription_id", self.config.subscription_id, 'str')
        }
        url = self._client.format_url(url, **path_format_arguments)
    
        # Construct parameters
        query_parameters = {}
        if skip_shutdown is not None:
            query_parameters['skipShutdown'] = self._serialize.query("skip_shutdown", skip_shutdown, 'bool')
        query_parameters['api-version'] = self._serialize.query("self.api_version", self.api_version, 'str')
    
        # Construct headers
        header_parameters = {}
        if self.config.generate_client_request_id:
            header_parameters['x-ms-client-request-id'] = str(uuid.uuid1())
        if custom_headers:
            header_parameters.update(custom_headers)
        if self.config.accept_language is not None:
            header_parameters['accept-language'] = self._serialize.header("self.config.accept_language", self.config.accept_language, 'str')
    
        # Construct and send request
        request = self._client.post(url, query_parameters, header_parameters)
        response = self._client.send(request, stream=False, **operation_config)
    
        if response.status_code not in [200, 202]:
            exp = CloudError(response)
            exp.request_id = response.headers.get('x-ms-request-id')
>           raise exp
E           msrestazure.azure_exceptions.CloudError: Azure Error: ResourceNotFound
E           Message: The Resource 'Microsoft.Compute/virtualMachines/test-wang542-vm-5' under resource group 'cloudmesh' was not found.

..\..\lib\site-packages\azure\mgmt\compute\v2019_03_01\operations\virtual_machines_operations.py:1089: CloudError
___________________ Test_provider_vm.test_provider_vm_start ___________________

self = <test_08_vm_provider.Test_provider_vm object at 0x0000017D5F399E48>

    def test_provider_vm_start(self):
        HEADING()
        name = str(Name())
        Benchmark.Start()
>       data = provider.start(name=name)

tests\cloud\test_08_vm_provider.py:145: 
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _
cloudmesh\mongo\DataBaseDecorator.py:86: in wrapper
    current = f(*args, **kwargs)
cloudmesh\compute\vm\Provider.py:298: in start
    return self.loop_name(name, self.p.start)
cloudmesh\compute\vm\Provider.py:96: in loop_name
    vm = func(name=name)
cloudmesh\compute\azure\Provider.py:1221: in start
    async_vm_start = self.vms.start(group, name)
..\..\lib\site-packages\azure\mgmt\compute\v2019_03_01\operations\virtual_machines_operations.py:1285: in start
    **operation_config
_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _

self = <azure.mgmt.compute.v2019_03_01.operations.virtual_machines_operations.VirtualMachinesOperations object at 0x0000017D5F153F48>
resource_group_name = 'cloudmesh', vm_name = 'test-wang542-vm-5'
custom_headers = None, raw = True, operation_config = {}
url = 'https://management.azure.com/subscriptions/1b552345-85f2-4a12-97af-c67f27be817b/resourceGroups/cloudmesh/providers/Microsoft.Compute/virtualMachines/test-wang542-vm-5/start'
path_format_arguments = {'resourceGroupName': 'cloudmesh', 'subscriptionId': '1b552345-85f2-4a12-97af-c67f27be817b', 'vmName': 'test-wang542-vm-5'}
query_parameters = {'api-version': '2019-03-01'}
header_parameters = {'accept-language': 'en-US', 'x-ms-client-request-id': '1c6b6058-155b-11ea-a893-9078413e7703'}
request = <ClientRequest [POST]>, response = <Response [404]>
exp = CloudError("The Resource 'Microsoft.Compute/virtualMachines/test-wang542-vm-5' under resource group 'cloudmesh' was not found.")

    def _start_initial(
            self, resource_group_name, vm_name, custom_headers=None, raw=False, **operation_config):
        # Construct URL
        url = self.start.metadata['url']
        path_format_arguments = {
            'resourceGroupName': self._serialize.url("resource_group_name", resource_group_name, 'str'),
            'vmName': self._serialize.url("vm_name", vm_name, 'str'),
            'subscriptionId': self._serialize.url("self.config.subscription_id", self.config.subscription_id, 'str')
        }
        url = self._client.format_url(url, **path_format_arguments)
    
        # Construct parameters
        query_parameters = {}
        query_parameters['api-version'] = self._serialize.query("self.api_version", self.api_version, 'str')
    
        # Construct headers
        header_parameters = {}
        if self.config.generate_client_request_id:
            header_parameters['x-ms-client-request-id'] = str(uuid.uuid1())
        if custom_headers:
            header_parameters.update(custom_headers)
        if self.config.accept_language is not None:
            header_parameters['accept-language'] = self._serialize.header("self.config.accept_language", self.config.accept_language, 'str')
    
        # Construct and send request
        request = self._client.post(url, query_parameters, header_parameters)
        response = self._client.send(request, stream=False, **operation_config)
    
        if response.status_code not in [200, 202]:
            exp = CloudError(response)
            exp.request_id = response.headers.get('x-ms-request-id')
>           raise exp
E           msrestazure.azure_exceptions.CloudError: Azure Error: ResourceNotFound
E           Message: The Resource 'Microsoft.Compute/virtualMachines/test-wang542-vm-5' under resource group 'cloudmesh' was not found.

..\..\lib\site-packages\azure\mgmt\compute\v2019_03_01\operations\virtual_machines_operations.py:1255: CloudError
_________________ Test_cm_find.test_cm_find_ubuntu_in_images __________________

self = <test_09_cm_names_find.Test_cm_find object at 0x0000017D5F041048>

    def test_cm_find_ubuntu_in_images(self):
        HEADING()
        print()
        query = {"name": {'$regex': ".*Ubuntu.*"}}
        print(query)
    
        Benchmark.Start()
        entries = cm.find(collection=f"{cloud}-image", query=query)
        Benchmark.Stop()
    
        kind = "image"
        if benchmark_print:
            print(entries)
            for entry in entries:
                print(entry['name'])
        else:
            print(f"Number of entries [{kind}", len(entries))
    
>       assert len(entries) > 0
E       assert 0 > 0
E        +  where 0 = len([])

tests\cloud\test_09_cm_names_find.py:149: AssertionError
============================== warnings summary ===============================
tests/cloud/test_01_clean_local_remote.py::Test_Clean_Local_Remote::test_delete_all_secgroups_from_cloud
tests/cloud/test_07_secgroup_provider.py::Test_secgroup_provider::test_list_secgroups
tests/cloud/test_07_secgroup_provider.py::Test_secgroup_provider::test_list_secgroups_rules
tests/cloud/test_07_secgroup_provider.py::Test_secgroup_provider::test_secgroups_add
tests/cloud/test_07_secgroup_provider.py::Test_secgroup_provider::test_secgroups_add
tests/cloud/test_07_secgroup_provider.py::Test_secgroup_provider::test_upload_secgroup
tests/cloud/test_07_secgroup_provider.py::Test_secgroup_provider::test_upload_secgroup
tests/cloud/test_07_secgroup_provider.py::Test_secgroup_provider::test_secgroups_delete
tests/cloud/test_07_secgroup_provider.py::Test_secgroup_provider::test_secgroups_delete_again
tests/cloud/test_08_vm_provider.py::Test_provider_vm::test_provider_vm_create
  d:\school\b649_engineeringcloudcomputing\env4\cm\cloudmesh-cloud\cloudmesh\compute\azure\Provider.py:673: DeprecationWarning: count is deprecated. Use Collection.count_documents instead.
    if local_sec_group.count() == 0:

-- Docs: https://docs.pytest.org/en/latest/warnings.html