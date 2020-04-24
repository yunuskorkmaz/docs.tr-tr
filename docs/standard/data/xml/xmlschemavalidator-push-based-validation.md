---
title: XmlSchemaValidator Gönderim Temelli Doğrulaması
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
ms.openlocfilehash: 6a0cc110c2b8bcd97b9f5c16a344db5a63046353
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709809"
---
# <a name="xmlschemavalidator-push-based-validation"></a>XmlSchemaValidator Gönderim Temelli Doğrulaması

Sınıfı <xref:System.Xml.Schema.XmlSchemaValidator> , XML verilerini gönderme temelli BIR şekilde XML şemalarına karşı doğrulamak için etkili ve yüksek performanslı bir mekanizma sağlar. Örneğin <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı, bir XML bilgisi KÜMESINI bir XML belgesi olarak seri hale getirmek ve ardından belgeyi BIR doğrulama XML okuyucusu kullanarak yeniden yerleştirmek zorunda kalmadan, yerinde doğrulamanızı sağlar.

Sınıfı <xref:System.Xml.Schema.XmlSchemaValidator> , özel XML veri kaynakları üzerinde doğrulama motorları oluşturmak veya BIR doğrulama XML yazıcısı oluşturmak için bir yol olarak, Gelişmiş senaryolarda kullanılabilir.

Aşağıda, <xref:System.Xml.Schema.XmlSchemaValidator> `contosoBooks.xml` dosyayı `contosoBooks.xsd` şemaya karşı doğrulamak için sınıfının kullanılmasına bir örnek verilmiştir. Örnek, <xref:System.Xml.Serialization.XmlSerializer> `contosoBooks.xml` dosyanın serisini kaldırmak ve düğümlerin değerini <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının yöntemlerine geçirmek için sınıfını kullanır.

> [!NOTE]
> Bu örnek, bu konunun bölümleri boyunca kullanılır.

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

Örnek, `contosoBooks.xml` dosyayı giriş olarak alır.

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

Örnek de bir giriş `contosoBooks.xsd` olarak alır.

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

Bir XML bilgi kümesini doğrulamaya başlamak için, önce <xref:System.Xml.Schema.XmlSchemaValidator> <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> oluşturucuyu kullanarak sınıfının yeni bir örneğini başlatmalısınız.

<xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Oluşturucu, <xref:System.Xml.Schema.XmlSchemaSet>ve <xref:System.Xml.XmlNameTable> <xref:System.Xml.Schema.XmlSchemaValidationFlags> değerlerini parametre olarak <xref:System.Xml.XmlNamespaceManager> ve bir parametresi olarak alır. <xref:System.Xml.XmlNameTable> Nesnesi, şema ad alanı, XML ad alanı vb. gibi iyi bilinen ad alanı dizelerini ayrılamaz ve basit içerik doğrulanırken <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> yöntemine geçirilir. <xref:System.Xml.Schema.XmlSchemaSet> NESNESI, XML bilgi kümesini doğrulamak IÇIN kullanılan XML şemalarını içerir. Nesne <xref:System.Xml.XmlNamespaceManager> , doğrulama sırasında karşılaşılan ad alanlarını çözümlemek için kullanılır. Bu <xref:System.Xml.Schema.XmlSchemaValidationFlags> değer, doğrulamanın belirli özelliklerini devre dışı bırakmak için kullanılır.

<xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Oluşturucu hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.

### <a name="initializing-validation"></a>Doğrulama başlatılıyor

Bir <xref:System.Xml.Schema.XmlSchemaValidator> nesne oluşturulduktan sonra, <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> <xref:System.Xml.Schema.XmlSchemaValidator> nesnenin durumunu başlatmak için kullanılan iki aşırı yüklenmiş yöntem vardır. Aşağıdaki iki <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntem vardır.

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Varsayılan yöntem, bir <xref:System.Xml.Schema.XmlSchemaValidator> nesneyi başlangıç durumuna başlatır ve bir parametresi <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> <xref:System.Xml.Schema.XmlSchemaObject> olarak alan aşırı yüklenmiş yöntem, kısmi doğrulama için bir <xref:System.Xml.Schema.XmlSchemaValidator> nesneyi başlangıç durumuna başlatır.

Her <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> iki yöntem de yalnızca bir <xref:System.Xml.Schema.XmlSchemaValidator> nesne oluşturulduktan sonra veya bir çağrısından sonra çağrılabilir <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.

