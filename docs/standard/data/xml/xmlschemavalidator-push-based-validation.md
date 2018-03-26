---
title: XmlSchemaValidator gönderim tabanlı doğrulama
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
caps.latest.revision: ''
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 60c2effea612a579b4c66b7c30243b785b86a263
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="xmlschemavalidator-push-based-validation"></a>XmlSchemaValidator gönderim tabanlı doğrulama
<xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı bir gönderim tabanlı şekilde XML şemaları karşı XML verileri doğrulamak için verimli, yüksek performanslı bir mekanizma sağlar. Örneğin, <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı bir XML belgesi olarak serileştirir ve bir doğrulama XML okuyucusu kullanarak belgeyi yeniden ayrıştırma zorunda kalmadan bir XML bilgi yerinde doğrulamanıza olanak verir.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı, doğrulama altyapılarını özel XML veri kaynaklarını üzerinden veya doğrulama XML yazıcısı oluşturmak için bir yol olarak oluşturma gibi gelişmiş senaryolarda kullanılabilir.  
  
 Kullanarak bir örnek verilmiştir <xref:System.Xml.Schema.XmlSchemaValidator> doğrulamak için sınıf `contosoBooks.xml` karşı dosya `contosoBooks.xsd` şema. Örnek kullanır <xref:System.Xml.Serialization.XmlSerializer> seri durumdan çıkarılacak sınıfı `contosoBooks.xml` dosya ve düğümlerin değerini yöntemlere <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı.  
  
> [!NOTE]
>  Bu örnekte, bu konunun bölümleri kullanılır.  
  
 [!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
 [!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]  
  
 Örnek alır `contosoBooks.xml` dosya giriş olarak.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Bu örnek ayrıca alır `contosoBooks.xsd` bir girdi olarak.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" targetNamespace="http://www.contoso.com/books" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name="bookstore">  
        <xs:complexType>  
            <xs:sequence>  
                <xs:element maxOccurs="unbounded" name="book">  
                    <xs:complexType>  
                        <xs:sequence>  
                            <xs:element name="title" type="xs:string" />  
                            <xs:element name="author">  
                                <xs:complexType>  
                                    <xs:sequence>  
                                        <xs:element minOccurs="0" name="name" type="xs:string" />  
                                        <xs:element minOccurs="0" name="first-name" type="xs:string" />  
                                        <xs:element minOccurs="0" name="last-name" type="xs:string" />  
                                    </xs:sequence>  
                                </xs:complexType>  
                            </xs:element>  
                            <xs:element name="price" type="xs:decimal" />  
                        </xs:sequence>  
                        <xs:attribute name="genre" type="xs:string" use="required" />  
                        <xs:attribute name="publicationdate" type="xs:date" use="required" />  
                        <xs:attribute name="ISBN" type="xs:string" use="required" />  
                    </xs:complexType>  
                </xs:element>  
            </xs:sequence>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="validating-xml-data-using-xmlschemavalidator"></a>XML XmlSchemaValidator kullanarak verileri doğrulama  
 Bir XML bilgi doğrulama başlamak için önce yeni bir örneğini başlatmalıdır <xref:System.Xml.Schema.XmlSchemaValidator> kullanarak sınıfı <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Oluşturucusu.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Oluşturucusu alır <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, ve <xref:System.Xml.XmlNamespaceManager> parametre olarak nesneleri yanı sıra bir <xref:System.Xml.Schema.XmlSchemaValidationFlags> bir parametre değeri. <xref:System.Xml.XmlNameTable> Nesne Şema ad alanını, XML ad alanı vb. gibi bilinen ad alanı dizeleri küçük parçalara ayrılamıyor için kullanılır ve geçirilir <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> basit içerik doğrulanırken yöntemi. <xref:System.Xml.Schema.XmlSchemaSet> Nesne XML bilgi doğrulamak için kullanılan XML şemaları içerir. <xref:System.Xml.XmlNamespaceManager> Nesnesi, doğrulama sırasında karşılaşılan ad alanları çözmek için kullanılır. <xref:System.Xml.Schema.XmlSchemaValidationFlags> Doğrulama belirli özelliklerini devre dışı bırakmak için kullanılır.  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> oluşturucusu, bkz: <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.  
  
### <a name="initializing-validation"></a>Doğrulama başlatılıyor  
 Sonra bir <xref:System.Xml.Schema.XmlSchemaValidator> nesne oluşturulan, var olan iki aşırı <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> durumunu başlatmak için kullanılan yöntemleri <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi. Aşağıdaki iki olan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemleri.  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
 Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yöntemi başlatır bir <xref:System.Xml.Schema.XmlSchemaValidator> başlangıç durumuna ve aşırı yüklenmiş nesnesine <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yönteminin alan bir <xref:System.Xml.Schema.XmlSchemaObject> bir parametre başlatır gibi bir <xref:System.Xml.Schema.XmlSchemaValidator> kısmi için başlangıç durumuna nesnesi doğrulama.  
  
 Her ikisi de <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemleri yalnızca çağırılabilir hemen sonra bir <xref:System.Xml.Schema.XmlSchemaValidator> nesne oluşturulan veya çağrı sonra <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.  
  
 Bir örnek için <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yöntemi, giriş örneğe bakın. Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi, bkz: <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.  
  
#### <a name="partial-validation"></a>Kısmi doğrulama  
 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Yönteminin alan bir <xref:System.Xml.Schema.XmlSchemaObject> bir parametre başlatır gibi bir <xref:System.Xml.Schema.XmlSchemaValidator> kısmi doğrulama için başlangıç durumuna nesnesi.  
  
 Aşağıdaki örnekte, bir <xref:System.Xml.Schema.XmlSchemaObject> kısmi doğrulama kullanmak için başlatılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yöntemi. `orderNumber` Schema öğesi şema öğesi tarafından seçerek geçirilir <xref:System.Xml.XmlQualifiedName> içinde <xref:System.Xml.Schema.XmlSchemaObjectTable> tarafından döndürülen koleksiyon <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet> nesnesi. <xref:System.Xml.Schema.XmlSchemaValidator> Nesneyi sonra bu belirli öğe doğrular.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add(Nothing, "schema.xsd")  
schemaSet.Compile()  
Dim nameTable As NameTable = New NameTable()  
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(nameTable)  
  
Dim validator As XmlSchemaValidator = New XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None)  
validator.Initialize(schemaSet.GlobalElements.Item(New XmlQualifiedName("orderNumber")))  
  
