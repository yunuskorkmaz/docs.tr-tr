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
# <a name="xmlschemavalidator-push-based-validation"></a><span data-ttu-id="aeb4f-102">XmlSchemaValidator Gönderim Temelli Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="aeb4f-102">XmlSchemaValidator Push-Based Validation</span></span>

<span data-ttu-id="aeb4f-103">Sınıfı <xref:System.Xml.Schema.XmlSchemaValidator> , XML verilerini gönderme temelli BIR şekilde XML şemalarına karşı doğrulamak için etkili ve yüksek performanslı bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-103">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides an efficient, high-performance mechanism to validate XML data against XML schemas in a push-based manner.</span></span> <span data-ttu-id="aeb4f-104">Örneğin <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı, bir XML bilgisi KÜMESINI bir XML belgesi olarak seri hale getirmek ve ardından belgeyi BIR doğrulama XML okuyucusu kullanarak yeniden yerleştirmek zorunda kalmadan, yerinde doğrulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-104">For example, the <xref:System.Xml.Schema.XmlSchemaValidator> class allows you to validate an XML infoset in-place without having to serialize it as an XML document and then reparse the document using a validating XML reader.</span></span>

<span data-ttu-id="aeb4f-105">Sınıfı <xref:System.Xml.Schema.XmlSchemaValidator> , özel XML veri kaynakları üzerinde doğrulama motorları oluşturmak veya BIR doğrulama XML yazıcısı oluşturmak için bir yol olarak, Gelişmiş senaryolarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-105">The <xref:System.Xml.Schema.XmlSchemaValidator> class can be used in advanced scenarios such as building validation engines over custom XML data sources or as a way to build a validating XML writer.</span></span>

<span data-ttu-id="aeb4f-106">Aşağıda, <xref:System.Xml.Schema.XmlSchemaValidator> `contosoBooks.xml` dosyayı `contosoBooks.xsd` şemaya karşı doğrulamak için sınıfının kullanılmasına bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-106">The following is an example of using the <xref:System.Xml.Schema.XmlSchemaValidator> class to validate the `contosoBooks.xml` file against the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="aeb4f-107">Örnek, <xref:System.Xml.Serialization.XmlSerializer> `contosoBooks.xml` dosyanın serisini kaldırmak ve düğümlerin değerini <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının yöntemlerine geçirmek için sınıfını kullanır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-107">The example uses the <xref:System.Xml.Serialization.XmlSerializer> class to deserialize the `contosoBooks.xml` file and pass the value of the nodes to the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

> [!NOTE]
> <span data-ttu-id="aeb4f-108">Bu örnek, bu konunun bölümleri boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-108">This example is used throughout the sections of this topic.</span></span>

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

<span data-ttu-id="aeb4f-109">Örnek, `contosoBooks.xml` dosyayı giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-109">The example takes the `contosoBooks.xml` file as input.</span></span>

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

<span data-ttu-id="aeb4f-110">Örnek de bir giriş `contosoBooks.xsd` olarak alır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-110">The example also takes the `contosoBooks.xsd` as an input.</span></span>

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

## <a name="validating-xml-data-using-xmlschemavalidator"></a><span data-ttu-id="aeb4f-111">XmlSchemaValidator kullanarak XML verilerini doğrulama</span><span class="sxs-lookup"><span data-stu-id="aeb4f-111">Validating XML Data using XmlSchemaValidator</span></span>

<span data-ttu-id="aeb4f-112">Bir XML bilgi kümesini doğrulamaya başlamak için, önce <xref:System.Xml.Schema.XmlSchemaValidator> <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> oluşturucuyu kullanarak sınıfının yeni bir örneğini başlatmalısınız.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-112">To begin validating an XML infoset, you must first initialize a new instance of the <xref:System.Xml.Schema.XmlSchemaValidator> class using the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor.</span></span>

<span data-ttu-id="aeb4f-113"><xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Oluşturucu, <xref:System.Xml.Schema.XmlSchemaSet>ve <xref:System.Xml.XmlNameTable> <xref:System.Xml.Schema.XmlSchemaValidationFlags> değerlerini parametre olarak <xref:System.Xml.XmlNamespaceManager> ve bir parametresi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-113">The <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor takes <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, and <xref:System.Xml.XmlNamespaceManager> objects as parameters as well as a <xref:System.Xml.Schema.XmlSchemaValidationFlags> value as a parameter.</span></span> <span data-ttu-id="aeb4f-114"><xref:System.Xml.XmlNameTable> Nesnesi, şema ad alanı, XML ad alanı vb. gibi iyi bilinen ad alanı dizelerini ayrılamaz ve basit içerik doğrulanırken <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-114">The <xref:System.Xml.XmlNameTable> object is used to atomize well-known namespace strings like the schema namespace, the XML namespace, and so on, and is passed to the <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> method while validating simple content.</span></span> <span data-ttu-id="aeb4f-115"><xref:System.Xml.Schema.XmlSchemaSet> NESNESI, XML bilgi kümesini doğrulamak IÇIN kullanılan XML şemalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-115">The <xref:System.Xml.Schema.XmlSchemaSet> object contains the XML schemas used to validate the XML infoset.</span></span> <span data-ttu-id="aeb4f-116">Nesne <xref:System.Xml.XmlNamespaceManager> , doğrulama sırasında karşılaşılan ad alanlarını çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-116">The <xref:System.Xml.XmlNamespaceManager> object is used to resolve namespaces encountered during validation.</span></span> <span data-ttu-id="aeb4f-117">Bu <xref:System.Xml.Schema.XmlSchemaValidationFlags> değer, doğrulamanın belirli özelliklerini devre dışı bırakmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-117">The <xref:System.Xml.Schema.XmlSchemaValidationFlags> value is used to disable certain features of validation.</span></span>

<span data-ttu-id="aeb4f-118"><xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Oluşturucu hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-118">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="initializing-validation"></a><span data-ttu-id="aeb4f-119">Doğrulama başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="aeb4f-119">Initializing Validation</span></span>