<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Yöntemine bir örnek için, giriş bölümündeki örneğe bakın. <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> Yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.

#### <a name="partial-validation"></a>Kısmi doğrulama

Bir <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> parametre <xref:System.Xml.Schema.XmlSchemaObject> olarak alan yöntemi, kısmi doğrulama için bir <xref:System.Xml.Schema.XmlSchemaValidator> nesneyi başlangıç durumuna başlatır.

Aşağıdaki örnekte, <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yöntemi kullanılarak kısmi <xref:System.Xml.Schema.XmlSchemaObject> doğrulama için bir başlatılır. `orderNumber` Şema <xref:System.Xml.XmlQualifiedName> öğesi, <xref:System.Xml.Schema.XmlSchemaObjectTable> <xref:System.Xml.Schema.XmlSchemaSet> nesnesinin <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> özelliği tarafından döndürülen koleksiyonda tarafından şema öğesi seçilerek geçirilir. <xref:System.Xml.Schema.XmlSchemaValidator> Nesne daha sonra bu özel öğeyi doğrular.

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

<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> Yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.

### <a name="adding-additional-schemas"></a>Ek şemalar ekleme

<xref:System.Xml.Schema.XmlSchemaValidator> Sınıfının <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemi, doğrulama sırasında kullanılan şemalar kümesine bir XML şeması eklemek için kullanılır. <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Yöntemi, doğrulanan xml bilgi kümesindeki bir satır içi xml şeması ile karşılaşanın etkisinin benzetimini yapmak için kullanılabilir.

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchema> Parametrenin hedef ad alanı, <xref:System.Xml.Schema.XmlSchemaValidator> nesne tarafından zaten karşılaşılan hiçbir öğe veya öznitelikle eşleşmiyor.
>
> <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> Değer, <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> oluşturucuya bir parametre olarak geçirilmemişse, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntem hiçbir şey yapmaz.

<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Yöntemin sonucu, DOĞRULANAN geçerli XML düğümü bağlamına bağlıdır. Doğrulama bağlamları hakkında daha fazla bilgi için bu konunun "doğrulama bağlamı" bölümüne bakın.

<xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.

### <a name="validating-elements-attributes-and-content"></a>Öğeleri, öznitelikleri ve Içeriği doğrulama

<xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı, XML şemalarında xml bilgi kümesindeki öğeleri, öznitelikleri ve içerikleri doğrulamak için kullanılan çeşitli yöntemler sağlar. Aşağıdaki tabloda bu yöntemlerin her biri açıklanmaktadır.

|Yöntem|Açıklama|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Geçerli bağlamdaki öğe adını doğrular.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Geçerli öğe bağlamındaki özniteliği veya <xref:System.Xml.Schema.XmlSchemaAttribute> <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemine parametre olarak geçirilen nesneye karşı doğrular.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|Öğe bağlamındaki tüm gerekli özniteliklerin mevcut olup olmadığını doğrular ve <xref:System.Xml.Schema.XmlSchemaValidator> nesneyi öğenin alt içeriğini doğrulamak üzere hazırlar.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Geçerli öğe bağlamında metnin izin verilip verilmeyeceğini doğrular ve geçerli öğede basit içerik varsa doğrulama için metni biriktirir.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Geçerli öğe bağlamında beyaz boşluğa izin verilip verilmeyeceğini doğrular ve geçerli öğenin basit içeriğe sahip olup olmadığını doğrulamak için beyaz boşluğu biriktirir.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|Öğenin metin içeriğinin basit içeriğe sahip öğeler için kendi veri türüne göre geçerli olup olmadığını doğrular ve karmaşık içerikli öğeler için geçerli öğenin içeriğinin tamamlanıp tamamlanmadığını doğrular.|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Geçerli öğe içeriğinin geçerliliğini atlar ve üst öğenin bağlamındaki içeriği <xref:System.Xml.Schema.XmlSchemaValidator> doğrulamak için nesneyi hazırlar.|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Doğrulama seçeneği ayarlandıysa, doğrulamayı sonlandırır ve tüm XML belgesi <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> için kimlik kısıtlamalarını denetler.|

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaValidator> Sınıfında, önceki tabloda açıklanan yöntemlerin her birine yapılan çağrıların sırasını ve tekrarını uygulayan tanımlı bir durum geçişi vardır. <xref:System.Xml.Schema.XmlSchemaValidator> Sınıfın belirli durum geçişi, bu konunun "XmlSchemaValidator durum geçişi" bölümünde açıklanmaktadır.

