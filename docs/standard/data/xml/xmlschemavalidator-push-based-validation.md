---
title: XmlSchemaValidator gönderim temelli doğrulaması
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c4d1d5602ff224c1c8f3e0948fc93c9200b9661e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44133694"
---
# <a name="xmlschemavalidator-push-based-validation"></a>XmlSchemaValidator gönderim temelli doğrulaması
<xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı XML şemaları XML verileriyle gönderim temelli bir şekilde doğrulamak için verimli, yüksek performanslı bir mekanizma sağlar. Örneğin, <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı doğrulama bir XML okuyucusu kullanarak belgeyi daha sonra ayrıştırma ve bir XML belgesi olarak seri hale getirmek zorunda kalmadan bir XML bilgi kümesi yerinde doğrulamanıza olanak verir.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı, doğrulama motoru özel XML veri kaynaklarıyla üzerinden veya doğrulama bir XML yazıcısı oluşturmak için bir yol olarak oluşturma gibi gelişmiş senaryolarda kullanılabilir.  
  
 Kullanımının bir örneği verilmiştir <xref:System.Xml.Schema.XmlSchemaValidator> doğrulamak için sınıf `contosoBooks.xml` karşı dosya `contosoBooks.xsd` şema. Örnekte <xref:System.Xml.Serialization.XmlSerializer> sınıfı seri durumdan çıkarılacak `contosoBooks.xml` dosya ve düğüm değerini yöntemlere <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı.  
  
