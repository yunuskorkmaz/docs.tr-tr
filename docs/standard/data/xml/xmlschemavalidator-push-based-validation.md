---
description: Daha fazla bilgi için bkz. XmlSchemaValidator Push-Based doğrulaması
title: XmlSchemaValidator Gönderim Temelli Doğrulaması
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
ms.openlocfilehash: 6492285b26659fabbc72bf56304c5f24790af170
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782617"
---
# <a name="xmlschemavalidator-push-based-validation"></a><span data-ttu-id="33275-103">XmlSchemaValidator Gönderim Temelli Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="33275-103">XmlSchemaValidator Push-Based Validation</span></span>

<span data-ttu-id="33275-104">Sınıfı, XML <xref:System.Xml.Schema.XmlSchemaValidator> verilerini gönderme temelli bir şekılde XML şemalarına karşı doğrulamak için etkili ve yüksek performanslı bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="33275-104">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides an efficient, high-performance mechanism to validate XML data against XML schemas in a push-based manner.</span></span> <span data-ttu-id="33275-105">Örneğin sınıfı, bir XML <xref:System.Xml.Schema.XmlSchemaValidator> bilgisi kümesini BIR XML belgesi olarak seri hale getirmek ve ardından belgeyi bir doğrulama XML okuyucusu kullanarak yeniden yerleştirmek zorunda kalmadan, yerinde doğrulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="33275-105">For example, the <xref:System.Xml.Schema.XmlSchemaValidator> class allows you to validate an XML infoset in-place without having to serialize it as an XML document and then reparse the document using a validating XML reader.</span></span>

<span data-ttu-id="33275-106"><xref:System.Xml.Schema.XmlSchemaValidator>Sınıfı, özel XML veri kaynakları üzerinde doğrulama motorları oluşturmak veya bir doğrulama XML yazıcısı oluşturmak için bir yol olarak, Gelişmiş senaryolarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33275-106">The <xref:System.Xml.Schema.XmlSchemaValidator> class can be used in advanced scenarios such as building validation engines over custom XML data sources or as a way to build a validating XML writer.</span></span>

<span data-ttu-id="33275-107">Aşağıda, <xref:System.Xml.Schema.XmlSchemaValidator> dosyayı şemaya karşı doğrulamak için sınıfının kullanılmasına bir örnek verilmiştir `contosoBooks.xml` `contosoBooks.xsd` .</span><span class="sxs-lookup"><span data-stu-id="33275-107">The following is an example of using the <xref:System.Xml.Schema.XmlSchemaValidator> class to validate the `contosoBooks.xml` file against the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="33275-108">Örnek, <xref:System.Xml.Serialization.XmlSerializer> dosyanın serisini kaldırmak `contosoBooks.xml` ve düğümlerin değerini sınıfının yöntemlerine geçirmek için sınıfını kullanır <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="33275-108">The example uses the <xref:System.Xml.Serialization.XmlSerializer> class to deserialize the `contosoBooks.xml` file and pass the value of the nodes to the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

> [!NOTE]
> <span data-ttu-id="33275-109">Bu örnek, bu konunun bölümleri boyunca kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33275-109">This example is used throughout the sections of this topic.</span></span>

