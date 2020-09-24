---
title: LINQ to SQL’de Kod Oluşturma
ms.date: 03/30/2017
ms.assetid: ddcbdaa1-e7fa-4d85-a379-313b49965c07
ms.openlocfilehash: f58448e0fc0c22795005b55a737b42374a750ec3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161535"
---
# <a name="code-generation-in-linq-to-sql"></a><span data-ttu-id="f1086-102">LINQ to SQL’de Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f1086-102">Code Generation in LINQ to SQL</span></span>

<span data-ttu-id="f1086-103">Nesne İlişkisel Tasarımcısı ya da SQLMetal komut satırı aracını kullanarak bir veritabanını temsil etmek için kod oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1086-103">You can generate code to represent a database by using either the Object Relational Designer or the SQLMetal command-line tool.</span></span> <span data-ttu-id="f1086-104">Her iki durumda da, uçtan uca kod oluşturma üç aşamada gerçekleşir:</span><span class="sxs-lookup"><span data-stu-id="f1086-104">In either case, end-to-end code generation occurs in three stages:</span></span>  
  
1. <span data-ttu-id="f1086-105">*DBML ayıklayıcısı* veritabanından şema bilgilerini ayıklar ve bu bilgileri XML biçimli bir dbml dosyasına yeniden birleştirir.</span><span class="sxs-lookup"><span data-stu-id="f1086-105">The *DBML Extractor* extracts schema information from the database and reassembles the information into an XML-formatted DBML file.</span></span>  
  
2. <span data-ttu-id="f1086-106">DBML dosyası hatalar için *DBML doğrulayıcısı* tarafından taranır.</span><span class="sxs-lookup"><span data-stu-id="f1086-106">The DBML file is scanned by the *DBML Validator* for errors.</span></span>  
  
3. <span data-ttu-id="f1086-107">Doğrulama hatası görünmüyorsa dosya kod oluşturucuya geçirilir.</span><span class="sxs-lookup"><span data-stu-id="f1086-107">If no validation errors appear, the file is passed to the Code Generator.</span></span>  
  
 <span data-ttu-id="f1086-108">Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="f1086-108">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="f1086-109">Visual Studio kullanan geliştiriciler ayrıca kod oluşturmak için Nesne İlişkisel Tasarımcısı de kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="f1086-109">Developers using Visual Studio can also use the Object Relational Designer to generate code.</span></span> <span data-ttu-id="f1086-110">Bkz. [Visual Studio 'da LINQ to SQL araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="f1086-110">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
## <a name="dbml-extractor"></a><span data-ttu-id="f1086-111">DBML ayıklayıcısı</span><span class="sxs-lookup"><span data-stu-id="f1086-111">DBML Extractor</span></span>  

 <span data-ttu-id="f1086-112">DBML ayıklayıcısı, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veritabanı meta verilerini girdi olarak alan ve bır DBML dosyasını çıktı olarak üreten bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="f1086-112">The DBML Extractor is a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] component that takes database metadata as input and produces a DBML file as output.</span></span>  
  
## <a name="code-generator"></a><span data-ttu-id="f1086-113">Kod Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="f1086-113">Code Generator</span></span>  

 <span data-ttu-id="f1086-114">Kod Oluşturucu, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] DBML dosyalarını Visual Basic, C# veya XML eşleme dosyalarına çeviren bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="f1086-114">The Code Generator is a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] component that translates DBML files to Visual Basic, C#, or XML mapping files.</span></span>  
  