> [!NOTE]
>  Bu örnekte, bu konu başlığının bölümleri kullanılır.  
  
 [!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
 [!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]  
  
 Örnek alan `contosoBooks.xml` dosya giriş olarak.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Bu örnek ayrıca alır `contosoBooks.xsd` girdi olarak.  
  
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
  
## <a name="validating-xml-data-using-xmlschemavalidator"></a>XmlSchemaValidator kullanarak XML verilerini doğrulanıyor  
 Bir XML bilgi kümesi doğrulama başlamak için öncelikle yeni bir örneğini başlatmalıdır <xref:System.Xml.Schema.XmlSchemaValidator> kullanarak <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Oluşturucusu.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Oluşturucusu alır <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, ve <xref:System.Xml.XmlNamespaceManager> parametre olarak nesnelerin yanı sıra bir <xref:System.Xml.Schema.XmlSchemaValidationFlags> bir parametre olarak değer. <xref:System.Xml.XmlNameTable> Nesnesi Şema ad alanı, XML ad alanı ve benzeri gibi iyi bilinen ad alanı dizeleri küçük parçalara için kullanılır ve geçirilir <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> basit içerik doğrulanırken yöntemi. <xref:System.Xml.Schema.XmlSchemaSet> Nesne XML bilgi kümesi doğrulamak için kullanılan XML şemaları içerir. <xref:System.Xml.XmlNamespaceManager> Nesnesi, doğrulama sırasında karşılaşılan ad alanları çözmek için kullanılır. <xref:System.Xml.Schema.XmlSchemaValidationFlags> Değeri doğrulama belirli özelliklerini devre dışı bırakmak için kullanılır.  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Oluşturucusu bkz <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı başvuru belgeleri.  
  
### <a name="initializing-validation"></a>Doğrulama başlatılıyor  
 Sonra bir <xref:System.Xml.Schema.XmlSchemaValidator> nesne oluşturulur, iki aşırı <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> durumunu başlatmak için kullanılan yöntemleri <xref:System.Xml.Schema.XmlSchemaValidator> nesne. İki şunlardır <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemleri.  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
 Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yöntemi başlatır bir <xref:System.Xml.Schema.XmlSchemaValidator> başlangıç durumuna ve aşırı yüklenmiş bir nesneye <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> gereken yöntemini bir <xref:System.Xml.Schema.XmlSchemaObject> başlatan bir parametre olarak bir <xref:System.Xml.Schema.XmlSchemaValidator> kısmi için başlangıç durumuna nesnesi doğrulama.  
  
 Her ikisi de <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemler yalnızca çağrılabilir hemen sonra bir <xref:System.Xml.Schema.XmlSchemaValidator> nesne oluşturulmuş veya çağrısı yapıldıktan sonra <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.  
  
 Bir örneği <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yöntemi giriş örneğe bakın. Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi bkz <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı başvuru belgeleri.  
  
#### <a name="partial-validation"></a>Kısmi doğrulama  
 <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Gereken yöntemini bir <xref:System.Xml.Schema.XmlSchemaObject> başlatan bir parametre olarak bir <xref:System.Xml.Schema.XmlSchemaValidator> başlangıç durumuna kısmi doğrulama için nesne.  
  
 Aşağıdaki örnekte, bir <xref:System.Xml.Schema.XmlSchemaObject> kısmi doğrulama kullanmak için başlatılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yöntemi. `orderNumber` Şema öğesi, şema öğesi tarafından seçerek geçirilir <xref:System.Xml.XmlQualifiedName> içinde <xref:System.Xml.Schema.XmlSchemaObjectTable> tarafından döndürülen koleksiyon <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet> nesne. <xref:System.Xml.Schema.XmlSchemaValidator> Nesneyi daha sonra bu belirli öğe doğrular.  
  
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
  
 Örneğin aşağıdaki XML Şeması girdi olarak alır.  
  
 `<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">`  
  
 `<xs:element name="orderNumber" type="xs:int" />`  
  
 `</xs:schema>`  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi bkz <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı başvuru belgeleri.  
  
### <a name="adding-additional-schemas"></a>Ek şemalar ekleme  
 <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Yöntemi <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı, bir XML Şeması doğrulama sırasında kullanılan şemalar kümesi eklemek için kullanılır. <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Yöntemi, bir satır içi XML Şeması Doğrulanmakta olan XML bilgi kümesi içinde karşılaşıldığında etkisini benzetimini yapmak için kullanılabilir.  
  
> [!NOTE]
>  Hedef ad alanı <xref:System.Xml.Schema.XmlSchema> parametresi, herhangi bir öğe veya öznitelik zaten karşılaştığı eşleşemez <xref:System.Xml.Schema.XmlSchemaValidator> nesne.  
>   
>  Varsa <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> değer parametre olarak değil geçildi <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Oluşturucusu <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemi hiçbir şey yapmaz.  
  
 Sonucu <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Doğrulanmakta olan geçerli XML düğümü bağlam bağımlı bir yöntemdir. Doğrulama bağlamı hakkında daha fazla bilgi için bu konunun "Doğrulama bağlamı" bölümüne bakın.  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemi bkz <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı başvuru belgeleri.  
  
### <a name="validating-elements-attributes-and-content"></a>Öğe, öznitelik ve içerik doğrulanıyor  
 <xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı öğeleri, öznitelikleri ve içeriği bir XML bilgi kümesi XML şemaları karşı doğrulamak için kullanılan çeşitli yöntemler sağlar. Aşağıdaki tabloda bu yöntemlerin her biri açıklanmaktadır.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Öğe adı geçerli bağlamda doğrular.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Öznitelik öğesi geçerli bağlamda veya karşı doğrular <xref:System.Xml.Schema.XmlSchemaAttribute> nesne geçirilen bir parametre olarak <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|Tüm gerekli öznitelikleri öğe bağlamında döndürülüp döndürülmeyeceğini doğrular ve hazırlar <xref:System.Xml.Schema.XmlSchemaValidator> öğenin alt içeriği doğrulamak için nesne.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Metin öğesi bağlamda izin verilir ve geçerli öğe basit içerik varsa, doğrulama için metin biriktirir olup olmadığını doğrular.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Boşluk geçerli öğe bağlamında izin verilir ve geçerli öğe basit içerik olup olmadığını doğrulama için boşluk biriktirir olup olmadığını doğrular.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|Öğenin metin içeriğini basit içeriğe sahip öğeleri için kendi veri türüne göre geçerli olup olmadığını doğrular ve geçerli öğenin içeriği ile karmaşık içerik öğeleri için tam olup olmadığını doğrular.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Geçerli öğenin içeriğinin doğrulama atlar ve hazırlar <xref:System.Xml.Schema.XmlSchemaValidator> üst öğenin bağlamındaki içerikleri doğrulamak için nesne.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Doğrulama sona erer ve tüm XML belgesi için kimlik kısıtlamaları denetler <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> doğrulama seçeneği ayarlanır.|  
  
> [!NOTE]
>  <xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı, dizisi ve önceki tabloda açıklanan yöntemlerin her biri için yapılan çağrılar, oluşumunu zorlayan tanımlanmış bir durum geçiş sahiptir. Belirli bir durum geçişi <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı, bu konunun "XmlSchemaValidator durum geçişi" bölümünde açıklanmıştır.  
  
 Öğe, öznitelik ve bir XML bilgi kümesi içeriği doğrulamak için kullanılan yöntemleri, örneğin, önceki bölümde örneğe bakın. Bu yöntemler hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı başvuru belgeleri.  
  
#### <a name="validating-content-using-an-xmlvaluegetter"></a>Bir XmlValueGetter kullanarak içerik doğrulanıyor  
 <xref:System.Xml.Schema.XmlValueGetter> `delegate` Değeri özniteliği, metin veya boşluk düğümleri özniteliği, metin veya boşluk düğüm XML Şeması Tanım Dili (XSD) türüyle uyumlu bir ortak dil çalışma zamanı (CLR) türleri olarak geçirmek için kullanılabilir. Bir <xref:System.Xml.Schema.XmlValueGetter> `delegate` CLR değeri bir öznitelik, metin veya boşluk düğümü zaten mevcuttur ve dönüştürerek maliyetini ortadan kaldırır yararlıdır bir `string` ve doğrulama için yeniden reparsing.  
  
 <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, Ve <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> yöntemleri aşırı ve öznitelik, metin veya boşluk düğümleri olarak değerini bir `string` veya <xref:System.Xml.Schema.XmlValueGetter> `delegate`.  
  
 Aşağıdaki yöntemlerden birini <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı kabul bir <xref:System.Xml.Schema.XmlValueGetter> `delegate` bir parametre olarak.  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>  
  
 Bir örneği verilmiştir <xref:System.Xml.Schema.XmlValueGetter> `delegate` alınan <xref:System.Xml.Schema.XmlSchemaValidator> giriş sınıfı örneği. <xref:System.Xml.Schema.XmlValueGetter> `delegate` Öznitelik olarak değerini döndürür bir <xref:System.DateTime> nesne. Bunu doğrulamak için <xref:System.DateTime> tarafından döndürülen nesne <xref:System.Xml.Schema.XmlValueGetter>, <xref:System.Xml.Schema.XmlSchemaValidator> nesne ilk ValueType için bunu dönüştürür (XSD türü için varsayılan CLR eşlemeyi ValueType'dir) veri türü özniteliği ve ardından dönüştürülmüş üzerinde denetimleri modelleri değer.  
  
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
  
 Tam bir örnek için <xref:System.Xml.Schema.XmlValueGetter> `delegate`, giriş örneğe bakın. Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlValueGetter> `delegate`, bkz: <xref:System.Xml.Schema.XmlValueGetter>, ve <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı başvuru belgeleri.  
  
#### <a name="post-schema-validation-information"></a>Sonrası-Schema-doğrulama-bilgileri  
 <xref:System.Xml.Schema.XmlSchemaInfo> Sınıfı sonrası-Schema-doğrulama-bilgilerden bazılarını doğrulayan bir XML düğümü temsil eden <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı. Çeşitli yöntemleri <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı kabul bir <xref:System.Xml.Schema.XmlSchemaInfo> nesnesi bir isteğe bağlı olarak (`null`) `out` parametresi.  
  
 Doğrulama başarılı, özelliklerini bağlı <xref:System.Xml.Schema.XmlSchemaInfo> nesne doğrulama sonuçlarını ayarlanır. Özniteliğini kullanarak, örneğin, başarılı doğrulama sırasında <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaInfo> nesne (belirtilmişse) kullanıcının <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, ve <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> özellikleri, doğrulama sonuçlarını ayarlanır .  
  
 Aşağıdaki <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı yöntemleri kabul bir <xref:System.Xml.Schema.XmlSchemaInfo> out parametresi olarak nesnesi.  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>  
  
 Tam bir örnek için <xref:System.Xml.Schema.XmlSchemaInfo> sınıfı, giriş örneğe bakın. Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaInfo> sınıfı <xref:System.Xml.Schema.XmlSchemaInfo> sınıfı başvuru belgeleri.  
  
### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a>Beklenen Particles, öznitelikler ve belirtilmeyen varsayılan özniteliklerini alma  
 <xref:System.Xml.Schema.XmlSchemaValidator> Sağlar sınıfını <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, ve <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> beklenen particles, öznitelikler ve geçerli doğrulama bağlamda belirsiz varsayılan öznitelikleri almak için yöntemler.  
  
#### <a name="retrieving-expected-particles"></a>Beklenen Particles alınıyor  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemi, bir dizi döndürür <xref:System.Xml.Schema.XmlSchemaParticle> geçerli öğe bağlamda beklenen particles içeren nesne. Tarafından döndürülen geçerli particles <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi örnekleridir <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAny> sınıfları.  
  
 İçerik modeli için oluşturucu olduğunda bir `xs:sequence`, yalnızca sonraki parçacık sırayla döndürülür. İçerik modeli için oluşturucu ise bir `xs:all` veya bir `xs:choice`, ardından öğesi bağlamda izleyebilirsiniz tüm geçerli particles döndürülür.  
  
> [!NOTE]
>  Varsa <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi çağırdıktan hemen sonra çağrılır <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> tüm genel öğeler yöntemi döndürür.  
  
 Örneğin, XML Şeması Tanım Dili (XSD) şeması XML doğrulama sonra anlatılmaktadır, belge ve `book` öğesi `book` geçerli öğe bağlamı bir öğedir. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemi içeren tek bir dizi döndürür <xref:System.Xml.Schema.XmlSchemaElement> nesnesini temsil eden `title` öğesi. Doğrulama bağlamını olduğunda `title` öğesi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntem boş bir dizi döndürür. Varsa <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi çağrıldıktan sonra `title` öğesi doğrulanmış önce `description` öğesi doğrulanmış, tek bir içeren bir dizi döndürür <xref:System.Xml.Schema.XmlSchemaElement> nesnesini temsil eden `description` öğesi. Varsa <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi çağrıldıktan sonra `description` öğesi doğrulanmış sonra tek bir içeren bir dizi döndürür <xref:System.Xml.Schema.XmlSchemaAny> joker karakteri temsil eden nesne.  
  
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
  
 Örneğin aşağıdaki XML, girdi olarak alır.  
  
 `<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">`  
  
 `<xs:element name="book">`  
  
 `<xs:sequence>`  
  
 `<xs:element name="title" type="xs:string" />`  
  
 `<xs:element name="description" type="xs:string" />`  
  
 `<xs:any processContent="lax" maxOccurs="unbounded" />`  
  
 `</xs:sequence>`  
  
 `</xs:element>`  
  
 `</xs:schema>`  
  
 Örneğin, aşağıdaki XSD şeması girdi olarak alır.  
  
 `<book>`  
  
 `<title>My Book</title>`  
  
 `<description>My Book's Description</description>`  
  
 `<namespace>System.Xml.Schema</namespace>`  
  
 `</book>`  
  
> [!NOTE]
>  Sonuçları <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı Doğrulanmakta olan geçerli bağlam bağımlı. Daha fazla bilgi için bu konunun "Doğrulama bağlamı" bölümüne bakın.  
  
 Bir örneği <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi giriş örneğe bakın. Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi bkz <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı başvuru belgeleri.  
  
#### <a name="retrieving-expected-attributes"></a>Beklenen özniteliklerini alma  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Yöntemi, bir dizi döndürür <xref:System.Xml.Schema.XmlSchemaAttribute> geçerli öğe bağlamda beklenen öznitelikleri içeren nesne.  
  
 Örneğin, giriş örnekte <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi tüm öznitelikleri almak için kullanılan `book` öğesi.  
  
 Eğer <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi hemen sonra <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> yöntemi, XML belgesindeki görünebilir tüm öznitelikler döndürülür. Ancak, eğer <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi için bir veya daha fazla çağırdıktan sonra <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntemi, henüz geçerli öğe için doğrulanmış değil öznitelikleri döndürülür.  
  
> [!NOTE]
>  Sonuçları <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı Doğrulanmakta olan geçerli bağlam bağımlı. Daha fazla bilgi için bu konunun "Doğrulama bağlamı" bölümüne bakın.  
  
 Bir örneği <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi giriş örneğe bakın. Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi bkz <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı başvuru belgeleri.  
  
#### <a name="retrieving-unspecified-default-attributes"></a>Belirtilmeyen varsayılan özniteliklerini alma  
 <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Yöntemi doldurur <xref:System.Collections.ArrayList> ile belirtilen <xref:System.Xml.Schema.XmlSchemaAttribute> nesneler için varsayılan değerlerle önceden kullanılarak doğrulandı değil herhangi bir özniteliği <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntemi öğesi bağlamı. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Yöntemini çağırdıktan sonra adında <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> öznitelik öğe bağlamında yöntemi. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Yöntemi, varsayılan öznitelikler Doğrulanmakta olan XML belgeye eklenecek olduğunu belirlemek için kullanılmalıdır.  
  
 Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> yöntemi bkz <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı başvuru belgeleri.  
  
### <a name="handling-schema-validation-events"></a>Şema doğrulama olayları işleme  
 Şema doğrulama uyarıları ve doğrulama sırasında karşılaşılan hataları tarafından işlenmesini <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> olayı <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı.  
  
 Şema doğrulama uyarıları sahip bir <xref:System.Xml.Schema.XmlSeverityType> değerini <xref:System.Xml.Schema.XmlSeverityType.Warning> ve şema doğrulama hataları bir <xref:System.Xml.Schema.XmlSeverityType> değerini <xref:System.Xml.Schema.XmlSeverityType.Error>. Hayır ise <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> atanmış, bir <xref:System.Xml.Schema.XmlSchemaValidationException> ile tüm şema doğrulama hataları için özel bir <xref:System.Xml.Schema.XmlSeverityType> değerini <xref:System.Xml.Schema.XmlSeverityType.Error>. Ancak, bir <xref:System.Xml.Schema.XmlSchemaValidationException> şema doğrulama uyarılarla durum olmayan bir <xref:System.Xml.Schema.XmlSeverityType> değerini <xref:System.Xml.Schema.XmlSeverityType.Warning>.  
  
 Aşağıdaki örneğidir bir <xref:System.Xml.Schema.ValidationEventHandler> şema doğrulama uyarıları ve giriş örnek runbook'undan şema doğrulaması sırasında karşılaşılan hataları alır.  
  
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
  
 Tam bir örnek için <xref:System.Xml.Schema.ValidationEventHandler>, giriş örneğe bakın. Daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaInfo> sınıfı başvuru belgeleri.  
  
## <a name="xmlschemavalidator-state-transition"></a>XmlSchemaValidator durum geçişi  
 <xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı, dizisi ve öğe, öznitelik ve bir XML bilgi kümesi içeriği doğrulamak için kullanılan yöntemlerin her biri için yapılan çağrılar, oluşumunu zorlayan tanımlanmış bir durum geçiş sahiptir.  
  
 Durum geçişi, aşağıdaki tabloda açıklanmıştır <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı, dizisi ve her durumda yapılan yöntem çağrılarını oluşumunu.  
  
|Durum|geçiş|  
|-----------|----------------|  
|Doğrulama|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel *) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|  
|TopLevel|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124;<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Öğesi|  
|Öğe|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> İçerik\*)? <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> İçerik\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>&#124;|  
|İçerik|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124;<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Öğesi|  
  