<span data-ttu-id="aeb4f-120">Bir <xref:System.Xml.Schema.XmlSchemaValidator> nesne oluşturulduktan sonra, <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> <xref:System.Xml.Schema.XmlSchemaValidator> nesnenin durumunu başlatmak için kullanılan iki aşırı yüklenmiş yöntem vardır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-120">After an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed, there are two overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods used to initialize the state of the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="aeb4f-121">Aşağıdaki iki <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntem vardır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-121">The following are the two <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

<span data-ttu-id="aeb4f-122"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Varsayılan yöntem, bir <xref:System.Xml.Schema.XmlSchemaValidator> nesneyi başlangıç durumuna başlatır ve bir parametresi <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> <xref:System.Xml.Schema.XmlSchemaObject> olarak alan aşırı yüklenmiş yöntem, kısmi doğrulama için bir <xref:System.Xml.Schema.XmlSchemaValidator> nesneyi başlangıç durumuna başlatır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-122">The default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state, and the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="aeb4f-123">Her <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> iki yöntem de yalnızca bir <xref:System.Xml.Schema.XmlSchemaValidator> nesne oluşturulduktan sonra veya bir çağrısından sonra çağrılabilir <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-123">Both <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods can only be called immediately after an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed or after a call to <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span></span>

<span data-ttu-id="aeb4f-124"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Yöntemine bir örnek için, giriş bölümündeki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-124">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method, see the example in the introduction.</span></span> <span data-ttu-id="aeb4f-125"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> Yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-125">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="partial-validation"></a><span data-ttu-id="aeb4f-126">Kısmi doğrulama</span><span class="sxs-lookup"><span data-stu-id="aeb4f-126">Partial Validation</span></span>

<span data-ttu-id="aeb4f-127">Bir <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> parametre <xref:System.Xml.Schema.XmlSchemaObject> olarak alan yöntemi, kısmi doğrulama için bir <xref:System.Xml.Schema.XmlSchemaValidator> nesneyi başlangıç durumuna başlatır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-127">The <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="aeb4f-128">Aşağıdaki örnekte, <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yöntemi kullanılarak kısmi <xref:System.Xml.Schema.XmlSchemaObject> doğrulama için bir başlatılır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-128">In the following example, an <xref:System.Xml.Schema.XmlSchemaObject> is initialized for partial validation using the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="aeb4f-129">`orderNumber` Şema <xref:System.Xml.XmlQualifiedName> öğesi, <xref:System.Xml.Schema.XmlSchemaObjectTable> <xref:System.Xml.Schema.XmlSchemaSet> nesnesinin <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> özelliği tarafından döndürülen koleksiyonda tarafından şema öğesi seçilerek geçirilir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-129">The `orderNumber` schema element is passed by selecting the schema element by <xref:System.Xml.XmlQualifiedName> in the <xref:System.Xml.Schema.XmlSchemaObjectTable> collection returned by the <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> object.</span></span> <span data-ttu-id="aeb4f-130"><xref:System.Xml.Schema.XmlSchemaValidator> Nesne daha sonra bu özel öğeyi doğrular.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-130">The <xref:System.Xml.Schema.XmlSchemaValidator> object then validates this specific element.</span></span>

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