## <a name="xml-schema-definition-file"></a><span data-ttu-id="f1086-115">XML şema tanımı dosyası</span><span class="sxs-lookup"><span data-stu-id="f1086-115">XML Schema Definition File</span></span>  

 <span data-ttu-id="f1086-116">DBML dosyası, XSD dosyası olarak aşağıdaki şema tanımına karşı geçerli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f1086-116">The DBML file must be valid against the following schema definition as an XSD file.</span></span>  
  
 <span data-ttu-id="f1086-117">Bu şema tanımı dosyasını, bir dış eşleme dosyasını doğrulamak için kullanılan şema tanımı dosyasından ayırt edin.</span><span class="sxs-lookup"><span data-stu-id="f1086-117">Distinguish this schema definition file from the schema definition file that is used to validate an external mapping file.</span></span> <span data-ttu-id="f1086-118">Daha fazla bilgi için bkz. [dış eşleme](external-mapping.md)).</span><span class="sxs-lookup"><span data-stu-id="f1086-118">For more information, see [External Mapping](external-mapping.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f1086-119">Visual Studio kullanıcıları Ayrıca bu XSD dosyasını "DbmlSchema. xsd" olarak XML şemaları iletişim kutusunda bulur.</span><span class="sxs-lookup"><span data-stu-id="f1086-119">Visual Studio users will also find this XSD file in the XML Schemas dialog box as "DbmlSchema.xsd".</span></span> <span data-ttu-id="f1086-120">Bir DBML dosyasını doğrulamak için XSD dosyasını doğru şekilde kullanmak için bkz. [nasıl yapılır: dbml ve dış eşleme dosyalarını doğrulama](how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="f1086-120">To use the XSD file correctly for validating a DBML file, see [How to: Validate DBML and External Mapping Files](how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://schemas.microsoft.com/linqtosql/dbml/2007" xmlns="http://schemas.microsoft.com/linqtosql/dbml/2007"  
elementFormDefault="qualified" >  
  <xs:element name="Database" type="Database" />  
  <xs:complexType name="Database">  
    <xs:sequence>  
      <xs:element name="Connection" type="Connection" minOccurs="0" maxOccurs="1" />  
      <xs:element name="Table" type="Table" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="Function" type="Function" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="EntityNamespace" type="xs:string" use="optional" />  
    <xs:attribute name="ContextNamespace" type="xs:string" use="optional" />  
    <xs:attribute name="Class" type="xs:string" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="ClassModifier" use="optional" />  
    <xs:attribute name="BaseType" type="xs:string" use="optional" />  
    <xs:attribute name="Provider" type="xs:string" use="optional" />  
    <xs:attribute name="ExternalMapping" type="xs:boolean" use="optional" />  
    <xs:attribute name="Serialization" type="SerializationMode" use="optional" />  
    <xs:attribute name="EntityBase" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Table">  
    <xs:all>  
      <xs:element name="Type" type="Type" minOccurs="1" maxOccurs="1" />  
      <xs:element name="InsertFunction" type="TableFunction" minOccurs="0" maxOccurs="1" />  
      <xs:element name="UpdateFunction" type="TableFunction" minOccurs="0" maxOccurs="1" />  
      <xs:element name="DeleteFunction" type="TableFunction" minOccurs="0" maxOccurs="1" />  
    </xs:all>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Member" type="xs:string" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="MemberModifier" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Type">  
    <xs:sequence>  
      <xs:choice minOccurs="0" maxOccurs="unbounded">  
        <xs:element name="Column" type="Column" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Association" type="Association" minOccurs="0" maxOccurs="unbounded" />  
      </xs:choice>  
      <xs:element name="Type" type="Type" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="IdRef" type="xs:IDREF" use="optional" />  
    <xs:attribute name="Id" type="xs:ID" use="optional" />  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="InheritanceCode" type="xs:string" use="optional" />  
    <xs:attribute name="IsInheritanceDefault" type="xs:boolean" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="ClassModifier" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Column">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="optional" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="MemberModifier" use="optional" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="IsReadOnly" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsPrimaryKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsDbGenerated" type="xs:boolean" use="optional" />  
    <xs:attribute name="CanBeNull" type="xs:boolean" use="optional" />  
    <xs:attribute name="UpdateCheck" type="UpdateCheck" use="optional" />  
    <xs:attribute name="IsDiscriminator" type="xs:boolean" use="optional" />  
    <xs:attribute name="Expression" type="xs:string" use="optional" />  
    <xs:attribute name="IsVersion" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsDelayLoaded" type="xs:boolean" use="optional" />  
    <xs:attribute name="AutoSync" type="AutoSync" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Association">  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="MemberModifier" use="optional" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attribute name="ThisKey" type="xs:string" use="optional" />  
    <xs:attribute name="OtherKey" type="xs:string" use="optional" />  
    <xs:attribute name="IsForeignKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="Cardinality" type="Cardinality" use="optional" />  
    <xs:attribute name="DeleteRule" type="xs:string" use="optional" />  
    <xs:attribute name="DeleteOnNull" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Function">  
    <xs:sequence>  
      <xs:element name="Parameter" type="Parameter" minOccurs="0" maxOccurs="unbounded" />  
      <xs:choice>  
        <xs:element name="ElementType" type="Type" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Return" type="Return" minOccurs="0" maxOccurs="1" />  
      </xs:choice>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Id" type="xs:ID" use="optional" />  
    <xs:attribute name="Method" type="xs:string" use="optional" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
    <xs:attribute name="Modifier" type="MemberModifier" use="optional" />  
    <xs:attribute name="HasMultipleResults" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsComposable" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="TableFunction">  
    <xs:sequence>  
      <xs:element name="Argument" type="TableFunctionParameter" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="Return" type="TableFunctionReturn" minOccurs="0" maxOccurs="1" />  
    </xs:sequence>  
    <xs:attribute name="FunctionId" type="xs:IDREF" use="required" />  
    <xs:attribute name="AccessModifier" type="AccessModifier" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Parameter">  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="Parameter" type="xs:string" use="optional" />  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="Direction" type="ParameterDirection" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Return">  
    <xs:attribute name="Type" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="TableFunctionParameter">  
    <xs:attribute name="Parameter" type="xs:string" use="required" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Version" type="Version" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="TableFunctionReturn">  
    <xs:attribute name="Member" type="xs:string" use="required" />  
  </xs:complexType>  
  <xs:complexType name="Connection">  
    <xs:attribute name="Provider" type="xs:string" use="required" />  
    <xs:attribute name="Mode" type="ConnectionMode" use="optional" />  
    <xs:attribute name="ConnectionString" type="xs:string" use="optional" />  
    <xs:attribute name="SettingsObjectName" type="xs:string" use="optional" />  
    <xs:attribute name="SettingsPropertyName" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:simpleType name="ConnectionMode">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="ConnectionString" />  
      <xs:enumeration value="AppSettings" />  
      <xs:enumeration value="WebSettings" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="AccessModifier">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Public" />  
      <xs:enumeration value="Internal" />  
      <xs:enumeration value="Protected" />  
      <xs:enumeration value="ProtectedInternal" />  
      <xs:enumeration value="Private" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="UpdateCheck">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="WhenChanged" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="SerializationMode">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="None" />  
      <xs:enumeration value="Unidirectional" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="ParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In" />  
      <xs:enumeration value="Out" />  
      <xs:enumeration value="InOut" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="Version">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Current" />  
      <xs:enumeration value="Original" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="AutoSync">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="OnInsert" />  
      <xs:enumeration value="OnUpdate" />  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Default" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="ClassModifier">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Sealed" />  
      <xs:enumeration value="Abstract" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="MemberModifier">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Virtual" />  
      <xs:enumeration value="Override" />  
      <xs:enumeration value="New" />  
      <xs:enumeration value="NewVirtual" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="Cardinality">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="One" />  
      <xs:enumeration value="Many" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="sample-dbml-file"></a><span data-ttu-id="f1086-121">Örnek DBML dosyası</span><span class="sxs-lookup"><span data-stu-id="f1086-121">Sample DBML File</span></span>  

 <span data-ttu-id="f1086-122">Aşağıdaki kod, Northwind örnek veritabanından oluşturulan DBML dosyasından bir alıntıdır.</span><span class="sxs-lookup"><span data-stu-id="f1086-122">The following code is an excerpt from the DBML file created from the Northwind sample database.</span></span> <span data-ttu-id="f1086-123">Tüm dosyayı SQLMetal 'ı **/XML** seçeneğiyle kullanarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1086-123">You can generate the whole file by using SQLMetal with the **/xml** option.</span></span> <span data-ttu-id="f1086-124">Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="f1086-124">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
<Database Name="northwnd" Class="Northwnd" xmlns="http://schemas.microsoft.com/dsltools/DLinqML">  
  
  <Table Name="Customers">  
    <Type Name="Customer">  
      <Column Name="CustomerID" Type="System.String" DbType="NChar(5) NOT NULL" IsPrimaryKey="True" CanBeNull="False" />  
      <Column Name="CompanyName" Type="System.String" DbType="NVarChar(40) NOT NULL" CanBeNull="False" />  
      <Column Name="ContactName" Type="System.String" DbType="NVarChar(30)" CanBeNull="True" />  
      <Column Name="ContactTitle" Type="System.String" DbType="NVarChar(30)" CanBeNull="True" />  
      <Column Name="Address" Type="System.String" DbType="NVarChar(60)" CanBeNull="True" />  
      <Column Name="City" Type="System.String" DbType="NVarChar(15)" CanBeNull="True" />  
      <Column Name="Region" Type="System.String" DbType="NVarChar(15)" CanBeNull="True" />  
      <Column Name="PostalCode" Type="System.String" DbType="NVarChar(10)" CanBeNull="True" />  
      <Column Name="Country" Type="System.String" DbType="NVarChar(15)" CanBeNull="True" />  
      <Column Name="Phone" Type="System.String" DbType="NVarChar(24)" CanBeNull="True" />  
      <Column Name="Fax" Type="System.String" DbType="NVarChar(24)" CanBeNull="True" />  
      <Association Name="FK_CustomerCustomerDemo_Customers" Member="CustomerCustomerDemos" ThisKey="CustomerID" OtherKey="CustomerID" OtherTable="CustomerCustomerDemo" DeleteRule="NO ACTION" />  
      <Association Name="FK_Orders_Customers" Member="Orders" ThisKey="CustomerID" OtherKey="CustomerID" OtherTable="Orders" DeleteRule="NO ACTION" />  
    </Type>  
  </Table>  
</Database>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1086-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1086-125">See also</span></span>

- [<span data-ttu-id="f1086-126">Arka Plan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="f1086-126">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="f1086-127">Dış Eşleme</span><span class="sxs-lookup"><span data-stu-id="f1086-127">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="f1086-128">Nasıl yapılır: Nesne Modelini Dış Dosya Olarak Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f1086-128">How to: Generate the Object Model as an External File</span></span>](how-to-generate-the-object-model-as-an-external-file.md)
- [<span data-ttu-id="f1086-129">Örnek Veritabanları İndirme</span><span class="sxs-lookup"><span data-stu-id="f1086-129">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="f1086-130">Başvuru</span><span class="sxs-lookup"><span data-stu-id="f1086-130">Reference</span></span>](reference.md)