> [!NOTE]
>  Bir <xref:System.InvalidOperationException> yukarıdaki tabloda yöntemlerin her biri tarafından yanlış sırada geçerli durumuna göre yöntemine çağrı yapıldığında oluşturulan bir <xref:System.Xml.Schema.XmlSchemaValidator> nesne.  
  
 Yukarıdaki durumu geçiş tablo noktalama simgeleri yöntemleri tanımlamak için kullanır. ve diğer durum geçiş her durum için çağrılabilir durumları <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı. Kullanılan sembolleri, belge türü tanımı (DTD'nin) XML standartları Başvurusu'nda bulunan aynı simgelerdir.  
  
 Durum geçişi yukarıdaki tabloda bulunan noktalama simgeleri yöntemleri nasıl etkileyeceğini aşağıdaki tabloda açıklanmıştır ve diğer her durumda durum geçişi için çağrılabilir durumları <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı.  
  
|Sembol|Açıklama|  
|------------|-----------------|  
|&#124;|Yöntem veya durumu (bir çubuk önce) veya bir sonraki çağrılabilir.|  
|?|Yöntem veya soru işareti önündeki durumu isteğe bağlıdır ancak çağrılırsa, yalnızca bir kez çağrılabilir.|  
|*|Yöntem veya önündeki durumu * sembol isteğe bağlıdır ve birden çok kez çağrılabilir.|  
  
## <a name="validation-context"></a>Doğrulama bağlamını  
 Yöntemlerinin <xref:System.Xml.Schema.XmlSchemaValidator> öğeleri, öznitelikleri ve içeriği bir XML bilgi kümesi doğrulayın, doğrulama bağlamı değiştirmek için kullanılan sınıf bir <xref:System.Xml.Schema.XmlSchemaValidator> nesne. Örneğin, <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> yöntemi geçerli öğe içeriği doğrulama atlar ve hazırlar <xref:System.Xml.Schema.XmlSchemaValidator> üst öğenin bağlamındaki içerikleri doğrulamak için nesne; geçerli öğenin tüm alt öğeleri için doğrulama atlama için eşdeğerdir ve ardından arama <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> yöntemi.  
  
 Sonuçları <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı Doğrulanmakta olan geçerli bağlam bağımlı.  
  
 Aşağıdaki tabloda bu yöntemleri yöntemlerinden birini çağrıldıktan sonra çağırma sonuçları açıklanmaktadır <xref:System.Xml.Schema.XmlSchemaValidator> öğe, öznitelik ve bir XML bilgi kümesi içeriği doğrulamak için kullanılan sınıf.  
  
|Yöntem|GetExpectedParticles|GetExpectedAttributes|AddSchema|  
|------------|--------------------------|---------------------------|---------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi çağrıldığında <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> tüm genel öğeler içeren bir dizi döndürür.<br /><br /> Aşırı yüklenmiş <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> gereken yöntemini bir <xref:System.Xml.Schema.XmlSchemaObject> kısmi doğrulama, bir öğenin başlatmak için bir parametre adıyla <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yalnızca öğe döndüren <xref:System.Xml.Schema.XmlSchemaValidator> nesne başlatıldı.|Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi çağrıldığında <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.<br /><br /> Varsa aşırı yüklemesini <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> gereken yöntemini bir <xref:System.Xml.Schema.XmlSchemaObject> bir özniteliğin, kısmi doğrulama başlatmak için bir parametre adıyla <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yalnızca öznitelik döndüren <xref:System.Xml.Schema.XmlSchemaValidator> nesne başlatıldı.|Şemaya ekler <xref:System.Xml.Schema.XmlSchemaSet> , <xref:System.Xml.Schema.XmlSchemaValidator> hiçbir ön işleme hataları olan nesne.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Bağlam öğesi geçerliyse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğenin alt öğeleri beklenen öğelerinin bir dizisini döndürür.<br /><br /> Bağlam öğesi geçersizse <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.|Bağlam öğesi geçerliyse ve hiçbir çağrısı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> daha önce yapılmış, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bağlam öğesinde tanımlanan tüm öznitelikler listesi döndürür.<br /><br /> Bazı öznitelikler zaten doğrulanmış durumunda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> doğrulanacak kalan öznitelikler listesi döndürür.<br /><br /> Bağlam öğesi geçersizse <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.|Yukarıdakiyle aynı.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Bağlam özniteliği bir üst düzey özniteliği ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.<br /><br /> Aksi takdirde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin ilk alt beklenen öğelerinin bir dizisini döndürür.|Bağlam özniteliği bir üst düzey özniteliği ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.<br /><br /> Aksi takdirde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> doğrulanacak kalan öznitelikler listesi döndürür.|Yukarıdakiyle aynı.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin ilk alt beklenen öğelerinin bir dizisini döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> henüz içerik öğe için doğrulanması için gerekli ve isteğe bağlı öznitelikleri listesi döndürür.|Yukarıdakiyle aynı.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin ilk alt beklenen öğelerinin bir dizisini döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Boş bir dizi döndürür.|Yukarıdakiyle aynı.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Bağlam öğenin contentType karıştırıldığında <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sonraki konumda beklenen öğelerinin bir dizisini döndürür.<br /><br /> Bağlam öğenin contentType TextOnly veya boş ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.<br /><br /> Bağlam öğenin contentType ElementOnly, ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sonraki konumuna ancak bir doğrulama hatası beklenen öğeler sırası zaten oluştu döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bağlam öğenin öznitelikleri doğrulanmamış listesini döndürür.|Yukarıdakiyle aynı.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Üst düzey beyaz-boşluk, bağlam boşluk olması durumunda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.<br /><br /> Aksi takdirde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemin davranışını aynı olan <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Üst düzey beyaz-boşluk, bağlam boşluk olması durumunda <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.<br /><br /> Aksi takdirde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemin davranışını aynı olan <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Yukarıdakiyle aynı.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesi (olası eşdüzey) sonra beklenen öğelerinin bir dizisini döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bağlam öğenin öznitelikleri doğrulanmamış listesini döndürür.<br /><br /> Bağlam öğesi üst öğe sahipse <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir liste döndürür (içerik, geçerli öğenin üst öğedir <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> olarak adlandırılıyordu).|Yukarıdakiyle aynı.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Yukarıdakiyle aynı.|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Boş bir dizi döndürür.|Boş bir dizi döndürür.|Yukarıdakiyle aynı.|  
  
> [!NOTE]
>  Çeşitli özellikleri tarafından döndürülen değerler <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı değiştirilmediğini yukarıdaki tabloda herhangi bir yöntemi çağırarak.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Schema.XmlSchemaValidator>
