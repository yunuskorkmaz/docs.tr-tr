---
title: XmlSchemaValidator Gönderim Temelli Doğrulaması
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a420a134eda6c62758b0d218e3c0a4a4922b048c
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250051"
---
# <a name="xmlschemavalidator-push-based-validation"></a>XmlSchemaValidator Gönderim Temelli Doğrulaması

<xref:System.Xml.Schema.XmlSchemaValidator> sınıfı, XML verilerini gönderme temelli bir şekilde XML şemalarına karşı doğrulamak için etkili ve yüksek performanslı bir mekanizma sağlar. Örneğin, <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı bir XML bilgisi kümesini bir XML belgesi olarak serileştirmek ve ardından belgeyi bir doğrulama XML okuyucusu kullanarak yeniden yerleştirmek zorunda kalmadan, yerinde doğrulamanızı sağlar.

<xref:System.Xml.Schema.XmlSchemaValidator> sınıfı, özel XML veri kaynakları üzerinde doğrulama motorları oluşturma veya bir doğrulama XML yazıcısı oluşturmak için bir yol gibi Gelişmiş senaryolarda kullanılabilir.

Aşağıda, `contosoBooks.xml` dosyasını `contosoBooks.xsd` şemasına karşı doğrulamak için <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının kullanılmasına bir örnek verilmiştir. Örnek, `contosoBooks.xml` dosyasının serisini kaldırmak ve düğümlerin değerini <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının yöntemlerine geçirmek için <xref:System.Xml.Serialization.XmlSerializer> sınıfını kullanır.

> [!NOTE]
> Bu örnek, bu konunun bölümleri boyunca kullanılır.

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

Örnek ayrıca `contosoBooks.xsd` giriş olarak alır.

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

Bir XML bilgi kümesini doğrulamaya başlamak için önce <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> oluşturucuyu kullanarak <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının yeni bir örneğini başlatmalısınız.

<xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Oluşturucu <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>ve <xref:System.Xml.XmlNamespaceManager> nesneleri parametre olarak ve bir <xref:System.Xml.Schema.XmlSchemaValidationFlags> değeri de parametre olarak alır. <xref:System.Xml.XmlNameTable> nesnesi, şema ad alanı, XML ad alanı vb. gibi iyi bilinen ad alanı dizelerini ayrılamaz ve basit içerik doğrulanırken <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> yöntemine geçirilir. <xref:System.Xml.Schema.XmlSchemaSet> nesnesi, XML bilgi kümesini doğrulamak için kullanılan XML şemalarını içerir. <xref:System.Xml.XmlNamespaceManager> nesnesi, doğrulama sırasında karşılaşılan ad alanlarını çözümlemek için kullanılır. <xref:System.Xml.Schema.XmlSchemaValidationFlags> değeri, doğrulamanın belirli özelliklerini devre dışı bırakmak için kullanılır.

<xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Oluşturucusu hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.

### <a name="initializing-validation"></a>Doğrulama başlatılıyor

Bir <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi oluşturulduktan sonra, <xref:System.Xml.Schema.XmlSchemaValidator> nesnesinin durumunu başlatmak için kullanılan iki aşırı yüklenmiş <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi vardır. İki <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi aşağıda verilmiştir.

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yöntemi, başlangıç durumuna bir <xref:System.Xml.Schema.XmlSchemaValidator> nesnesini başlatır ve bir <xref:System.Xml.Schema.XmlSchemaObject> parametre olarak alan aşırı yüklenmiş <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yöntemi, kısmi doğrulamanın başlangıç durumuna bir <xref:System.Xml.Schema.XmlSchemaValidator> nesnesini başlatır.

<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemlerinin her ikisi de yalnızca bir <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi oluşturulduktan sonra veya <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>çağrısından sonra çağrılabilir.

<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yöntemine bir örnek için, giriş bölümündeki örneğe bakın. <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.

#### <a name="partial-validation"></a>Kısmi doğrulama

Parametre olarak bir <xref:System.Xml.Schema.XmlSchemaObject> alan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yöntemi, kısmi doğrulama için bir <xref:System.Xml.Schema.XmlSchemaValidator> nesnesini başlangıç durumuna başlatır.

