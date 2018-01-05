---
title: "XmlSchemaValidator gönderim tabanlı doğrulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 911d4460-dd91-4958-85b2-2ca3299f9ec6
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 60c2effea612a579b4c66b7c30243b785b86a263
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xmlschemavalidator-push-based-validation"></a><span data-ttu-id="80f09-102">XmlSchemaValidator gönderim tabanlı doğrulama</span><span class="sxs-lookup"><span data-stu-id="80f09-102">XmlSchemaValidator Push-Based Validation</span></span>
<span data-ttu-id="80f09-103"><xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı bir gönderim tabanlı şekilde XML şemaları karşı XML verileri doğrulamak için verimli, yüksek performanslı bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="80f09-103">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides an efficient, high-performance mechanism to validate XML data against XML schemas in a push-based manner.</span></span> <span data-ttu-id="80f09-104">Örneğin, <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı bir XML belgesi olarak serileştirir ve bir doğrulama XML okuyucusu kullanarak belgeyi yeniden ayrıştırma zorunda kalmadan bir XML bilgi yerinde doğrulamanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="80f09-104">For example, the <xref:System.Xml.Schema.XmlSchemaValidator> class allows you to validate an XML infoset in-place without having to serialize it as an XML document and then reparse the document using a validating XML reader.</span></span>  
  
 <span data-ttu-id="80f09-105"><xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı, doğrulama altyapılarını özel XML veri kaynaklarını üzerinden veya doğrulama XML yazıcısı oluşturmak için bir yol olarak oluşturma gibi gelişmiş senaryolarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="80f09-105">The <xref:System.Xml.Schema.XmlSchemaValidator> class can be used in advanced scenarios such as building validation engines over custom XML data sources or as a way to build a validating XML writer.</span></span>  
  
 <span data-ttu-id="80f09-106">Kullanarak bir örnek verilmiştir <xref:System.Xml.Schema.XmlSchemaValidator> doğrulamak için sınıf `contosoBooks.xml` karşı dosya `contosoBooks.xsd` şema.</span><span class="sxs-lookup"><span data-stu-id="80f09-106">The following is an example of using the <xref:System.Xml.Schema.XmlSchemaValidator> class to validate the `contosoBooks.xml` file against the `contosoBooks.xsd` schema.</span></span> <span data-ttu-id="80f09-107">Örnek kullanır <xref:System.Xml.Serialization.XmlSerializer> seri durumdan çıkarılacak sınıfı `contosoBooks.xml` dosya ve düğümlerin değerini yöntemlere <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="80f09-107">The example uses the <xref:System.Xml.Serialization.XmlSerializer> class to deserialize the `contosoBooks.xml` file and pass the value of the nodes to the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80f09-108">Bu örnekte, bu konunun bölümleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="80f09-108">This example is used throughout the sections of this topic.</span></span>  
  
 [!code-csharp[XmlSchemaValidatorExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaValidatorExamples/CS/XmlSchemaValidatorExamples.cs#1)]
 [!code-vb[XmlSchemaValidatorExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaValidatorExamples/VB/XmlSchemaValidatorExamples.vb#1)]  
  
 <span data-ttu-id="80f09-109">Örnek alır `contosoBooks.xml` dosya giriş olarak.</span><span class="sxs-lookup"><span data-stu-id="80f09-109">The example takes the `contosoBooks.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="80f09-110">Bu örnek ayrıca alır `contosoBooks.xsd` bir girdi olarak.</span><span class="sxs-lookup"><span data-stu-id="80f09-110">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
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
  
## <a name="validating-xml-data-using-xmlschemavalidator"></a><span data-ttu-id="80f09-111">XML XmlSchemaValidator kullanarak verileri doğrulama</span><span class="sxs-lookup"><span data-stu-id="80f09-111">Validating XML Data using XmlSchemaValidator</span></span>  
 <span data-ttu-id="80f09-112">Bir XML bilgi doğrulama başlamak için önce yeni bir örneğini başlatmalıdır <xref:System.Xml.Schema.XmlSchemaValidator> kullanarak sınıfı <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="80f09-112">To begin validating an XML infoset, you must first initialize a new instance of the <xref:System.Xml.Schema.XmlSchemaValidator> class using the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor.</span></span>  
  
 <span data-ttu-id="80f09-113"><xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> Oluşturucusu alır <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, ve <xref:System.Xml.XmlNamespaceManager> parametre olarak nesneleri yanı sıra bir <xref:System.Xml.Schema.XmlSchemaValidationFlags> bir parametre değeri.</span><span class="sxs-lookup"><span data-stu-id="80f09-113">The <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor takes <xref:System.Xml.XmlNameTable>, <xref:System.Xml.Schema.XmlSchemaSet>, and <xref:System.Xml.XmlNamespaceManager> objects as parameters as well as a <xref:System.Xml.Schema.XmlSchemaValidationFlags> value as a parameter.</span></span> <span data-ttu-id="80f09-114"><xref:System.Xml.XmlNameTable> Nesne Şema ad alanını, XML ad alanı vb. gibi bilinen ad alanı dizeleri küçük parçalara ayrılamıyor için kullanılır ve geçirilir <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> basit içerik doğrulanırken yöntemi.</span><span class="sxs-lookup"><span data-stu-id="80f09-114">The <xref:System.Xml.XmlNameTable> object is used to atomize well-known namespace strings like the schema namespace, the XML namespace, and so on, and is passed to the <xref:System.Xml.Schema.XmlSchemaDatatype.ParseValue%2A> method while validating simple content.</span></span> <span data-ttu-id="80f09-115"><xref:System.Xml.Schema.XmlSchemaSet> Nesne XML bilgi doğrulamak için kullanılan XML şemaları içerir.</span><span class="sxs-lookup"><span data-stu-id="80f09-115">The <xref:System.Xml.Schema.XmlSchemaSet> object contains the XML schemas used to validate the XML infoset.</span></span> <span data-ttu-id="80f09-116"><xref:System.Xml.XmlNamespaceManager> Nesnesi, doğrulama sırasında karşılaşılan ad alanları çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="80f09-116">The <xref:System.Xml.XmlNamespaceManager> object is used to resolve namespaces encountered during validation.</span></span> <span data-ttu-id="80f09-117"><xref:System.Xml.Schema.XmlSchemaValidationFlags> Doğrulama belirli özelliklerini devre dışı bırakmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="80f09-117">The <xref:System.Xml.Schema.XmlSchemaValidationFlags> value is used to disable certain features of validation.</span></span>  
  
 <span data-ttu-id="80f09-118">Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> oluşturucusu, bkz: <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="80f09-118">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="initializing-validation"></a><span data-ttu-id="80f09-119">Doğrulama başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="80f09-119">Initializing Validation</span></span>  
 <span data-ttu-id="80f09-120">Sonra bir <xref:System.Xml.Schema.XmlSchemaValidator> nesne oluşturulan, var olan iki aşırı <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> durumunu başlatmak için kullanılan yöntemleri <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="80f09-120">After an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed, there are two overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods used to initialize the state of the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="80f09-121">Aşağıdaki iki olan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="80f09-121">The following are the two <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods.</span></span>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="80f09-122">Varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yöntemi başlatır bir <xref:System.Xml.Schema.XmlSchemaValidator> başlangıç durumuna ve aşırı yüklenmiş nesnesine <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yönteminin alan bir <xref:System.Xml.Schema.XmlSchemaObject> bir parametre başlatır gibi bir <xref:System.Xml.Schema.XmlSchemaValidator> kısmi için başlangıç durumuna nesnesi doğrulama.</span><span class="sxs-lookup"><span data-stu-id="80f09-122">The default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state, and the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>  
  
 <span data-ttu-id="80f09-123">Her ikisi de <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemleri yalnızca çağırılabilir hemen sonra bir <xref:System.Xml.Schema.XmlSchemaValidator> nesne oluşturulan veya çağrı sonra <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span><span class="sxs-lookup"><span data-stu-id="80f09-123">Both <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> methods can only be called immediately after an <xref:System.Xml.Schema.XmlSchemaValidator> object has been constructed or after a call to <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>.</span></span>  
  
 <span data-ttu-id="80f09-124">Bir örnek için <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yöntemi, giriş örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="80f09-124">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method, see the example in the introduction.</span></span> <span data-ttu-id="80f09-125">Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi, bkz: <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="80f09-125">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="partial-validation"></a><span data-ttu-id="80f09-126">Kısmi doğrulama</span><span class="sxs-lookup"><span data-stu-id="80f09-126">Partial Validation</span></span>  
 <span data-ttu-id="80f09-127"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> Yönteminin alan bir <xref:System.Xml.Schema.XmlSchemaObject> bir parametre başlatır gibi bir <xref:System.Xml.Schema.XmlSchemaValidator> kısmi doğrulama için başlangıç durumuna nesnesi.</span><span class="sxs-lookup"><span data-stu-id="80f09-127">The <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter initializes an <xref:System.Xml.Schema.XmlSchemaValidator> object to its starting state for partial validation.</span></span>  
  
 <span data-ttu-id="80f09-128">Aşağıdaki örnekte, bir <xref:System.Xml.Schema.XmlSchemaObject> kısmi doğrulama kullanmak için başlatılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="80f09-128">In the following example, an <xref:System.Xml.Schema.XmlSchemaObject> is initialized for partial validation using the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="80f09-129">`orderNumber` Schema öğesi şema öğesi tarafından seçerek geçirilir <xref:System.Xml.XmlQualifiedName> içinde <xref:System.Xml.Schema.XmlSchemaObjectTable> tarafından döndürülen koleksiyon <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> özelliği <xref:System.Xml.Schema.XmlSchemaSet> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="80f09-129">The `orderNumber` schema element is passed by selecting the schema element by <xref:System.Xml.XmlQualifiedName> in the <xref:System.Xml.Schema.XmlSchemaObjectTable> collection returned by the <xref:System.Xml.Schema.XmlSchemaSet.GlobalElements%2A> property of the <xref:System.Xml.Schema.XmlSchemaSet> object.</span></span> <span data-ttu-id="80f09-130"><xref:System.Xml.Schema.XmlSchemaValidator> Nesneyi sonra bu belirli öğe doğrular.</span><span class="sxs-lookup"><span data-stu-id="80f09-130">The <xref:System.Xml.Schema.XmlSchemaValidator> object then validates this specific element.</span></span>  
  
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
  
 <span data-ttu-id="80f09-131">Örneğin, aşağıdaki XML Şeması girdi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="80f09-131">The example takes the following XML schema as input.</span></span>  
  
 `<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">`  
  
 `<xs:element name="orderNumber" type="xs:int" />`  
  
 `</xs:schema>`  
  
 <span data-ttu-id="80f09-132">Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi, bkz: <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="80f09-132">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="adding-additional-schemas"></a><span data-ttu-id="80f09-133">Ek şemaları ekleme</span><span class="sxs-lookup"><span data-stu-id="80f09-133">Adding Additional Schemas</span></span>  
 <span data-ttu-id="80f09-134"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Yöntemi <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı, bir XML Şeması doğrulama sırasında kullanılan şema kümesine eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="80f09-134">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method of the <xref:System.Xml.Schema.XmlSchemaValidator> class is used to add an XML schema to the set of schemas used during validation.</span></span> <span data-ttu-id="80f09-135"><xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Yöntemi, bir satır içi XML Şeması Doğrulanmakta olan XML bilgi içinde karşılaşmadan etkisini benzetimini yapmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="80f09-135">The <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method can be used to simulate the effect of encountering an inline XML schema in the XML infoset being validated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80f09-136">Hedef ad alanı <xref:System.Xml.Schema.XmlSchema> parametresi, herhangi bir öğe veya öznitelik tarafından zaten karşılaşılan eşleşemez <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="80f09-136">The target namespace of the <xref:System.Xml.Schema.XmlSchema> parameter cannot match that of any element or attribute already encountered by the <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>  
>   
>  <span data-ttu-id="80f09-137">Varsa <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> değer için bir parametre olarak değil geçildi <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> oluşturucusu, <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemi hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="80f09-137">If the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessInlineSchema?displayProperty=nameWithType> value was not passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.%23ctor%2A> constructor, the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method does nothing.</span></span>  
  
 <span data-ttu-id="80f09-138">Sonucu <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> Doğrulanmakta olan geçerli XML düğümünde içerik bağımlı bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="80f09-138">The result of the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method is dependant on the current XML node context being validated.</span></span> <span data-ttu-id="80f09-139">Doğrulama bağlamları hakkında daha fazla bilgi için bu konunun "Doğrulama bağlamını" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="80f09-139">For more information about validation contexts, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="80f09-140">Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemi, bkz: <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="80f09-140">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="validating-elements-attributes-and-content"></a><span data-ttu-id="80f09-141">Öğeleri, öznitelikleri ve içerik doğrulama</span><span class="sxs-lookup"><span data-stu-id="80f09-141">Validating Elements, Attributes, and Content</span></span>  
 <span data-ttu-id="80f09-142"><xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı öğeleri, öznitelikleri ve XML şemaları karşı bir XML bilgi içeriği doğrulamak için kullanılan birkaç yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="80f09-142">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides several methods used to validate elements, attributes, and content in an XML infoset against XML schemas.</span></span> <span data-ttu-id="80f09-143">Aşağıdaki tabloda bu yöntemlerin her biri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="80f09-143">The following table describes each of these methods.</span></span>  
  
|<span data-ttu-id="80f09-144">Yöntem</span><span class="sxs-lookup"><span data-stu-id="80f09-144">Method</span></span>|<span data-ttu-id="80f09-145">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80f09-145">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="80f09-146">Öğe adı geçerli bağlamda doğrular.</span><span class="sxs-lookup"><span data-stu-id="80f09-146">Validates the element name in the current context.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="80f09-147">Öznitelik geçerli öğe içeriğinde veya karşı doğrular <xref:System.Xml.Schema.XmlSchemaAttribute> nesne için bir parametre olarak geçirilen <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="80f09-147">Validates the attribute in the current element context or against the <xref:System.Xml.Schema.XmlSchemaAttribute> object passed as a parameter to the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="80f09-148">Tüm gerekli öznitelikler öğesi bağlamında döndürülüp döndürülmeyeceğini doğrular ve hazırlar <xref:System.Xml.Schema.XmlSchemaValidator> öğesinin alt içeriği doğrulamak için nesne.</span><span class="sxs-lookup"><span data-stu-id="80f09-148">Verifies whether all the required attributes in the element context are present and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate the child content of the element.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="80f09-149">Metin geçerli öğenin bağlamında izin verilir ve geçerli öğe basit içeriğe sahipse doğrulama için metin öğelerden olup olmadığını doğrular.</span><span class="sxs-lookup"><span data-stu-id="80f09-149">Validates whether text is allowed in the current element context, and accumulates the text for validation if the current element has simple content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="80f09-150">Boşluk geçerli öğenin bağlamında izin verilir ve geçerli öğe basit içerik olup olmadığını doğrulama için beyaz alan öğelerden olup olmadığını doğrular.</span><span class="sxs-lookup"><span data-stu-id="80f09-150">Validates whether white-space is allowed in the current element context, and accumulates the white-space for validation whether the current element has simple content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="80f09-151">Öğenin metin içeriğini basit içeriğe sahip öğeler için veri türüne göre geçerli olup olmadığını doğrular ve geçerli öğenin içeriği ile karmaşık içerik öğeleri için tam olup olmadığını doğrular.</span><span class="sxs-lookup"><span data-stu-id="80f09-151">Verifies whether the text content of the element is valid according to its data type for elements with simple content, and verifies whether the content of the current element is complete for elements with complex content.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="80f09-152">Geçerli öğe içeriği doğrulama atlar ve hazırlar <xref:System.Xml.Schema.XmlSchemaValidator> üst öğenin bağlamında içeriği doğrulamak için nesne.</span><span class="sxs-lookup"><span data-stu-id="80f09-152">Skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="80f09-153">Doğrulama sona erer ve tüm XML belgesi kimlik kısıtlamalarını denetler <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> doğrulama seçeneği ayarlanmış.</span><span class="sxs-lookup"><span data-stu-id="80f09-153">Ends validation and checks identity constraints for the entire XML document if the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ProcessIdentityConstraints> validation option is set.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="80f09-154"><xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı dizisi ve yukarıdaki tabloda açıklanan yöntemlerin her biri için yapılan çağrılar oluşumunu zorlayan bir tanımlanan durum geçişi sahiptir.</span><span class="sxs-lookup"><span data-stu-id="80f09-154">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods described in the previous table.</span></span> <span data-ttu-id="80f09-155">Özel durum geçişini <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı bu konunun "XmlSchemaValidator durum geçişi" bölümünde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="80f09-155">The specific state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class is described in the "XmlSchemaValidator State Transition" section of this topic.</span></span>  
  
 <span data-ttu-id="80f09-156">Önceki bölümdeki örnek örneği öğeleri, öznitelikleri ve bir XML bilgi içeriği doğrulamak için kullanılan yöntemler için bkz.</span><span class="sxs-lookup"><span data-stu-id="80f09-156">For an example of the methods used to validate elements, attributes, and content in an XML infoset, see the example in the previous section.</span></span> <span data-ttu-id="80f09-157">Bu yöntemler hakkında daha fazla bilgi için bkz: <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="80f09-157">For more information about these methods, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="validating-content-using-an-xmlvaluegetter"></a><span data-ttu-id="80f09-158">Bir XmlValueGetter kullanarak içerik doğrulama</span><span class="sxs-lookup"><span data-stu-id="80f09-158">Validating Content Using an XmlValueGetter</span></span>  
 <span data-ttu-id="80f09-159"><xref:System.Xml.Schema.XmlValueGetter> `delegate` Özniteliği, metin ya da boşluk düğümleri değerini ortak dil çalışma zamanı (CLR) türleri olarak özniteliği, metin veya boşluk düğümünün XML Şeması Tanım Dili (XSD) türüyle uyumlu geçirmek için kullanılan.</span><span class="sxs-lookup"><span data-stu-id="80f09-159">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` can be used to pass the value of attribute, text, or white-space nodes as a Common Language Runtime (CLR) types compatible with the XML Schema Definition Language (XSD) type of the attribute, text, or white-space node.</span></span> <span data-ttu-id="80f09-160">Bir <xref:System.Xml.Schema.XmlValueGetter> `delegate` özniteliği, metin ya da boşluk düğümü CLR değeri zaten varsa ve kendisine dönüştürme maliyetini ortadan kaldırır, yararlıdır bir `string` ve sonra bunu yeniden doğrulama için yeniden ayrıştırmayı.</span><span class="sxs-lookup"><span data-stu-id="80f09-160">An <xref:System.Xml.Schema.XmlValueGetter>`delegate` is useful if the CLR value of an attribute, text, or white-space node is already available, and avoids the cost of converting it to a `string` and then reparsing it again for validation.</span></span>  
  
 <span data-ttu-id="80f09-161"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, Ve <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> yöntemlerini aşırı yüklü ve öznitelik, metin ya da boşluk düğümleri olarak değerini kabul bir `string` veya <xref:System.Xml.Schema.XmlValueGetter> `delegate`.</span><span class="sxs-lookup"><span data-stu-id="80f09-161">The <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> methods are overloaded and accept the value of attribute, text, or white-space nodes as a `string` or <xref:System.Xml.Schema.XmlValueGetter>`delegate`.</span></span>  
  
 <span data-ttu-id="80f09-162">Aşağıdaki yöntemlerden birini <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı kabul bir <xref:System.Xml.Schema.XmlValueGetter> `delegate` bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="80f09-162">The following methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlValueGetter>`delegate` as a parameter.</span></span>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>  
  
 <span data-ttu-id="80f09-163">Aşağıda bir örnek verilmiştir <xref:System.Xml.Schema.XmlValueGetter> `delegate` alınan <xref:System.Xml.Schema.XmlSchemaValidator> giriş sınıfı örneği.</span><span class="sxs-lookup"><span data-stu-id="80f09-163">The following is an example <xref:System.Xml.Schema.XmlValueGetter>`delegate` taken from the <xref:System.Xml.Schema.XmlSchemaValidator> class example in the introduction.</span></span> <span data-ttu-id="80f09-164"><xref:System.Xml.Schema.XmlValueGetter> `delegate` Özniteliğin değerini döndüren bir <xref:System.DateTime> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="80f09-164">The <xref:System.Xml.Schema.XmlValueGetter>`delegate` returns the value of an attribute as a <xref:System.DateTime> object.</span></span> <span data-ttu-id="80f09-165">Bunu doğrulamak için <xref:System.DateTime> tarafından döndürülen nesne <xref:System.Xml.Schema.XmlValueGetter>, <xref:System.Xml.Schema.XmlSchemaValidator> nesnesini ilk ValueType onu dönüştürür (XSD türü için varsayılan CLR eşleme ValueType'dir) veri türü özniteliği ve ardından dönüştürülen üzerinde denetimleri modelleri için değer.</span><span class="sxs-lookup"><span data-stu-id="80f09-165">To validate this <xref:System.DateTime> object returned by the <xref:System.Xml.Schema.XmlValueGetter>, the <xref:System.Xml.Schema.XmlSchemaValidator> object first converts it to the ValueType (ValueType is the default CLR mapping for the XSD type) for the data type of the attribute and then checks facets on the converted value.</span></span>  
  
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
  
 <span data-ttu-id="80f09-166">Tam bir örnek için <xref:System.Xml.Schema.XmlValueGetter> `delegate`, giriş örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="80f09-166">For a complete example of the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the example in the introduction.</span></span> <span data-ttu-id="80f09-167">Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlValueGetter> `delegate`, bkz: <xref:System.Xml.Schema.XmlValueGetter>, ve <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="80f09-167">For more information about the <xref:System.Xml.Schema.XmlValueGetter>`delegate`, see the <xref:System.Xml.Schema.XmlValueGetter>, and <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="post-schema-validation-information"></a><span data-ttu-id="80f09-168">Sonrası-Schema-doğrulama-bilgileri</span><span class="sxs-lookup"><span data-stu-id="80f09-168">Post-Schema-Validation-Information</span></span>  
 <span data-ttu-id="80f09-169"><xref:System.Xml.Schema.XmlSchemaInfo> Sınıfı, bazı sonrası-Schema-doğrulama-bilgiler doğrulayan bir XML düğümü temsil eder <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="80f09-169">The <xref:System.Xml.Schema.XmlSchemaInfo> class represents some of the Post-Schema-Validation-Information of an XML node validated by the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="80f09-170">Çeşitli yöntemleri <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı kabul bir <xref:System.Xml.Schema.XmlSchemaInfo> nesnesi bir isteğe bağlı olarak (`null`) `out` parametresi.</span><span class="sxs-lookup"><span data-stu-id="80f09-170">Various methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an optional, (`null`) `out` parameter.</span></span>  
  
 <span data-ttu-id="80f09-171">Doğrulama başarılı, özelliklerini üzerine <xref:System.Xml.Schema.XmlSchemaInfo> nesne doğrulama sonuçlarını ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="80f09-171">Upon successful validation, properties of the <xref:System.Xml.Schema.XmlSchemaInfo> object are set with the results of the validation.</span></span> <span data-ttu-id="80f09-172">Özniteliğini kullanarak, örneğin, doğrulama başarılı bağlı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntemi, <xref:System.Xml.Schema.XmlSchemaInfo> nesne kullanıcının (belirtilmişse) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, ve <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> özelliklerini doğrulama sonuçlarını ayarlama .</span><span class="sxs-lookup"><span data-stu-id="80f09-172">For example, upon successful validation of an attribute using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the <xref:System.Xml.Schema.XmlSchemaInfo> object's (if specified) <xref:System.Xml.Schema.XmlSchemaInfo.SchemaAttribute%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.SchemaType%2A>, <xref:System.Xml.Schema.XmlSchemaInfo.MemberType%2A>, and <xref:System.Xml.Schema.XmlSchemaInfo.Validity%2A> properties are set with the results of the validation.</span></span>  
  
 <span data-ttu-id="80f09-173">Aşağıdaki <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı yöntemleri kabul bir <xref:System.Xml.Schema.XmlSchemaInfo> nesnesi out parametresi olarak.</span><span class="sxs-lookup"><span data-stu-id="80f09-173">The following <xref:System.Xml.Schema.XmlSchemaValidator> class methods accept an <xref:System.Xml.Schema.XmlSchemaInfo> object as an out parameter.</span></span>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>  
  
-   <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>  
  
 <span data-ttu-id="80f09-174">Tam bir örnek için <xref:System.Xml.Schema.XmlSchemaInfo> sınıfı, giriş örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="80f09-174">For a complete example of the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the example in the introduction.</span></span> <span data-ttu-id="80f09-175">Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaInfo> sınıfı için bkz: <xref:System.Xml.Schema.XmlSchemaInfo> sınıf başvurusu belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="80f09-175">For more information about the <xref:System.Xml.Schema.XmlSchemaInfo> class, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>  
  
### <a name="retrieving-expected-particles-attributes-and-unspecified-default-attributes"></a><span data-ttu-id="80f09-176">Beklenen Parçacık, öznitelikleri ve belirtilmeyen varsayılan öznitelikleri alma</span><span class="sxs-lookup"><span data-stu-id="80f09-176">Retrieving Expected Particles, Attributes, and Unspecified Default Attributes</span></span>  
 <span data-ttu-id="80f09-177"><xref:System.Xml.Schema.XmlSchemaValidator> SAX <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, ve <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> beklenen Parçacık, öznitelikleri ve geçerli doğrulama bağlamını belirtilmeyen varsayılan öznitelikleri almak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="80f09-177">The <xref:System.Xml.Schema.XmlSchemaValidator> class provides the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> methods to retrieve the expected particles, attributes, and unspecified default attributes in the current validation context.</span></span>  
  
#### <a name="retrieving-expected-particles"></a><span data-ttu-id="80f09-178">Beklenen parçacık alınıyor</span><span class="sxs-lookup"><span data-stu-id="80f09-178">Retrieving Expected Particles</span></span>  
 <span data-ttu-id="80f09-179"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemi bir dizi döndürür <xref:System.Xml.Schema.XmlSchemaParticle> geçerli öğe bağlamda beklenen parçacık içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="80f09-179">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaParticle> objects containing the expected particles in the current element context.</span></span> <span data-ttu-id="80f09-180">Tarafından döndürülen geçerli parçacık <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi örnekleridir <xref:System.Xml.Schema.XmlSchemaElement> ve <xref:System.Xml.Schema.XmlSchemaAny> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="80f09-180">The valid particles that can be returned by the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method are instances of the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaAny> classes.</span></span>  
  
 <span data-ttu-id="80f09-181">İçerik modeli oluşturucuya olduğunda bir `xs:sequence`, yalnızca ileri parçacığın dizisi döndürülür.</span><span class="sxs-lookup"><span data-stu-id="80f09-181">When the compositor for the content model is an `xs:sequence`, only the next particle in the sequence is returned.</span></span> <span data-ttu-id="80f09-182">Oluşturucuya içerik modeli için ise bir `xs:all` veya bir `xs:choice`, geçerli öğenin bağlamında izleyen tüm geçerli parçacık döndürülen sonra.</span><span class="sxs-lookup"><span data-stu-id="80f09-182">If the compositor for the content model is an `xs:all` or an `xs:choice`, then all valid particles that could follow in the current element context are returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80f09-183">Varsa <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi çağrıldıktan sonra hemen çağrılır <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi tüm genel öğeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-183">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called immediately after calling the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns all global elements.</span></span>  
  
 <span data-ttu-id="80f09-184">Örneğin, XML Şeması Tanım Dili (XSD) doğrulama sonra bu izleme, şema ve XML belge `book` öğesi, `book` geçerli öğe bağlamı bir öğedir.</span><span class="sxs-lookup"><span data-stu-id="80f09-184">For example, in the XML Schema Definition Language (XSD) schema and XML document that follow, after validating the `book` element, the `book` element is the current element context.</span></span> <span data-ttu-id="80f09-185"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> Yöntemi tek bir içeren bir dizi döndürür <xref:System.Xml.Schema.XmlSchemaElement> nesnesini temsil eden `title` öğesi.</span><span class="sxs-lookup"><span data-stu-id="80f09-185">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `title` element.</span></span> <span data-ttu-id="80f09-186">Doğrulama bağlamını olduğunda `title` öğesi <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntem boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-186">When the validation context is the `title` element, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method returns an empty array.</span></span> <span data-ttu-id="80f09-187">Varsa <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi çağrıldıktan sonra `title` öğesi doğrulanmış önce `description` öğesi doğrulanmış, tek bir içeren bir dizi döndürür <xref:System.Xml.Schema.XmlSchemaElement> nesnesini temsil eden `description` öğesi.</span><span class="sxs-lookup"><span data-stu-id="80f09-187">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `title` element has been validated but before the `description` element has been validated, it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaElement> object representing the `description` element.</span></span> <span data-ttu-id="80f09-188">Varsa <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi çağrıldıktan sonra `description` öğesi doğrulanmış sonra tek bir içeren bir dizi döndürür <xref:System.Xml.Schema.XmlSchemaAny> joker karakteri temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="80f09-188">If the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method is called after the `description` element has been validated then it returns an array containing a single <xref:System.Xml.Schema.XmlSchemaAny> object representing the wildcard.</span></span>  
  
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
  
 <span data-ttu-id="80f09-189">Örneğin, aşağıdaki XML girdi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="80f09-189">The example takes the following XML as input.</span></span>  
  
 `<xs:schema xmlns:xs="http://www.w3c.org/2001/XMLSchema">`  
  
 `<xs:element name="book">`  
  
 `<xs:sequence>`  
  
 `<xs:element name="title" type="xs:string" />`  
  
 `<xs:element name="description" type="xs:string" />`  
  
 `<xs:any processContent="lax" maxOccurs="unbounded" />`  
  
 `</xs:sequence>`  
  
 `</xs:element>`  
  
 `</xs:schema>`  
  
 <span data-ttu-id="80f09-190">Örneğin aşağıdaki XSD şema girdi olarak alır.</span><span class="sxs-lookup"><span data-stu-id="80f09-190">The example takes the following XSD schema as input.</span></span>  
  
 `<book>`  
  
 `<title>My Book</title>`  
  
 `<description>My Book's Description</description>`  
  
 `<namespace>System.Xml.Schema</namespace>`  
  
 `</book>`  
  
> [!NOTE]
>  <span data-ttu-id="80f09-191">Sonuçlarını <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı Doğrulanmakta olan geçerli bağlamda bağımlı.</span><span class="sxs-lookup"><span data-stu-id="80f09-191">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="80f09-192">Daha fazla bilgi için bu konunun "Doğrulama bağlamını" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="80f09-192">For more information, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="80f09-193">Bir örnek için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi, giriş örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="80f09-193">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="80f09-194">Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemi, bkz: <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="80f09-194">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="retrieving-expected-attributes"></a><span data-ttu-id="80f09-195">Beklenen öznitelikleri alma</span><span class="sxs-lookup"><span data-stu-id="80f09-195">Retrieving Expected Attributes</span></span>  
 <span data-ttu-id="80f09-196"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> Yöntemi bir dizi döndürür <xref:System.Xml.Schema.XmlSchemaAttribute> geçerli öğe bağlamda beklenen öznitelikleri içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="80f09-196">The <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method returns an array of <xref:System.Xml.Schema.XmlSchemaAttribute> objects containing the expected attributes in the current element context.</span></span>  
  
 <span data-ttu-id="80f09-197">Örneğin, giriş örnekte <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi, tüm öznitelikleri almak için kullanılan `book` öğesi.</span><span class="sxs-lookup"><span data-stu-id="80f09-197">For example, in the example in the introduction, the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method is used to retrieve all the attributes of the `book` element.</span></span>  
  
 <span data-ttu-id="80f09-198">Çağırırsanız <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi hemen sonra <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> yöntemi, XML belgesinde görünebilir tüm öznitelikleri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="80f09-198">If you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method immediately after the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> method, all the attributes that could appear in the XML document are returned.</span></span> <span data-ttu-id="80f09-199">Ancak, çağırırsanız <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi için bir veya daha fazla çağrıları sonra <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> yöntemi, henüz geçerli öğe için doğrulandı değil öznitelikleri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="80f09-199">However, if you call the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method after one or more calls to the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method, the attributes that have not yet been validated for the current element are returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80f09-200">Sonuçlarını <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı Doğrulanmakta olan geçerli bağlamda bağımlı.</span><span class="sxs-lookup"><span data-stu-id="80f09-200">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span> <span data-ttu-id="80f09-201">Daha fazla bilgi için bu konunun "Doğrulama bağlamını" bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="80f09-201">For more information, see the "Validation Context" section of this topic.</span></span>  
  
 <span data-ttu-id="80f09-202">Bir örnek için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi, giriş örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="80f09-202">For an example of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the example in the introduction.</span></span> <span data-ttu-id="80f09-203">Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemi, bkz: <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="80f09-203">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
#### <a name="retrieving-unspecified-default-attributes"></a><span data-ttu-id="80f09-204">Belirtilmeyen varsayılan öznitelikleri alma</span><span class="sxs-lookup"><span data-stu-id="80f09-204">Retrieving Unspecified Default Attributes</span></span>  
 <span data-ttu-id="80f09-205"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Yöntemi doldurur <xref:System.Collections.ArrayList> ile belirtilen <xref:System.Xml.Schema.XmlSchemaAttribute> nesneler için varsayılan değerlerle daha önce kullanılarak doğrulandı değil tüm öznitelikleri <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> öğesi bağlamında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="80f09-205">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method populates the <xref:System.Collections.ArrayList> specified with <xref:System.Xml.Schema.XmlSchemaAttribute> objects for any attributes with default values that have not been previously validated using the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method in the element context.</span></span> <span data-ttu-id="80f09-206"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Yöntemi çağrıldıktan sonra çağrılabilir <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> her özniteliği öğesi bağlamında yöntemi.</span><span class="sxs-lookup"><span data-stu-id="80f09-206">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be called after calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> method on each attribute in the element context.</span></span> <span data-ttu-id="80f09-207"><xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> Yöntemi, varsayılan öznitelikleri Doğrulanmakta olan XML belgesine eklenecek olduğunu belirlemek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="80f09-207">The <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method should be used to determine what default attributes are to be inserted into the XML document being validated.</span></span>  
  
 <span data-ttu-id="80f09-208">Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> yöntemi, bkz: <xref:System.Xml.Schema.XmlSchemaValidator> sınıf başvurusu belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="80f09-208">For more information about the <xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A> method, see the <xref:System.Xml.Schema.XmlSchemaValidator> class reference documentation.</span></span>  
  
### <a name="handling-schema-validation-events"></a><span data-ttu-id="80f09-209">Şema doğrulama olayları işleme</span><span class="sxs-lookup"><span data-stu-id="80f09-209">Handling Schema Validation Events</span></span>  
 <span data-ttu-id="80f09-210">Şema doğrulama uyarıları ve doğrulama sırasında oluşan hatalar tarafından işlenmesini <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> olayı <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="80f09-210">Schema validation warnings and errors encountered during validation are handled by the <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> event of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
 <span data-ttu-id="80f09-211">Şema doğrulama uyarıları olan bir <xref:System.Xml.Schema.XmlSeverityType> değerini <xref:System.Xml.Schema.XmlSeverityType.Warning> ve şema doğrulama hatalarıyla sahip bir <xref:System.Xml.Schema.XmlSeverityType> değerini <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="80f09-211">Schema validation warnings have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning> and schema validation errors have an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="80f09-212">Öyle değilse <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> atanmış olan, bir <xref:System.Xml.Schema.XmlSchemaValidationException> tüm şema doğrulama hatalarıyla için oluşturulan bir <xref:System.Xml.Schema.XmlSeverityType> değerini <xref:System.Xml.Schema.XmlSeverityType.Error>.</span><span class="sxs-lookup"><span data-stu-id="80f09-212">If no <xref:System.Xml.Schema.XmlSchemaValidator.ValidationEventHandler> has been assigned, an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown for all schema validation errors with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Error>.</span></span> <span data-ttu-id="80f09-213">Ancak, bir <xref:System.Xml.Schema.XmlSchemaValidationException> şema doğrulama uyarılarla durum olmayan bir <xref:System.Xml.Schema.XmlSeverityType> değerini <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span><span class="sxs-lookup"><span data-stu-id="80f09-213">However, an <xref:System.Xml.Schema.XmlSchemaValidationException> is not thrown for schema validation warnings with an <xref:System.Xml.Schema.XmlSeverityType> value of <xref:System.Xml.Schema.XmlSeverityType.Warning>.</span></span>  
  
 <span data-ttu-id="80f09-214">Aşağıdaki örneğidir bir <xref:System.Xml.Schema.ValidationEventHandler> şema doğrulama uyarıları ve hataları giriş örnekte alınan şema doğrulaması sırasında karşılaşılan alır.</span><span class="sxs-lookup"><span data-stu-id="80f09-214">The following is an example of a <xref:System.Xml.Schema.ValidationEventHandler> that receives schema validation warnings and errors encountered during schema validation taken from the example in the introduction.</span></span>  
  
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
  
 <span data-ttu-id="80f09-215">Tam bir örnek için <xref:System.Xml.Schema.ValidationEventHandler>, giriş örneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="80f09-215">For a complete example of the <xref:System.Xml.Schema.ValidationEventHandler>, see the example in the introduction.</span></span> <span data-ttu-id="80f09-216">Daha fazla bilgi için bkz: <xref:System.Xml.Schema.XmlSchemaInfo> sınıf başvurusu belgelerinde.</span><span class="sxs-lookup"><span data-stu-id="80f09-216">For more information, see the <xref:System.Xml.Schema.XmlSchemaInfo> class reference documentation.</span></span>  
  
## <a name="xmlschemavalidator-state-transition"></a><span data-ttu-id="80f09-217">XmlSchemaValidator durum geçişi</span><span class="sxs-lookup"><span data-stu-id="80f09-217">XmlSchemaValidator State Transition</span></span>  
 <span data-ttu-id="80f09-218"><xref:System.Xml.Schema.XmlSchemaValidator> Sınıfı dizisi ve öğeleri, öznitelikleri ve bir XML bilgi içeriği doğrulamak için kullanılan yöntemlerin her biri için yapılan çağrılar oluşumunu zorlayan bir tanımlanan durum geçişi sahiptir.</span><span class="sxs-lookup"><span data-stu-id="80f09-218">The <xref:System.Xml.Schema.XmlSchemaValidator> class has a defined state transition that enforces the sequence and occurrence of calls made to each of the methods used to validate elements, attributes, and content in an XML infoset.</span></span>  
  
 <span data-ttu-id="80f09-219">Durum geçişi, aşağıdaki tabloda açıklanmaktadır <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı ve dizisi ve her durumda yapılabilmesi için yöntem çağrılarını geçişi.</span><span class="sxs-lookup"><span data-stu-id="80f09-219">The following table describes the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class, and the sequence and occurrence of method calls that can be made in each state.</span></span>  
  
|<span data-ttu-id="80f09-220">Durum</span><span class="sxs-lookup"><span data-stu-id="80f09-220">State</span></span>|<span data-ttu-id="80f09-221">geçiş</span><span class="sxs-lookup"><span data-stu-id="80f09-221">Transition</span></span>|  
|-----------|----------------|  
|<span data-ttu-id="80f09-222">Doğrula</span><span class="sxs-lookup"><span data-stu-id="80f09-222">Validate</span></span>|<span data-ttu-id="80f09-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>(<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel*)<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span><span class="sxs-lookup"><span data-stu-id="80f09-223"><xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> &#124; TopLevel*) <xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A></span></span>|  
|<span data-ttu-id="80f09-224">TopLevel</span><span class="sxs-lookup"><span data-stu-id="80f09-224">TopLevel</span></span>|<span data-ttu-id="80f09-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>&#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Öğesi</span><span class="sxs-lookup"><span data-stu-id="80f09-225"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|  
|<span data-ttu-id="80f09-226">Öğe</span><span class="sxs-lookup"><span data-stu-id="80f09-226">Element</span></span>|<span data-ttu-id="80f09-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> İçerik\*)?</span><span class="sxs-lookup"><span data-stu-id="80f09-227"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>* (<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\*)?</span></span> <span data-ttu-id="80f09-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="80f09-228"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="80f09-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="80f09-229"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span><br /><br /> <span data-ttu-id="80f09-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A><xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> \* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> İçerik\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span><span class="sxs-lookup"><span data-stu-id="80f09-230"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A> <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>\* <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A> Content\* <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> &#124;</span></span>|  
|<span data-ttu-id="80f09-231">İçerik</span><span class="sxs-lookup"><span data-stu-id="80f09-231">Content</span></span>|<span data-ttu-id="80f09-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>&#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Öğesi</span><span class="sxs-lookup"><span data-stu-id="80f09-232"><xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A> &#124; <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A> &#124; Element</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="80f09-233">Bir <xref:System.InvalidOperationException> geçerli durumuna göre yanlış sırayla yöntemi çağrısı yapıldığında, yukarıdaki tabloda yöntemlerin her biri tarafından oluşturulan bir <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="80f09-233">An <xref:System.InvalidOperationException> is thrown by each of the methods in the table above when the call to the method is made in the incorrect sequence according to the current state of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span>  
  
 <span data-ttu-id="80f09-234">Yukarıdaki durumu geçiş tablosunu yöntemleri açıklamak için noktalama simgeleri kullanır ve diğer durum geçişi her durum için çağrılabilir durumları <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="80f09-234">The state transition table above uses punctuation symbols to describe the methods and other states that can be called for each state of the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span> <span data-ttu-id="80f09-235">Kullanılan simgeler belge türü tanımı (DTD) XML standartları Başvurusu'nda bulunan aynı simgelerdir.</span><span class="sxs-lookup"><span data-stu-id="80f09-235">The symbols used are the same symbols found in the XML Standards reference for Document Type Definition (DTD).</span></span>  
  
 <span data-ttu-id="80f09-236">Aşağıdaki tabloda durumu geçişi yukarıdaki tabloda bulunan noktalama simgeler yöntemleri nasıl etkilediğini açıklar ve diğer her durumda durum geçişi için çağrılabilir durumları <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="80f09-236">The following table describes how the punctuation symbols found in the state transition table above affect the methods and other states that can be called for each state in the state transition of the <xref:System.Xml.Schema.XmlSchemaValidator> class.</span></span>  
  
|<span data-ttu-id="80f09-237">Simgesi</span><span class="sxs-lookup"><span data-stu-id="80f09-237">Symbol</span></span>|<span data-ttu-id="80f09-238">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80f09-238">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="80f09-239">&#124;</span><span class="sxs-lookup"><span data-stu-id="80f09-239">&#124;</span></span>|<span data-ttu-id="80f09-240">Yöntem veya durumu (çubuğu önce) veya bir sonraki çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="80f09-240">Either method or state (the one before the bar or the one after it) can be called.</span></span>|  
|<span data-ttu-id="80f09-241">?</span><span class="sxs-lookup"><span data-stu-id="80f09-241">?</span></span>|<span data-ttu-id="80f09-242">Yöntem veya soru işareti önündeki durumu isteğe bağlıdır ancak çağrılırsa, yalnızca bir kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="80f09-242">The method or state that precedes the question mark is optional but if it is called it can only be called once.</span></span>|  
|*|<span data-ttu-id="80f09-243">Yöntem veya önündeki durumu * simgesi isteğe bağlıdır ve birden çok kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="80f09-243">The method or state that precedes the * symbol is optional, and can be called more than once.</span></span>|  
  
## <a name="validation-context"></a><span data-ttu-id="80f09-244">Doğrulama bağlamı</span><span class="sxs-lookup"><span data-stu-id="80f09-244">Validation Context</span></span>  
 <span data-ttu-id="80f09-245">Yöntemlerinin <xref:System.Xml.Schema.XmlSchemaValidator> öğeleri, öznitelikleri ve bir XML bilgi içeriği doğrulamak, doğrulama bağlamı değiştirmek için kullanılan sınıf bir <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="80f09-245">The methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset, change the validation context of an <xref:System.Xml.Schema.XmlSchemaValidator> object.</span></span> <span data-ttu-id="80f09-246">Örneğin, <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> yöntemi geçerli öğe içeriği doğrulama atlar ve hazırlar <xref:System.Xml.Schema.XmlSchemaValidator> üst öğenin bağlamında içeriği doğrulamak için nesne; geçerli öğenin tüm alt öğeleri için doğrulama atlanıyor için eşdeğerdir ve ardından çağırma <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="80f09-246">For example, the <xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A> method skips validation of the current element content and prepares the <xref:System.Xml.Schema.XmlSchemaValidator> object to validate content in the parent element's context; it is equivalent to skipping validation for all the children of the current element and then calling the <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> method.</span></span>  
  
 <span data-ttu-id="80f09-247">Sonuçlarını <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, ve <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> yöntemlerinin <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı Doğrulanmakta olan geçerli bağlamda bağımlı.</span><span class="sxs-lookup"><span data-stu-id="80f09-247">The results of the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>, and <xref:System.Xml.Schema.XmlSchemaValidator.AddSchema%2A> methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class are dependent on the current context being validated.</span></span>  
  
 <span data-ttu-id="80f09-248">Aşağıdaki tabloda bu yöntemleri yöntemlerinden birini çağrıldıktan sonra çağırma sonuçlarını açıklar <xref:System.Xml.Schema.XmlSchemaValidator> öğeleri, öznitelikleri ve bir XML bilgi içeriği doğrulamak için kullanılan bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="80f09-248">The following table describes the results of calling these methods after calling one of the methods of the <xref:System.Xml.Schema.XmlSchemaValidator> class used to validate elements, attributes, and content in an XML infoset.</span></span>  
  
|<span data-ttu-id="80f09-249">Yöntem</span><span class="sxs-lookup"><span data-stu-id="80f09-249">Method</span></span>|<span data-ttu-id="80f09-250">GetExpectedParticles</span><span class="sxs-lookup"><span data-stu-id="80f09-250">GetExpectedParticles</span></span>|<span data-ttu-id="80f09-251">GetExpectedAttributes</span><span class="sxs-lookup"><span data-stu-id="80f09-251">GetExpectedAttributes</span></span>|<span data-ttu-id="80f09-252">AddSchema</span><span class="sxs-lookup"><span data-stu-id="80f09-252">AddSchema</span></span>|  
|------------|--------------------------|---------------------------|---------------|  
|<xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A>|<span data-ttu-id="80f09-253">Varsa varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi çağrıldığında, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> tüm genel öğeleri içeren bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-253">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an array containing all global elements.</span></span><br /><br /> <span data-ttu-id="80f09-254">Varsa aşırı yüklenmiş <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yönteminin alan bir <xref:System.Xml.Schema.XmlSchemaObject> bir öğenin kısmi doğrulama başlatmak için bir parametre denir <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yalnızca öğesi döndüğü <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi başlatılmadı.</span><span class="sxs-lookup"><span data-stu-id="80f09-254">If the overloaded <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an element, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns only the element to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="80f09-255">Varsa varsayılan <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yöntemi çağrıldığında, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-255">If the default <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method is called, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="80f09-256">Varsa aşırı yüklemesini <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> yönteminin alan bir <xref:System.Xml.Schema.XmlSchemaObject> bir özniteliğin kısmi doğrulama başlatmak için bir parametre adıyla <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yalnızca öznitelik döndüren <xref:System.Xml.Schema.XmlSchemaValidator> nesnesi başlatılmadı.</span><span class="sxs-lookup"><span data-stu-id="80f09-256">If the overload of the <xref:System.Xml.Schema.XmlSchemaValidator.Initialize%2A> method that takes an <xref:System.Xml.Schema.XmlSchemaObject> as a parameter is called to initialize partial validation of an attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns only the attribute to which the <xref:System.Xml.Schema.XmlSchemaValidator> object was initialized.</span></span>|<span data-ttu-id="80f09-257">Şemaya ekler <xref:System.Xml.Schema.XmlSchemaSet> , <xref:System.Xml.Schema.XmlSchemaValidator> önişlem hata olup olmadığını nesne.</span><span class="sxs-lookup"><span data-stu-id="80f09-257">Adds the schema to the <xref:System.Xml.Schema.XmlSchemaSet> of the <xref:System.Xml.Schema.XmlSchemaValidator> object if it has no preprocessing errors.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateElement%2A>|<span data-ttu-id="80f09-258">Bağlam öğesi geçerliyse, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin alt öğesi olarak beklenen öğe dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-258">If the context element is valid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as children of the context element.</span></span><br /><br /> <span data-ttu-id="80f09-259">Bağlam öğesi geçersizse <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-259">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span>|<span data-ttu-id="80f09-260">Bağlam öğesi geçerli olup olmadığını ve hiçbir çağrısına varsa <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> daha önce yapılmış, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> bağlamı öğesinde tanımlanan tüm öznitelikler listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-260">If the context element is valid, and if no call to <xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A> has been previously made, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of all the attributes defined on the context element.</span></span><br /><br /> <span data-ttu-id="80f09-261">Bazı öznitelikler zaten doğrulandı, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> doğrulanacak kalan öznitelikler listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-261">If some attributes have already been validated, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the remaining attributes to be validated.</span></span><br /><br /> <span data-ttu-id="80f09-262">Bağlam öğesi geçersizse <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-262">If the context element is invalid, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="80f09-263">Yukarıdaki ile aynı.</span><span class="sxs-lookup"><span data-stu-id="80f09-263">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateAttribute%2A>|<span data-ttu-id="80f09-264">Context özniteliği bir üst düzey özniteliği ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-264">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="80f09-265">Aksi takdirde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> bağlam öğesinin ilk alt olarak beklenen öğe dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-265">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="80f09-266">Context özniteliği bir üst düzey özniteliği ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-266">If the context attribute is a top-level attribute, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="80f09-267">Aksi takdirde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> doğrulanacak kalan öznitelikler listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-267">Otherwise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the list of remaining attributes to be validated.</span></span>|<span data-ttu-id="80f09-268">Yukarıdaki ile aynı.</span><span class="sxs-lookup"><span data-stu-id="80f09-268">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.GetUnspecifiedDefaultAttributes%2A>|<span data-ttu-id="80f09-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>bağlam öğesinin ilk alt olarak beklenen öğe dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-269"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="80f09-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>henüz için bağlam öğesi doğrulanması için gerekli ve isteğe bağlı öznitelikleri listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-270"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns a list of the required and optional attributes that are yet to be validated for the context element.</span></span>|<span data-ttu-id="80f09-271">Yukarıdaki ile aynı.</span><span class="sxs-lookup"><span data-stu-id="80f09-271">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndOfAttributes%2A>|<span data-ttu-id="80f09-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>bağlam öğesinin ilk alt olarak beklenen öğe dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-272"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected as the first child of the context element.</span></span>|<span data-ttu-id="80f09-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-273"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span>|<span data-ttu-id="80f09-274">Yukarıdaki ile aynı.</span><span class="sxs-lookup"><span data-stu-id="80f09-274">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>|<span data-ttu-id="80f09-275">Bağlam öğenin contentType farklıysa, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sonraki konumu beklenen öğe dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-275">If the context element's contentType is Mixed, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position.</span></span><br /><br /> <span data-ttu-id="80f09-276">Bağlam öğenin contentType TextOnly ya da boş, ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-276">If the context element's contentType is TextOnly or Empty, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="80f09-277">Bağlam öğenin contentType ElementOnly, ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> sonraki konuma ancak bir doğrulama hatası beklenen öğe dizisi zaten oluştu döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-277">If the context element's contentType is ElementOnly, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected in the next position but a validation error has already occurred.</span></span>|<span data-ttu-id="80f09-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>bağlam öğenin doğrulanmamış öznitelikler listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-278"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span>|<span data-ttu-id="80f09-279">Yukarıdaki ile aynı.</span><span class="sxs-lookup"><span data-stu-id="80f09-279">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateWhitespace%2A>|<span data-ttu-id="80f09-280">Bağlam boşluk üst düzey boşluk, ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-280">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="80f09-281">Aksi takdirde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> yöntemin davranıştır de aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="80f09-281">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="80f09-282">Bağlam boşluk üst düzey boşluk, ise <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-282">If the context white-space is top-level white-space, <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty array.</span></span><br /><br /> <span data-ttu-id="80f09-283">Aksi takdirde <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> yöntemin davranıştır de aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span><span class="sxs-lookup"><span data-stu-id="80f09-283">Otherwise the <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> method's behavior is the same as in <xref:System.Xml.Schema.XmlSchemaValidator.ValidateText%2A>.</span></span>|<span data-ttu-id="80f09-284">Yukarıdaki ile aynı.</span><span class="sxs-lookup"><span data-stu-id="80f09-284">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>|<span data-ttu-id="80f09-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A>bağlam öğesi (olası eşdüzey) sonra beklenen öğe dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-285"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedParticles%2A> returns the sequence of elements expected after the context element (possible siblings).</span></span>|<span data-ttu-id="80f09-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A>bağlam öğenin doğrulanmamış öznitelikler listesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-286"><xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns the context element's list of attributes not validated.</span></span><br /><br /> <span data-ttu-id="80f09-287">Bağlam öğesi üst öğeye sahipse <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> boş bir liste döndürür (geçerli öğede üst bağlam öğedir <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> olarak adlandırılıyordu).</span><span class="sxs-lookup"><span data-stu-id="80f09-287">If the context element has no parent then <xref:System.Xml.Schema.XmlSchemaValidator.GetExpectedAttributes%2A> returns an empty list (the context element is the parent of the current element on which <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A> was called).</span></span>|<span data-ttu-id="80f09-288">Yukarıdaki ile aynı.</span><span class="sxs-lookup"><span data-stu-id="80f09-288">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.SkipToEndElement%2A>|<span data-ttu-id="80f09-289">Aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="80f09-289">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="80f09-290">Aynı <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span><span class="sxs-lookup"><span data-stu-id="80f09-290">Same as <xref:System.Xml.Schema.XmlSchemaValidator.ValidateEndElement%2A>.</span></span>|<span data-ttu-id="80f09-291">Yukarıdaki ile aynı.</span><span class="sxs-lookup"><span data-stu-id="80f09-291">Same as above.</span></span>|  
|<xref:System.Xml.Schema.XmlSchemaValidator.EndValidation%2A>|<span data-ttu-id="80f09-292">Boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-292">Returns an empty array.</span></span>|<span data-ttu-id="80f09-293">Boş bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="80f09-293">Returns an empty array.</span></span>|<span data-ttu-id="80f09-294">Yukarıdaki ile aynı.</span><span class="sxs-lookup"><span data-stu-id="80f09-294">Same as above.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="80f09-295">Çeşitli özellikleri tarafından döndürülen değerler <xref:System.Xml.Schema.XmlSchemaValidator> sınıfı değiştirilmediğini yöntemlerinden herhangi birini yukarıdaki tabloda çağırarak.</span><span class="sxs-lookup"><span data-stu-id="80f09-295">The values returned by the various properties of the <xref:System.Xml.Schema.XmlSchemaValidator> class are not altered by calling any of the methods in the above table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80f09-296">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80f09-296">See Also</span></span>  
 <xref:System.Xml.Schema.XmlSchemaValidator>