<span data-ttu-id="aeb4f-131">Örnek, aşağıdaki XML şemasını giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-131">The example takes the following XML schema as input.</span></span>

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="orderNumber" type="xs:int" />
</xs:schema>
```

<span data-ttu-id="aeb4f-132"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> Yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-132">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="adding-additional-schemas"></a><span data-ttu-id="aeb4f-133">Ek şemalar ekleme</span><span class="sxs-lookup"><span data-stu-id="aeb4f-133">Adding Additional Schemas</span></span>

<span data-ttu-id="aeb4f-134"><xref:System.Xml.Schema.XmlSchemaValidator> Sınıfının <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemi, doğrulama sırasında kullanılan şemalar kümesine bir XML şeması eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-134">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method of the <xref:System.Xml.Schema.XmlSchemaValidator> class is used to add an XML schema to the set of schemas used during validation.</span></span> <span data-ttu-id="aeb4f-135"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Yöntemi, doğrulanan xml bilgi kümesindeki bir satır içi xml şeması ile karşılaşanın etkisinin benzetimini yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-135">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method can be used to simulate the effect of encountering an inline XML schema in the XML infoset being validated.</span></span>

> [!NOTE]
> <span data-ttu-id="aeb4f-136"><xref:System.Xml.Schema.XmlSchema> Parametrenin hedef ad alanı, <xref:System.Xml.Schema.XmlSchemaValidator> nesne tarafından zaten karşılaşılan hiçbir öğe veya öznitelikle eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-136">The target namespace of the <xref:System.Xml.Schema.XmlSchema> parameter cannot match that of any element or attribute already encountered by the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>
>
> <span data-ttu-id="aeb4f-137"><xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> Değer, <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> oluşturucuya bir parametre olarak geçirilmemişse, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntem hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-137">If the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> value was not passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method does nothing.</span></span>

<span data-ttu-id="aeb4f-138"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Yöntemin sonucu, DOĞRULANAN geçerli XML düğümü bağlamına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-138">The result of the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method is dependant on the current XML node context being validated.</span></span> <span data-ttu-id="aeb4f-139">Doğrulama bağlamları hakkında daha fazla bilgi için bu konunun "doğrulama bağlamı" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-139">For more information about validation contexts, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="aeb4f-140"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-140">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="validating-elements-attributes-and-content"></a><span data-ttu-id="aeb4f-141">Öğeleri, öznitelikleri ve Içeriği doğrulama</span><span class="sxs-lookup"><span data-stu-id="aeb4f-141">Validating Elements, Attributes, and Content</span></span>

<span data-ttu-id="aeb4f-142"><xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı, XML şemalarında xml bilgi kümesindeki öğeleri, öznitelikleri ve içerikleri doğrulamak için kullanılan çeşitli yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-142">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides several methods used to validate elements, attributes, and content in an XML infoset against XML schemas.</span></span> <span data-ttu-id="aeb4f-143">Aşağıdaki tabloda bu yöntemlerin her biri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-143">The following table describes each of these methods.</span></span>

|<span data-ttu-id="aeb4f-144">Yöntem</span><span class="sxs-lookup"><span data-stu-id="aeb4f-144">Method</span></span>|<span data-ttu-id="aeb4f-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aeb4f-145">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="aeb4f-146">Geçerli bağlamdaki öğe adını doğrular.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-146">Validates the element name in the current context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="aeb4f-147">Geçerli öğe bağlamındaki özniteliği veya <xref:System.Xml.Schema.XmlSchemaAttribute> <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemine parametre olarak geçirilen nesneye karşı doğrular.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-147">Validates the attribute in the current element context or against the <xref:System.Xml.Schema.XmlSchemaAttribute> object passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="aeb4f-148">Öğe bağlamındaki tüm gerekli özniteliklerin mevcut olup olmadığını doğrular ve <xref:System.Xml.Schema.XmlSchemaValidator> nesneyi öğenin alt içeriğini doğrulamak üzere hazırlar.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-148">Verifies whether all the required attributes in the element context are present and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate the child content of the element.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="aeb4f-149">Geçerli öğe bağlamında metnin izin verilip verilmeyeceğini doğrular ve geçerli öğede basit içerik varsa doğrulama için metni biriktirir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-149">Validates whether text is allowed in the current element context, and accumulates the text for validation if the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="aeb4f-150">Geçerli öğe bağlamında beyaz boşluğa izin verilip verilmeyeceğini doğrular ve geçerli öğenin basit içeriğe sahip olup olmadığını doğrulamak için beyaz boşluğu biriktirir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-150">Validates whether white-space is allowed in the current element context, and accumulates the white-space for validation whether the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="aeb4f-151">Öğenin metin içeriğinin basit içeriğe sahip öğeler için kendi veri türüne göre geçerli olup olmadığını doğrular ve karmaşık içerikli öğeler için geçerli öğenin içeriğinin tamamlanıp tamamlanmadığını doğrular.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-151">Verifies whether the text content of the element is valid according to its data type for elements with simple content, and verifies whether the content of the current element is complete for elements with complex content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="aeb4f-152">Geçerli öğe içeriğinin geçerliliğini atlar ve üst öğenin bağlamındaki içeriği <xref:System.Xml.Schema.XmlSchemaValidator> doğrulamak için nesneyi hazırlar.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-152">Skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="aeb4f-153">Doğrulama seçeneği ayarlandıysa, doğrulamayı sonlandırır ve tüm XML belgesi <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> için kimlik kısıtlamalarını denetler.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-153">Ends validation and checks identity constraints for the entire XML document if the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> validation option is set.</span></span>|

> [!NOTE]
> <span data-ttu-id="aeb4f-154"><xref:System.Xml.Schema.XmlSchemaValidator> Sınıfında, önceki tabloda açıklanan yöntemlerin her birine yapılan çağrıların sırasını ve tekrarını uygulayan tanımlı bir durum geçişi vardır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-154">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods described in the previous table.</span></span> <span data-ttu-id="aeb4f-155"><xref:System.Xml.Schema.XmlSchemaValidator> Sınıfın belirli durum geçişi, bu konunun "XmlSchemaValidator durum geçişi" bölümünde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-155">The specific state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class is described in the "XmlSchemaValidator State Transition" section of this topic.</span></span>

<span data-ttu-id="aeb4f-156">Bir XML bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan yöntemlere örnek olarak, önceki bölümde bulunan örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-156">For an example of the methods used to validate elements, attributes, and content in an XML infoset, see the example in the previous section.</span></span> <span data-ttu-id="aeb4f-157">Bu yöntemler hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-157">For more information about these methods, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="validating-content-using-an-xmlvaluegetter"></a><span data-ttu-id="aeb4f-158">XmlValueGetter kullanarak Içerik doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="aeb4f-158">Validating Content Using an XmlValueGetter</span></span>

<span data-ttu-id="aeb4f-159"><xref:System.Xml.Schema.XmlValueGetter> Öznitelik, metin veya boşluk düğümlerinin değerini öznitelik, metin veya boşluk düğümünün XML şeması tanım dili (xsd) türüyle uyumlu ortak dil çalışma zamanı (CLR) türleri olarak geçirmek için `delegate` kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-159">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` can be used to pass the value of attribute, text, or white-space nodes as a Common Language Runtime (CLR) types compatible with the XML Schema Definition Language (XSD) type of the attribute, text, or white-space node.</span></span> <span data-ttu-id="aeb4f-160">Bir <xref:System.Xml.Schema.XmlValueGetter> `delegate` özniteliğin, metnin veya boşluk düğümünün clr değeri zaten kullanılabilirse ve bunu bir `string` ve daha sonra doğrulama için yeniden ayrıştırmanın maliyetini önlediği durumlarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-160">An <xref:System.Xml.Schema.XmlValueGetter>`delegate` is useful if the CLR value of an attribute, text, or white-space node is already available, and avoids the cost of converting it to a `string` and then reparsing it again for validation.</span></span>

<span data-ttu-id="aeb4f-161"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>,, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> Ve yöntemleri aşırı yüklenmiş ve öznitelik, metin veya boşluk düğümlerinin değeri `string` veya <xref:System.Xml.Schema.XmlValueGetter> `delegate`olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-161">The <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> methods are overloaded and accept the value of attribute, text, or white-space nodes as a `string` or <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span></span>

<span data-ttu-id="aeb4f-162"><xref:System.Xml.Schema.XmlSchemaValidator> Sınıfının aşağıdaki yöntemleri bir parametre <xref:System.Xml.Schema.XmlValueGetter> `delegate` olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-162">The following methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlValueGetter>`delegate` as a parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