Aşağıdaki örnekte, bir <xref:System.Xml.Schema.XmlSchemaObject> <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yöntemi kullanılarak kısmi doğrulama için başlatılır. `orderNumber` şeması öğesi, <xref:System.Xml.Schema.XmlSchemaSet> nesnesinin <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> özelliği tarafından döndürülen <xref:System.Xml.Schema.XmlSchemaObjectTable> koleksiyonundaki <xref:System.Xml.XmlQualifiedName> şema öğesi seçilerek geçirilir. <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi bundan sonra bu özel öğeyi doğrular.

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

<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.

### <a name="adding-additional-schemas"></a>Ek şemalar ekleme

<xref:System.Xml.Schema.XmlSchemaValidator> sınıfının <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemi, doğrulama sırasında kullanılan şemalar kümesine bir XML şeması eklemek için kullanılır. <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemi, doğrulanan XML bilgi kümesindeki bir satır içi XML şeması ile karşılaşanın etkisinin benzetimini yapmak için kullanılabilir.

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchema> parametresinin hedef ad alanı, <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi tarafından zaten karşılaşılan hiçbir öğe veya özniteliğe uymuyor.
>
> <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> değeri <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> oluşturucusuna parametre olarak geçirilmemişse, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemi hiçbir şey yapmaz.

<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yönteminin sonucu, doğrulanan geçerli XML düğümü bağlamına bağlıdır. Doğrulama bağlamları hakkında daha fazla bilgi için bu konunun "doğrulama bağlamı" bölümüne bakın.

<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.

### <a name="validating-elements-attributes-and-content"></a>Öğeleri, öznitelikleri ve Içeriği doğrulama

<xref:System.Xml.Schema.XmlSchemaValidator> sınıfı, XML şemalarında xml bilgi kümesindeki öğeleri, öznitelikleri ve içerikleri doğrulamak için kullanılan çeşitli yöntemler sunar. Aşağıdaki tabloda bu yöntemlerin her biri açıklanmaktadır.

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Geçerli bağlamdaki öğe adını doğrular.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Geçerli öğe bağlamındaki özniteliği veya <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemine parametre olarak geçirilen <xref:System.Xml.Schema.XmlSchemaAttribute> nesnesine karşı doğrular.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|Öğe bağlamındaki tüm gerekli özniteliklerin mevcut olup olmadığını doğrular ve öğenin alt içeriğini doğrulamak için <xref:System.Xml.Schema.XmlSchemaValidator> nesnesini hazırlar.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Geçerli öğe bağlamında metnin izin verilip verilmeyeceğini doğrular ve geçerli öğede basit içerik varsa doğrulama için metni biriktirir.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Geçerli öğe bağlamında beyaz boşluğa izin verilip verilmeyeceğini doğrular ve geçerli öğenin basit içeriğe sahip olup olmadığını doğrulamak için beyaz boşluğu biriktirir.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|Öğenin metin içeriğinin basit içeriğe sahip öğeler için kendi veri türüne göre geçerli olup olmadığını doğrular ve karmaşık içerikli öğeler için geçerli öğenin içeriğinin tamamlanıp tamamlanmadığını doğrular.|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Geçerli öğe içeriğini doğrulamayı atlar ve üst öğenin bağlamındaki içeriği doğrulamak için <xref:System.Xml.Schema.XmlSchemaValidator> nesnesini hazırlar.|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> doğrulama seçeneği ayarlandıysa, doğrulamayı sonlandırır ve tüm XML belgesi için kimlik kısıtlamalarını denetler.|

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı, önceki tabloda açıklanan yöntemlerin her birine yapılan çağrıların sırasını ve tekrarını uygulayan tanımlı bir durum geçişine sahiptir. <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının belirli durum geçişi, bu konunun "XmlSchemaValidator durum geçişi" bölümünde açıklanmaktadır.

Bir XML bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan yöntemlere örnek olarak, önceki bölümde bulunan örneğe bakın. Bu yöntemler hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı başvuru belgelerine bakın.

