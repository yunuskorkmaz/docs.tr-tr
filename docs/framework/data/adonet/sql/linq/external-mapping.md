---
title: "Dış eşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 076606b8-d889-4ba0-b5da-ae577b146f23
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ae67c80e4637281a26b15d7faa2dbdbe7171ba1c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="external-mapping"></a><span data-ttu-id="15a0d-102">Dış eşleme</span><span class="sxs-lookup"><span data-stu-id="15a0d-102">External Mapping</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="15a0d-103">destekleyen *dış eşleme*, bir işlem olarak, ayrı bir XML dosyası veritabanının veri modeli ve nesne modeli arasında eşleme belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="15a0d-103"> supports *external mapping*, a process by which you use a separate XML file to specify mapping between the data model of the database and your object model.</span></span> <span data-ttu-id="15a0d-104">Bir dış eşleme dosyası kullanmanın avantajları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="15a0d-104">Advantages of using an external mapping file include the following:</span></span>  
  
-   <span data-ttu-id="15a0d-105">Eşleme kodunuzu uygulama kodunuz dışında tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15a0d-105">You can keep your mapping code out of your application code.</span></span> <span data-ttu-id="15a0d-106">Bu yaklaşım, uygulama kodunuzda dağınıklığı azaltır.</span><span class="sxs-lookup"><span data-stu-id="15a0d-106">This approach reduces clutter in your application code.</span></span>  
  
-   <span data-ttu-id="15a0d-107">Bir yapılandırma dosyası gibi bir dış eşleme dosyası davranabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15a0d-107">You can treat an external mapping file something like a configuration file.</span></span> <span data-ttu-id="15a0d-108">Örneğin, yalnızca dış eşleme dosyası takas etme ikili dosyaları aktarma sonra uygulamanızın nasıl davranacağını güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15a0d-108">For example, you can update how your application behaves after shipping the binaries by just swapping out the external mapping file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15a0d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="15a0d-109">Requirements</span></span>  
 <span data-ttu-id="15a0d-110">Eşleme dosyasını bir XML dosyası olmalıdır ve dosya karşı doğrulamalısınız bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] şema tanımı (.xsd) dosyası.</span><span class="sxs-lookup"><span data-stu-id="15a0d-110">The mapping file must be an XML file, and the file must validate against a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] schema definition (.xsd) file.</span></span>  
  
 <span data-ttu-id="15a0d-111">Aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="15a0d-111">The following rules apply:</span></span>  
  
-   <span data-ttu-id="15a0d-112">Eşleme dosyasını bir XML dosyası olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="15a0d-112">The mapping file must be an XML file.</span></span>  
  
-   <span data-ttu-id="15a0d-113">XML eşleme dosyası karşı XML şema tanımı dosyası geçerli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="15a0d-113">The XML mapping file must be valid against the XML schema definition file.</span></span> <span data-ttu-id="15a0d-114">Daha fazla bilgi için bkz: [nasıl yapılır: DBML doğrulamak ve dış eşleme dosyaları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="15a0d-114">For more information, see [How to: Validate DBML and External Mapping Files](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
-   <span data-ttu-id="15a0d-115">Dış eşleme öznitelik tabanlı eşleme geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="15a0d-115">External mapping overrides attribute-based mapping.</span></span> <span data-ttu-id="15a0d-116">Diğer bir deyişle, kullandığınızda, bir dış eşleme kaynak oluşturmak için bir <xref:System.Data.Linq.DataContext>, <xref:System.Data.Linq.DataContext> sınıflarında oluşturduğunuz tüm eşleme öznitelikleri yok sayar.</span><span class="sxs-lookup"><span data-stu-id="15a0d-116">In other words, when you use an external mapping source to create a <xref:System.Data.Linq.DataContext>, the <xref:System.Data.Linq.DataContext> ignores all mapping attributes you have created on classes.</span></span> <span data-ttu-id="15a0d-117">Bu davranış sınıfı dış eşleme dosyasında olup olmadığı dahil geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="15a0d-117">This behavior is true whether the class is included in the external mapping file.</span></span>  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="15a0d-118">(öznitelik tabanlı ve dış) iki eşleme yaklaşım karma kullanımını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="15a0d-118"> does not support the hybrid use of the two mapping approaches (attribute-based and external).</span></span>  
  
## <a name="xml-schema-definition-file"></a><span data-ttu-id="15a0d-119">XML şema tanımı dosyası</span><span class="sxs-lookup"><span data-stu-id="15a0d-119">XML Schema Definition File</span></span>  
 <span data-ttu-id="15a0d-120">Dış eşlemesindeki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] karşı aşağıdaki XML şema tanımı geçerli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="15a0d-120">External mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be valid against the following XML schema definition.</span></span>  
  
 <span data-ttu-id="15a0d-121">DBML dosyasını doğrulamak için kullanılan şema tanımı dosyası bu şema tanımı dosyasındaki ayırt etmek.</span><span class="sxs-lookup"><span data-stu-id="15a0d-121">Distinguish this schema definition file from the schema definition file that is used to validate a DBML file.</span></span> <span data-ttu-id="15a0d-122">Daha fazla bilgi için bkz: [LINQ-SQL kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)).</span><span class="sxs-lookup"><span data-stu-id="15a0d-122">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)).</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]<span data-ttu-id="15a0d-123">Kullanıcılar ayrıca bu XSD dosyası XML şemaları iletişim kutusuna "LinqToSqlMapping.xsd" bulur.</span><span class="sxs-lookup"><span data-stu-id="15a0d-123"> users will also find this XSD file in the XML Schemas dialog box as "LinqToSqlMapping.xsd".</span></span> <span data-ttu-id="15a0d-124">Bir dış eşleme dosyasını doğrulamak için bu dosyayı doğru bir şekilde kullanmak için bkz: [nasıl yapılır: DBML doğrulamak ve dış eşleme dosyaları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="15a0d-124">To use this file correctly for validating an external mapping file, see [How to: Validate DBML and External Mapping Files](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
```  
?<?xml version="1.0" encoding="utf-16"?>  
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
  
## <a name="see-also"></a><span data-ttu-id="15a0d-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="15a0d-125">See Also</span></span>  
 [<span data-ttu-id="15a0d-126">LINQ to SQL’de Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="15a0d-126">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="15a0d-127">Başvuru</span><span class="sxs-lookup"><span data-stu-id="15a0d-127">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [<span data-ttu-id="15a0d-128">Nasıl yapılır: Nesne Modelini Dış Dosya Olarak Oluşturma</span><span class="sxs-lookup"><span data-stu-id="15a0d-128">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)