validator.ValidateElement("orderNumber", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
validator.ValidateText("123")  
validator.ValidateEndElement(Nothing)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add(null, "schema.xsd");  
schemaSet.Compile();  
NameTable nameTable = new NameTable();  
XmlNamespaceManager manager = new XmlNamespaceManager(nameTable);  
  
XmlSchemaValidator validator = new XmlSchemaValidator(nameTable, schemaSet, manager, XmlSchemaValidationFlags.None);  
validator.Initialize(schemaSet.GlobalElements[new XmlQualifiedName("orderNumber")]);  
  
validator.ValidateElement("orderNumber", "", null);  
validator.ValidateEndOfAttributes(null);  
validator.ValidateText("123");  
validator.ValidateEndElement(null);  
```  
  
 Örneğin, aşağıdaki XML Şeması girdi olarak alır.  
  
 `<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">`  
  
 `<xs:element name="orderNumber" type="xs:int" />`  
  
 `</xs:schema>`  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi, bkz: <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.  
  
### <a name="adding-additional-schemas"></a>Ek şemaları ekleme  
 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Yöntemi <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı, bir XML Şeması doğrulama sırasında kullanılan şema kümesine eklemek için kullanılır. <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Yöntemi, bir satır içi XML Şeması Doğrulanmakta olan XML bilgi içinde karşılaşmadan etkisini benzetimini yapmak için kullanılabilir.  
  
> [!NOTE]
>  Hedef ad alanı <xref:System.Xml.Schema.XmlSchema> parametresi, herhangi bir öğe veya öznitelik tarafından zaten karşılaşılan eşleşemez <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi.  
>   
>  Varsa <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> değer için bir parametre olarak değil geçildi <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> oluşturucusu, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemi hiçbir şey yapmaz.  
  
 Sonucu <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Doğrulanmakta olan geçerli XML düğümünde içerik bağımlı bir yöntemdir. Doğrulama bağlamları hakkında daha fazla bilgi için bu konunun "Doğrulama bağlamını" bölümüne bakın.  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemi, bkz: <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.  
  
### <a name="validating-elements-attributes-and-content"></a>Öğeleri, öznitelikleri ve içerik doğrulama  
 <xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı öğeleri, öznitelikleri ve XML şemaları karşı bir XML bilgi içeriği doğrulamak için kullanılan birkaç yöntem sağlar. Aşağıdaki tabloda bu yöntemlerin her biri açıklanmaktadır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Öğe adı geçerli bağlamda doğrular.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Öznitelik geçerli öğe içeriğinde veya karşı doğrular <xref:System.Xml.Schema.XmlSchemaAttribute> nesne için bir parametre olarak geçirilen <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|Tüm gerekli öznitelikler öğesi bağlamında döndürülüp döndürülmeyeceğini doğrular ve hazırlar <xref:System.Xml.Schema.XmlSchemaValidator> öğesinin alt içeriği doğrulamak için nesne.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Metin geçerli öğenin bağlamında izin verilir ve geçerli öğe basit içeriğe sahipse doğrulama için metin öğelerden olup olmadığını doğrular.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Boşluk geçerli öğenin bağlamında izin verilir ve geçerli öğe basit içerik olup olmadığını doğrulama için beyaz alan öğelerden olup olmadığını doğrular.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|Öğenin metin içeriğini basit içeriğe sahip öğeler için veri türüne göre geçerli olup olmadığını doğrular ve geçerli öğenin içeriği ile karmaşık içerik öğeleri için tam olup olmadığını doğrular.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Geçerli öğe içeriği doğrulama atlar ve hazırlar <xref:System.Xml.Schema.XmlSchemaValidator> üst öğenin bağlamında içeriği doğrulamak için nesne.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Doğrulama sona erer ve tüm XML belgesi kimlik kısıtlamalarını denetler <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> doğrulama seçeneği ayarlanmış.|  
  
> [!NOTE]
>  <xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı dizisi ve yukarıdaki tabloda açıklanan yöntemlerin her biri için yapılan çağrılar oluşumunu zorlayan bir tanımlanan durum geçişi sahiptir. Özel durum geçişini <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı bu konunun "XmlSchemaValidator durum geçişi" bölümünde açıklanmıştır.  
  
 Önceki bölümdeki örnek örneği öğeleri, öznitelikleri ve bir XML bilgi içeriği doğrulamak için kullanılan yöntemler için bkz. Bu yöntemler hakkında daha fazla bilgi için bkz: <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.  
  
#### <a name="validating-content-using-an-xmlvaluegetter"></a>Bir XmlValueGetter kullanarak içerik doğrulama  
 <xref:System.Xml.Schema.XmlValueGetter> `delegate` Özniteliği, metin ya da boşluk düğümleri değerini ortak dil çalışma zamanı (CLR) türleri olarak özniteliği, metin veya boşluk düğümünün XML Şeması Tanım Dili (XSD) türüyle uyumlu geçirmek için kullanılan. Bir <xref:System.Xml.Schema.XmlValueGetter> `delegate` özniteliği, metin ya da boşluk düğümü CLR değeri zaten varsa ve kendisine dönüştürme maliyetini ortadan kaldırır, yararlıdır bir `string` ve sonra bunu yeniden doğrulama için yeniden ayrıştırmayı.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, Ve <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> yöntemlerini aşırı yüklü ve öznitelik, metin ya da boşluk düğümleri olarak değerini kabul bir `string` veya <xref:System.Xml.Schema.XmlValueGetter> `delegate`.  
  
 Aşağıdaki yöntemlerden birini <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı kabul bir <xref:System.Xml.Schema.XmlValueGetter> `delegate` bir parametre olarak.  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>  
  
 Aşağıda bir örnek verilmiştir <xref:System.Xml.Schema.XmlValueGetter> `delegate` alınan <xref:System.Xml.Schema.XmlSchemaValidator> giriş sınıfı örneği. <xref:System.Xml.Schema.XmlValueGetter> `delegate` Özniteliğin değerini döndüren bir <xref:System.DateTime> nesnesi. Bunu doğrulamak için <xref:System.DateTime> tarafından döndürülen nesne <xref:System.Xml.Schema.XmlValueGetter>, <xref:System.Xml.Schema.XmlSchemaValidator> nesnesini ilk ValueType onu dönüştürür (XSD türü için varsayılan CLR eşleme ValueType'dir) veri türü özniteliği ve ardından dönüştürülen üzerinde denetimleri modelleri için değer.  
  
```vb  
Shared dateTimeGetterContent As Object  
  
Shared Function dateTimeGetterHandle() As Object  
    Return dateTimeGetterContent  
End Function  
  
Shared Function dateTimeGetter(ByVal dateTime As DateTime) As XmlValueGetter  
    dateTimeGetterContent = dateTime  
    Return New XmlValueGetter(AddressOf dateTimeGetterHandle)  
End Function  
```  
  
```csharp  
static object dateTimeGetterContent;  
  
static object dateTimeGetterHandle()  
{  
    return dateTimeGetterContent;  
}  
  
static XmlValueGetter dateTimeGetter(DateTime dateTime)  
{  
    dateTimeGetterContent = dateTime;  
    return new XmlValueGetter(dateTimeGetterHandle);  
}  
```  
  
 Tam bir örnek için <xref:System.Xml.Schema.XmlValueGetter> `delegate`, giriş örneğe bakın. Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlValueGetter> `delegate`, bkz: <xref:System.Xml.Schema.XmlValueGetter>, ve <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.  
  
#### <a name="post-schema-validation-information"></a>Sonrası-Schema-doğrulama-bilgileri  
 <xref:System.Xml.Schema.XmlSchemaInfo> Sınıfı, bazı sonrası-Schema-doğrulama-bilgiler doğrulayan bir XML düğümü temsil eder <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı. Çeşitli yöntemleri <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı kabul bir <xref:System.Xml.Schema.XmlSchemaInfo> nesnesi bir isteğe bağlı olarak (`null`) `out` parametresi.  
  
 Doğrulama başarılı, özelliklerini üzerine <xref:System.Xml.Schema.XmlSchemaInfo> nesne doğrulama sonuçlarını ayarlanır. Özniteliğini kullanarak, örneğin, doğrulama başarılı bağlı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntemi, <xref:System.Xml.Schema.XmlSchemaInfo> nesne kullanıcının (belirtilmişse) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, ve <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> özelliklerini doğrulama sonuçlarını ayarlama .  
  
 Aşağıdaki <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı yöntemleri kabul bir <xref:System.Xml.Schema.XmlSchemaInfo> nesnesi out parametresi olarak.  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>  
  
 Tam bir örnek için <xref:System.Xml.Schema.XmlSchemaInfo> sınıfı, giriş örneğe bakın. Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaInfo> sınıfı için bkz: <xref:System.Xml.Schema.XmlSchemaInfo> sınıf başvurusu belgelerinde.  
  
### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a>Beklenen Parçacık, öznitelikleri ve belirtilmeyen varsayılan öznitelikleri alma  
 <xref:System.Xml.Schema.XmlSchemaValidator> SAX <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, ve <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> beklenen Parçacık, öznitelikleri ve geçerli doğrulama bağlamını belirtilmeyen varsayılan öznitelikleri almak için yöntemleri.  
  
#### <a name="retrieving-expected-particles"></a>Beklenen parçacık alınıyor  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemi bir dizi döndürür <xref:System.Xml.Schema.XmlSchemaParticle> geçerli öğe bağlamda beklenen parçacık içeren nesne. Tarafından döndürülen geçerli parçacık <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi örnekleridir <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAny> sınıfları.  
  
 İçerik modeli oluşturucuya olduğunda bir `xs:sequence`, yalnızca ileri parçacığın dizisi döndürülür. Oluşturucuya içerik modeli için ise bir `xs:all` veya bir `xs:choice`, geçerli öğenin bağlamında izleyen tüm geçerli parçacık döndürülen sonra.  
  
> [!NOTE]
>  Varsa <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi çağrıldıktan sonra hemen çağrılır <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi tüm genel öğeleri döndürür.  
  
 Örneğin, XML Şeması Tanım Dili (XSD) doğrulama sonra bu izleme, şema ve XML belge `book` öğesi, `book` geçerli öğe bağlamı bir öğedir. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemi tek bir içeren bir dizi döndürür <xref:System.Xml.Schema.XmlSchemaElement> nesnesini temsil eden `title` öğesi. Doğrulama bağlamını olduğunda `title` öğesi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntem boş bir dizi döndürür. Varsa <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi çağrıldıktan sonra `title` öğesi doğrulanmış önce `description` öğesi doğrulanmış, tek bir içeren bir dizi döndürür <xref:System.Xml.Schema.XmlSchemaElement> nesnesini temsil eden `description` öğesi. Varsa <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi çağrıldıktan sonra `description` öğesi doğrulanmış sonra tek bir içeren bir dizi döndürür <xref:System.Xml.Schema.XmlSchemaAny> joker karakteri temsil eden nesne.  
  
```vb  
Dim reader As XmlReader =  XmlReader.Create("input.xml")   
  
Dim schemaSet As XmlSchemaSet =  New XmlSchemaSet()   
schemaSet.Add(Nothing, "schema.xsd")  
Dim manager As XmlNamespaceManager =  New XmlNamespaceManager(reader.NameTable)   
  
Dim validator As XmlSchemaValidator =  New XmlSchemaValidator(reader.NameTable,schemaSet,manager,XmlSchemaValidationFlags.None)  
validator.Initialize()  
  
validator.ValidateElement("book", "", Nothing)  
  
validator.ValidateEndOfAttributes(Nothing)  
For Each element As XmlSchemaElement In validator.GetExpectedParticles()  
    Console.WriteLine(element.Name)  
Next  
  
validator.ValidateElement("title", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
For Each element As XmlSchemaElement In validator.GetExpectedParticles()  
    Console.WriteLine(element.Name)  
Next  
validator.ValidateEndElement(Nothing)  
  
For Each element As XmlSchemaElement In validator.GetExpectedParticles()  
    Console.WriteLine(element.Name)  
Next  
  
validator.ValidateElement("description", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
validator.ValidateEndElement(Nothing)  
  
For Each particle As XmlSchemaParticle In validator.GetExpectedParticles()  
    Console.WriteLine(particle.GetType())  
Next  
  
validator.ValidateElement("namespace", "", Nothing)  
validator.ValidateEndOfAttributes(Nothing)  
validator.ValidateEndElement(Nothing)  
  
validator.ValidateEndElement(Nothing)  
```  
  
```csharp  
XmlReader reader = XmlReader.Create("input.xml");  
  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add(null, "schema.xsd");  
XmlNamespaceManager manager = new XmlNamespaceManager(reader.NameTable);  
  
XmlSchemaValidator validator = new XmlSchemaValidator(reader.NameTable, schemaSet, manager, XmlSchemaValidationFlags.None);  
validator.Initialize();  
  
validator.ValidateElement("book", "", null);  
  
validator.ValidateEndOfAttributes(null);  
foreach (XmlSchemaElement element in validator.GetExpectedParticles())  
{  
    Console.WriteLine(element.Name);  
}  
  
validator.ValidateElement("title", "", null);  
validator.ValidateEndOfAttributes(null);  
foreach (XmlSchemaElement element in validator.GetExpectedParticles())  
{  
    Console.WriteLine(element.Name);  
}  
validator.ValidateEndElement(null);  
  
foreach (XmlSchemaElement element in validator.GetExpectedParticles())  
{  
    Console.WriteLine(element.Name);  
}  
  
validator.ValidateElement("description", "", null);  
validator.ValidateEndOfAttributes(null);  
validator.ValidateEndElement(null);  
  
foreach (XmlSchemaParticle particle in validator.GetExpectedParticles())  
{  
    Console.WriteLine(particle.GetType());  
}  
  
validator.ValidateElement("namespace", "", null);  
validator.ValidateEndOfAttributes(null);  
validator.ValidateEndElement(null);  
  
validator.ValidateEndElement(null);  
```  
  
 Örneğin, aşağıdaki XML girdi olarak alır.  
  
 `<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">`  
  
 `<xs:element name="book">`  
  
 `<xs:sequence>`  
  
 `<xs:element name="title" type="xs:string" />`  
  
 `<xs:element name="description" type="xs:string" />`  
  
 `<xs:any processContent="lax" maxOccurs="unbounded" />`  
  
 `</xs:sequence>`  
  
 `</xs:element>`  
  
 `</xs:schema>`  
  
 Örneğin aşağıdaki XSD şema girdi olarak alır.  
  
 `<book>`  
  
 `<title>My Book</title>`  
  
 `<description>My Book's Description</description>`  
  
 `<namespace>System.Xml.Schema</namespace>`  
  
 `</book>`  
  
> [!NOTE]
>  Sonuçlarını <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı Doğrulanmakta olan geçerli bağlamda bağımlı. Daha fazla bilgi için bu konunun "Doğrulama bağlamını" bölümüne bakın.  
  
 Bir örnek için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi, giriş örneğe bakın. Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi, bkz: <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.  
  
#### <a name="retrieving-expected-attributes"></a>Beklenen öznitelikleri alma  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Yöntemi bir dizi döndürür <xref:System.Xml.Schema.XmlSchemaAttribute> geçerli öğe bağlamda beklenen öznitelikleri içeren nesne.  
  
 Örneğin, giriş örnekte <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi, tüm öznitelikleri almak için kullanılan `book` öğesi.  
  
 Çağırırsanız <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi hemen sonra <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> yöntemi, XML belgesinde görünebilir tüm öznitelikleri döndürülür. Ancak, çağırırsanız <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi için bir veya daha fazla çağrıları sonra <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntemi, henüz geçerli öğe için doğrulandı değil öznitelikleri döndürülür.  
  
> [!NOTE]
>  Sonuçlarını <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı Doğrulanmakta olan geçerli bağlamda bağımlı. Daha fazla bilgi için bu konunun "Doğrulama bağlamını" bölümüne bakın.  
  
 Bir örnek için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi, giriş örneğe bakın. Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi, bkz: <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.  
  
#### <a name="retrieving-unspecified-default-attributes"></a>Belirtilmeyen varsayılan öznitelikleri alma  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Yöntemi doldurur <xref:System.Collections.ArrayList> ile belirtilen <xref:System.Xml.Schema.XmlSchemaAttribute> nesneler için varsayılan değerlerle daha önce kullanılarak doğrulandı değil tüm öznitelikleri <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> öğesi bağlamında yöntemi. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Yöntemi çağrıldıktan sonra çağrılabilir <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> her özniteliği öğesi bağlamında yöntemi. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Yöntemi, varsayılan öznitelikleri Doğrulanmakta olan XML belgesine eklenecek olduğunu belirlemek için kullanılmalıdır.  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> yöntemi, bkz: <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.  
  
### <a name="handling-schema-validation-events"></a>Şema doğrulama olayları işleme  
 Şema doğrulama uyarıları ve doğrulama sırasında oluşan hatalar tarafından işlenmesini <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> olayı <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı.  
  
 Şema doğrulama uyarıları olan bir <xref:System.Xml.Schema.XmlSeverityType> değerini <xref:System.Xml.Schema.XmlSeverityType.Warning> ve şema doğrulama hatalarıyla sahip bir <xref:System.Xml.Schema.XmlSeverityType> değerini <xref:System.Xml.Schema.XmlSeverityType.Error>. Öyle değilse <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> atanmış olan, bir <xref:System.Xml.Schema.XmlSchemaValidationException> tüm şema doğrulama hatalarıyla için oluşturulan bir <xref:System.Xml.Schema.XmlSeverityType> değerini <xref:System.Xml.Schema.XmlSeverityType.Error>. Ancak, bir <xref:System.Xml.Schema.XmlSchemaValidationException> şema doğrulama uyarılarla durum olmayan bir <xref:System.Xml.Schema.XmlSeverityType> değerini <xref:System.Xml.Schema.XmlSeverityType.Warning>.  
  
 Aşağıdaki örneğidir bir <xref:System.Xml.Schema.ValidationEventHandler> şema doğrulama uyarıları ve hataları giriş örnekte alınan şema doğrulaması sırasında karşılaşılan alır.  
  
```vb  
Shared Sub SchemaValidationEventHandler(ByVal sender As Object, ByVal e As ValidationEventArgs)  
  
    Select Case e.Severity  
        Case XmlSeverityType.Error  
            Console.WriteLine(vbCrLf & "Error: {0}", e.Message)  
            Exit Sub  
        Case XmlSeverityType.Warning  
            Console.WriteLine(vbCrLf & "Warning: {0}", e.Message)  
            Exit Sub  
    End Select  
End Sub  
```  
  
```csharp  
static void SchemaValidationEventHandler(object sender, ValidationEventArgs e)  
{  
    switch (e.Severity)  
    {  
        case XmlSeverityType.Error:  
            Console.WriteLine("\nError: {0}", e.Message);  
            break;  
        case XmlSeverityType.Warning:  
            Console.WriteLine("\nWarning: {0}", e.Message);  
            break;  
    }  
}  
```  
  
 Tam bir örnek için <xref:System.Xml.Schema.ValidationEventHandler>, giriş örneğe bakın. Daha fazla bilgi için bkz: <xref:System.Xml.Schema.XmlSchemaInfo> sınıf başvurusu belgelerinde.  
  
## <a name="xmlschemavalidator-state-transition"></a>XmlSchemaValidator durum geçişi  
 <xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı dizisi ve öğeleri, öznitelikleri ve bir XML bilgi içeriği doğrulamak için kullanılan yöntemlerin her biri için yapılan çağrılar oluşumunu zorlayan bir tanımlanan durum geçişi sahiptir.  
  
 Durum geçişi, aşağıdaki tabloda açıklanmaktadır <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı ve dizisi ve her durumda yapılabilmesi için yöntem çağrılarını geçişi.  
  
|Durum|geçiş|  
|-----------|----------------|  
|Doğrula|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel *) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|  
|TopLevel|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124;<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Öğesi|  
|Öğe|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> İçerik\*)? <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;|  
|İçerik|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124;<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Öğesi|  
  