#### <a name="validating-content-using-an-xmlvaluegetter"></a>XmlValueGetter kullanarak Içerik doğrulanıyor

<xref:System.Xml.Schema.XmlValueGetter>`delegate`, öznitelik, metin veya boşluk düğümlerinin değerini öznitelik, metin veya boşluk düğümünün XML şeması tanım dili (XSD) türüyle uyumlu ortak dil çalışma zamanı (CLR) türleri olarak geçirmek için kullanılabilir. Bir özniteliğin, metnin veya boşluk düğümünün CLR değeri zaten kullanılabiliyorsa, bir <xref:System.Xml.Schema.XmlValueGetter>`delegate` yararlıdır ve bunu bir `string` dönüştürmenin ve daha sonra doğrulama için yeniden ayrıştırmanın maliyetini önler.

<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>ve <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> Yöntemler aşırı yüklenmiş ve `string` veya <xref:System.Xml.Schema.XmlValueGetter>`delegate`olarak öznitelik, metin veya boşluk düğümlerinin değerini kabul eder.

<xref:System.Xml.Schema.XmlSchemaValidator> sınıfının aşağıdaki yöntemleri bir <xref:System.Xml.Schema.XmlValueGetter>`delegate` parametre olarak kabul eder.

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

Aşağıda, giriş içindeki <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı örneğinde alınan `delegate` bir örnek <xref:System.Xml.Schema.XmlValueGetter>verilmiştir. <xref:System.Xml.Schema.XmlValueGetter>`delegate` bir özniteliğin değerini <xref:System.DateTime> nesnesi olarak döndürür. <xref:System.Xml.Schema.XmlValueGetter>tarafından döndürülen bu <xref:System.DateTime> nesnesini doğrulamak için, <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi değeri özniteliğin veri türü için önce ValueType öğesine dönüştürür (ValueType, XSD türü için varsayılan CLR eşlemedir) ve ardından dönüştürülen değer üzerindeki modelleri denetler.

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

<xref:System.Xml.Schema.XmlValueGetter>`delegate`hakkında daha fazla örnek için, giriş bölümündeki örneğe bakın. <xref:System.Xml.Schema.XmlValueGetter>`delegate`hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlValueGetter>ve <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı başvuru belgelerine bakın.

#### <a name="post-schema-validation-information"></a>Şema sonrası doğrulama-bilgi

<xref:System.Xml.Schema.XmlSchemaInfo> sınıfı, <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı tarafından doğrulanan bir XML düğümünün şema sonrası-doğrulama bilgilerinin bazılarını temsil eder. <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının çeşitli yöntemleri <xref:System.Xml.Schema.XmlSchemaInfo> nesnesini isteğe bağlı, (`null`) `out` parametresi olarak kabul eder.

Doğrulama başarılı olduğunda, <xref:System.Xml.Schema.XmlSchemaInfo> nesnesinin özellikleri doğrulamanın sonuçlarıyla ayarlanır. Örneğin, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntemi kullanılarak bir özniteliğin başarıyla doğrulanması sırasında, <xref:System.Xml.Schema.XmlSchemaInfo> nesnesinin (belirtilmişse) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>ve <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> özellikleri doğrulamanın sonuçlarıyla ayarlanır.

Aşağıdaki <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı yöntemleri bir <xref:System.Xml.Schema.XmlSchemaInfo> nesnesini out parametresi olarak kabul eder.

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

<xref:System.Xml.Schema.XmlSchemaInfo> sınıfının tamamen bir örneği için bkz. giriş bölümündeki örnek. <xref:System.Xml.Schema.XmlSchemaInfo> sınıfı hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaInfo> sınıf başvurusu belgeleri.

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a>Beklenen parçacık, öznitelik ve belirtilmemiş varsayılan öznitelikleri alma

<xref:System.Xml.Schema.XmlSchemaValidator> sınıfı, geçerli doğrulama bağlamında beklenen parçacıkların, özniteliklerin ve belirtilmemiş varsayılan özniteliklerin alınması için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>ve <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> yöntemleri sağlar.