Bir XML bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan yöntemlere örnek olarak, önceki bölümde bulunan örneğe bakın. Bu yöntemler hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.

#### <a name="validating-content-using-an-xmlvaluegetter"></a>XmlValueGetter kullanarak Içerik doğrulanıyor

<xref:System.Xml.Schema.XmlValueGetter> Öznitelik, metin veya boşluk düğümlerinin değerini öznitelik, metin veya boşluk düğümünün XML şeması tanım dili (xsd) türüyle uyumlu ortak dil çalışma zamanı (CLR) türleri olarak geçirmek için `delegate` kullanılabilir. Bir <xref:System.Xml.Schema.XmlValueGetter> `delegate` özniteliğin, metnin veya boşluk düğümünün clr değeri zaten kullanılabilirse ve bunu bir `string` ve daha sonra doğrulama için yeniden ayrıştırmanın maliyetini önlediği durumlarda yararlıdır.

<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>,, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> Ve yöntemleri aşırı yüklenmiş ve öznitelik, metin veya boşluk düğümlerinin değeri `string` veya <xref:System.Xml.Schema.XmlValueGetter> `delegate`olarak kabul edilir.

<xref:System.Xml.Schema.XmlSchemaValidator> Sınıfının aşağıdaki yöntemleri bir parametre <xref:System.Xml.Schema.XmlValueGetter> `delegate` olarak kabul eder.

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

Aşağıda, giriş içindeki <xref:System.Xml.Schema.XmlValueGetter> `delegate` <xref:System.Xml.Schema.XmlSchemaValidator> sınıf örneğinizden alınan bir örnek verilmiştir. , <xref:System.Xml.Schema.XmlValueGetter> `delegate` Bir özniteliğin değerini bir <xref:System.DateTime> nesne olarak döndürür. Tarafından döndürülen bu <xref:System.DateTime> nesneyi doğrulamak için <xref:System.Xml.Schema.XmlValueGetter>, <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi, özniteliğin veri türü için önce onu ValueType öğesine dönüştürür (ValueType, xsd türü için varsayılan clr eşlemedir) ve ardından dönüştürülen değer üzerindeki modelleri denetler.

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

Öğesinin <xref:System.Xml.Schema.XmlValueGetter> `delegate`tamamen bir örneği için giriş bölümündeki örneğe bakın. Hakkında <xref:System.Xml.Schema.XmlValueGetter> `delegate`daha fazla bilgi için, ve <xref:System.Xml.Schema.XmlValueGetter> <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerine bakın.

#### <a name="post-schema-validation-information"></a>Şema sonrası doğrulama-bilgi

<xref:System.Xml.Schema.XmlSchemaInfo> Sınıfı, <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı tarafından doğrulanan bir XML düğümünün şema sonrası-doğrulama bilgilerinin bazılarını temsil eder. <xref:System.Xml.Schema.XmlSchemaValidator> Sınıfının çeşitli yöntemleri bir <xref:System.Xml.Schema.XmlSchemaInfo> nesneyi isteğe bağlı, (`null`) `out` parametre olarak kabul eder.

Doğrulama başarılı olduğunda, <xref:System.Xml.Schema.XmlSchemaInfo> nesnesinin özellikleri doğrulamanın sonuçlarıyla ayarlanır. <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> Örneğin, <xref:System.Xml.Schema.XmlSchemaInfo> yöntemini kullanarak bir özniteliğin başarıyla doğrulanması sırasında, nesnenin (belirtilmişse) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>ve <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> özellikleri doğrulamanın sonuçlarıyla ayarlanır.

Aşağıdaki <xref:System.Xml.Schema.XmlSchemaValidator> sınıf yöntemleri bir <xref:System.Xml.Schema.XmlSchemaInfo> nesneyi out parametresi olarak kabul eder.

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

<xref:System.Xml.Schema.XmlSchemaInfo> Sınıfının tamamen bir örneği için, giriş bölümündeki örneğe bakın. <xref:System.Xml.Schema.XmlSchemaInfo> Sınıfı hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaInfo> sınıf başvurusu belgeleri.

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a>Beklenen parçacık, öznitelik ve belirtilmemiş varsayılan öznitelikleri alma

<xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, geçerli doğrulama bağlamında <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>beklenen parçacıkların, özniteliklerin ve belirtilmemiş varsayılan özniteliklerin alınması için, ve <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> yöntemlerini sağlar.

#### <a name="retrieving-expected-particles"></a>Beklenen parçacık alınıyor

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemi, geçerli öğe bağlamında beklenen <xref:System.Xml.Schema.XmlSchemaParticle> parçacık içeren bir nesne dizisi döndürür. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemi tarafından döndürülebilecek geçerli parçacık, <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAny> sınıflarının örnekleridir.

İçerik modeli için Oluşturucu bir `xs:sequence`ise, yalnızca dizideki bir sonraki parçacık döndürülür. İçerik modeli için Oluşturucu bir `xs:all` veya ise `xs:choice`, geçerli öğe bağlamında izleyelebilecek tüm geçerli parçacık döndürülür.

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemi çağrıldıktan hemen sonra <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntem çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi tüm genel öğeleri döndürür.

Örneğin, XML şeması tanım dili (XSD) şeması ve izleyen XML belgesinde `book` öğesi doğrulandıktan sonra `book` öğesi geçerli öğe bağlamıdır. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemi, <xref:System.Xml.Schema.XmlSchemaElement> `title` öğesini temsil eden tek bir nesne içeren bir dizi döndürür. Doğrulama bağlamı `title` öğesi olduğunda, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi boş bir dizi döndürür. `title` Öğe doğrulandıktan <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sonra, ancak `description` öğe doğrulandıktan sonra yöntemi çağrılırsa, <xref:System.Xml.Schema.XmlSchemaElement> `description` öğesini temsil eden tek bir nesne içeren bir dizi döndürür. Öğe doğrulandıktan <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sonra yöntemi çağrılırsa, joker karakteri temsil eden tek <xref:System.Xml.Schema.XmlSchemaAny> bir nesne içeren bir dizi döndürür. `description`

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
> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Sınıfının, ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin sonuçları, doğrulanan geçerli bağlamına bağımlıdır. <xref:System.Xml.Schema.XmlSchemaValidator> Daha fazla bilgi için bu konunun "doğrulama bağlamı" bölümüne bakın.

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemine bir örnek için, giriş bölümündeki örneğe bakın. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.

#### <a name="retrieving-expected-attributes"></a>Beklenen öznitelikleri alma

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Yöntemi, geçerli öğe bağlamında beklenen <xref:System.Xml.Schema.XmlSchemaAttribute> öznitelikleri içeren bir nesne dizisi döndürür.

Örneğin, giriş bölümündeki örnekte <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi, `book` öğesinin tüm özniteliklerini almak için kullanılır.

Yöntemi hemen sonra <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> ÇAĞıRDıĞıNıZDA <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> , XML belgesinde görünebilen tüm öznitelikler döndürülür. Ancak, yöntemi bir veya daha <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> fazla <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntem çağrısından sonra çağırdığınızda, geçerli öğe için henüz doğrulanmamış öznitelikler döndürülür.

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Sınıfının, ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin sonuçları, doğrulanan geçerli bağlamına bağımlıdır. <xref:System.Xml.Schema.XmlSchemaValidator> Daha fazla bilgi için bu konunun "doğrulama bağlamı" bölümüne bakın.

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Yöntemine bir örnek için, giriş bölümündeki örneğe bakın. <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.

#### <a name="retrieving-unspecified-default-attributes"></a>Belirtilmeyen varsayılan öznitelikler alınıyor

<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Yöntemi, öğe bağlamındaki <xref:System.Collections.ArrayList> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntemi kullanılarak daha önce doğrulanmamış varsayılan değerlere sahip herhangi bir öznitelik için nesneleri ile belirtilen şekilde <xref:System.Xml.Schema.XmlSchemaAttribute> doldurur. <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Yöntemi, öğe bağlamındaki her bir öznitelikte <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntemi çağrıldıktan sonra çağrılmalıdır. Yöntemi <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> , doğrulanan xml belgesine hangi varsayılan özniteliklerin ekleneceğini belirlemek için kullanılmalıdır.

<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.

### <a name="handling-schema-validation-events"></a>Şema doğrulama olaylarını işleme

Şema doğrulama uyarıları ve doğrulama sırasında karşılaşılan hatalar, <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının olayı tarafından işlenir.