> [!NOTE]
>  Bir <xref:System.InvalidOperationException> geçerli durumuna göre yanlış sırayla yöntemi çağrısı yapıldığında, yukarıdaki tabloda yöntemlerin her biri tarafından oluşturulan bir <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi.  
  
 Yukarıdaki durumu geçiş tablosunu yöntemleri açıklamak için noktalama simgeleri kullanır ve diğer durum geçişi her durum için çağrılabilir durumları <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı. Kullanılan simgeler belge türü tanımı (DTD) XML standartları Başvurusu'nda bulunan aynı simgelerdir.  
  
 Aşağıdaki tabloda durumu geçişi yukarıdaki tabloda bulunan noktalama simgeler yöntemleri nasıl etkilediğini açıklar ve diğer her durumda durum geçişi için çağrılabilir durumları <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı.  
  
|Simgesi|Açıklama|  
|------------|-----------------|  
|&#124;|Yöntem veya durumu (çubuğu önce) veya bir sonraki çağrılabilir.|  
|?|Yöntem veya soru işareti önündeki durumu isteğe bağlıdır ancak çağrılırsa, yalnızca bir kez çağrılabilir.|  
|*|Yöntem veya önündeki durumu * simgesi isteğe bağlıdır ve birden çok kez çağrılabilir.|  
  
