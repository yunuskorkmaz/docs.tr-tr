---
title: Dış Eşleme
ms.date: 03/30/2017
ms.assetid: 076606b8-d889-4ba0-b5da-ae577b146f23
ms.openlocfilehash: 39cdd7b23bd90ff8938dda9eee630149ce6ddbea
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793992"
---
# <a name="external-mapping"></a>Dış Eşleme
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], veritabanının veri modeliyle nesne modelinize eşleme belirtmek için ayrı bir XML dosyası kullandığınız bir işlem olan *dış eşlemeyi*destekler. Dış eşleme dosyası kullanmanın avantajları şunlardır:  
  
- Eşleme kodunuzu uygulama kodunuzun dışında tutabilirsiniz. Bu yaklaşım, uygulama kodunuzda dağınıklığı azaltır.  
  
- Bir dış eşleme dosyasını bir yapılandırma dosyası gibi bir şekilde kabul edebilirsiniz. Örneğin, ikili dosyaları gönderdikten sonra, dış eşleme dosyasını değiştirerek uygulamanızın davranışını güncelleştirebilirsiniz.  
  
## <a name="requirements"></a>Gereksinimler  
 Eşleme dosyası bir XML dosyası olmalıdır ve dosyanın bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] şema tanımı (. xsd) dosyası ile doğrulanması gerekir.  
  
 Aşağıdaki kurallar geçerlidir:  
  
- Eşleme dosyası bir XML dosyası olmalıdır.  
  
- XML eşleme dosyası XML şema tanımı dosyasında geçerli olmalıdır. Daha fazla bilgi için [nasıl yapılır: DBML ve dış eşleme dosyalarını](how-to-validate-dbml-and-external-mapping-files.md)doğrulayın.  
  
- Dış eşleme, öznitelik tabanlı eşlemeyi geçersiz kılar. Diğer bir deyişle, oluşturmak için bir <xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.DataContext> dış eşleme kaynağı kullandığınızda sınıflarda oluşturduğunuz tüm eşleme özniteliklerini yoksayar. Bu davranış, sınıfın dış eşleme dosyasına dahil edilip edilmemesinin doğru olması durumunda geçerlidir.  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]iki eşleme yaklaşımının karma kullanımını desteklemez (öznitelik tabanlı ve harici).  
  
## <a name="xml-schema-definition-file"></a>XML şema tanımı dosyası  
 ' Deki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dış eşleme, aşağıdaki XML şema tanımına karşı geçerli olmalıdır.  
  
 Bu şema tanımı dosyasını bir DBML dosyasını doğrulamak için kullanılan şema tanım dosyasından ayırt edin. Daha fazla bilgi için bkz. [LINQ to SQL 'de kod oluşturma](code-generation-in-linq-to-sql.md)).  
  
> [!NOTE]
> Visual Studio kullanıcıları Ayrıca bu XSD dosyasını XML şemaları iletişim kutusunda "LinqToSqlMapping. xsd" olarak bulur. Bir dış eşleme dosyasını doğrulamak için bu dosyayı doğru şekilde kullanmak için bkz [. nasıl yapılır: DBML ve dış eşleme dosyalarını](how-to-validate-dbml-and-external-mapping-files.md)doğrulayın.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to SQL’de Kod Oluşturma](code-generation-in-linq-to-sql.md)
- [Başvuru](reference.md)
- [Nasıl yapılır: Nesne modelini dış dosya olarak oluşturma](how-to-generate-the-object-model-as-an-external-file.md)