[!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
[!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]

<span data-ttu-id="33275-110">Örnek, `contosoBooks.xml` dosyayı giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="33275-110">The example takes the `contosoBooks.xml` file as input.</span></span>

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

<span data-ttu-id="33275-111">Örnek de `contosoBooks.xsd` bir giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="33275-111">The example also takes the `contosoBooks.xsd` as an input.</span></span>

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

## <a name="validating-xml-data-using-xmlschemavalidator"></a><span data-ttu-id="33275-112">XmlSchemaValidator kullanarak XML verilerini doğrulama</span><span class="sxs-lookup"><span data-stu-id="33275-112">Validating XML Data using XmlSchemaValidator</span></span>

<span data-ttu-id="33275-113">Bir XML bilgi kümesini doğrulamaya başlamak için, önce oluşturucuyu kullanarak sınıfının yeni bir örneğini başlatmalısınız <xref:System.Xml.Schema.XmlSchemaValidator> <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> .</span><span class="sxs-lookup"><span data-stu-id="33275-113">To begin validating an XML infoset, you must first initialize a new instance of the <xref:System.Xml.Schema.XmlSchemaValidator> class using the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor.</span></span>

<span data-ttu-id="33275-114"><xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A>Oluşturucu <xref:System.Xml.XmlNameTable> , <xref:System.Xml.Schema.XmlSchemaSet> ve değerlerini parametre olarak ve bir parametresi olarak alır <xref:System.Xml.XmlNamespaceManager> <xref:System.Xml.Schema.XmlSchemaValidationFlags> .</span><span class="sxs-lookup"><span data-stu-id="33275-114">The <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor takes <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, and <xref:System.Xml.XmlNamespaceManager> objects as parameters as well as a <xref:System.Xml.Schema.XmlSchemaValidationFlags> value as a parameter.</span></span> <span data-ttu-id="33275-115"><xref:System.Xml.XmlNameTable>Nesnesi, şema ad alanı, XML ad alanı vb. gibi iyi bilinen ad alanı dizelerini ayrılamaz ve <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> basit içerik doğrulanırken yöntemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="33275-115">The <xref:System.Xml.XmlNameTable> object is used to atomize well-known namespace strings like the schema namespace, the XML namespace, and so on, and is passed to the <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> method while validating simple content.</span></span> <span data-ttu-id="33275-116"><xref:System.Xml.Schema.XmlSchemaSet>Nesnesi, XML bilgi kümesini doğrulamak için kullanılan XML şemalarını içerir.</span><span class="sxs-lookup"><span data-stu-id="33275-116">The <xref:System.Xml.Schema.XmlSchemaSet> object contains the XML schemas used to validate the XML infoset.</span></span> <span data-ttu-id="33275-117"><xref:System.Xml.XmlNamespaceManager>Nesne, doğrulama sırasında karşılaşılan ad alanlarını çözümlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33275-117">The <xref:System.Xml.XmlNamespaceManager> object is used to resolve namespaces encountered during validation.</span></span> <span data-ttu-id="33275-118">Bu <xref:System.Xml.Schema.XmlSchemaValidationFlags> değer, doğrulamanın belirli özelliklerini devre dışı bırakmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33275-118">The <xref:System.Xml.Schema.XmlSchemaValidationFlags> value is used to disable certain features of validation.</span></span>

<span data-ttu-id="33275-119">Oluşturucu hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> bkz <xref:System.Xml.Schema.XmlSchemaValidator> . sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="33275-119">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="initializing-validation"></a><span data-ttu-id="33275-120">Doğrulama başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="33275-120">Initializing Validation</span></span>

<span data-ttu-id="33275-121">Bir nesne oluşturulduktan sonra <xref:System.Xml.Schema.XmlSchemaValidator> , <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> nesnenin durumunu başlatmak için kullanılan iki aşırı yüklenmiş yöntem vardır <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="33275-121">After an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed, there are two overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods used to initialize the state of the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="33275-122">Aşağıdaki iki <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> Yöntem vardır.</span><span class="sxs-lookup"><span data-stu-id="33275-122">The following are the two <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

- <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>

<span data-ttu-id="33275-123">Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Yöntem, bir <xref:System.Xml.Schema.XmlSchemaValidator> nesneyi başlangıç durumuna başlatır ve bir <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> parametresi olarak alan aşırı yüklenmiş yöntem, <xref:System.Xml.Schema.XmlSchemaObject> <xref:System.Xml.Schema.XmlSchemaValidator> kısmi doğrulama için bir nesneyi başlangıç durumuna başlatır.</span><span class="sxs-lookup"><span data-stu-id="33275-123">The default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state, and the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="33275-124">Her iki <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> Yöntem de yalnızca bir nesne oluşturulduktan sonra <xref:System.Xml.Schema.XmlSchemaValidator> veya bir çağrısından sonra çağrılabilir <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A> .</span><span class="sxs-lookup"><span data-stu-id="33275-124">Both <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods can only be called immediately after an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed or after a call to <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span></span>

<span data-ttu-id="33275-125">Yöntemine bir örnek için <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> , giriş bölümündeki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="33275-125">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method, see the example in the introduction.</span></span> <span data-ttu-id="33275-126">Yöntemi hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> bkz <xref:System.Xml.Schema.XmlSchemaValidator> . sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="33275-126">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="partial-validation"></a><span data-ttu-id="33275-127">Kısmi doğrulama</span><span class="sxs-lookup"><span data-stu-id="33275-127">Partial Validation</span></span>

<span data-ttu-id="33275-128">Bir <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> parametre olarak alan yöntemi, <xref:System.Xml.Schema.XmlSchemaObject> <xref:System.Xml.Schema.XmlSchemaValidator> kısmi doğrulama için bir nesneyi başlangıç durumuna başlatır.</span><span class="sxs-lookup"><span data-stu-id="33275-128">The <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>

<span data-ttu-id="33275-129">Aşağıdaki örnekte, <xref:System.Xml.Schema.XmlSchemaObject> yöntemi kullanılarak kısmi doğrulama için bir başlatılır <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="33275-129">In the following example, an <xref:System.Xml.Schema.XmlSchemaObject> is initialized for partial validation using the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="33275-130">`orderNumber`Şema öğesi, <xref:System.Xml.XmlQualifiedName> <xref:System.Xml.Schema.XmlSchemaObjectTable> nesnesinin özelliği tarafından döndürülen koleksiyonda tarafından şema öğesi seçilerek geçirilir <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> <xref:System.Xml.Schema.XmlSchemaSet> .</span><span class="sxs-lookup"><span data-stu-id="33275-130">The `orderNumber` schema element is passed by selecting the schema element by <xref:System.Xml.XmlQualifiedName> in the <xref:System.Xml.Schema.XmlSchemaObjectTable> collection returned by the <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> object.</span></span> <span data-ttu-id="33275-131"><xref:System.Xml.Schema.XmlSchemaValidator>Nesne daha sonra bu özel öğeyi doğrular.</span><span class="sxs-lookup"><span data-stu-id="33275-131">The <xref:System.Xml.Schema.XmlSchemaValidator> object then validates this specific element.</span></span>

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

<span data-ttu-id="33275-132">Örnek, aşağıdaki XML şemasını giriş olarak alır.</span><span class="sxs-lookup"><span data-stu-id="33275-132">The example takes the following XML schema as input.</span></span>

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="orderNumber" type="xs:int" />
</xs:schema>
```

<span data-ttu-id="33275-133">Yöntemi hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> bkz <xref:System.Xml.Schema.XmlSchemaValidator> . sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="33275-133">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="adding-additional-schemas"></a><span data-ttu-id="33275-134">Ek şemalar ekleme</span><span class="sxs-lookup"><span data-stu-id="33275-134">Adding Additional Schemas</span></span>

<span data-ttu-id="33275-135"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A>Sınıfının yöntemi, <xref:System.Xml.Schema.XmlSchemaValidator> doğrulama sırasında kullanılan şemalar KÜMESINE bir XML şeması eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33275-135">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method of the <xref:System.Xml.Schema.XmlSchemaValidator> class is used to add an XML schema to the set of schemas used during validation.</span></span> <span data-ttu-id="33275-136"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A>Yöntemi, DOĞRULANAN xml bilgi kümesindeki bir satır ıçı XML şeması ile karşılaşanın etkisinin benzetimini yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33275-136">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method can be used to simulate the effect of encountering an inline XML schema in the XML infoset being validated.</span></span>

> [!NOTE]
> <span data-ttu-id="33275-137">Parametrenin hedef ad alanı, <xref:System.Xml.Schema.XmlSchema> nesne tarafından zaten karşılaşılan hiçbir öğe veya öznitelikle eşleşmiyor <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="33275-137">The target namespace of the <xref:System.Xml.Schema.XmlSchema> parameter cannot match that of any element or attribute already encountered by the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>
>
> <span data-ttu-id="33275-138">Değer, <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> oluşturucuya bir parametre olarak geçirilmemişse <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> , <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Yöntem hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="33275-138">If the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> value was not passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method does nothing.</span></span>

<span data-ttu-id="33275-139">Yöntemin sonucu, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> doğrulanan GEÇERLI XML düğümü bağlamına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-139">The result of the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method is dependant on the current XML node context being validated.</span></span> <span data-ttu-id="33275-140">Doğrulama bağlamları hakkında daha fazla bilgi için bu konunun "doğrulama bağlamı" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="33275-140">For more information about validation contexts, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="33275-141">Yöntemi hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> bkz <xref:System.Xml.Schema.XmlSchemaValidator> . sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="33275-141">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="validating-elements-attributes-and-content"></a><span data-ttu-id="33275-142">Öğeleri, öznitelikleri ve Içeriği doğrulama</span><span class="sxs-lookup"><span data-stu-id="33275-142">Validating Elements, Attributes, and Content</span></span>

<span data-ttu-id="33275-143">Sınıfı, XML <xref:System.Xml.Schema.XmlSchemaValidator> şemalarında xml bilgi kümesindeki öğeleri, öznitelikleri ve içerikleri doğrulamak için kullanılan çeşitli yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="33275-143">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides several methods used to validate elements, attributes, and content in an XML infoset against XML schemas.</span></span> <span data-ttu-id="33275-144">Aşağıdaki tabloda bu yöntemlerin her biri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="33275-144">The following table describes each of these methods.</span></span>

|<span data-ttu-id="33275-145">Yöntem</span><span class="sxs-lookup"><span data-stu-id="33275-145">Method</span></span>|<span data-ttu-id="33275-146">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33275-146">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="33275-147">Geçerli bağlamdaki öğe adını doğrular.</span><span class="sxs-lookup"><span data-stu-id="33275-147">Validates the element name in the current context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="33275-148">Geçerli öğe bağlamındaki özniteliği veya <xref:System.Xml.Schema.XmlSchemaAttribute> yöntemine parametre olarak geçirilen nesneye karşı doğrular <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> .</span><span class="sxs-lookup"><span data-stu-id="33275-148">Validates the attribute in the current element context or against the <xref:System.Xml.Schema.XmlSchemaAttribute> object passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="33275-149">Öğe bağlamındaki tüm gerekli özniteliklerin mevcut olup olmadığını doğrular ve <xref:System.Xml.Schema.XmlSchemaValidator> nesneyi öğenin alt içeriğini doğrulamak üzere hazırlar.</span><span class="sxs-lookup"><span data-stu-id="33275-149">Verifies whether all the required attributes in the element context are present and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate the child content of the element.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="33275-150">Geçerli öğe bağlamında metnin izin verilip verilmeyeceğini doğrular ve geçerli öğede basit içerik varsa doğrulama için metni biriktirir.</span><span class="sxs-lookup"><span data-stu-id="33275-150">Validates whether text is allowed in the current element context, and accumulates the text for validation if the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="33275-151">Geçerli öğe bağlamında beyaz boşluğa izin verilip verilmeyeceğini doğrular ve geçerli öğenin basit içeriğe sahip olup olmadığını doğrulamak için beyaz boşluğu biriktirir.</span><span class="sxs-lookup"><span data-stu-id="33275-151">Validates whether white-space is allowed in the current element context, and accumulates the white-space for validation whether the current element has simple content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="33275-152">Öğenin metin içeriğinin basit içeriğe sahip öğeler için kendi veri türüne göre geçerli olup olmadığını doğrular ve karmaşık içerikli öğeler için geçerli öğenin içeriğinin tamamlanıp tamamlanmadığını doğrular.</span><span class="sxs-lookup"><span data-stu-id="33275-152">Verifies whether the text content of the element is valid according to its data type for elements with simple content, and verifies whether the content of the current element is complete for elements with complex content.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="33275-153">Geçerli öğe içeriğinin geçerliliğini atlar ve <xref:System.Xml.Schema.XmlSchemaValidator> üst öğenin bağlamındaki içeriği doğrulamak için nesneyi hazırlar.</span><span class="sxs-lookup"><span data-stu-id="33275-153">Skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="33275-154">Doğrulama seçeneği ayarlandıysa, doğrulamayı sonlandırır ve tüm XML belgesi için kimlik kısıtlamalarını denetler <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> .</span><span class="sxs-lookup"><span data-stu-id="33275-154">Ends validation and checks identity constraints for the entire XML document if the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> validation option is set.</span></span>|

> [!NOTE]
> <span data-ttu-id="33275-155"><xref:System.Xml.Schema.XmlSchemaValidator>Sınıfında, önceki tabloda açıklanan yöntemlerin her birine yapılan çağrıların sırasını ve tekrarını uygulayan tanımlı bir durum geçişi vardır.</span><span class="sxs-lookup"><span data-stu-id="33275-155">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods described in the previous table.</span></span> <span data-ttu-id="33275-156">Sınıfın belirli durum geçişi, <xref:System.Xml.Schema.XmlSchemaValidator> Bu konunun "XmlSchemaValidator durum geçişi" bölümünde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="33275-156">The specific state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class is described in the "XmlSchemaValidator State Transition" section of this topic.</span></span>

<span data-ttu-id="33275-157">Bir XML bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan yöntemlere örnek olarak, önceki bölümde bulunan örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="33275-157">For an example of the methods used to validate elements, attributes, and content in an XML infoset, see the example in the previous section.</span></span> <span data-ttu-id="33275-158">Bu yöntemler hakkında daha fazla bilgi için bkz <xref:System.Xml.Schema.XmlSchemaValidator> . sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="33275-158">For more information about these methods, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="validating-content-using-an-xmlvaluegetter"></a><span data-ttu-id="33275-159">XmlValueGetter kullanarak Içerik doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="33275-159">Validating Content Using an XmlValueGetter</span></span>

<span data-ttu-id="33275-160">Öznitelik, <xref:System.Xml.Schema.XmlValueGetter> `delegate` metin veya boşluk düğümlerinin değerini öznitelik, metin veya boşluk düğümünün XML şeması tanım DILI (xsd) türüyle uyumlu ortak dil çalışma zamanı (CLR) türleri olarak geçirmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33275-160">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` can be used to pass the value of attribute, text, or white-space nodes as a Common Language Runtime (CLR) types compatible with the XML Schema Definition Language (XSD) type of the attribute, text, or white-space node.</span></span> <span data-ttu-id="33275-161">Bir <xref:System.Xml.Schema.XmlValueGetter> `delegate` özniteliğin, metnin veya boşluk düğümünün clr değeri zaten kullanılabilirse ve bunu bir `string` ve daha sonra doğrulama için yeniden ayrıştırmanın maliyetini önlediği durumlarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-161">An <xref:System.Xml.Schema.XmlValueGetter>`delegate` is useful if the CLR value of an attribute, text, or white-space node is already available, and avoids the cost of converting it to a `string` and then reparsing it again for validation.</span></span>

<span data-ttu-id="33275-162"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> , Ve <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> yöntemleri aşırı yüklenmiş ve öznitelik, metin veya boşluk düğümlerinin değeri veya olarak kabul edilir `string` <xref:System.Xml.Schema.XmlValueGetter> `delegate` .</span><span class="sxs-lookup"><span data-stu-id="33275-162">The <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> methods are overloaded and accept the value of attribute, text, or white-space nodes as a `string` or <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span></span>

<span data-ttu-id="33275-163">Sınıfının aşağıdaki yöntemleri bir <xref:System.Xml.Schema.XmlSchemaValidator> parametre olarak kabul eder <xref:System.Xml.Schema.XmlValueGetter> `delegate` .</span><span class="sxs-lookup"><span data-stu-id="33275-163">The following methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlValueGetter>`delegate` as a parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>

<span data-ttu-id="33275-164">Aşağıda, <xref:System.Xml.Schema.XmlValueGetter> `delegate` <xref:System.Xml.Schema.XmlSchemaValidator> giriş içindeki sınıf örneğinizden alınan bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="33275-164">The following is an example <xref:System.Xml.Schema.XmlValueGetter>`delegate` taken from the <xref:System.Xml.Schema.XmlSchemaValidator> class example in the introduction.</span></span> <span data-ttu-id="33275-165">, Bir <xref:System.Xml.Schema.XmlValueGetter> `delegate` özniteliğin değerini bir nesne olarak döndürür <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="33275-165">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` returns the value of an attribute as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="33275-166"><xref:System.DateTime>Tarafından döndürülen bu nesneyi doğrulamak için <xref:System.Xml.Schema.XmlValueGetter> , nesnesi, <xref:System.Xml.Schema.XmlSchemaValidator> özniteliğin veri türü Için önce onu ValueType öğesine dönüştürür (ValueType, xsd türü için varsayılan clr eşlemedir) ve ardından dönüştürülen değer üzerindeki modelleri denetler.</span><span class="sxs-lookup"><span data-stu-id="33275-166">To validate this <xref:System.DateTime> object returned by the <xref:System.Xml.Schema.XmlValueGetter>, the <xref:System.Xml.Schema.XmlSchemaValidator> object first converts it to the ValueType (ValueType is the default CLR mapping for the XSD type) for the data type of the attribute and then checks facets on the converted value.</span></span>

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

<span data-ttu-id="33275-167">Öğesinin tamamen bir örneği için <xref:System.Xml.Schema.XmlValueGetter> `delegate` giriş bölümündeki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="33275-167">For a complete example of the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the example in the introduction.</span></span> <span data-ttu-id="33275-168">Hakkında daha fazla bilgi için, <xref:System.Xml.Schema.XmlValueGetter> `delegate` <xref:System.Xml.Schema.XmlValueGetter> ve <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="33275-168">For more information about the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the <xref:System.Xml.Schema.XmlValueGetter>, and <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="post-schema-validation-information"></a><span data-ttu-id="33275-169">Şema sonrası doğrulama-bilgi</span><span class="sxs-lookup"><span data-stu-id="33275-169">Post-Schema-Validation-Information</span></span>

<span data-ttu-id="33275-170"><xref:System.Xml.Schema.XmlSchemaInfo>Sınıfı, sınıfı tarafından doğrulanan BIR XML düğümünün şema sonrası-doğrulama bilgilerinin bazılarını temsil eder <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="33275-170">The <xref:System.Xml.Schema.XmlSchemaInfo> class represents some of the Post-Schema-Validation-Information of an XML node validated by the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="33275-171">Sınıfının çeşitli yöntemleri <xref:System.Xml.Schema.XmlSchemaValidator> bir <xref:System.Xml.Schema.XmlSchemaInfo> nesneyi isteğe bağlı, () parametre olarak kabul `null` eder `out` .</span><span class="sxs-lookup"><span data-stu-id="33275-171">Various methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an optional, (`null`) `out` parameter.</span></span>

<span data-ttu-id="33275-172">Doğrulama başarılı olduğunda, <xref:System.Xml.Schema.XmlSchemaInfo> nesnesinin özellikleri doğrulamanın sonuçlarıyla ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="33275-172">Upon successful validation, properties of the <xref:System.Xml.Schema.XmlSchemaInfo> object are set with the results of the validation.</span></span> <span data-ttu-id="33275-173">Örneğin, yöntemini kullanarak bir özniteliğin başarıyla doğrulanması sırasında <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> , <xref:System.Xml.Schema.XmlSchemaInfo> nesnenin (belirtilmişse) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A> , <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A> , <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A> ve <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> özellikleri doğrulamanın sonuçlarıyla ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="33275-173">For example, upon successful validation of an attribute using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the <xref:System.Xml.Schema.XmlSchemaInfo> object's (if specified) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, and <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> properties are set with the results of the validation.</span></span>

<span data-ttu-id="33275-174">Aşağıdaki <xref:System.Xml.Schema.XmlSchemaValidator> sınıf yöntemleri bir <xref:System.Xml.Schema.XmlSchemaInfo> nesneyi out parametresi olarak kabul eder.</span><span class="sxs-lookup"><span data-stu-id="33275-174">The following <xref:System.Xml.Schema.XmlSchemaValidator> class methods accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an out parameter.</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>

- <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>

<span data-ttu-id="33275-175">Sınıfının tamamen bir örneği için <xref:System.Xml.Schema.XmlSchemaInfo> , giriş bölümündeki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="33275-175">For a complete example of the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the example in the introduction.</span></span> <span data-ttu-id="33275-176">Sınıfı hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaInfo> bkz <xref:System.Xml.Schema.XmlSchemaInfo> . sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="33275-176">For more information about the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a><span data-ttu-id="33275-177">Beklenen parçacık, öznitelik ve belirtilmemiş varsayılan öznitelikleri alma</span><span class="sxs-lookup"><span data-stu-id="33275-177">Retrieving Expected Particles, Attributes, and Unspecified Default Attributes</span></span>

<span data-ttu-id="33275-178"><xref:System.Xml.Schema.XmlSchemaValidator>Sınıfı <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> , <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> geçerli doğrulama bağlamında beklenen parçacıkların, özniteliklerin ve belirtilmemiş varsayılan özniteliklerin alınması için, ve yöntemlerini sağlar.</span><span class="sxs-lookup"><span data-stu-id="33275-178">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> methods to retrieve the expected particles, attributes, and unspecified default attributes in the current validation context.</span></span>

#### <a name="retrieving-expected-particles"></a><span data-ttu-id="33275-179">Beklenen parçacık alınıyor</span><span class="sxs-lookup"><span data-stu-id="33275-179">Retrieving Expected Particles</span></span>

<span data-ttu-id="33275-180"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>Yöntemi, <xref:System.Xml.Schema.XmlSchemaParticle> geçerli öğe bağlamında beklenen parçacık içeren bir nesne dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-180">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaParticle> objects containing the expected particles in the current element context.</span></span> <span data-ttu-id="33275-181">Yöntemi tarafından döndürülebilecek geçerli parçacık <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> , <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAny> sınıflarının örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="33275-181">The valid particles that can be returned by the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method are instances of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAny> classes.</span></span>

<span data-ttu-id="33275-182">İçerik modeli için Oluşturucu bir ise `xs:sequence` , yalnızca dizideki bir sonraki parçacık döndürülür.</span><span class="sxs-lookup"><span data-stu-id="33275-182">When the compositor for the content model is an `xs:sequence`, only the next particle in the sequence is returned.</span></span> <span data-ttu-id="33275-183">İçerik modeli için Oluşturucu bir `xs:all` veya ise `xs:choice` , geçerli öğe bağlamında izleyelebilecek tüm geçerli parçacık döndürülür.</span><span class="sxs-lookup"><span data-stu-id="33275-183">If the compositor for the content model is an `xs:all` or an `xs:choice`, then all valid particles that could follow in the current element context are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="33275-184">Yöntemi çağrıldıktan <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> hemen sonra yöntem çağrılırsa <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> , <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi tüm genel öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-184">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called immediately after calling the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns all global elements.</span></span>

<span data-ttu-id="33275-185">Örneğin, XML şeması tanım dili (XSD) şeması ve izleyen XML belgesinde öğesi doğrulandıktan sonra `book` `book` öğesi geçerli öğe bağlamıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-185">For example, in the XML Schema Definition Language (XSD) schema and XML document that follow, after validating the `book` element, the `book` element is the current element context.</span></span> <span data-ttu-id="33275-186"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>Yöntemi <xref:System.Xml.Schema.XmlSchemaElement> , öğesini temsil eden tek bir nesne içeren bir dizi döndürür `title` .</span><span class="sxs-lookup"><span data-stu-id="33275-186">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `title` element.</span></span> <span data-ttu-id="33275-187">Doğrulama bağlamı `title` öğesi olduğunda, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-187">When the validation context is the `title` element, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an empty array.</span></span> <span data-ttu-id="33275-188"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> `title` Öğe doğrulandıktan sonra, ancak öğe doğrulandıktan sonra yöntemi çağrılırsa `description` , <xref:System.Xml.Schema.XmlSchemaElement> öğesini temsil eden tek bir nesne içeren bir dizi döndürür `description` .</span><span class="sxs-lookup"><span data-stu-id="33275-188">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `title` element has been validated but before the `description` element has been validated, it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `description` element.</span></span> <span data-ttu-id="33275-189"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>Öğe doğrulandıktan sonra yöntemi çağrılırsa, `description` <xref:System.Xml.Schema.XmlSchemaAny> joker karakteri temsil eden tek bir nesne içeren bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-189">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `description` element has been validated then it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaAny> object representing the wildcard.</span></span>

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

 <span data-ttu-id="33275-190">Örnek aşağıdaki XML 'i giriş olarak alır:</span><span class="sxs-lookup"><span data-stu-id="33275-190">The example takes the following XML as input:</span></span>

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

<span data-ttu-id="33275-191">Örnek, aşağıdaki XSD şemasını giriş olarak alır:</span><span class="sxs-lookup"><span data-stu-id="33275-191">The example takes the following XSD schema as input:</span></span>

```xml
<book>
  <title>My Book</title>
  <description>My Book's Description</description>
  <namespace>System.Xml.Schema</namespace>
</book>
```

> [!NOTE]
> <span data-ttu-id="33275-192"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Sınıfının, ve yöntemlerinin sonuçları, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> <xref:System.Xml.Schema.XmlSchemaValidator> doğrulanan geçerli bağlamına bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-192">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="33275-193">Daha fazla bilgi için bu konunun "doğrulama bağlamı" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="33275-193">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="33275-194">Yöntemine bir örnek için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> , giriş bölümündeki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="33275-194">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="33275-195">Yöntemi hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bkz <xref:System.Xml.Schema.XmlSchemaValidator> . sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="33275-195">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-expected-attributes"></a><span data-ttu-id="33275-196">Beklenen öznitelikleri alma</span><span class="sxs-lookup"><span data-stu-id="33275-196">Retrieving Expected Attributes</span></span>

<span data-ttu-id="33275-197"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>Yöntemi, <xref:System.Xml.Schema.XmlSchemaAttribute> geçerli öğe bağlamında beklenen öznitelikleri içeren bir nesne dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-197">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaAttribute> objects containing the expected attributes in the current element context.</span></span>

<span data-ttu-id="33275-198">Örneğin, giriş bölümündeki örnekte <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi, öğesinin tüm özniteliklerini almak için kullanılır `book` .</span><span class="sxs-lookup"><span data-stu-id="33275-198">For example, in the example in the introduction, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method is used to retrieve all the attributes of the `book` element.</span></span>

<span data-ttu-id="33275-199">Yöntemi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> hemen sonra çağırdığınızda <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> , XML belgesinde görünebilen tüm öznitelikler döndürülür.</span><span class="sxs-lookup"><span data-stu-id="33275-199">If you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method immediately after the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> method, all the attributes that could appear in the XML document are returned.</span></span> <span data-ttu-id="33275-200">Ancak, yöntemi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bir veya daha fazla yöntem çağrısından sonra çağırdığınızda <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> , geçerli öğe için henüz doğrulanmamış öznitelikler döndürülür.</span><span class="sxs-lookup"><span data-stu-id="33275-200">However, if you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method after one or more calls to the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the attributes that have not yet been validated for the current element are returned.</span></span>

> [!NOTE]
> <span data-ttu-id="33275-201"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Sınıfının, ve yöntemlerinin sonuçları, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> <xref:System.Xml.Schema.XmlSchemaValidator> doğrulanan geçerli bağlamına bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-201">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="33275-202">Daha fazla bilgi için bu konunun "doğrulama bağlamı" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="33275-202">For more information, see the "Validation Context" section of this topic.</span></span>

<span data-ttu-id="33275-203">Yöntemine bir örnek için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> , giriş bölümündeki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="33275-203">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="33275-204">Yöntemi hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bkz <xref:System.Xml.Schema.XmlSchemaValidator> . sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="33275-204">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

#### <a name="retrieving-unspecified-default-attributes"></a><span data-ttu-id="33275-205">Belirtilmeyen varsayılan öznitelikler alınıyor</span><span class="sxs-lookup"><span data-stu-id="33275-205">Retrieving Unspecified Default Attributes</span></span>

<span data-ttu-id="33275-206"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>Yöntemi, <xref:System.Collections.ArrayList> <xref:System.Xml.Schema.XmlSchemaAttribute> öğe bağlamındaki yöntemi kullanılarak daha önce doğrulanmamış varsayılan değerlere sahip herhangi bir öznitelik için nesneleri ile belirtilen şekilde doldurur <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> .</span><span class="sxs-lookup"><span data-stu-id="33275-206">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method populates the <xref:System.Collections.ArrayList> specified with <xref:System.Xml.Schema.XmlSchemaAttribute> objects for any attributes with default values that have not been previously validated using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method in the element context.</span></span> <span data-ttu-id="33275-207">Yöntemi, <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> öğe bağlamındaki her bir öznitelikte yöntemi çağrıldıktan sonra çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-207">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be called after calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method on each attribute in the element context.</span></span> <span data-ttu-id="33275-208"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>Yöntemi, DOĞRULANAN XML belgesine hangi varsayılan özniteliklerin ekleneceğini belirlemek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-208">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be used to determine what default attributes are to be inserted into the XML document being validated.</span></span>

<span data-ttu-id="33275-209">Yöntemi hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> bkz <xref:System.Xml.Schema.XmlSchemaValidator> . sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="33275-209">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>

### <a name="handling-schema-validation-events"></a><span data-ttu-id="33275-210">Şema doğrulama olaylarını işleme</span><span class="sxs-lookup"><span data-stu-id="33275-210">Handling Schema Validation Events</span></span>

<span data-ttu-id="33275-211">Şema doğrulama uyarıları ve doğrulama sırasında karşılaşılan hatalar, <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> sınıfının olayı tarafından işlenir <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="33275-211">Schema validation warnings and errors encountered during validation are handled by the <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> event of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

<span data-ttu-id="33275-212">Şema doğrulama uyarıları bir <xref:System.Xml.Schema.XmlSeverityType> değere sahiptir <xref:System.Xml.Schema.XmlSeverityType.Warning> ve şema doğrulama hatalarının değeri vardır <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Error> .</span><span class="sxs-lookup"><span data-stu-id="33275-212">Schema validation warnings have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning> and schema validation errors have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="33275-213">Hiçbiri <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> atanmamışsa, bir <xref:System.Xml.Schema.XmlSchemaValidationException> değeri olan tüm şema doğrulama hataları için bir atılır <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Error> .</span><span class="sxs-lookup"><span data-stu-id="33275-213">If no <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> has been assigned, an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown for all schema validation errors with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="33275-214">Ancak, bir <xref:System.Xml.Schema.XmlSchemaValidationException> değeri olan şema doğrulama uyarıları için bir oluşturulmaz <xref:System.Xml.Schema.XmlSeverityType> <xref:System.Xml.Schema.XmlSeverityType.Warning> .</span><span class="sxs-lookup"><span data-stu-id="33275-214">However, an <xref:System.Xml.Schema.XmlSchemaValidationException> is not thrown for schema validation warnings with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span></span>

<span data-ttu-id="33275-215">Aşağıda, <xref:System.Xml.Schema.ValidationEventHandler> giriş içindeki örnekte alınan şema doğrulama uyarılarını ve şema doğrulama sırasında karşılaşılan hataları alan bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="33275-215">The following is an example of a <xref:System.Xml.Schema.ValidationEventHandler> that receives schema validation warnings and errors encountered during schema validation taken from the example in the introduction.</span></span>

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

<span data-ttu-id="33275-216">Öğesinin tamamen bir örneği için <xref:System.Xml.Schema.ValidationEventHandler> giriş bölümündeki örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="33275-216">For a complete example of the <xref:System.Xml.Schema.ValidationEventHandler>, see the example in the introduction.</span></span> <span data-ttu-id="33275-217">Daha fazla bilgi için bkz <xref:System.Xml.Schema.XmlSchemaInfo> . sınıf başvurusu belgeleri.</span><span class="sxs-lookup"><span data-stu-id="33275-217">For more information, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>

## <a name="xmlschemavalidator-state-transition"></a><span data-ttu-id="33275-218">XmlSchemaValidator durum geçişi</span><span class="sxs-lookup"><span data-stu-id="33275-218">XmlSchemaValidator State Transition</span></span>

<span data-ttu-id="33275-219"><xref:System.Xml.Schema.XmlSchemaValidator>Sınıfında, BIR XML bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan yöntemlerin her birine yapılan çağrıların sırasını ve oluşumunu uygulayan tanımlı bir durum geçişi vardır.</span><span class="sxs-lookup"><span data-stu-id="33275-219">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods used to validate elements, attributes, and content in an XML infoset.</span></span>

<span data-ttu-id="33275-220">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaValidator> , sınıfının durum geçişi ve her durumda yapılabilecek Yöntem çağrılarının sırası ve oluşumu açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="33275-220">The following table describes the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class, and the sequence and occurrence of method calls that can be made in each state.</span></span>

|<span data-ttu-id="33275-221">Durum</span><span class="sxs-lookup"><span data-stu-id="33275-221">State</span></span>|<span data-ttu-id="33275-222">Transition</span><span class="sxs-lookup"><span data-stu-id="33275-222">Transition</span></span>|
|-----------|----------------|
|<span data-ttu-id="33275-223">Doğrulama</span><span class="sxs-lookup"><span data-stu-id="33275-223">Validate</span></span>|<span data-ttu-id="33275-224"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> ( <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel \*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span><span class="sxs-lookup"><span data-stu-id="33275-224"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel\*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span></span>|
|<span data-ttu-id="33275-225">TopLevel</span><span class="sxs-lookup"><span data-stu-id="33275-225">TopLevel</span></span>|<span data-ttu-id="33275-226"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; öğesi</span><span class="sxs-lookup"><span data-stu-id="33275-226"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|
|<span data-ttu-id="33275-227">Öğe</span><span class="sxs-lookup"><span data-stu-id="33275-227">Element</span></span>|<span data-ttu-id="33275-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* ( <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> İçerik \* )?</span><span class="sxs-lookup"><span data-stu-id="33275-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span></span> <span data-ttu-id="33275-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="33275-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="33275-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="33275-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="33275-231"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> İçerik \* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="33275-231"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span>|
|<span data-ttu-id="33275-232">Content</span><span class="sxs-lookup"><span data-stu-id="33275-232">Content</span></span>|<span data-ttu-id="33275-233"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; öğesi</span><span class="sxs-lookup"><span data-stu-id="33275-233"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|

> [!NOTE]
> <span data-ttu-id="33275-234">Bir <xref:System.InvalidOperationException> nesnenin geçerli durumuna göre yanlış sırada Yöntem çağrısı yapıldığında Yukarıdaki tablodaki yöntemlerin her biri tarafından oluşturulur <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="33275-234">An <xref:System.InvalidOperationException> is thrown by each of the methods in the table above when the call to the method is made in the incorrect sequence according to the current state of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>

<span data-ttu-id="33275-235">Yukarıdaki durum geçiş tablosu, sınıfının durum geçişinin her durumu için çağrılabilecek yöntemleri ve diğer durumları betimleyen noktalama sembolleri kullanır <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="33275-235">The state transition table above uses punctuation symbols to describe the methods and other states that can be called for each state of the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="33275-236">Kullanılan semboller, belge türü tanımı (DTD) için XML standartları başvurusunda bulunan sembollerdir.</span><span class="sxs-lookup"><span data-stu-id="33275-236">The symbols used are the same symbols found in the XML Standards reference for Document Type Definition (DTD).</span></span>

<span data-ttu-id="33275-237">Aşağıdaki tabloda, yukarıdaki durum geçiş tablosunda bulunan noktalama simgelerinin, sınıfının durum geçişi içindeki her durum için çağrılabilecek yöntemleri ve diğer durumları nasıl etkilediği açıklanır <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="33275-237">The following table describes how the punctuation symbols found in the state transition table above affect the methods and other states that can be called for each state in the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>

|<span data-ttu-id="33275-238">Sembol</span><span class="sxs-lookup"><span data-stu-id="33275-238">Symbol</span></span>|<span data-ttu-id="33275-239">Description</span><span class="sxs-lookup"><span data-stu-id="33275-239">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="33275-240">&#124;</span><span class="sxs-lookup"><span data-stu-id="33275-240">&#124;</span></span>|<span data-ttu-id="33275-241">Ya Yöntem ya da durum (çubuk veya sonrasında bir veya sonrasında) çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="33275-241">Either method or state (the one before the bar or the one after it) can be called.</span></span>|
|<span data-ttu-id="33275-242">?</span><span class="sxs-lookup"><span data-stu-id="33275-242">?</span></span>|<span data-ttu-id="33275-243">Soru işaretinden önce gelen yöntem veya durum isteğe bağlıdır, ancak çağrılırsa yalnızca bir kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="33275-243">The method or state that precedes the question mark is optional but if it is called it can only be called once.</span></span>|
|\*|<span data-ttu-id="33275-244">Simgeden önceki yöntem veya durum \* isteğe bağlıdır ve birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="33275-244">The method or state that precedes the \* symbol is optional, and can be called more than once.</span></span>|

## <a name="validation-context"></a><span data-ttu-id="33275-245">Doğrulama bağlamı</span><span class="sxs-lookup"><span data-stu-id="33275-245">Validation Context</span></span>

<span data-ttu-id="33275-246"><xref:System.Xml.Schema.XmlSchemaValidator>BIR XML bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan sınıfının yöntemleri, bir nesnenin doğrulama bağlamını değiştirir <xref:System.Xml.Schema.XmlSchemaValidator> .</span><span class="sxs-lookup"><span data-stu-id="33275-246">The methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset, change the validation context of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="33275-247">Örneğin, <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> yöntemi geçerli öğe içeriğinin doğrulanmasını atlar ve <xref:System.Xml.Schema.XmlSchemaValidator> nesneyi üst öğenin bağlamındaki içeriği doğrulamaya hazırlar; geçerli öğenin tüm alt öğeleri için doğrulama atlanmak ve sonra yöntemi çağırmak eşdeğerdir <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> .</span><span class="sxs-lookup"><span data-stu-id="33275-247">For example, the <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> method skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context; it is equivalent to skipping validation for all the children of the current element and then calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> method.</span></span>

<span data-ttu-id="33275-248"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Sınıfının, ve yöntemlerinin sonuçları, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> <xref:System.Xml.Schema.XmlSchemaValidator> doğrulanan geçerli bağlamına bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-248">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span>

<span data-ttu-id="33275-249">Aşağıdaki tabloda <xref:System.Xml.Schema.XmlSchemaValidator> , BIR XML bilgi kümesindeki öğeleri, öznitelikleri ve içeriği doğrulamak için kullanılan sınıfının yöntemlerinden biri çağrıldıktan sonra bu yöntemleri çağırma sonuçları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="33275-249">The following table describes the results of calling these methods after calling one of the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset.</span></span>

|<span data-ttu-id="33275-250">Yöntem</span><span class="sxs-lookup"><span data-stu-id="33275-250">Method</span></span>|<span data-ttu-id="33275-251">Getexlartedparçacıya</span><span class="sxs-lookup"><span data-stu-id="33275-251">GetExpectedParticles</span></span>|<span data-ttu-id="33275-252">Getexeditedattributes</span><span class="sxs-lookup"><span data-stu-id="33275-252">GetExpectedAttributes</span></span>|<span data-ttu-id="33275-253">AddSchema</span><span class="sxs-lookup"><span data-stu-id="33275-253">AddSchema</span></span>|
|------------|--------------------------|---------------------------|---------------|
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|<span data-ttu-id="33275-254">Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntem çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> tüm genel öğeleri içeren bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-254">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an array containing all global elements.</span></span><br /><br /> <span data-ttu-id="33275-255">Bir <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> parametre olarak alan aşırı yüklenmiş yöntem <xref:System.Xml.Schema.XmlSchemaObject> bir öğenin kısmi doğrulanmasını başlatmak için çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yalnızca <xref:System.Xml.Schema.XmlSchemaValidator> nesnenin başlatıldığı öğeyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-255">If the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns only the element to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="33275-256">Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntem çağrılırsa <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-256">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="33275-257">Bir <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> <xref:System.Xml.Schema.XmlSchemaObject> özniteliğin kısmi doğrulanmasını başlatmak için bir parametre olarak alan yönteminin aşırı yüklemesi çağrılırsa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yalnızca <xref:System.Xml.Schema.XmlSchemaValidator> nesnenin başlatıldığı özniteliği döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-257">If the overload of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns only the attribute to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="33275-258"><xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaValidator> Ön işleme hataları yoksa şemayı nesnenin öğesine ekler.</span><span class="sxs-lookup"><span data-stu-id="33275-258">Adds the schema to the <xref:System.Xml.Schema.XmlSchemaSet> of the <xref:System.Xml.Schema.XmlSchemaValidator> object if it has no preprocessing errors.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="33275-259">Bağlam öğesi geçerliyse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin alt öğeleri olarak beklenen öğe dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-259">If the context element is valid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as children of the context element.</span></span><br /><br /> <span data-ttu-id="33275-260">Bağlam öğesi geçersizse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-260">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span>|<span data-ttu-id="33275-261">Bağlam öğesi geçerliyse ve <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> daha önce yapılan bir çağrı yoksa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bağlam öğesinde tanımlanan tüm özniteliklerin bir listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-261">If the context element is valid, and if no call to <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> has been previously made, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of all the attributes defined on the context element.</span></span><br /><br /> <span data-ttu-id="33275-262">Bazı öznitelikler zaten doğrulandıktan sonra, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> doğrulanacak kalan özniteliklerin listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-262">If some attributes have already been validated, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the remaining attributes to be validated.</span></span><br /><br /> <span data-ttu-id="33275-263">Bağlam öğesi geçersizse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-263">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="33275-264">Yukarıdakiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-264">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="33275-265">Bağlam özniteliği en üst düzey bir öznitelik ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-265">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="33275-266">Aksi halde, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin ilk alt öğesi olarak beklenen öğe dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-266">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="33275-267">Bağlam özniteliği en üst düzey bir öznitelik ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-267">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="33275-268">Aksi takdirde, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> doğrulanacak özniteliklerin listesini geri döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-268">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the list of remaining attributes to be validated.</span></span>|<span data-ttu-id="33275-269">Yukarıdakiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-269">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<span data-ttu-id="33275-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin ilk alt öğesi olarak beklenen öğelerin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="33275-271"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bağlam öğesi için henüz doğrulanamayan gerekli ve isteğe bağlı özniteliklerin listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-271"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the required and optional attributes that are yet to be validated for the context element.</span></span>|<span data-ttu-id="33275-272">Yukarıdakiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-272">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="33275-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin ilk alt öğesi olarak beklenen öğelerin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="33275-274"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-274"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="33275-275">Yukarıdakiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-275">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="33275-276">Bağlam öğesinin contentType öğesi karmaysa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sonraki konumda beklenen öğelerin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-276">If the context element's contentType is Mixed, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position.</span></span><br /><br /> <span data-ttu-id="33275-277">Bağlam öğesinin contentType öğesi TextOnly veya boşsa <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-277">If the context element's contentType is TextOnly or Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="33275-278">Bağlam öğesinin contentType öğesi Öğetonly ise, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bir sonraki konumda beklenen öğe dizisini döndürür, ancak bir doğrulama hatası zaten oluştu.</span><span class="sxs-lookup"><span data-stu-id="33275-278">If the context element's contentType is ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position but a validation error has already occurred.</span></span>|<span data-ttu-id="33275-279"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bağlam öğesinin doğrulanmadı özniteliklerin listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-279"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span>|<span data-ttu-id="33275-280">Yukarıdakiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-280">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="33275-281">Bağlam beyaz alanı üst düzey boşluk ise, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-281">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="33275-282">Aksi halde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemin davranışı ile aynıdır <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> .</span><span class="sxs-lookup"><span data-stu-id="33275-282">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="33275-283">Bağlam beyaz alanı üst düzey boşluk ise, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-283">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="33275-284">Aksi halde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemin davranışı ile aynıdır <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> .</span><span class="sxs-lookup"><span data-stu-id="33275-284">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="33275-285">Yukarıdakiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-285">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="33275-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinden (olası eşdüzey öğeler) sonra beklenen öğe dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected after the context element (possible siblings).</span></span>|<span data-ttu-id="33275-287"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bağlam öğesinin doğrulanmadı özniteliklerin listesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-287"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span><br /><br /> <span data-ttu-id="33275-288">Bağlam öğesinin üst öğesi yoksa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir liste döndürür (bağlam öğesi, üzerinde çağrılan geçerli öğenin üst öğesidir <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> ).</span><span class="sxs-lookup"><span data-stu-id="33275-288">If the context element has no parent then <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty list (the context element is the parent of the current element on which <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> was called).</span></span>|<span data-ttu-id="33275-289">Yukarıdakiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-289">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="33275-290">Aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> .</span><span class="sxs-lookup"><span data-stu-id="33275-290">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="33275-291">Aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> .</span><span class="sxs-lookup"><span data-stu-id="33275-291">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="33275-292">Yukarıdakiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-292">Same as above.</span></span>|
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="33275-293">Boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-293">Returns an empty array.</span></span>|<span data-ttu-id="33275-294">Boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="33275-294">Returns an empty array.</span></span>|<span data-ttu-id="33275-295">Yukarıdakiyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="33275-295">Same as above.</span></span>|

> [!NOTE]
> <span data-ttu-id="33275-296">Sınıfın çeşitli özelliklerinin döndürdüğü değerler <xref:System.Xml.Schema.XmlSchemaValidator> Yukarıdaki tablodaki yöntemlerden herhangi biri çağırarak değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="33275-296">The values returned by the various properties of the <xref:System.Xml.Schema.XmlSchemaValidator> class are not altered by calling any of the methods in the above table.</span></span>

## <a name="see-also"></a><span data-ttu-id="33275-297">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33275-297">See also</span></span>

- <xref:System.Xml.Schema.XmlSchemaValidator>
