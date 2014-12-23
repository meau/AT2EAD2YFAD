AT2EAD2YFAD
===========

pipeline of scripts to batch export EAD from AT and then rename, store, transform and publish finding aids

Notes

Two pipelines -- files exported from AT and rendered in PDF every night for editing/QC, and edited/QC files ready for publication

AT -> PDF for QC

Presumption -- resource records must have proper finding aid status set. These scripts should run to provide a PDF preview of work done nightly.

1. Every Monday, export EAD from AT based on time last updated and finding aid status. if "Ready for Review", download with internal-only components suppressed to FindingAids/MSSA/QCCopies. if "Ready for Review Internal Only", download one copy with internal-only components suppressed to FindingAids/MSSA/QCCopies. Download another copy without components suppressed to FindingAids_MSSA/QCCopies/Internal-Only
2. Rename files based on MSSA conventions -- mssa.ms.0000.xml mssa.ru.0000.xml (talk to Mary about updating the EADID)
3. For files in QCCopies, transform ATEAD to YaleBPGEAD.pdf with xsl-fo, suppressInternalComponents = Y. For files in QCCopies/Internal-Only, transform ATEAD to YaleBPGEAD.pdf with xsl-fo, suppressInternalComponents = N.
4. Delete intermediate xml files, save PDFs in folders labelled by date.

AT -> EAD for YFAD

Presumption -- resource records must have proper finding aid status set. These scripts should run to update YFAD once per week (Thursday evening?)

1. Export EAD from AT based on time last updated and finding aid status. if "Complete", download with internal-only components suppressed to FindingAids_MSSA/AT_EAD_Export. if "Complete Internal Only", download one copy with internal-only components suppressed to FindingAids_MSSA/AT_EAD_Export. Download another copy without components suppressed to XXXX (place where dumb sharepoint shit goes)
2. Rename files based on MSSA conventions
3. For files in AT_EAD_Export, transform ATEAD to YaleBPGEAD with xslt, suppressInternalComponents = Y. For files in XXXX, transform ATEAD to YaleBPGEAD with xslt, suppressInternalComponents = N.
4. Check that files are still valid EAD. If not, move to FixMeInAT
5. Valid files should be saved to Edits_completed_for_YFAD_upload
6. Copies of valid files should also be saved to MasterEAD2002_AT
7. Upload files from edits_completed_for_YFAD to fedora/mssa
8. Create log/database(?) of transformation steps.

AT -> EAD for ArchiveGrid

AT -> EAD for Connecticut Archives Online 
