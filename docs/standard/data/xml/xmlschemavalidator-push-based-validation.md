---
title: XmlSchemaValidator Gönderim Temelli Doğrulaması
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
ms.openlocfilehash: d5b2fe4325000023acc98580a2a6d014f56fecbd
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419115"
---
# <a name="xmlschemavalidator-push-based-validation"></a>XmlSchemaValidator Gönderim Temelli Doğrulaması

Sınıfı, XML <xref:System.Xml.Schema.XmlSchemaValidator> verilerini gönderme temelli bir şekılde XML şemalarına karşı doğrulamak için etkili ve yüksek performanslı bir mekanizma sağlar. Örneğin sınıfı, bir XML <xref:System.Xml.Schema.XmlSchemaValidator> bilgisi kümesini BIR XML belgesi olarak seri hale getirmek ve ardından belgeyi bir doğrulama XML okuyucusu kullanarak yeniden yerleştirmek zorunda kalmadan, yerinde doğrulamanızı sağlar.

<xref:System.Xml.Schema.XmlSchemaValidator>Sınıfı, özel XML veri kaynakları üzerinde doğrulama motorları oluşturmak veya bir doğrulama XML yazıcısı oluşturmak için bir yol olarak, Gelişmiş senaryolarda kullanılabilir.

Aşağıda, <xref:System.Xml.Schema.XmlSchemaValidator> dosyayı şemaya karşı doğrulamak için sınıfının kullanılmasına bir örnek verilmiştir `contosoBooks.xml` `contosoBooks.xsd` . Örnek, <xref:System.Xml.Serialization.XmlSerializer> dosyanın serisini kaldırmak `contosoBooks.xml` ve düğümlerin değerini sınıfının yöntemlerine geçirmek için sınıfını kullanır <xref:System.Xml.Schema.XmlSchemaValidator> .

> [!NOTE]
> Bu örnek, bu konunun bölümleri boyunca kullanılır.

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

Örnek, `contosoBooks.xml` dosyayı giriş olarak alır.

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

Örnek de `contosoBooks.xsd` bir giriş olarak alır.

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

## <a name="validating-xml-data-using-xmlschemavalidator"></a>XmlSchemaValidator kullanarak XML verilerini doğrulama

Bir XML bilgi kümesini doğrulamaya başlamak için, önce oluşturucuyu kullanarak sınıfının yeni bir örneğini başlatmalısınız <xref:System.Xml.Schema.XmlSchemaValidator> <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> .

<xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>Oluşturucu <xref:System.Xml.XmlNameTable> , <xref:System.Xml.Schema.XmlSchemaSet> ve değerlerini parametre olarak ve bir parametresi olarak alır <xref:System.Xml.XmlNamespaceManager> <xref:System.Xml.Schema.XmlSchemaValidationFlags> . <xref:System.Xml.XmlNameTable>Nesnesi, şema ad alanı, XML ad alanı vb. gibi iyi bilinen ad alanı dizelerini ayrılamaz ve <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> basit içerik doğrulanırken yöntemine geçirilir. <xref:System.Xml.Schema.XmlSchemaSet>Nesnesi, XML bilgi kümesini doğrulamak için kullanılan XML şemalarını içerir. <xref:System.Xml.XmlNamespaceManager>Nesne, doğrulama sırasında karşılaşılan ad alanlarını çözümlemek için kullanılır. Bu <xref:System.Xml.Schema.XmlSchemaValidationFlags> değer, doğrulamanın belirli özelliklerini devre dışı bırakmak için kullanılır.

Oluşturucu hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> bkz <xref:System.Xml.Schema.XmlSchemaValidator> . sınıf başvurusu belgeleri.

### <a name="initializing-validation"></a>Doğrulama başlatılıyor

Bir nesne oluşturulduktan sonra <xref:System.Xml.Schema.XmlSchemaValidator> , <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> nesnenin durumunu başlatmak için kullanılan iki aşırı yüklenmiş yöntem vardır <xref:System.Xml.Schema.XmlSchemaValidator> . Aşağıdaki iki <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> Yöntem vardır.

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Yöntem, bir <xref:System.Xml.Schema.XmlSchemaValidator> nesneyi başlangıç durumuna başlatır ve bir <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> parametresi olarak alan aşırı yüklenmiş yöntem, <xref:System.Xml.Schema.XmlSchemaObject> <xref:System.Xml.Schema.XmlSchemaValidator> kısmi doğrulama için bir nesneyi başlangıç durumuna başlatır.