Şema doğrulama <xref:System.Xml.Schema.XmlSeverityType> uyarıları bir değere sahiptir <xref:System.Xml.Schema.XmlSeverityType.Warning> ve şema doğrulama hatalarının <xref:System.Xml.Schema.XmlSeverityType> değeri vardır. <xref:System.Xml.Schema.XmlSeverityType.Error> Hiçbiri <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> atanmamışsa, bir <xref:System.Xml.Schema.XmlSchemaValidationException> <xref:System.Xml.Schema.XmlSeverityType> değeri olan tüm şema doğrulama hataları için bir atılır. <xref:System.Xml.Schema.XmlSeverityType.Error> Ancak, bir <xref:System.Xml.Schema.XmlSchemaValidationException> <xref:System.Xml.Schema.XmlSeverityType> değeri olan şema doğrulama uyarıları için bir oluşturulmaz <xref:System.Xml.Schema.XmlSeverityType.Warning>.

Aşağıda, giriş içindeki örnekte alınan şema <xref:System.Xml.Schema.ValidationEventHandler> doğrulama uyarılarını ve şema doğrulama sırasında karşılaşılan hataları alan bir örneği verilmiştir.

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

Öğesinin <xref:System.Xml.Schema.ValidationEventHandler>tamamen bir örneği için giriş bölümündeki örneğe bakın. Daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaInfo> sınıf başvurusu belgeleri.

## <a name="xmlschemavalidator-state-transition"></a>XmlSchemaValidator durum geçişi

<xref:System.Xml.Schema.XmlSchemaValidator> Sınıfında, bir xml bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan yöntemlerin her birine yapılan çağrıların sırasını ve oluşumunu uygulayan tanımlı bir durum geçişi vardır.

Aşağıdaki tabloda, <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının durum geçişi ve her durumda yapılabilecek Yöntem çağrılarının sırası ve oluşumu açıklanmaktadır.

|Durum|Transition|
|-----------|----------------|
|Doğrulama|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>(<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel *)<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|
|TopLevel|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>&#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; öğesi|
|Öğe|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> İçerik\*)? <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>&#124;<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; \* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A><br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> \* İçerik\* &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|
|İçerik|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>&#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; öğesi|

> [!NOTE]
> Bir <xref:System.InvalidOperationException> <xref:System.Xml.Schema.XmlSchemaValidator> nesnenin geçerli durumuna göre yanlış sırada Yöntem çağrısı yapıldığında Yukarıdaki tablodaki yöntemlerin her biri tarafından oluşturulur.

Yukarıdaki durum geçiş tablosu, <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının durum geçişinin her durumu için çağrılabilecek yöntemleri ve diğer durumları betimleyen noktalama sembolleri kullanır. Kullanılan semboller, belge türü tanımı (DTD) için XML standartları başvurusunda bulunan sembollerdir.

Aşağıdaki tabloda, yukarıdaki durum geçiş tablosunda bulunan noktalama simgelerinin, <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının durum geçişi içindeki her durum için çağrılabilecek yöntemleri ve diğer durumları nasıl etkilediği açıklanır.

|Sembol|Açıklama|
|------------|-----------------|
|&#124;|Ya Yöntem ya da durum (çubuk veya sonrasında bir veya sonrasında) çağrılabilir.|
|?|Soru işaretinden önce gelen yöntem veya durum isteğe bağlıdır, ancak çağrılırsa yalnızca bir kez çağrılabilir.|
|*|* Simgesinden önce gelen yöntem veya durum isteğe bağlıdır ve birden çok kez çağrılabilir.|

## <a name="validation-context"></a>Doğrulama bağlamı

Bir XML bilgi kümesindeki <xref:System.Xml.Schema.XmlSchemaValidator> öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan sınıfının yöntemleri, bir <xref:System.Xml.Schema.XmlSchemaValidator> nesnenin doğrulama bağlamını değiştirir. Örneğin, <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> yöntemi geçerli öğe içeriğinin doğrulanmasını atlar ve <xref:System.Xml.Schema.XmlSchemaValidator> nesneyi üst öğenin bağlamındaki içeriği doğrulamaya hazırlar; geçerli öğenin tüm alt öğeleri için doğrulama atlanmak ve sonra <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> yöntemi çağırmak eşdeğerdir.