#### <a name="retrieving-expected-particles"></a>Beklenen parçacık alınıyor

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi, geçerli öğe bağlamında beklenen parçacıkların bulunduğu <xref:System.Xml.Schema.XmlSchemaParticle> nesnelerden oluşan bir dizi döndürür. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi tarafından döndürülebilecek geçerli parçacık <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAny> sınıflarının örnekleridir.

İçerik modeli için Oluşturucu bir `xs:sequence`olduğunda, yalnızca dizideki bir sonraki parçacık döndürülür. İçerik modeli için Oluşturucu bir `xs:all` veya bir `xs:choice`ise, geçerli öğe bağlamında izleyelebilecek tüm geçerli parçacık döndürülür.

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi, <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi çağrıldıktan hemen sonra çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi tüm genel öğeleri döndürür.

Örneğin, XML şeması tanım dili (XSD) şeması ve izleyen XML belgesinde, `book` öğesi doğrulandıktan sonra, `book` öğesi geçerli öğe bağlamıdır. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi `title` öğesini temsil eden tek bir <xref:System.Xml.Schema.XmlSchemaElement> nesnesi içeren bir dizi döndürür. Doğrulama bağlamı `title` öğesi olduğunda, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi boş bir dizi döndürür. `title` öğesi doğrulandıktan sonra, ancak `description` öğesi doğrulandıktan sonra <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi çağrılırsa, `description` öğesini temsil eden tek bir <xref:System.Xml.Schema.XmlSchemaElement> nesnesi içeren bir dizi döndürür. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi `description` öğesi doğrulandıktan sonra çağrılırsa, joker karakteri temsil eden tek bir <xref:System.Xml.Schema.XmlSchemaAny> nesnesi içeren bir dizi döndürür.

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
> <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin sonuçları, doğrulanan geçerli bağlamına bağımlıdır. Daha fazla bilgi için bu konunun "doğrulama bağlamı" bölümüne bakın.

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemine bir örnek için, giriş bölümündeki örneğe bakın. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.

#### <a name="retrieving-expected-attributes"></a>Beklenen öznitelikleri alma

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi, geçerli öğe bağlamında beklenen öznitelikleri içeren bir <xref:System.Xml.Schema.XmlSchemaAttribute> nesneleri dizisi döndürüyor.

Örneğin, giriş bölümündeki örnekte, `book` öğesinin tüm özniteliklerini almak için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi kullanılır.

<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> yönteminden hemen sonra <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemini çağırırsanız, XML belgesinde görünebilen tüm öznitelikler döndürülür. Ancak, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntemine yapılan bir veya daha fazla çağrıdan sonra <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemini çağırırsanız, geçerli öğe için henüz doğrulanmamış öznitelikler döndürülür.

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin sonuçları, doğrulanan geçerli bağlamına bağımlıdır. Daha fazla bilgi için bu konunun "doğrulama bağlamı" bölümüne bakın.

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemine bir örnek için, giriş bölümündeki örneğe bakın. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.

#### <a name="retrieving-unspecified-default-attributes"></a>Belirtilmeyen varsayılan öznitelikler alınıyor

<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> yöntemi, daha önce öğe bağlamındaki <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntemi kullanılarak doğrulanmamış varsayılan değerlere sahip tüm öznitelikler için <xref:System.Xml.Schema.XmlSchemaAttribute> nesneleriyle belirtilen <xref:System.Collections.ArrayList> doldurur. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> yöntemi, öğe bağlamındaki her bir öznitelikte <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntemi çağrıldıktan sonra çağrılmalıdır. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> yöntemi, doğrulanan XML belgesine hangi varsayılan özniteliklerin ekleneceğini belirlemek için kullanılmalıdır.

<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.

### <a name="handling-schema-validation-events"></a>Şema doğrulama olaylarını işleme

Şema doğrulama uyarıları ve doğrulama sırasında karşılaşılan hatalar <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> olayı tarafından işlenir.