Her iki <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> Yöntem de yalnızca bir nesne oluşturulduktan sonra <xref:System.Xml.Schema.XmlSchemaValidator> veya bir çağrısından sonra çağrılabilir <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A> .

Yöntemine bir örnek için <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> , giriş bölümündeki örneğe bakın. Yöntemi hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> bkz <xref:System.Xml.Schema.XmlSchemaValidator> . sınıf başvurusu belgeleri.

#### <a name="partial-validation"></a>Kısmi doğrulama

Bir <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> parametre olarak alan yöntemi, <xref:System.Xml.Schema.XmlSchemaObject> <xref:System.Xml.Schema.XmlSchemaValidator> kısmi doğrulama için bir nesneyi başlangıç durumuna başlatır.

Aşağıdaki örnekte, <xref:System.Xml.Schema.XmlSchemaObject> yöntemi kullanılarak kısmi doğrulama için bir başlatılır <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> . `orderNumber`Şema öğesi, <xref:System.Xml.XmlQualifiedName> <xref:System.Xml.Schema.XmlSchemaObjectTable> nesnesinin özelliği tarafından döndürülen koleksiyonda tarafından şema öğesi seçilerek geçirilir <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> <xref:System.Xml.Schema.XmlSchemaSet> . <xref:System.Xml.Schema.XmlSchemaValidator>Nesne daha sonra bu özel öğeyi doğrular.

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

