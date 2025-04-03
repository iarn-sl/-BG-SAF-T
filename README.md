BG SAF-T

AuditFile

    Description: Root element of the Bulgarian SAF-T file.
    Български: Основен елемент на българския SAF-T файл.

    Type: Complex Type

    Required: Yes

Header

    Description: General information about the SAF-T audit file.
    Български: Обща информация за този стандартен одитен файл.

    Type: Complex Type

    Required: Yes

TaxAccountingBasis

    Description: Specifies the type of data included in the SAF-T file.
    Български: Тип данни в одитния файл.

    Type: Complex Type

    Required: Yes

    Allowed Enumerations:

        A – Търговски предприятия (Commercial enterprises)

        P – Бюджетни предприятия (Budget enterprises)

        BANK – Банкови институции (Banks)

        INSURANCE – Застрахователни компании (Insurance companies)

TaxEntity

    Description: Identification of the tax entity (company, subsidiary, or branch).
    Български: Файл за фирма/подразделение/клон.

    Type: nsSAFT:SAFmiddle2textType

    Required: No

MasterFiles

    Description: Contains master data related to accounting, suppliers, clients, and products.
    Български: Основни данни за счетоводни сметки, доставчици, клиенти, продукти и др.

    Type: Complex Type

    Required: Yes

GeneralLedgerAccounts

    Description: A list of general ledger accounts.
    Български: Списък на счетоводните сметки.

    Type: Complex Type

    Required: Yes

Account

    Description: Represents an individual general ledger account.
    Български: Информация за счетоводни сметки.

    Type: Complex Type

    Required: No (Multiple entries allowed)

AccountID

    Description: A unique identifier for an account, which should match the provided chart of accounts from the National Revenue Agency.
    Български: Код на аналитична счетоводна сметка, който трябва да съответства на предоставената номенклатура от сметки от НАП.

    Type: nsSAFT:SAFmiddle2textType

    Required: Yes

AccountDescription

    Description: The name of the account as recorded in the taxpayer’s system.
    Български: Наименование на сметката от системата на задълженото лице.

    Type: nsSAFT:SAFlongtextType

    Required: Yes

TaxpayerAccountID

    Description: The account number as used in the taxpayer’s accounting system.
    Български: Номер на сметка от информационната система, използвана за счетоводно отчитане от данъкоплатеца.

    Type: nsSAFT:SAFmiddle1textType

    Required: Yes