Şema doğrulama uyarıları <xref:System.Xml.Schema.XmlSeverityType> bir <xref:System.Xml.Schema.XmlSeverityType.Warning> değerine sahiptir ve şema doğrulama hatalarının <xref:System.Xml.Schema.XmlSeverityType.Error><xref:System.Xml.Schema.XmlSeverityType> değeri vardır. <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> atanmamışsa, <xref:System.Xml.Schema.XmlSeverityType.Error><xref:System.Xml.Schema.XmlSeverityType> değeri olan tüm şema doğrulama hataları için bir <xref:System.Xml.Schema.XmlSchemaValidationException> oluşturulur. Ancak, <xref:System.Xml.Schema.XmlSeverityType.Warning><xref:System.Xml.Schema.XmlSeverityType> değeri olan şema doğrulama uyarıları için <xref:System.Xml.Schema.XmlSchemaValidationException> oluşturulmaz.

Aşağıda, giriş içindeki örnekte alınan şema doğrulama uyarılarını ve şema doğrulama sırasında karşılaşılan hataları alan bir <xref:System.Xml.Schema.ValidationEventHandler> örneği verilmiştir.

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

<xref:System.Xml.Schema.ValidationEventHandler>için tüm bir örnek için, giriş bölümündeki örneğe bakın. Daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaInfo> sınıfı başvuru belgelerine bakın.

## <a name="xmlschemavalidator-state-transition"></a>XmlSchemaValidator durum geçişi

<xref:System.Xml.Schema.XmlSchemaValidator> sınıfı, bir XML bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan yöntemlerin her birine yapılan çağrıların sırasını ve oluşumunu uygulayan tanımlı bir durum geçişine sahiptir.

Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının durum geçişi ve her durumda yapılabilecek Yöntem çağrılarının sırası ve oluşumu açıklanmaktadır.

|Durum|Transition|
|-----------|----------------|
|doğrulamalısınız|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel *) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|
|TopLevel|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; öğesi|
|Öğe|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Içerik\*) <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>? <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Içerik\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>&#124;|
|İçerik|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; öğesi|

> [!NOTE]
> Bir <xref:System.InvalidOperationException>, yukarıdaki tablodaki her bir yöntem tarafından bir <xref:System.Xml.Schema.XmlSchemaValidator> nesnesinin geçerli durumuna göre yanlış sırada yapıldığında oluşur.

Yukarıdaki durum geçiş tablosu, <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının durum geçişinin her durumu için çağrılabilecek yöntemleri ve diğer durumları anlatmak için noktalama sembolleri kullanır. Kullanılan semboller, belge türü tanımı (DTD) için XML standartları başvurusunda bulunan sembollerdir.

Aşağıdaki tabloda, yukarıdaki durum geçiş tablosunda bulunan noktalama simgelerinin, <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının durum geçişi içindeki her durum için çağrılabilecek yöntemleri ve diğer durumları nasıl etkilediği açıklanır.

|Sembol|Açıklama|
|------------|-----------------|
|&#124;|Ya Yöntem ya da durum (çubuk veya sonrasında bir veya sonrasında) çağrılabilir.|
|?|Soru işaretinden önce gelen yöntem veya durum isteğe bağlıdır, ancak çağrılırsa yalnızca bir kez çağrılabilir.|
|*|\* Simgesinden önce gelen yöntem veya durum isteğe bağlıdır ve birden çok kez çağrılabilir.|

## <a name="validation-context"></a>Doğrulama bağlamı

Bir XML bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının yöntemleri, bir <xref:System.Xml.Schema.XmlSchemaValidator> nesnesinin doğrulama bağlamını değiştirir. Örneğin <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> yöntemi, geçerli öğe içeriğinin doğrulanmasını atlar ve üst öğenin bağlamındaki içeriği doğrulamak için <xref:System.Xml.Schema.XmlSchemaValidator> nesnesini hazırlar; geçerli öğenin tüm alt öğeleri için doğrulama atlanmak ve sonra <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> yöntemi çağırmak eşdeğerdir.

<xref:System.Xml.Schema.XmlSchemaValidator> sınıfının <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin sonuçları, doğrulanan geçerli bağlamına bağımlıdır.