Örnek, aşağıdaki XML şemasını giriş olarak alır.

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="orderNumber" type="xs:int" />
</xs:schema>
```

Yöntemi hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> bkz <xref:System.Xml.Schema.XmlSchemaValidator> . sınıf başvurusu belgeleri.

### <a name="adding-additional-schemas"></a>Ek şemalar ekleme

<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A>Sınıfının yöntemi, <xref:System.Xml.Schema.XmlSchemaValidator> doğrulama sırasında kullanılan şemalar KÜMESINE bir XML şeması eklemek için kullanılır. <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A>Yöntemi, DOĞRULANAN xml bilgi kümesindeki bir satır ıçı XML şeması ile karşılaşanın etkisinin benzetimini yapmak için kullanılabilir.

> [!NOTE]
> Parametrenin hedef ad alanı, <xref:System.Xml.Schema.XmlSchema> nesne tarafından zaten karşılaşılan hiçbir öğe veya öznitelikle eşleşmiyor <xref:System.Xml.Schema.XmlSchemaValidator> .
>
> Değer, <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> oluşturucuya bir parametre olarak geçirilmemişse <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> , <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Yöntem hiçbir şey yapmaz.

Yöntemin sonucu, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> doğrulanan GEÇERLI XML düğümü bağlamına bağlıdır. Doğrulama bağlamları hakkında daha fazla bilgi için bu konunun "doğrulama bağlamı" bölümüne bakın.

Yöntemi hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> bkz <xref:System.Xml.Schema.XmlSchemaValidator> . sınıf başvurusu belgeleri.

### <a name="validating-elements-attributes-and-content"></a>Öğeleri, öznitelikleri ve Içeriği doğrulama

Sınıfı, XML <xref:System.Xml.Schema.XmlSchemaValidator> şemalarında xml bilgi kümesindeki öğeleri, öznitelikleri ve içerikleri doğrulamak için kullanılan çeşitli yöntemler sağlar. Aşağıdaki tabloda bu yöntemlerin her biri açıklanmaktadır.

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Geçerli bağlamdaki öğe adını doğrular.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Geçerli öğe bağlamındaki özniteliği veya <xref:System.Xml.Schema.XmlSchemaAttribute> yöntemine parametre olarak geçirilen nesneye karşı doğrular <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> .|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|Öğe bağlamındaki tüm gerekli özniteliklerin mevcut olup olmadığını doğrular ve <xref:System.Xml.Schema.XmlSchemaValidator> nesneyi öğenin alt içeriğini doğrulamak üzere hazırlar.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Geçerli öğe bağlamında metnin izin verilip verilmeyeceğini doğrular ve geçerli öğede basit içerik varsa doğrulama için metni biriktirir.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Geçerli öğe bağlamında beyaz boşluğa izin verilip verilmeyeceğini doğrular ve geçerli öğenin basit içeriğe sahip olup olmadığını doğrulamak için beyaz boşluğu biriktirir.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|Öğenin metin içeriğinin basit içeriğe sahip öğeler için kendi veri türüne göre geçerli olup olmadığını doğrular ve karmaşık içerikli öğeler için geçerli öğenin içeriğinin tamamlanıp tamamlanmadığını doğrular.|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Geçerli öğe içeriğinin geçerliliğini atlar ve <xref:System.Xml.Schema.XmlSchemaValidator> üst öğenin bağlamındaki içeriği doğrulamak için nesneyi hazırlar.|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Doğrulama seçeneği ayarlandıysa, doğrulamayı sonlandırır ve tüm XML belgesi için kimlik kısıtlamalarını denetler <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> .|

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaValidator>Sınıfında, önceki tabloda açıklanan yöntemlerin her birine yapılan çağrıların sırasını ve tekrarını uygulayan tanımlı bir durum geçişi vardır. Sınıfın belirli durum geçişi, <xref:System.Xml.Schema.XmlSchemaValidator> Bu konunun "XmlSchemaValidator durum geçişi" bölümünde açıklanmaktadır.

Bir XML bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan yöntemlere örnek olarak, önceki bölümde bulunan örneğe bakın. Bu yöntemler hakkında daha fazla bilgi için bkz <xref:System.Xml.Schema.XmlSchemaValidator> . sınıf başvurusu belgeleri.

#### <a name="validating-content-using-an-xmlvaluegetter"></a>XmlValueGetter kullanarak Içerik doğrulanıyor

Öznitelik, <xref:System.Xml.Schema.XmlValueGetter> `delegate` metin veya boşluk düğümlerinin değerini öznitelik, metin veya boşluk düğümünün XML şeması tanım DILI (xsd) türüyle uyumlu ortak dil çalışma zamanı (CLR) türleri olarak geçirmek için kullanılabilir. Bir <xref:System.Xml.Schema.XmlValueGetter> `delegate` özniteliğin, metnin veya boşluk düğümünün clr değeri zaten kullanılabilirse ve bunu bir `string` ve daha sonra doğrulama için yeniden ayrıştırmanın maliyetini önlediği durumlarda yararlıdır.

<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> , Ve <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> yöntemleri aşırı yüklenmiş ve öznitelik, metin veya boşluk düğümlerinin değeri veya olarak kabul edilir `string` <xref:System.Xml.Schema.XmlValueGetter> `delegate` .

Sınıfının aşağıdaki yöntemleri bir <xref:System.Xml.Schema.XmlSchemaValidator> parametre olarak kabul eder <xref:System.Xml.Schema.XmlValueGetter> `delegate` .

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

Aşağıda, <xref:System.Xml.Schema.XmlValueGetter> `delegate` <xref:System.Xml.Schema.XmlSchemaValidator> giriş içindeki sınıf örneğinizden alınan bir örnek verilmiştir. , Bir <xref:System.Xml.Schema.XmlValueGetter> `delegate` özniteliğin değerini bir nesne olarak döndürür <xref:System.DateTime> . <xref:System.DateTime>Tarafından döndürülen bu nesneyi doğrulamak için <xref:System.Xml.Schema.XmlValueGetter> , nesnesi, <xref:System.Xml.Schema.XmlSchemaValidator> özniteliğin veri türü Için önce onu ValueType öğesine dönüştürür (ValueType, xsd türü için varsayılan clr eşlemedir) ve ardından dönüştürülen değer üzerindeki modelleri denetler.

```vb
Shared dateTimeGetterContent As Object

Shared Function DateTimeGetterHandle() As Object
    Return dateTimeGetterContent
End Function

Shared Function DateTimeGetter(dateTime As DateTime) As XmlValueGetter
    dateTimeGetterContent = dateTime
    Return New XmlValueGetter(AddressOf DateTimeGetterHandle)
End Function
```

```csharp
static object dateTimeGetterContent;

static object DateTimeGetterHandle()
{
    return dateTimeGetterContent;
}