<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Sınıfının, ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin sonuçları, doğrulanan geçerli bağlamına bağımlıdır. <xref:System.Xml.Schema.XmlSchemaValidator>

Aşağıdaki tabloda, bir XML bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının yöntemlerinden biri çağrıldıktan sonra bu yöntemleri çağırma sonuçları açıklanmaktadır.

|Yöntem|Getexlartedparçacıya|Getexeditedattributes|AddSchema|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntem çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> tüm genel öğeleri içeren bir dizi döndürür.<br /><br /> <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> Bir parametre <xref:System.Xml.Schema.XmlSchemaObject> olarak alan aşırı yüklenmiş yöntem bir öğenin kısmi doğrulanmasını başlatmak için çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yalnızca <xref:System.Xml.Schema.XmlSchemaValidator> nesnenin başlatıldığı öğeyi döndürür.|Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntem çağrılırsa boş bir dizi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> döndürür.<br /><br /> Bir özniteliğin kısmi doğrulanmasını başlatmak <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> için bir parametre <xref:System.Xml.Schema.XmlSchemaObject> olarak alan yönteminin aşırı yüklemesi çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yalnızca <xref:System.Xml.Schema.XmlSchemaValidator> nesnenin başlatıldığı özniteliği döndürür.|Ön işleme hataları yoksa şemayı <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaValidator> nesnenin öğesine ekler.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|Bağlam öğesi geçerliyse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin alt öğeleri olarak beklenen öğe dizisini döndürür.<br /><br /> Bağlam öğesi geçersizse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.|Bağlam öğesi geçerliyse ve daha önce yapılan bir çağrı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yoksa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bağlam öğesinde tanımlanan tüm özniteliklerin bir listesini döndürür.<br /><br /> Bazı öznitelikler zaten doğrulandıktan sonra, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> doğrulanacak kalan özniteliklerin listesini döndürür.<br /><br /> Bağlam öğesi geçersizse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|Bağlam özniteliği en üst düzey bir öznitelik ise boş bir dizi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> döndürür.<br /><br /> Aksi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> halde, bağlam öğesinin ilk alt öğesi olarak beklenen öğe dizisini döndürür.|Bağlam özniteliği en üst düzey bir öznitelik ise boş bir dizi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> döndürür.<br /><br /> Aksi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> takdirde, doğrulanacak özniteliklerin listesini geri döndürür.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>bağlam öğesinin ilk alt öğesi olarak beklenen öğelerin dizisini döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>bağlam öğesi için henüz doğrulanamayan gerekli ve isteğe bağlı özniteliklerin listesini döndürür.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>bağlam öğesinin ilk alt öğesi olarak beklenen öğelerin dizisini döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>boş bir dizi döndürür.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|Bağlam öğesinin contentType öğesi karmaysa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sonraki konumda beklenen öğelerin dizisini döndürür.<br /><br /> Bağlam öğesinin contentType öğesi TextOnly veya boşsa boş bir dizi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> döndürür.<br /><br /> Bağlam öğesinin contentType öğesi Öğetonly ise, bir sonraki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> konumda beklenen öğe dizisini döndürür, ancak bir doğrulama hatası zaten oluştu.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>bağlam öğesinin doğrulanmadı özniteliklerin listesini döndürür.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|Bağlam beyaz alanı üst düzey boşluk ise, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.<br /><br /> Aksi halde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemin davranışı ile aynıdır <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Bağlam beyaz alanı üst düzey boşluk ise, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.<br /><br /> Aksi halde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemin davranışı ile aynıdır <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>bağlam öğesinden (olası eşdüzey öğeler) sonra beklenen öğe dizisini döndürür.|<xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>bağlam öğesinin doğrulanmadı özniteliklerin listesini döndürür.<br /><br /> Bağlam öğesinin üst öğesi yoksa, boş bir <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> liste döndürür (bağlam öğesi, üzerinde <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> çağrılan geçerli öğenin üst öğesidir).|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|Aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.|Yukarıdaki gibi.|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|Boş bir dizi döndürür.|Boş bir dizi döndürür.|Yukarıdaki gibi.|

> [!NOTE]
> <xref:System.Xml.Schema.XmlSchemaValidator> Sınıfın çeşitli özelliklerinin döndürdüğü değerler yukarıdaki tablodaki yöntemlerden herhangi biri çağırarak değiştirilmez.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Schema.XmlSchemaValidator>