<span data-ttu-id="aeb4f-163">Aşağıda, giriş içindeki <xref:System.Xml.Schema.XmlValueGetter> `delegate` <xref:System.Xml.Schema.XmlSchemaValidator> sınıf örneğinizden alınan bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-163">The following is an example <xref:System.Xml.Schema.XmlValueGetter>`delegate` taken from the <xref:System.Xml.Schema.XmlSchemaValidator> class example in the introduction.</span></span> <span data-ttu-id="aeb4f-164">, <xref:System.Xml.Schema.XmlValueGetter> `delegate` Bir özniteliğin değerini bir <xref:System.DateTime> nesne olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-164">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` returns the value of an attribute as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="aeb4f-165">Tarafından döndürülen bu <xref:System.DateTime> nesneyi doğrulamak için <xref:System.Xml.Schema.XmlValueGetter>, <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi, özniteliğin veri türü için önce onu ValueType öğesine dönüştürür (ValueType, xsd türü için varsayılan clr eşlemedir) ve ardından dönüştürülen değer üzerindeki modelleri denetler.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-165">To validate this <xref:System.DateTime> object returned by the <xref:System.Xml.Schema.XmlValueGetter>, the <xref:System.Xml.Schema.XmlSchemaValidator> object first converts it to the ValueType (ValueType is the default CLR mapping for the XSD type) for the data type of the attribute and then checks facets on the converted value.</span></span>

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

<span data-ttu-id="aeb4f-166">Öğesinin <xref:System.Xml.Schema.XmlValueGetter> `delegate`tamamen bir örneği için giriş bölümündeki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-166">For a complete example of the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the example in the introduction.</span></span> <span data-ttu-id="aeb4f-167">Hakkında <xref:System.Xml.Schema.XmlValueGetter> `delegate`daha fazla bilgi için, ve <xref:System.Xml.Schema.XmlValueGetter> <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-167">For more information about the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the <xref:System.Xml.Schema.XmlValueGetter>, and <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="post-schema-validation-information"></a><span data-ttu-id="aeb4f-168">Şema sonrası doğrulama-bilgi</span><span class="sxs-lookup"><span data-stu-id="aeb4f-168">Post-Schema-Validation-Information</span></span>

<span data-ttu-id="aeb4f-169"><xref:System.Xml.Schema.XmlSchemaInfo> Sınıfı, <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı tarafından doğrulanan bir XML düğümünün şema sonrası-doğrulama bilgilerinin bazılarını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-169">The <xref:System.Xml.Schema.XmlSchemaInfo> class represents some of the Post-Schema-Validation-Information of an XML node validated by the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="aeb4f-170"><xref:System.Xml.Schema.XmlSchemaValidator> Sınıfının çeşitli yöntemleri bir <xref:System.Xml.Schema.XmlSchemaInfo> nesneyi isteğe bağlı, (`null`) `out` parametre olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-170">Various methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an optional, (`null`) `out` parameter.</span></span>

<span data-ttu-id="aeb4f-171">Doğrulama başarılı olduğunda, <xref:System.Xml.Schema.XmlSchemaInfo> nesnesinin özellikleri doğrulamanın sonuçlarıyla ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-171">Upon successful validation, properties of the <xref:System.Xml.Schema.XmlSchemaInfo> object are set with the results of the validation.</span></span> <span data-ttu-id="aeb4f-172"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> Örneğin, <xref:System.Xml.Schema.XmlSchemaInfo> yöntemini kullanarak bir özniteliğin başarıyla doğrulanması sırasında, nesnenin (belirtilmişse) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>ve <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> özellikleri doğrulamanın sonuçlarıyla ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-172">For example, upon successful validation of an attribute using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the <xref:System.Xml.Schema.XmlSchemaInfo> object's (if specified) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, and <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> properties are set with the results of the validation.</span></span>

<span data-ttu-id="aeb4f-173">Aşağıdaki <xref:System.Xml.Schema.XmlSchemaValidator> sınıf yöntemleri bir <xref:System.Xml.Schema.XmlSchemaInfo> nesneyi out parametresi olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-173">The following <xref:System.Xml.Schema.XmlSchemaValidator> class methods accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an out parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

<span data-ttu-id="aeb4f-174"><xref:System.Xml.Schema.XmlSchemaInfo> Sınıfının tamamen bir örneği için, giriş bölümündeki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-174">For a complete example of the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the example in the introduction.</span></span> <span data-ttu-id="aeb4f-175"><xref:System.Xml.Schema.XmlSchemaInfo> Sınıfı hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaInfo> sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-175">For more information about the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a><span data-ttu-id="aeb4f-176">Beklenen parçacık, öznitelik ve belirtilmemiş varsayılan öznitelikleri alma</span><span class="sxs-lookup"><span data-stu-id="aeb4f-176">Retrieving Expected Particles, Attributes, and Unspecified Default Attributes</span></span>

<span data-ttu-id="aeb4f-177"><xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, geçerli doğrulama bağlamında <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>beklenen parçacıkların, özniteliklerin ve belirtilmemiş varsayılan özniteliklerin alınması için, ve <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-177">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> methods to retrieve the expected particles, attributes, and unspecified default attributes in the current validation context.</span></span>

#### <a name="retrieving-expected-particles"></a><span data-ttu-id="aeb4f-178">Beklenen parçacık alınıyor</span><span class="sxs-lookup"><span data-stu-id="aeb4f-178">Retrieving Expected Particles</span></span>

<span data-ttu-id="aeb4f-179"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemi, geçerli öğe bağlamında beklenen <xref:System.Xml.Schema.XmlSchemaParticle> parçacık içeren bir nesne dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-179">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaParticle> objects containing the expected particles in the current element context.</span></span> <span data-ttu-id="aeb4f-180"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemi tarafından döndürülebilecek geçerli parçacık, <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAny> sınıflarının örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-180">The valid particles that can be returned by the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method are instances of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAny> classes.</span></span>

<span data-ttu-id="aeb4f-181">İçerik modeli için Oluşturucu bir `xs:sequence`ise, yalnızca dizideki bir sonraki parçacık döndürülür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-181">When the compositor for the content model is an `xs:sequence`, only the next particle in the sequence is returned.</span></span> <span data-ttu-id="aeb4f-182">İçerik modeli için Oluşturucu bir `xs:all` veya ise `xs:choice`, geçerli öğe bağlamında izleyelebilecek tüm geçerli parçacık döndürülür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-182">If the compositor for the content model is an `xs:all` or an `xs:choice`, then all valid particles that could follow in the current element context are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="aeb4f-183"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemi çağrıldıktan hemen sonra <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntem çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi tüm genel öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-183">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called immediately after calling the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns all global elements.</span></span>

<span data-ttu-id="aeb4f-184">Örneğin, XML şeması tanım dili (XSD) şeması ve izleyen XML belgesinde `book` öğesi doğrulandıktan sonra `book` öğesi geçerli öğe bağlamıdır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-184">For example, in the XML Schema Definition Language (XSD) schema and XML document that follow, after validating the `book` element, the `book` element is the current element context.</span></span> <span data-ttu-id="aeb4f-185"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemi, <xref:System.Xml.Schema.XmlSchemaElement> `title` öğesini temsil eden tek bir nesne içeren bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-185">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `title` element.</span></span> <span data-ttu-id="aeb4f-186">Doğrulama bağlamı `title` öğesi olduğunda, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-186">When the validation context is the `title` element, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an empty array.</span></span> <span data-ttu-id="aeb4f-187">`title` Öğe doğrulandıktan <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sonra, ancak `description` öğe doğrulandıktan sonra yöntemi çağrılırsa, <xref:System.Xml.Schema.XmlSchemaElement> `description` öğesini temsil eden tek bir nesne içeren bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-187">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `title` element has been validated but before the `description` element has been validated, it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `description` element.</span></span> <span data-ttu-id="aeb4f-188">Öğe doğrulandıktan <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sonra yöntemi çağrılırsa, joker karakteri temsil eden tek <xref:System.Xml.Schema.XmlSchemaAny> bir nesne içeren bir dizi döndürür. `description`</span><span class="sxs-lookup"><span data-stu-id="aeb4f-188">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `description` element has been validated then it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaAny> object representing the wildcard.</span></span>

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

 <span data-ttu-id="aeb4f-189">Örnek aşağıdaki XML 'i giriş olarak alır:</span><span class="sxs-lookup"><span data-stu-id="aeb4f-189">The example takes the following XML as input:</span></span>

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

<span data-ttu-id="aeb4f-190">Örnek, aşağıdaki XSD şemasını giriş olarak alır:</span><span class="sxs-lookup"><span data-stu-id="aeb4f-190">The example takes the following XSD schema as input:</span></span>

```xml
<book>
  <title>My Book</title>
  <description>My Book's Description</description>
  <namespace>System.Xml.Schema</namespace>