static XmlValueGetter DateTimeGetter(DateTime dateTime)
{
    dateTimeGetterContent = dateTime;
    return new XmlValueGetter(dateTimeGetterHandle);
}
```

Öğesinin tamamen bir örneği için <xref:System.Xml.Schema.XmlValueGetter> `delegate` giriş bölümündeki örneğe bakın. Hakkında daha fazla bilgi için, <xref:System.Xml.Schema.XmlValueGetter> `delegate` <xref:System.Xml.Schema.XmlValueGetter> ve <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerine bakın.

#### <a name="post-schema-validation-information"></a>Şema sonrası doğrulama-bilgi

<xref:System.Xml.Schema.XmlSchemaInfo>Sınıfı, sınıfı tarafından doğrulanan BIR XML düğümünün şema sonrası-doğrulama bilgilerinin bazılarını temsil eder <xref:System.Xml.Schema.XmlSchemaValidator> . Sınıfının çeşitli yöntemleri <xref:System.Xml.Schema.XmlSchemaValidator> bir <xref:System.Xml.Schema.XmlSchemaInfo> nesneyi isteğe bağlı, () parametre olarak kabul `null` eder `out` .

Doğrulama başarılı olduğunda, <xref:System.Xml.Schema.XmlSchemaInfo> nesnesinin özellikleri doğrulamanın sonuçlarıyla ayarlanır. Örneğin, yöntemini kullanarak bir özniteliğin başarıyla doğrulanması sırasında <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> , <xref:System.Xml.Schema.XmlSchemaInfo> nesnenin (belirtilmişse) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A> , <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A> , <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A> ve <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> özellikleri doğrulamanın sonuçlarıyla ayarlanır.

Aşağıdaki <xref:System.Xml.Schema.XmlSchemaValidator> sınıf yöntemleri bir <xref:System.Xml.Schema.XmlSchemaInfo> nesneyi out parametresi olarak kabul eder.

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

Sınıfının tamamen bir örneği için <xref:System.Xml.Schema.XmlSchemaInfo> , giriş bölümündeki örneğe bakın. Sınıfı hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaInfo> bkz <xref:System.Xml.Schema.XmlSchemaInfo> . sınıf başvurusu belgeleri.

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a>Beklenen parçacık, öznitelik ve belirtilmemiş varsayılan öznitelikleri alma

<xref:System.Xml.Schema.XmlSchemaValidator>Sınıfı <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> , <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> geçerli doğrulama bağlamında beklenen parçacıkların, özniteliklerin ve belirtilmemiş varsayılan özniteliklerin alınması için, ve yöntemlerini sağlar.

#### <a name="retrieving-expected-particles"></a>Beklenen parçacık alınıyor

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>Yöntemi, <xref:System.Xml.Schema.XmlSchemaParticle> geçerli öğe bağlamında beklenen parçacık içeren bir nesne dizisi döndürür. Yöntemi tarafından döndürülebilecek geçerli parçacık <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> , <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAny> sınıflarının örnekleridir.

İçerik modeli için Oluşturucu bir ise `xs:sequence` , yalnızca dizideki bir sonraki parçacık döndürülür. İçerik modeli için Oluşturucu bir `xs:all` veya ise `xs:choice` , geçerli öğe bağlamında izleyelebilecek tüm geçerli parçacık döndürülür.

> [!NOTE]
> Yöntemi çağrıldıktan <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> hemen sonra yöntem çağrılırsa <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> , <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi tüm genel öğeleri döndürür.

Örneğin, XML şeması tanım dili (XSD) şeması ve izleyen XML belgesinde öğesi doğrulandıktan sonra `book` `book` öğesi geçerli öğe bağlamıdır. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>Yöntemi <xref:System.Xml.Schema.XmlSchemaElement> , öğesini temsil eden tek bir nesne içeren bir dizi döndürür `title` . Doğrulama bağlamı `title` öğesi olduğunda, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi boş bir dizi döndürür. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> `title` Öğe doğrulandıktan sonra, ancak öğe doğrulandıktan sonra yöntemi çağrılırsa `description` , <xref:System.Xml.Schema.XmlSchemaElement> öğesini temsil eden tek bir nesne içeren bir dizi döndürür `description` . <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>Öğe doğrulandıktan sonra yöntemi çağrılırsa, `description` <xref:System.Xml.Schema.XmlSchemaAny> joker karakteri temsil eden tek bir nesne içeren bir dizi döndürür.

```vb
Dim reader As XmlReader =  XmlReader.Create("input.xml")

