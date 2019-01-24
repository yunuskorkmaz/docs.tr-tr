---
title: XmlSchemaCollection Schema Compilation
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d47fa4d4ef7a55182dd27aa6f64542fec1fa99c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704322"
---
# <a name="xmlschemacollection-schema-compilation"></a><span data-ttu-id="7f0bf-102">XmlSchemaCollection Schema Compilation</span><span class="sxs-lookup"><span data-stu-id="7f0bf-102">XmlSchemaCollection Schema Compilation</span></span>
<span data-ttu-id="7f0bf-103">**XmlSchemaCollection** bir önbellek ya da burada XML verileri azaltılmış (XDR) ve XML Şeması Tanım Dili (XSD) şemalarını depolanabilir ve doğrulanmış kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-103">The **XmlSchemaCollection** is a cache or library where XML-Data Reduced (XDR) and XML Schema definition language (XSD) schemas can be stored and validated.</span></span> <span data-ttu-id="7f0bf-104">**XmlSchemaCollection** şemaları bir dosyadan veya URL'den erişmek yerine bellekte önbelleğe alarak performansını artırır.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-104">**XmlSchemaCollection** improves performance by caching schemas in memory instead of accessing them from a file or URL.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f0bf-105">Ancak **XmlSchemaCollection** sınıfı, hem XDR şema hem de XML şemaları, herhangi bir yöntemi ve alan veya döndüren özellik depolayan bir **XmlSchema** nesnesi XML şemaları yalnızca destekler.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-105">Although the **XmlSchemaCollection** class stores both XDR schemas and XML Schemas, any method and property that takes or returns an **XmlSchema** object supports XML Schemas only.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7f0bf-106"><xref:System.Xml.Schema.XmlSchemaCollection> Sınıf artık kullanımdan kalkmıştır ve ile değiştirilmiştir <xref:System.Xml.Schema.XmlSchemaSet> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="7f0bf-107">Hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet> sınıfı bakın [şema derleme için XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="7f0bf-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
## <a name="add-schemas-to-the-collection"></a><span data-ttu-id="7f0bf-108">Şemalar koleksiyonuna ekleme</span><span class="sxs-lookup"><span data-stu-id="7f0bf-108">Add Schemas to the Collection</span></span>  
 <span data-ttu-id="7f0bf-109">Şema koleksiyonu kullanarak yüklenir **Ekle** yöntemi **XmlSchemaCollection**, aynı zamanda Şema ad alanı URI ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-109">Schemas are loaded to the collection using the **Add** method of **XmlSchemaCollection**, at which time the schema is associated with a namespace URI.</span></span> <span data-ttu-id="7f0bf-110">XML şemaları için ad alanı URI genellikle şema hedef ad alanı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-110">For XML Schemas, the namespace URI will typically be the target namespace for the schema.</span></span> <span data-ttu-id="7f0bf-111">XDR Şema ad alanı URI ad alanı şema koleksiyonuna zaman eklendi belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-111">For XDR schemas, the namespace URI is the namespace specified when the schema was added to the collection.</span></span>  
  
## <a name="check-for-a-schema-in-the-collection"></a><span data-ttu-id="7f0bf-112">Bir şema koleksiyonunda denetle</span><span class="sxs-lookup"><span data-stu-id="7f0bf-112">Check for a Schema in the Collection</span></span>  
 <span data-ttu-id="7f0bf-113">Kullanarak bir şema koleksiyonunda olup olmadığını kontrol edebilirsiniz **içerir** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-113">You can check to see if a schema is in the collection by using the **Contains** method.</span></span> <span data-ttu-id="7f0bf-114">**İçerir** yöntemi alır ya da bir **XmlSchema** nesnesi (yalnızca XML şemaları) veya ad alanı URI temsil eden bir dize (için XML şemaları ve XDR şema) şema ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-114">The **Contains** method takes either an **XmlSchema** object (for XML Schemas only) or a string representing the namespace URI associated with the schema (for XML Schemas and XDR schemas).</span></span>  
  
## <a name="retrieve-a-schema-from-the-collection"></a><span data-ttu-id="7f0bf-115">Koleksiyondan bir şema alınamıyor</span><span class="sxs-lookup"><span data-stu-id="7f0bf-115">Retrieve a Schema from the Collection</span></span>  
 <span data-ttu-id="7f0bf-116">Kullanarak bir şema koleksiyondan alabilirsiniz **öğesi** özelliği.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-116">You can retrieve a schema from the collection by using the **Item** property.</span></span> <span data-ttu-id="7f0bf-117">**Öğesi** özelliği, hedef ad alanı genellikle, şema ile ilişkili URI ad alanı temsil eden bir dize alır ve döndürür bir **XmlSchema** nesne.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-117">The **Item** property takes a string representing the namespace URI associated with the schema, typically its target namespace, and returns an **XmlSchema** object.</span></span> <span data-ttu-id="7f0bf-118">**Öğesi** özelliği için XML şemaları yalnızca uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-118">The **Item** property applies to XML Schemas only.</span></span> <span data-ttu-id="7f0bf-119">Nesne modeli kullanılabilir olmadığı için dönüş değeri her zaman bir null XDR şema içindir.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-119">The return value is always a null reference for XDR schemas because they do not have an object model available.</span></span>  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a><span data-ttu-id="7f0bf-120">XmlSchemaCollection kullanarak XML belgeleri doğrulamak</span><span class="sxs-lookup"><span data-stu-id="7f0bf-120">Validate XML Documents Using XmlSchemaCollection</span></span>  
 <span data-ttu-id="7f0bf-121">Bir XML örneği belge kullanarak doğrulayabilirsiniz bir **XmlSchemaCollection** oluşturarak **XmlSchemaCollection** , şemalar koleksiyonuna ekleme ve ayar nesnesi **şemaları**  özelliği **XmlValidatingReader** oluşturulan atamak **XmlSchemaCollection** için **XmlValidatingReader**.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-121">You can validate an XML instance document using an **XmlSchemaCollection** by creating the **XmlSchemaCollection** object, adding your schemas to the collection, and setting the **Schemas** property on the **XmlValidatingReader** to assign the created **XmlSchemaCollection** to the **XmlValidatingReader**.</span></span>  
  
### <a name="improved-performance"></a><span data-ttu-id="7f0bf-122">Geliştirilmiş performans</span><span class="sxs-lookup"><span data-stu-id="7f0bf-122">Improved Performance</span></span>  
 <span data-ttu-id="7f0bf-123">Tavsiye edilir, aynı şemaya birden fazla belge doğrulamakta olduğunuz varsa kullanmanızı **XmlSchemaCollection** çünkü şemaları bellekte önbelleğe alarak daha iyi performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-123">It is recommended, if you are validating more than one document against the same schema, that you use the **XmlSchemaCollection** because it provides better performance by caching schemas in memory.</span></span>  
  
 <span data-ttu-id="7f0bf-124">Aşağıdaki kod örneği oluşturur **XmlSchemaCollection** nesnesi şemalar koleksiyonuna ekler ve ayarlar **şemaları** özelliği.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-124">The following code example creates the **XmlSchemaCollection** object, adds schemas to the collection, and sets the **Schemas** property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7f0bf-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f0bf-125">See also</span></span>

- [<span data-ttu-id="7f0bf-126">XmlSchemaCollection ile XDR Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="7f0bf-126">XDR Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xdr-validation-with-xmlschemacollection.md)
- [<span data-ttu-id="7f0bf-127">XmlSchemaCollection ile XML Şeması (XSD) Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="7f0bf-127">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemacollection.md)
