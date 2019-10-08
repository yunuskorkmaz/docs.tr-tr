---
title: Dış Eşleme
ms.date: 03/30/2017
ms.assetid: 076606b8-d889-4ba0-b5da-ae577b146f23
ms.openlocfilehash: ba5af75ae34b233354fec6e9074f3cc96d924c7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003049"
---
# <a name="external-mapping"></a><span data-ttu-id="7b015-102">Dış Eşleme</span><span class="sxs-lookup"><span data-stu-id="7b015-102">External Mapping</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7b015-103">, veritabanının veri modeliyle nesne modelinize eşleme belirtmek için ayrı bir XML dosyası kullandığınız bir işlem olan *dış eşlemeyi*destekler.</span><span class="sxs-lookup"><span data-stu-id="7b015-103">supports *external mapping*, a process by which you use a separate XML file to specify mapping between the data model of the database and your object model.</span></span> <span data-ttu-id="7b015-104">Dış eşleme dosyası kullanmanın avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7b015-104">Advantages of using an external mapping file include the following:</span></span>  
  
- <span data-ttu-id="7b015-105">Eşleme kodunuzu uygulama kodunuzun dışında tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b015-105">You can keep your mapping code out of your application code.</span></span> <span data-ttu-id="7b015-106">Bu yaklaşım, uygulama kodunuzda dağınıklığı azaltır.</span><span class="sxs-lookup"><span data-stu-id="7b015-106">This approach reduces clutter in your application code.</span></span>  
  
- <span data-ttu-id="7b015-107">Bir dış eşleme dosyasını bir yapılandırma dosyası gibi bir şekilde kabul edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b015-107">You can treat an external mapping file something like a configuration file.</span></span> <span data-ttu-id="7b015-108">Örneğin, ikili dosyaları gönderdikten sonra, dış eşleme dosyasını değiştirerek uygulamanızın davranışını güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b015-108">For example, you can update how your application behaves after shipping the binaries by just swapping out the external mapping file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b015-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b015-109">Requirements</span></span>  
 <span data-ttu-id="7b015-110">Eşleme dosyası bir XML dosyası olmalıdır ve dosya [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] şema tanımı (. xsd) dosyasına göre doğrulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b015-110">The mapping file must be an XML file, and the file must validate against a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] schema definition (.xsd) file.</span></span>  
  
 <span data-ttu-id="7b015-111">Aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="7b015-111">The following rules apply:</span></span>  
  
- <span data-ttu-id="7b015-112">Eşleme dosyası bir XML dosyası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b015-112">The mapping file must be an XML file.</span></span>  
  
- <span data-ttu-id="7b015-113">XML eşleme dosyası XML şema tanımı dosyasında geçerli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b015-113">The XML mapping file must be valid against the XML schema definition file.</span></span> <span data-ttu-id="7b015-114">Daha fazla bilgi için bkz. [nasıl yapılır: DBML ve dış eşleme dosyalarını doğrulama](how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="7b015-114">For more information, see [How to: Validate DBML and External Mapping Files](how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
- <span data-ttu-id="7b015-115">Dış eşleme, öznitelik tabanlı eşlemeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="7b015-115">External mapping overrides attribute-based mapping.</span></span> <span data-ttu-id="7b015-116">Diğer bir deyişle, bir <xref:System.Data.Linq.DataContext> oluşturmak için bir dış eşleme kaynağı kullandığınızda, <xref:System.Data.Linq.DataContext>, sınıflarda oluşturduğunuz tüm eşleme özniteliklerini yoksayar.</span><span class="sxs-lookup"><span data-stu-id="7b015-116">In other words, when you use an external mapping source to create a <xref:System.Data.Linq.DataContext>, the <xref:System.Data.Linq.DataContext> ignores all mapping attributes you have created on classes.</span></span> <span data-ttu-id="7b015-117">Bu davranış, sınıfın dış eşleme dosyasına dahil edilip edilmemesinin doğru olması durumunda geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7b015-117">This behavior is true whether the class is included in the external mapping file.</span></span>  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="7b015-118">iki eşleme yaklaşımının karma kullanımını desteklemez (öznitelik tabanlı ve harici).</span><span class="sxs-lookup"><span data-stu-id="7b015-118">does not support the hybrid use of the two mapping approaches (attribute-based and external).</span></span>  
  