Dim schemaSet As New XmlSchemaSet()
schemaSet.Add(Nothing, "schema.xsd")
Dim manager As New XmlNamespaceManager(reader.NameTable)

Dim validator As New XmlSchemaValidator(reader.NameTable,schemaSet,manager,XmlSchemaValidationFlags.None)
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

var schemaSet = new XmlSchemaSet();
schemaSet.Add(null, "schema.xsd");
var manager = new XmlNamespaceManager(reader.NameTable);

var validator = new XmlSchemaValidator(reader.NameTable, schemaSet, manager, XmlSchemaValidationFlags.None);
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

 Örnek aşağıdaki XML 'i giriş olarak alır:

```xml
<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">
  <xs:element name="book">
    <xs:sequence>
      <xs:element name="title" type="xs:string" />
      <xs:element name="description" type="xs:string" />
      <xs:any processContent="lax" maxOccurs="unbounded" />
    </xs:sequence>
  </xs:element>
</xs:schema>
```

Örnek, aşağıdaki XSD şemasını giriş olarak alır:

```xml
<book>
  <title>My Book</title>
  <description>My Book's Description</description>
  <namespace>System.Xml.Schema</namespace>
</book>
```

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Sınıfının, ve yöntemlerinin sonuçları, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> <xref:System.Xml.Schema.XmlSchemaValidator> doğrulanan geçerli bağlamına bağımlıdır. Daha fazla bilgi için bu konunun "doğrulama bağlamı" bölümüne bakın.

Yöntemine bir örnek için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> , giriş bölümündeki örneğe bakın. Yöntemi hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bkz <xref:System.Xml.Schema.XmlSchemaValidator> . sınıf başvurusu belgeleri.

#### <a name="retrieving-expected-attributes"></a>Beklenen öznitelikleri alma

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Yöntemi, <xref:System.Xml.Schema.XmlSchemaAttribute> geçerli öğe bağlamında beklenen öznitelikleri içeren bir nesne dizisi döndürür.

Örneğin, giriş bölümündeki örnekte <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi, öğesinin tüm özniteliklerini almak için kullanılır `book` .

Yöntemi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> hemen sonra çağırdığınızda <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> , XML belgesinde görünebilen tüm öznitelikler döndürülür. Ancak, yöntemi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bir veya daha fazla yöntem çağrısından sonra çağırdığınızda <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> , geçerli öğe için henüz doğrulanmamış öznitelikler döndürülür.

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Sınıfının, ve yöntemlerinin sonuçları, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> <xref:System.Xml.Schema.XmlSchemaValidator> doğrulanan geçerli bağlamına bağımlıdır. Daha fazla bilgi için bu konunun "doğrulama bağlamı" bölümüne bakın.

Yöntemine bir örnek için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> , giriş bölümündeki örneğe bakın. Yöntemi hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bkz <xref:System.Xml.Schema.XmlSchemaValidator> . sınıf başvurusu belgeleri.

#### <a name="retrieving-unspecified-default-attributes"></a>Belirtilmeyen varsayılan öznitelikler alınıyor

<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>Yöntemi, <xref:System.Collections.ArrayList> <xref:System.Xml.Schema.XmlSchemaAttribute> öğe bağlamındaki yöntemi kullanılarak daha önce doğrulanmamış varsayılan değerlere sahip herhangi bir öznitelik için nesneleri ile belirtilen şekilde doldurur <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> . Yöntemi, <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> öğe bağlamındaki her bir öznitelikte yöntemi çağrıldıktan sonra çağrılmalıdır. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>Yöntemi, DOĞRULANAN XML belgesine hangi varsayılan özniteliklerin ekleneceğini belirlemek için kullanılmalıdır.

Yöntemi hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> bkz <xref:System.Xml.Schema.XmlSchemaValidator> . sınıf başvurusu belgeleri.

### <a name="handling-schema-validation-events"></a>Şema doğrulama olaylarını işleme

Şema doğrulama uyarıları ve doğrulama sırasında karşılaşılan hatalar, <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> sınıfının olayı tarafından işlenir <xref:System.Xml.Schema.XmlSchemaValidator> .