## <a name="validation-context"></a>Doğrulama bağlamı  
 Yöntemlerinin <xref:System.Xml.Schema.XmlSchemaValidator> öğeleri, öznitelikleri ve bir XML bilgi içeriği doğrulamak, doğrulama bağlamı değiştirmek için kullanılan sınıf bir <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi. Örneğin, <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> yöntemi geçerli öğe içeriği doğrulama atlar ve hazırlar <xref:System.Xml.Schema.XmlSchemaValidator> üst öğenin bağlamında içeriği doğrulamak için nesne; geçerli öğenin tüm alt öğeleri için doğrulama atlanıyor için eşdeğerdir ve ardından çağırma <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> yöntemi.  
  
 Sonuçlarını <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı Doğrulanmakta olan geçerli bağlamda bağımlı.  
  
 Aşağıdaki tabloda bu yöntemleri yöntemlerinden birini çağrıldıktan sonra çağırma sonuçlarını açıklar <xref:System.Xml.Schema.XmlSchemaValidator> öğeleri, öznitelikleri ve bir XML bilgi içeriği doğrulamak için kullanılan bir sınıftır.  
  
|Yöntem|GetExpectedParticles|GetExpectedAttributes|AddSchema|  
|------------|--------------------------|---------------------------|---------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|Varsa varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi çağrıldığında, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> tüm genel öğeleri içeren bir dizi döndürür.<br /><br /> Varsa aşırı yüklenmiş <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yönteminin alan bir <xref:System.Xml.Schema.XmlSchemaObject> bir öğenin kısmi doğrulama başlatmak için bir parametre denir <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yalnızca öğesi döndüğü <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi başlatılmadı.|Varsa varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi çağrıldığında, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.<br /><br /> Varsa aşırı yüklemesini <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yönteminin alan bir <xref:System.Xml.Schema.XmlSchemaObject> bir özniteliğin kısmi doğrulama başlatmak için bir parametre adıyla <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yalnızca öznitelik döndüren <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi başlatılmadı.|Şemaya ekler <xref:System.Xml.Schema.XmlSchemaSet> , <xref:System.Xml.Schema.XmlSchemaValidator> önişlem hata olup olmadığını nesne.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Bağlam öğesi geçerliyse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin alt öğesi olarak beklenen öğe dizisi döndürür.<br /><br /> Bağlam öğesi geçersizse <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.|Bağlam öğesi geçerli olup olmadığını ve hiçbir çağrısına varsa <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> daha önce yapılmış, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bağlamı öğesinde tanımlanan tüm öznitelikler listesi döndürür.<br /><br /> Bazı öznitelikler zaten doğrulandı, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> doğrulanacak kalan öznitelikler listesi döndürür.<br /><br /> Bağlam öğesi geçersizse <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.|Yukarıdaki ile aynı.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Context özniteliği bir üst düzey özniteliği ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.<br /><br /> Aksi takdirde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin ilk alt olarak beklenen öğe dizisi döndürür.|Context özniteliği bir üst düzey özniteliği ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.<br /><br /> Aksi takdirde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> doğrulanacak kalan öznitelikler listesi döndürür.|Yukarıdaki ile aynı.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin ilk alt olarak beklenen öğe dizisi döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> henüz için bağlam öğesi doğrulanması için gerekli ve isteğe bağlı öznitelikleri listesi döndürür.|Yukarıdaki ile aynı.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin ilk alt olarak beklenen öğe dizisi döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Boş bir dizi döndürür.|Yukarıdaki ile aynı.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Bağlam öğenin contentType farklıysa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sonraki konumu beklenen öğe dizisi döndürür.<br /><br /> Bağlam öğenin contentType TextOnly ya da boş, ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.<br /><br /> Bağlam öğenin contentType ElementOnly, ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sonraki konuma ancak bir doğrulama hatası beklenen öğe dizisi zaten oluştu döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bağlam öğenin doğrulanmamış öznitelikler listesi döndürür.|Yukarıdaki ile aynı.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Bağlam boşluk üst düzey boşluk, ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.<br /><br /> Aksi takdirde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemin davranıştır de aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Bağlam boşluk üst düzey boşluk, ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.<br /><br /> Aksi takdirde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemin davranıştır de aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Yukarıdaki ile aynı.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesi (olası eşdüzey) sonra beklenen öğe dizisi döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bağlam öğenin doğrulanmamış öznitelikler listesi döndürür.<br /><br /> Bağlam öğesi üst öğeye sahipse <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir liste döndürür (geçerli öğede üst bağlam öğedir <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> olarak adlandırılıyordu).|Yukarıdaki ile aynı.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Yukarıdaki ile aynı.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Boş bir dizi döndürür.|Boş bir dizi döndürür.|Yukarıdaki ile aynı.|  
  
> [!NOTE]
>  Çeşitli özellikleri tarafından döndürülen değerler <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı değiştirilmediğini yöntemlerinden herhangi birini yukarıdaki tabloda çağırarak.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Schema.XmlSchemaValidator>