## <a name="xml-schema-definition-file"></a><span data-ttu-id="7b015-119">XML şema tanımı dosyası</span><span class="sxs-lookup"><span data-stu-id="7b015-119">XML Schema Definition File</span></span>  
 <span data-ttu-id="7b015-120">@No__t-0 ' daki dış eşleme, aşağıdaki XML şema tanımına karşı geçerli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7b015-120">External mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be valid against the following XML schema definition.</span></span>  
  
 <span data-ttu-id="7b015-121">Bu şema tanımı dosyasını bir DBML dosyasını doğrulamak için kullanılan şema tanım dosyasından ayırt edin.</span><span class="sxs-lookup"><span data-stu-id="7b015-121">Distinguish this schema definition file from the schema definition file that is used to validate a DBML file.</span></span> <span data-ttu-id="7b015-122">Daha fazla bilgi için bkz. [LINQ to SQL 'de kod oluşturma](code-generation-in-linq-to-sql.md)).</span><span class="sxs-lookup"><span data-stu-id="7b015-122">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b015-123">Visual Studio kullanıcıları Ayrıca bu XSD dosyasını XML şemaları iletişim kutusunda "LinqToSqlMapping. xsd" olarak bulur.</span><span class="sxs-lookup"><span data-stu-id="7b015-123">Visual Studio users will also find this XSD file in the XML Schemas dialog box as "LinqToSqlMapping.xsd".</span></span> <span data-ttu-id="7b015-124">Bir dış eşleme dosyasını doğrulamak için bu dosyayı doğru şekilde kullanmak için bkz. [nasıl yapılır: DBML ve dış eşleme dosyalarını doğrulama](how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="7b015-124">To use this file correctly for validating an external mapping file, see [How to: Validate DBML and External Mapping Files](how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://schemas.microsoft.com/linqtosql/mapping/2007" xmlns="http://schemas.microsoft.com/linqtosql/mapping/2007"  
elementFormDefault="qualified" >  
  <xs:element name="Database" type="Database" />  
  <xs:complexType name="Database">  
    <xs:sequence>  
      <xs:element name="Table" type="Table" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="Function" type="Function" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Provider" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Table">  
    <xs:sequence>  
      <xs:element name="Type" type="Type" minOccurs="1" maxOccurs="1" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Type">  
    <xs:sequence>  
      <xs:choice minOccurs="0" maxOccurs="unbounded">  
        <xs:element name="Column" type="Column" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Association" type="Association" minOccurs="0" maxOccurs="unbounded" />  
      </xs:choice>  
      <xs:element name="Type" type="Type" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="InheritanceCode" type="xs:string" use="optional" />  
    <xs:attribute name="IsInheritanceDefault" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Column">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="IsPrimaryKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsDbGenerated" type="xs:boolean" use="optional" />  
    <xs:attribute name="CanBeNull" type="xs:boolean" use="optional" />  
    <xs:attribute name="UpdateCheck" type="UpdateCheck" use="optional" />  
    <xs:attribute name="IsDiscriminator" type="xs:boolean" use="optional" />  
    <xs:attribute name="Expression" type="xs:string" use="optional" />  
    <xs:attribute name="IsVersion" type="xs:boolean" use="optional" />  
    <xs:attribute name="AutoSync" type="AutoSync" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Association">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="ThisKey" type="xs:string" use="optional" />  
    <xs:attribute name="OtherKey" type="xs:string" use="optional" />  
    <xs:attribute name="IsForeignKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsUnique" type="xs:boolean" use="optional" />  
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
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Method" type="xs:string" use="required" />  
    <xs:attribute name="IsComposable" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Parameter">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Parameter" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="Direction" type="ParameterDirection" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Return">  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:simpleType name="UpdateCheck">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="WhenChanged" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="ParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In" />  
      <xs:enumeration value="Out" />  
      <xs:enumeration value="InOut" />  
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
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b015-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b015-125">See also</span></span>

- [<span data-ttu-id="7b015-126">LINQ to SQL’de Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7b015-126">Code Generation in LINQ to SQL</span></span>](code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="7b015-127">Başvuru</span><span class="sxs-lookup"><span data-stu-id="7b015-127">Reference</span></span>](reference.md)
- [<span data-ttu-id="7b015-128">Nasıl yapılır: Nesne Modelini Dış Dosya Olarak Oluşturma</span><span class="sxs-lookup"><span data-stu-id="7b015-128">How to: Generate the Object Model as an External File</span></span>](how-to-generate-the-object-model-as-an-external-file.md)
