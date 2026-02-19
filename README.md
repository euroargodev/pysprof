⚠️ Work in progress, not ready for production.

# Sprof generator in Python

This tool is a Python implementation of [matsprof](https://github.com/euroargodev/matsprof), a stand-alone version of the "nc_create_synthetic_profile" tool used at the Coriolis GDAC to generate mono-cycle synthetic profile (S-PROF) files (from C and B mono-cycle (C-PROF and B-PROF) files).

See http://doi.org/10.13155/55637 for details.



## Mono-cycle files

### Naive Python implementation status
- One-to-one function translation
- Only change is the use of a class to carry Matlab global parameters in a Python dataclass and to store synthetic profile information.

Progress on original functions:
- [ ] function  create_mono_cycle_synthetic_profile(varargin)
- [ ] function  [o_inputError] = parse_input_param(a_varargin)
- [ ] function  print_help
- [ ] function  process_one_float(a_floatInputDir, a_outputDir)
- [ ] function  nc_create_synthetic_profile_(a_cProfFileName, a_bProfFileName, a_metaFileName, a_outputDir, a_bgcFloatFlag)
- [ ] function  [o_profData] = get_prof_data(a_cProfFileName, a_bProfFileName)
- [ ] function  [o_profDataStruct] = get_prof_data_init_struct
- [ ] function  [o_syntProfData] = process_prof_data(a_profData, a_profData, a_cProfFileName, a_bProfFileName, a_metaFileName, a_bgcFloatFlag)
- [x] function  [o_profDataStruct] = get_synthetic_prof_data_init_struct
- [ ] function  create_synthetic_mono_cycle_file(a_floatWmo, a_profData, a_outputDir)

Progress on functions from the Coriolis decoder:
- [ ] function  synthfull=ARGO_simplified_profile(varargin)
- [ ] function  S=lov_netcdf_pickprod(filename,varargin)
- [x] function  [xcon,ycon,ind] = consolidator(x,y,aggregation_mode,tol)

Progress on functions from the Coriolis decoder also used by the Multi-cycles encoder:
- [x] function  [o_now] = now_utc
- [x] function  init_default_values(varargin)
- [x] function  [o_julDay] = gregorian_2_julian_dec_argo(a_gregorianDate)
- [ ] function  [o_ncData] = get_data_from_nc_file(a_ncPathFileName, a_wantedVars)
- [ ] function  [o_varFlagList] = vars_are_present_dec_argo(a_ncId, a_varNameList)
- [ ] function  [o_dataValues] = get_data_from_name(a_dataName, a_dataList)
- [ ] function  [o_attributeStruct] = get_netcdf_param_attributes_extended(a_paramName, a_floatNum)
- [ ] function  [o_attributeStruct] = get_netcdf_param_attributes(a_paramName)
- [ ] function  [o_ncDataAtt] = get_att_from_nc_file(a_ncPathFileName, a_wantedVarAtts)
- [ ] function  [o_present] = var_is_present_dec_argo(a_ncId, a_varName)
- [ ] function  [o_present] = att_is_present_dec_argo(a_ncId, a_varName, a_attName)
- [ ] function  [o_dataValues] = get_att_from_name(a_varName, a_attName, a_dataList)
- [ ] function  [o_institution] = get_institution_from_data_centre(a_dataCentre, a_printWarningFlag)
- [ ] function  [o_profQc] = compute_profile_quality_flag(a_qcFlags)

## Multi-cycle files

### Naive Python implementation status

Progress on original functions:
- [ ] function create_multi_cycle_synthetic_profile(varargin)
- [ ] function print_help
- [ ] function process_one_float(a_floatInputDir, a_outputDir)
- [ ] function [o_syntProfAllData] = get_all_synthetic_prof_data(a_floatInputDir)
- [ ] function [o_syntProfData] = get_synthetic_prof_data(a_sProfFileName)
- [ ] function [o_profDataStruct] = get_synthetic_prof_data_init_struct
- [ ] function [a_syntProfAllData] = uniformize_n_calib_dimension(a_syntProfAllData)
- [ ] function create_synthetic_multi_cycle_file(a_floatWmo, a_profData, a_outputDir)
