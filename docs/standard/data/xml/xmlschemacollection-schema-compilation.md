---
title: "XmlSchemaCollection şema derleme"
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
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c891736534741d1d3d3edb93d75d9f191c2dd573
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xmlschemacollection-schema-compilation"></a><span data-ttu-id="f0190-102">XmlSchemaCollection şema derleme</span><span class="sxs-lookup"><span data-stu-id="f0190-102">XmlSchemaCollection Schema Compilation</span></span>
<span data-ttu-id="f0190-103">**XmlSchemaCollection** bir önbellek ya da nerede XML verileri azaltılmış (XDR) ve XML Şeması Tanım Dili (XSD) şemaları depolanabilir ve doğrulanmış kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="f0190-103">The **XmlSchemaCollection** is a cache or library where XML-Data Reduced (XDR) and XML Schema definition language (XSD) schemas can be stored and validated.</span></span> <span data-ttu-id="f0190-104">**XmlSchemaCollection** şemaları bir dosyaya veya URL'ye erişmesini yerine bellekte önbelleğe alarak performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="f0190-104">**XmlSchemaCollection** improves performance by caching schemas in memory instead of accessing them from a file or URL.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0190-105">Ancak **XmlSchemaCollection** sınıfı depolar XDR şemaları ve XML şemaları, yöntemi ve alır veya verir özelliği bir **XmlSchema** nesnesi XML şemaları yalnızca destekler.</span><span class="sxs-lookup"><span data-stu-id="f0190-105">Although the **XmlSchemaCollection** class stores both XDR schemas and XML Schemas, any method and property that takes or returns an **XmlSchema** object supports XML Schemas only.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f0190-106"><xref:System.Xml.Schema.XmlSchemaCollection> Sınıf artık kullanımdan kalkmıştır ve ile değiştirilmiştir <xref:System.Xml.Schema.XmlSchemaSet> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f0190-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="f0190-107">Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet> sınıfı bakın, [şema derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="f0190-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
## <a name="add-schemas-to-the-collection"></a><span data-ttu-id="f0190-108">Şema koleksiyonuna Ekle</span><span class="sxs-lookup"><span data-stu-id="f0190-108">Add Schemas to the Collection</span></span>  
 <span data-ttu-id="f0190-109">Şema koleksiyonu kullanarak yüklenir **Ekle** yöntemi **XmlSchemaCollection**, aynı zamanda Şema ad alanı URI'si ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="f0190-109">Schemas are loaded to the collection using the **Add** method of **XmlSchemaCollection**, at which time the schema is associated with a namespace URI.</span></span> <span data-ttu-id="f0190-110">XML şemaları için ad alanı URI şeması için hedef ad alanı genellikle olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f0190-110">For XML Schemas, the namespace URI will typically be the target namespace for the schema.</span></span> <span data-ttu-id="f0190-111">XDR şema için ad alanı URI'si ad şema koleksiyonuna zaman eklendi belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f0190-111">For XDR schemas, the namespace URI is the namespace specified when the schema was added to the collection.</span></span>  
  
## <a name="check-for-a-schema-in-the-collection"></a><span data-ttu-id="f0190-112">Bir şema koleksiyonunda denetle</span><span class="sxs-lookup"><span data-stu-id="f0190-112">Check for a Schema in the Collection</span></span>  
 <span data-ttu-id="f0190-113">Kullanarak bir şema koleksiyonunda olup olmadığını görmek için kontrol edebilirsiniz **içerir** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f0190-113">You can check to see if a schema is in the collection by using the **Contains** method.</span></span> <span data-ttu-id="f0190-114">**İçerir** yöntemi alır ya da bir **XmlSchema** nesnesi (yalnızca XML şemaları) veya ad alanı URI'si temsil eden bir dize (XML şemaları ve XDR şemaları için) şema ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="f0190-114">The **Contains** method takes either an **XmlSchema** object (for XML Schemas only) or a string representing the namespace URI associated with the schema (for XML Schemas and XDR schemas).</span></span>  
  