Şema doğrulama uyarıları bir <xref:System.Xml.Schema.XmlSeverityType> değere sahiptir <xref:System.Xml.Schema.XmlSeverityType.Warning> ve şema doğrulama hatalarının değeri vardır <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Error> . Hiçbiri <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> atanmamışsa, bir <xref:System.Xml.Schema.XmlSchemaValidationException> değeri olan tüm şema doğrulama hataları için bir atılır <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Error> . Ancak, bir <xref:System.Xml.Schema.XmlSchemaValidationException> değeri olan şema doğrulama uyarıları için bir oluşturulmaz <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Warning> .

Aşağıda, <xref:System.Xml.Schema.ValidationEventHandler> giriş içindeki örnekte alınan şema doğrulama uyarılarını ve şema doğrulama sırasında karşılaşılan hataları alan bir örneği verilmiştir.

```vb
Shared Sub SchemaValidationEventHandler(sender As Object, e As ValidationEventArgs)

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

Öğesinin tamamen bir örneği için <xref:System.Xml.Schema.ValidationEventHandler> giriş bölümündeki örneğe bakın. Daha fazla bilgi için bkz <xref:System.Xml.Schema.XmlSchemaInfo> . sınıf başvurusu belgeleri.

## <a name="xmlschemavalidator-state-transition"></a>XmlSchemaValidator durum geçişi

<xref:System.Xml.Schema.XmlSchemaValidator>Sınıfında, BIR XML bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan yöntemlerin her birine yapılan çağrıların sırasını ve oluşumunu uygulayan tanımlı bir durum geçişi vardır.

Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaValidator> , sınıfının durum geçişi ve her durumda yapılabilecek Yöntem çağrılarının sırası ve oluşumu açıklanmaktadır.

|Durum|Transition|
|-----------|----------------|
|Doğrulama|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>( <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel *)<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|
|TopLevel|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>&#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; öğesi|
|Öğe|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* ( <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> İçerik \* )? <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>&#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> İçerik \* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;|
|İçerik|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>&#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; öğesi|

> [!NOTE]
> Bir <xref:System.InvalidOperationException> nesnenin geçerli durumuna göre yanlış sırada Yöntem çağrısı yapıldığında Yukarıdaki tablodaki yöntemlerin her biri tarafından oluşturulur <xref:System.Xml.Schema.XmlSchemaValidator> .

Yukarıdaki durum geçiş tablosu, sınıfının durum geçişinin her durumu için çağrılabilecek yöntemleri ve diğer durumları betimleyen noktalama sembolleri kullanır <xref:System.Xml.Schema.XmlSchemaValidator> . Kullanılan semboller, belge türü tanımı (DTD) için XML standartları başvurusunda bulunan sembollerdir.

Aşağıdaki tabloda, yukarıdaki durum geçiş tablosunda bulunan noktalama simgelerinin, sınıfının durum geçişi içindeki her durum için çağrılabilecek yöntemleri ve diğer durumları nasıl etkilediği açıklanır <xref:System.Xml.Schema.XmlSchemaValidator> .

|Sembol|Açıklama|
|------------|-----------------|
|&#124;|Ya Yöntem ya da durum (çubuk veya sonrasında bir veya sonrasında) çağrılabilir.|
|?|Soru işaretinden önce gelen yöntem veya durum isteğe bağlıdır, ancak çağrılırsa yalnızca bir kez çağrılabilir.|
|\*|Simgeden önceki yöntem veya durum \* isteğe bağlıdır ve birden çok kez çağrılabilir.|

## <a name="validation-context"></a>Doğrulama bağlamı

<xref:System.Xml.Schema.XmlSchemaValidator>BIR XML bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan sınıfının yöntemleri, bir nesnenin doğrulama bağlamını değiştirir <xref:System.Xml.Schema.XmlSchemaValidator> . Örneğin, <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> yöntemi geçerli öğe içeriğinin doğrulanmasını atlar ve <xref:System.Xml.Schema.XmlSchemaValidator> nesneyi üst öğenin bağlamındaki içeriği doğrulamaya hazırlar; geçerli öğenin tüm alt öğeleri için doğrulama atlanmak ve sonra yöntemi çağırmak eşdeğerdir <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> .

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Sınıfının, ve yöntemlerinin sonuçları, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> <xref:System.Xml.Schema.XmlSchemaValidator> doğrulanan geçerli bağlamına bağımlıdır.

Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaValidator> , BIR XML bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan sınıfının yöntemlerinden biri çağrıldıktan sonra bu yöntemleri çağırma sonuçları açıklanmaktadır.

|Yöntem|Getexlartedparçacıya|Getexeditedattributes|AddSchema|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntem çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> tüm genel öğeleri içeren bir dizi döndürür.<br /><br /> Bir <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> parametre olarak alan aşırı yüklenmiş yöntem <xref:System.Xml.Schema.XmlSchemaObject> bir öğenin kısmi doğrulanmasını başlatmak için çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yalnızca <xref:System.Xml.Schema.XmlSchemaValidator> nesnenin başlatıldığı öğeyi döndürür.|Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntem çağrılırsa <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.<br /><br /> Bir <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> <xref:System.Xml.Schema.XmlSchemaObject> özniteliğin kısmi doğrulanmasını başlatmak için bir parametre olarak alan yönteminin aşırı yüklemesi çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yalnızca <xref:System.Xml.Schema.XmlSchemaValidator> nesnenin başlatıldığı özniteliği döndürür.|<xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaValidator> Ön işleme hataları yoksa şemayı nesnenin öğesine ekler.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Bağlam öğesi geçerliyse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin alt öğeleri olarak beklenen öğe dizisini döndürür.<br /><br /> Bağlam öğesi geçersizse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.|Bağlam öğesi geçerliyse ve <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> daha önce yapılan bir çağrı yoksa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bağlam öğesinde tanımlanan tüm özniteliklerin bir listesini döndürür.<br /><br /> Bazı öznitelikler zaten doğrulandıktan sonra, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> doğrulanacak kalan özniteliklerin listesini döndürür.<br /><br /> Bağlam öğesi geçersizse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Bağlam özniteliği en üst düzey bir öznitelik ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.<br /><br /> Aksi halde, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin ilk alt öğesi olarak beklenen öğe dizisini döndürür.|Bağlam özniteliği en üst düzey bir öznitelik ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.<br /><br /> Aksi takdirde, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> doğrulanacak özniteliklerin listesini geri döndürür.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>bağlam öğesinin ilk alt öğesi olarak beklenen öğelerin dizisini döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>bağlam öğesi için henüz doğrulanamayan gerekli ve isteğe bağlı özniteliklerin listesini döndürür.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>bağlam öğesinin ilk alt öğesi olarak beklenen öğelerin dizisini döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>boş bir dizi döndürür.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Bağlam öğesinin contentType öğesi karmaysa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sonraki konumda beklenen öğelerin dizisini döndürür.<br /><br /> Bağlam öğesinin contentType öğesi TextOnly veya boşsa <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.<br /><br /> Bağlam öğesinin contentType öğesi Öğetonly ise, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bir sonraki konumda beklenen öğe dizisini döndürür, ancak bir doğrulama hatası zaten oluştu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>bağlam öğesinin doğrulanmadı özniteliklerin listesini döndürür.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Bağlam beyaz alanı üst düzey boşluk ise, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.<br /><br /> Aksi halde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemin davranışı ile aynıdır <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> .|Bağlam beyaz alanı üst düzey boşluk ise, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.<br /><br /> Aksi halde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemin davranışı ile aynıdır <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> .|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>bağlam öğesinden (olası eşdüzey öğeler) sonra beklenen öğe dizisini döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>bağlam öğesinin doğrulanmadı özniteliklerin listesini döndürür.<br /><br /> Bağlam öğesinin üst öğesi yoksa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir liste döndürür (bağlam öğesi, üzerinde çağrılan geçerli öğenin üst öğesidir <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> ).|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> .|Aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> .|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Boş bir dizi döndürür.|Boş bir dizi döndürür.|Yukarıdaki gibi.|

> [!NOTE]
> Sınıfın çeşitli özelliklerinin döndürdüğü değerler <xref:System.Xml.Schema.XmlSchemaValidator> Yukarıdaki tablodaki yöntemlerden herhangi biri çağırarak değiştirilmez.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Schema.XmlSchemaValidator>
