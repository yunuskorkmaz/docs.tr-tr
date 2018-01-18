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
# <a name="external-mapping"></a>Dış eşleme
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]destekleyen *dış eşleme*, bir işlem olarak, ayrı bir XML dosyası veritabanının veri modeli ve nesne modeli arasında eşleme belirtmek için kullanın. Bir dış eşleme dosyası kullanmanın avantajları şunlardır:  
  
-   Eşleme kodunuzu uygulama kodunuz dışında tutabilirsiniz. Bu yaklaşım, uygulama kodunuzda dağınıklığı azaltır.  
  
-   Bir yapılandırma dosyası gibi bir dış eşleme dosyası davranabilirsiniz. Örneğin, yalnızca dış eşleme dosyası takas etme ikili dosyaları aktarma sonra uygulamanızın nasıl davranacağını güncelleştirebilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 Eşleme dosyasını bir XML dosyası olmalıdır ve dosya karşı doğrulamalısınız bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] şema tanımı (.xsd) dosyası.  
  
 Aşağıdaki kurallar geçerlidir:  
  
-   Eşleme dosyasını bir XML dosyası olmalıdır.  
  
-   XML eşleme dosyası karşı XML şema tanımı dosyası geçerli olmalıdır. Daha fazla bilgi için bkz: [nasıl yapılır: DBML doğrulamak ve dış eşleme dosyaları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).  
  
-   Dış eşleme öznitelik tabanlı eşleme geçersiz kılar. Diğer bir deyişle, kullandığınızda, bir dış eşleme kaynak oluşturmak için bir <xref:System.Data.Linq.DataContext>, <xref:System.Data.Linq.DataContext> sınıflarında oluşturduğunuz tüm eşleme öznitelikleri yok sayar. Bu davranış sınıfı dış eşleme dosyasında olup olmadığı dahil geçerlidir.  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)](öznitelik tabanlı ve dış) iki eşleme yaklaşım karma kullanımını desteklemez.  
  
## <a name="xml-schema-definition-file"></a>XML şema tanımı dosyası  
 Dış eşlemesindeki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] karşı aşağıdaki XML şema tanımı geçerli olmalıdır.  
  
 DBML dosyasını doğrulamak için kullanılan şema tanımı dosyası bu şema tanımı dosyasındaki ayırt etmek. Daha fazla bilgi için bkz: [LINQ-SQL kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)).  
  
> [!NOTE]
>  [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]Kullanıcılar ayrıca bu XSD dosyası XML şemaları iletişim kutusuna "LinqToSqlMapping.xsd" bulur. Bir dış eşleme dosyasını doğrulamak için bu dosyayı doğru bir şekilde kullanmak için bkz: [nasıl yapılır: DBML doğrulamak ve dış eşleme dosyaları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ to SQL’de Kod Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [Nasıl yapılır: Nesne Modelini Dış Dosya Olarak Oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)