</book>
```

> [!NOTE]
> <span data-ttu-id="aeb4f-191"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Sınıfının, ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin sonuçları, doğrulanan geçerli bağlamına bağımlıdır. <xref:System.Xml.Schema.XmlSchemaValidator></span><span class="sxs-lookup"><span data-stu-id="aeb4f-191">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="aeb4f-192">Daha fazla bilgi için bu konunun "doğrulama bağlamı" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-192">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="aeb4f-193"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemine bir örnek için, giriş bölümündeki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-193">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="aeb4f-194"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-194">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-expected-attributes"></a><span data-ttu-id="aeb4f-195">Beklenen öznitelikleri alma</span><span class="sxs-lookup"><span data-stu-id="aeb4f-195">Retrieving Expected Attributes</span></span>

<span data-ttu-id="aeb4f-196"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Yöntemi, geçerli öğe bağlamında beklenen <xref:System.Xml.Schema.XmlSchemaAttribute> öznitelikleri içeren bir nesne dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-196">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaAttribute> objects containing the expected attributes in the current element context.</span></span>

<span data-ttu-id="aeb4f-197">Örneğin, giriş bölümündeki örnekte <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi, `book` öğesinin tüm özniteliklerini almak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-197">For example, in the example in the introduction, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method is used to retrieve all the attributes of the `book` element.</span></span>

<span data-ttu-id="aeb4f-198">Yöntemi hemen sonra <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> ÇAĞıRDıĞıNıZDA <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> , XML belgesinde görünebilen tüm öznitelikler döndürülür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-198">If you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method immediately after the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> method, all the attributes that could appear in the XML document are returned.</span></span> <span data-ttu-id="aeb4f-199">Ancak, yöntemi bir veya daha <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> fazla <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntem çağrısından sonra çağırdığınızda, geçerli öğe için henüz doğrulanmamış öznitelikler döndürülür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-199">However, if you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method after one or more calls to the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the attributes that have not yet been validated for the current element are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="aeb4f-200"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Sınıfının, ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin sonuçları, doğrulanan geçerli bağlamına bağımlıdır. <xref:System.Xml.Schema.XmlSchemaValidator></span><span class="sxs-lookup"><span data-stu-id="aeb4f-200">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="aeb4f-201">Daha fazla bilgi için bu konunun "doğrulama bağlamı" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-201">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="aeb4f-202"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Yöntemine bir örnek için, giriş bölümündeki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-202">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="aeb4f-203"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-203">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-unspecified-default-attributes"></a><span data-ttu-id="aeb4f-204">Belirtilmeyen varsayılan öznitelikler alınıyor</span><span class="sxs-lookup"><span data-stu-id="aeb4f-204">Retrieving Unspecified Default Attributes</span></span>

<span data-ttu-id="aeb4f-205"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Yöntemi, öğe bağlamındaki <xref:System.Collections.ArrayList> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntemi kullanılarak daha önce doğrulanmamış varsayılan değerlere sahip herhangi bir öznitelik için nesneleri ile belirtilen şekilde <xref:System.Xml.Schema.XmlSchemaAttribute> doldurur.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-205">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method populates the <xref:System.Collections.ArrayList> specified with <xref:System.Xml.Schema.XmlSchemaAttribute> objects for any attributes with default values that have not been previously validated using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method in the element context.</span></span> <span data-ttu-id="aeb4f-206"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Yöntemi, öğe bağlamındaki her bir öznitelikte <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntemi çağrıldıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-206">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be called after calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method on each attribute in the element context.</span></span> <span data-ttu-id="aeb4f-207">Yöntemi <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> , doğrulanan xml belgesine hangi varsayılan özniteliklerin ekleneceğini belirlemek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-207">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be used to determine what default attributes are to be inserted into the XML document being validated.</span></span>

<span data-ttu-id="aeb4f-208"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Yöntemi hakkında daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-208">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="handling-schema-validation-events"></a><span data-ttu-id="aeb4f-209">Şema doğrulama olaylarını işleme</span><span class="sxs-lookup"><span data-stu-id="aeb4f-209">Handling Schema Validation Events</span></span>

<span data-ttu-id="aeb4f-210">Şema doğrulama uyarıları ve doğrulama sırasında karşılaşılan hatalar, <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının olayı tarafından işlenir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-210">Schema validation warnings and errors encountered during validation are handled by the <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> event of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

<span data-ttu-id="aeb4f-211">Şema doğrulama <xref:System.Xml.Schema.XmlSeverityType> uyarıları bir değere sahiptir <xref:System.Xml.Schema.XmlSeverityType.Warning> ve şema doğrulama hatalarının <xref:System.Xml.Schema.XmlSeverityType> değeri vardır. <xref:System.Xml.Schema.XmlSeverityType.Error></span><span class="sxs-lookup"><span data-stu-id="aeb4f-211">Schema validation warnings have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning> and schema validation errors have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="aeb4f-212">Hiçbiri <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> atanmamışsa, bir <xref:System.Xml.Schema.XmlSchemaValidationException> <xref:System.Xml.Schema.XmlSeverityType> değeri olan tüm şema doğrulama hataları için bir atılır. <xref:System.Xml.Schema.XmlSeverityType.Error></span><span class="sxs-lookup"><span data-stu-id="aeb4f-212">If no <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> has been assigned, an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown for all schema validation errors with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="aeb4f-213">Ancak, bir <xref:System.Xml.Schema.XmlSchemaValidationException> <xref:System.Xml.Schema.XmlSeverityType> değeri olan şema doğrulama uyarıları için bir oluşturulmaz <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-213">However, an <xref:System.Xml.Schema.XmlSchemaValidationException> is not thrown for schema validation warnings with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span></span>

<span data-ttu-id="aeb4f-214">Aşağıda, giriş içindeki örnekte alınan şema <xref:System.Xml.Schema.ValidationEventHandler> doğrulama uyarılarını ve şema doğrulama sırasında karşılaşılan hataları alan bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-214">The following is an example of a <xref:System.Xml.Schema.ValidationEventHandler> that receives schema validation warnings and errors encountered during schema validation taken from the example in the introduction.</span></span>

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

<span data-ttu-id="aeb4f-215">Öğesinin <xref:System.Xml.Schema.ValidationEventHandler>tamamen bir örneği için giriş bölümündeki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-215">For a complete example of the <xref:System.Xml.Schema.ValidationEventHandler>, see the example in the introduction.</span></span> <span data-ttu-id="aeb4f-216">Daha fazla bilgi için bkz. <xref:System.Xml.Schema.XmlSchemaInfo> sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-216">For more information, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

## <a name="xmlschemavalidator-state-transition"></a><span data-ttu-id="aeb4f-217">XmlSchemaValidator durum geçişi</span><span class="sxs-lookup"><span data-stu-id="aeb4f-217">XmlSchemaValidator State Transition</span></span>

<span data-ttu-id="aeb4f-218"><xref:System.Xml.Schema.XmlSchemaValidator> Sınıfında, bir xml bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan yöntemlerin her birine yapılan çağrıların sırasını ve oluşumunu uygulayan tanımlı bir durum geçişi vardır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-218">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods used to validate elements, attributes, and content in an XML infoset.</span></span>

<span data-ttu-id="aeb4f-219">Aşağıdaki tabloda, <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının durum geçişi ve her durumda yapılabilecek Yöntem çağrılarının sırası ve oluşumu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-219">The following table describes the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class, and the sequence and occurrence of method calls that can be made in each state.</span></span>

|<span data-ttu-id="aeb4f-220">Durum</span><span class="sxs-lookup"><span data-stu-id="aeb4f-220">State</span></span>|<span data-ttu-id="aeb4f-221">Transition</span><span class="sxs-lookup"><span data-stu-id="aeb4f-221">Transition</span></span>|
|-----------|----------------|
|<span data-ttu-id="aeb4f-222">Doğrulama</span><span class="sxs-lookup"><span data-stu-id="aeb4f-222">Validate</span></span>|<span data-ttu-id="aeb4f-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>(<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel \*)<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span><span class="sxs-lookup"><span data-stu-id="aeb4f-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span></span>|
|<span data-ttu-id="aeb4f-224">TopLevel</span><span class="sxs-lookup"><span data-stu-id="aeb4f-224">TopLevel</span></span>|<span data-ttu-id="aeb4f-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>&#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; öğesi</span><span class="sxs-lookup"><span data-stu-id="aeb4f-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|
|<span data-ttu-id="aeb4f-226">Öğe</span><span class="sxs-lookup"><span data-stu-id="aeb4f-226">Element</span></span>|<span data-ttu-id="aeb4f-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> İçerik\*)?</span><span class="sxs-lookup"><span data-stu-id="aeb4f-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span></span> <span data-ttu-id="aeb4f-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>&#124;</span><span class="sxs-lookup"><span data-stu-id="aeb4f-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="aeb4f-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; \* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A></span><span class="sxs-lookup"><span data-stu-id="aeb4f-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="aeb4f-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> \* İçerik\* &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A></span><span class="sxs-lookup"><span data-stu-id="aeb4f-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span>|
|<span data-ttu-id="aeb4f-231">İçerik</span><span class="sxs-lookup"><span data-stu-id="aeb4f-231">Content</span></span>|<span data-ttu-id="aeb4f-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>&#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; öğesi</span><span class="sxs-lookup"><span data-stu-id="aeb4f-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|

> [!NOTE]
> <span data-ttu-id="aeb4f-233">Bir <xref:System.InvalidOperationException> <xref:System.Xml.Schema.XmlSchemaValidator> nesnenin geçerli durumuna göre yanlış sırada Yöntem çağrısı yapıldığında Yukarıdaki tablodaki yöntemlerin her biri tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-233">An <xref:System.InvalidOperationException> is thrown by each of the methods in the table above when the call to the method is made in the incorrect sequence according to the current state of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>

<span data-ttu-id="aeb4f-234">Yukarıdaki durum geçiş tablosu, <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının durum geçişinin her durumu için çağrılabilecek yöntemleri ve diğer durumları betimleyen noktalama sembolleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-234">The state transition table above uses punctuation symbols to describe the methods and other states that can be called for each state of the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="aeb4f-235">Kullanılan semboller, belge türü tanımı (DTD) için XML standartları başvurusunda bulunan sembollerdir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-235">The symbols used are the same symbols found in the XML Standards reference for Document Type Definition (DTD).</span></span>

<span data-ttu-id="aeb4f-236">Aşağıdaki tabloda, yukarıdaki durum geçiş tablosunda bulunan noktalama simgelerinin, <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının durum geçişi içindeki her durum için çağrılabilecek yöntemleri ve diğer durumları nasıl etkilediği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-236">The following table describes how the punctuation symbols found in the state transition table above affect the methods and other states that can be called for each state in the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

|<span data-ttu-id="aeb4f-237">Sembol</span><span class="sxs-lookup"><span data-stu-id="aeb4f-237">Symbol</span></span>|<span data-ttu-id="aeb4f-238">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aeb4f-238">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="aeb4f-239">&#124;</span><span class="sxs-lookup"><span data-stu-id="aeb4f-239">&#124;</span></span>|<span data-ttu-id="aeb4f-240">Ya Yöntem ya da durum (çubuk veya sonrasında bir veya sonrasında) çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-240">Either method or state (the one before the bar or the one after it) can be called.</span></span>|
|<span data-ttu-id="aeb4f-241">?</span><span class="sxs-lookup"><span data-stu-id="aeb4f-241">?</span></span>|<span data-ttu-id="aeb4f-242">Soru işaretinden önce gelen yöntem veya durum isteğe bağlıdır, ancak çağrılırsa yalnızca bir kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-242">The method or state that precedes the question mark is optional but if it is called it can only be called once.</span></span>|
|*|<span data-ttu-id="aeb4f-243">\* Simgesinden önce gelen yöntem veya durum isteğe bağlıdır ve birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-243">The method or state that precedes the \* symbol is optional, and can be called more than once.</span></span>|

## <a name="validation-context"></a><span data-ttu-id="aeb4f-244">Doğrulama bağlamı</span><span class="sxs-lookup"><span data-stu-id="aeb4f-244">Validation Context</span></span>

<span data-ttu-id="aeb4f-245">Bir XML bilgi kümesindeki <xref:System.Xml.Schema.XmlSchemaValidator> öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan sınıfının yöntemleri, bir <xref:System.Xml.Schema.XmlSchemaValidator> nesnenin doğrulama bağlamını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-245">The methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset, change the validation context of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="aeb4f-246">Örneğin, <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> yöntemi geçerli öğe içeriğinin doğrulanmasını atlar ve <xref:System.Xml.Schema.XmlSchemaValidator> nesneyi üst öğenin bağlamındaki içeriği doğrulamaya hazırlar; geçerli öğenin tüm alt öğeleri için doğrulama atlanmak ve sonra <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> yöntemi çağırmak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-246">For example, the <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> method skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context; it is equivalent to skipping validation for all the children of the current element and then calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> method.</span></span>

<span data-ttu-id="aeb4f-247"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Sınıfının, ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin sonuçları, doğrulanan geçerli bağlamına bağımlıdır. <xref:System.Xml.Schema.XmlSchemaValidator></span><span class="sxs-lookup"><span data-stu-id="aeb4f-247">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span>

<span data-ttu-id="aeb4f-248">Aşağıdaki tabloda, bir XML bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan <xref:System.Xml.Schema.XmlSchemaValidator> sınıfının yöntemlerinden biri çağrıldıktan sonra bu yöntemleri çağırma sonuçları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-248">The following table describes the results of calling these methods after calling one of the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset.</span></span>

|<span data-ttu-id="aeb4f-249">Yöntem</span><span class="sxs-lookup"><span data-stu-id="aeb4f-249">Method</span></span>|<span data-ttu-id="aeb4f-250">Getexlartedparçacıya</span><span class="sxs-lookup"><span data-stu-id="aeb4f-250">GetExpectedParticles</span></span>|<span data-ttu-id="aeb4f-251">Getexeditedattributes</span><span class="sxs-lookup"><span data-stu-id="aeb4f-251">GetExpectedAttributes</span></span>|<span data-ttu-id="aeb4f-252">AddSchema</span><span class="sxs-lookup"><span data-stu-id="aeb4f-252">AddSchema</span></span>|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|<span data-ttu-id="aeb4f-253">Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntem çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> tüm genel öğeleri içeren bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-253">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an array containing all global elements.</span></span><br /><br /> <span data-ttu-id="aeb4f-254"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> Bir parametre <xref:System.Xml.Schema.XmlSchemaObject> olarak alan aşırı yüklenmiş yöntem bir öğenin kısmi doğrulanmasını başlatmak için çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yalnızca <xref:System.Xml.Schema.XmlSchemaValidator> nesnenin başlatıldığı öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-254">If the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns only the element to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="aeb4f-255">Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntem çağrılırsa boş bir dizi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-255">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="aeb4f-256">Bir özniteliğin kısmi doğrulanmasını başlatmak <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> için bir parametre <xref:System.Xml.Schema.XmlSchemaObject> olarak alan yönteminin aşırı yüklemesi çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yalnızca <xref:System.Xml.Schema.XmlSchemaValidator> nesnenin başlatıldığı özniteliği döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-256">If the overload of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns only the attribute to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="aeb4f-257">Ön işleme hataları yoksa şemayı <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaValidator> nesnenin öğesine ekler.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-257">Adds the schema to the <xref:System.Xml.Schema.XmlSchemaSet> of the <xref:System.Xml.Schema.XmlSchemaValidator> object if it has no preprocessing errors.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="aeb4f-258">Bağlam öğesi geçerliyse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin alt öğeleri olarak beklenen öğe dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-258">If the context element is valid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as children of the context element.</span></span><br /><br /> <span data-ttu-id="aeb4f-259">Bağlam öğesi geçersizse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-259">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span>|<span data-ttu-id="aeb4f-260">Bağlam öğesi geçerliyse ve daha önce yapılan bir çağrı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yoksa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bağlam öğesinde tanımlanan tüm özniteliklerin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-260">If the context element is valid, and if no call to <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> has been previously made, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of all the attributes defined on the context element.</span></span><br /><br /> <span data-ttu-id="aeb4f-261">Bazı öznitelikler zaten doğrulandıktan sonra, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> doğrulanacak kalan özniteliklerin listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-261">If some attributes have already been validated, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the remaining attributes to be validated.</span></span><br /><br /> <span data-ttu-id="aeb4f-262">Bağlam öğesi geçersizse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-262">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="aeb4f-263">Yukarıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-263">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="aeb4f-264">Bağlam özniteliği en üst düzey bir öznitelik ise boş bir dizi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-264">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="aeb4f-265">Aksi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> halde, bağlam öğesinin ilk alt öğesi olarak beklenen öğe dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-265">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="aeb4f-266">Bağlam özniteliği en üst düzey bir öznitelik ise boş bir dizi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-266">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="aeb4f-267">Aksi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> takdirde, doğrulanacak özniteliklerin listesini geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-267">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the list of remaining attributes to be validated.</span></span>|<span data-ttu-id="aeb4f-268">Yukarıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-268">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<span data-ttu-id="aeb4f-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>bağlam öğesinin ilk alt öğesi olarak beklenen öğelerin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="aeb4f-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>bağlam öğesi için henüz doğrulanamayan gerekli ve isteğe bağlı özniteliklerin listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the required and optional attributes that are yet to be validated for the context element.</span></span>|<span data-ttu-id="aeb4f-271">Yukarıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-271">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="aeb4f-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>bağlam öğesinin ilk alt öğesi olarak beklenen öğelerin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="aeb4f-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="aeb4f-274">Yukarıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-274">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="aeb4f-275">Bağlam öğesinin contentType öğesi karmaysa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sonraki konumda beklenen öğelerin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-275">If the context element's contentType is Mixed, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position.</span></span><br /><br /> <span data-ttu-id="aeb4f-276">Bağlam öğesinin contentType öğesi TextOnly veya boşsa boş bir dizi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-276">If the context element's contentType is TextOnly or Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="aeb4f-277">Bağlam öğesinin contentType öğesi Öğetonly ise, bir sonraki <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> konumda beklenen öğe dizisini döndürür, ancak bir doğrulama hatası zaten oluştu.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-277">If the context element's contentType is ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position but a validation error has already occurred.</span></span>|<span data-ttu-id="aeb4f-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>bağlam öğesinin doğrulanmadı özniteliklerin listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span>|<span data-ttu-id="aeb4f-279">Yukarıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-279">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="aeb4f-280">Bağlam beyaz alanı üst düzey boşluk ise, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-280">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="aeb4f-281">Aksi halde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemin davranışı ile aynıdır <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-281">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="aeb4f-282">Bağlam beyaz alanı üst düzey boşluk ise, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-282">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="aeb4f-283">Aksi halde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemin davranışı ile aynıdır <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-283">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="aeb4f-284">Yukarıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-284">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="aeb4f-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>bağlam öğesinden (olası eşdüzey öğeler) sonra beklenen öğe dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected after the context element (possible siblings).</span></span>|<span data-ttu-id="aeb4f-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>bağlam öğesinin doğrulanmadı özniteliklerin listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span><br /><br /> <span data-ttu-id="aeb4f-287">Bağlam öğesinin üst öğesi yoksa, boş bir <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> liste döndürür (bağlam öğesi, üzerinde <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> çağrılan geçerli öğenin üst öğesidir).</span><span class="sxs-lookup"><span data-stu-id="aeb4f-287">If the context element has no parent then <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty list (the context element is the parent of the current element on which <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> was called).</span></span>|<span data-ttu-id="aeb4f-288">Yukarıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-288">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="aeb4f-289">Aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-289">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="aeb4f-290">Aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-290">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="aeb4f-291">Yukarıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-291">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="aeb4f-292">Boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-292">Returns an empty array.</span></span>|<span data-ttu-id="aeb4f-293">Boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-293">Returns an empty array.</span></span>|<span data-ttu-id="aeb4f-294">Yukarıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-294">Same as above.</span></span>|

> [!NOTE]
> <span data-ttu-id="aeb4f-295"><xref:System.Xml.Schema.XmlSchemaValidator> Sınıfın çeşitli özelliklerinin döndürdüğü değerler yukarıdaki tablodaki yöntemlerden herhangi biri çağırarak değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-295">The values returned by the various properties of the <xref:System.Xml.Schema.XmlSchemaValidator> class are not altered by calling any of the methods in the above table.</span></span>

## <a name="see-also"></a><span data-ttu-id="aeb4f-296">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aeb4f-296">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator>