Aşağıdaki tabloda, bir XML bilgi kümesindeki öğeleri, öznitelikleri ve içerikleri doğrulamak için kullanılan <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının yöntemlerinden biri çağrıldıktan sonra bu yöntemleri çağırma sonuçları açıklanmaktadır.

|Yöntem|Getexlartedparçacıya|Getexeditedattributes|AddSchema|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> tüm genel öğeleri içeren bir dizi döndürür.<br /><br /> Bir <xref:System.Xml.Schema.XmlSchemaObject> bir parametre olarak alan aşırı yüklenmiş <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi bir öğenin kısmi doğrulanmasını başlatmak için çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yalnızca <xref:System.Xml.Schema.XmlSchemaValidator> nesnesinin başlatıldığı öğeyi döndürür.|Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.<br /><br /> Bir parametre olarak bir <xref:System.Xml.Schema.XmlSchemaObject> alan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yönteminin aşırı yüklemesi, bir özniteliğin kısmi doğrulanmasını başlatmak için çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yalnızca <xref:System.Xml.Schema.XmlSchemaValidator> nesnesinin başlatıldığı özniteliği döndürür.|Ön işleme hataları yoksa şemayı <xref:System.Xml.Schema.XmlSchemaValidator> nesnesinin <xref:System.Xml.Schema.XmlSchemaSet> ekler.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Bağlam öğesi geçerliyse <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, bağlam öğesinin alt öğeleri olarak beklenen öğelerin dizisini döndürür.<br /><br /> Bağlam öğesi geçersizse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.|Bağlam öğesi geçerliyse ve daha önce <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> çağrısı yapılmazsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bağlam öğesinde tanımlanan tüm özniteliklerin bir listesini döndürür.<br /><br /> Bazı öznitelikler zaten doğrulandıktan sonra, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> doğrulanacak kalan özniteliklerin bir listesini döndürür.<br /><br /> Bağlam öğesi geçersizse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Bağlam özniteliği en üst düzey bir özniteliktir, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.<br /><br /> Aksi takdirde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, bağlam öğesinin ilk alt öğesi olarak beklenen öğelerin dizisini döndürür.|Bağlam özniteliği en üst düzey bir özniteliktir, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.<br /><br /> Aksi takdirde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> doğrulanacak kalan özniteliklerin listesini döndürür.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, bağlam öğesinin ilk alt öğesi olarak beklenen öğelerin dizisini döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, henüz bağlam öğesi için doğrulanamayan gerekli ve isteğe bağlı özniteliklerin bir listesini döndürür.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, bağlam öğesinin ilk alt öğesi olarak beklenen öğelerin dizisini döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Bağlam öğesinin contentType öğesi karmaysa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sonraki konumda beklenen öğelerin dizisini döndürür.<br /><br /> Bağlam öğesinin contentType öğesi TextOnly veya boşsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.<br /><br /> Bağlam öğesinin contentType öğesi Öğetonly ise, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sonraki konumda beklenen öğelerin dizisini döndürür, ancak bir doğrulama hatası zaten oluştu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, bağlam öğesinin doğrulanmadı özniteliklerin listesini döndürür.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Bağlam beyaz alanı üst düzey boşluk ise, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.<br /><br /> Aksi takdirde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yönteminin davranışı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>ile aynıdır.|Bağlam beyaz alanı üst düzey boşluk ise, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.<br /><br /> Aksi takdirde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yönteminin davranışı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>ile aynıdır.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, bağlam öğesinden (olası eşdüzey öğeler) sonra beklenen öğelerin dizisini döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, bağlam öğesinin doğrulanmadı özniteliklerin listesini döndürür.<br /><br /> Bağlam öğesinin üst öğesi yoksa <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir liste döndürür (bağlam öğesi <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> çağrıldığı geçerli öğenin üst öğesidir).|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>ile aynı.|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>ile aynı.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Boş bir dizi döndürür.|Boş bir dizi döndürür.|Yukarıdaki gibi.|

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının çeşitli özelliklerinin döndürdüğü değerler yukarıdaki tablodaki yöntemlerden herhangi biri çağırarak değiştirilmez.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Schema.XmlSchemaValidator>