## <a name="retrieve-a-schema-from-the-collection"></a><span data-ttu-id="f0190-115">Koleksiyondan bir şema Al</span><span class="sxs-lookup"><span data-stu-id="f0190-115">Retrieve a Schema from the Collection</span></span>  
 <span data-ttu-id="f0190-116">Kullanarak bir şema koleksiyondan alabilirsiniz **öğesi** özelliği.</span><span class="sxs-lookup"><span data-stu-id="f0190-116">You can retrieve a schema from the collection by using the **Item** property.</span></span> <span data-ttu-id="f0190-117">**Öğesi** özelliği ad alanı URI şeması, genellikle hedef ad alanı, ilişkili temsil eden bir dize alır ve döndüren bir **XmlSchema** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="f0190-117">The **Item** property takes a string representing the namespace URI associated with the schema, typically its target namespace, and returns an **XmlSchema** object.</span></span> <span data-ttu-id="f0190-118">**Öğesi** özelliği için XML şemaları yalnızca uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f0190-118">The **Item** property applies to XML Schemas only.</span></span> <span data-ttu-id="f0190-119">Nesne modeli kullanılabilir olmadığından dönüş değeri her zaman null XDR şemaları için başvurudur.</span><span class="sxs-lookup"><span data-stu-id="f0190-119">The return value is always a null reference for XDR schemas because they do not have an object model available.</span></span>  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a><span data-ttu-id="f0190-120">XML belgeleri XmlSchemaCollection kullanarak doğrula</span><span class="sxs-lookup"><span data-stu-id="f0190-120">Validate XML Documents Using XmlSchemaCollection</span></span>  
 <span data-ttu-id="f0190-121">Bir XML örneği belge kullanarak doğrulayabilirsiniz bir **XmlSchemaCollection** oluşturarak **XmlSchemaCollection** , şemalar koleksiyona ekleme ve ayar nesnesi **şemaları**  özelliği **XmlValidatingReader** oluşturulan atamak için **XmlSchemaCollection** için **XmlValidatingReader**.</span><span class="sxs-lookup"><span data-stu-id="f0190-121">You can validate an XML instance document using an **XmlSchemaCollection** by creating the **XmlSchemaCollection** object, adding your schemas to the collection, and setting the **Schemas** property on the **XmlValidatingReader** to assign the created **XmlSchemaCollection** to the **XmlValidatingReader**.</span></span>  
  
### <a name="improved-performance"></a><span data-ttu-id="f0190-122">Geliştirilmiş performans</span><span class="sxs-lookup"><span data-stu-id="f0190-122">Improved Performance</span></span>  
 <span data-ttu-id="f0190-123">Önerilir, birden çok belgeyi aynı şemaya karşı doğrulama varsa, kullandığınız **XmlSchemaCollection** çünkü şemaları bellekte önbelleğe alarak daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="f0190-123">It is recommended, if you are validating more than one document against the same schema, that you use the **XmlSchemaCollection** because it provides better performance by caching schemas in memory.</span></span>  
  
 <span data-ttu-id="f0190-124">Aşağıdaki kod örneği oluşturur **XmlSchemaCollection** nesne, şema koleksiyonuna ekler ve ayarlar **şemaları** özelliği.</span><span class="sxs-lookup"><span data-stu-id="f0190-124">The following code example creates the **XmlSchemaCollection** object, adds schemas to the collection, and sets the **Schemas** property.</span></span>  
  
```vb  
Dim tr as XmlTextReader = new XmlTextReader("Books.xml")  
Dim vr as XmlValidatingReader = new XmlValidatingReader(tr)  
Dim xsc as XmlSchemaCollection = new XmlSchemaCollection  
xsc.Add("urn:bookstore-schema", "Books.xsd")  
vr.Schemas.Add(xsc)  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("Books.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
xsc.Add("urn:bookstore-schema", "Books.xsd");    
vr.Schemas.Add(xsc);  
```  
  
## <a name="see-also"></a><span data-ttu-id="f0190-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0190-125">See Also</span></span>  
 [<span data-ttu-id="f0190-126">XmlSchemaCollection ile XDR Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="f0190-126">XDR Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)  
 [<span data-ttu-id="f0190-127">XmlSchemaCollection ile XML Şeması (XSD) Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="f0190-127">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
