---
title: XmlSchemaCollection Şema Derlemesi
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 76f28770-7126-428f-9ed5-7b5ae8bad5ee
ms.openlocfilehash: 3d517652665d6d0693e141d623483ff8946bbbf4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290246"
---
# <a name="xmlschemacollection-schema-compilation"></a><span data-ttu-id="43f24-102">XmlSchemaCollection Şema Derlemesi</span><span class="sxs-lookup"><span data-stu-id="43f24-102">XmlSchemaCollection Schema Compilation</span></span>
<span data-ttu-id="43f24-103">**XmlSchemaCollection** , XML verileri AZALTıLMıŞ (xdr) ve XML şeması tanım DILI (xsd) şemaları depolanabilecek ve doğrulanabilen bir önbellek veya kitaplıktır.</span><span class="sxs-lookup"><span data-stu-id="43f24-103">The **XmlSchemaCollection** is a cache or library where XML-Data Reduced (XDR) and XML Schema definition language (XSD) schemas can be stored and validated.</span></span> <span data-ttu-id="43f24-104">**XmlSchemaCollection** , şemaları bir dosya veya URL 'den erişmek yerine bellekte önbelleğe alarak performansı geliştirir.</span><span class="sxs-lookup"><span data-stu-id="43f24-104">**XmlSchemaCollection** improves performance by caching schemas in memory instead of accessing them from a file or URL.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="43f24-105">**XmlSchemaCollection** sınıfı hem XDR şemaları hem de XML şemaları depolasa da, **XmlSchema** nesnesi alan veya döndüren herhangi bir yöntem ve özellik yalnızca XML şemalarını destekler.</span><span class="sxs-lookup"><span data-stu-id="43f24-105">Although the **XmlSchemaCollection** class stores both XDR schemas and XML Schemas, any method and property that takes or returns an **XmlSchema** object supports XML Schemas only.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="43f24-106"><xref:System.Xml.Schema.XmlSchemaCollection>Sınıf artık kullanımdan kalkmıştır ve <xref:System.Xml.Schema.XmlSchemaSet> sınıfıyla değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="43f24-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="43f24-107">Sınıf hakkında daha fazla bilgi için <xref:System.Xml.Schema.XmlSchemaSet> bkz. [şema derlemesi için XmlSchemaSet](xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="43f24-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](xmlschemaset-for-schema-compilation.md).</span></span>  
  
## <a name="add-schemas-to-the-collection"></a><span data-ttu-id="43f24-108">Koleksiyona şemalar ekleme</span><span class="sxs-lookup"><span data-stu-id="43f24-108">Add Schemas to the Collection</span></span>  
 <span data-ttu-id="43f24-109">Şemalar, şema bir ad alanı URI 'siyle ilişkili olan **XmlSchemaCollection**'ın **Add** yöntemi kullanılarak koleksiyona yüklenir.</span><span class="sxs-lookup"><span data-stu-id="43f24-109">Schemas are loaded to the collection using the **Add** method of **XmlSchemaCollection**, at which time the schema is associated with a namespace URI.</span></span> <span data-ttu-id="43f24-110">XML şemaları için ad alanı URI 'SI genellikle şemanın hedef ad alanı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="43f24-110">For XML Schemas, the namespace URI will typically be the target namespace for the schema.</span></span> <span data-ttu-id="43f24-111">XDR şemaları için ad alanı URI 'SI, şema koleksiyona eklendiğinde belirtilen ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="43f24-111">For XDR schemas, the namespace URI is the namespace specified when the schema was added to the collection.</span></span>  
  
## <a name="check-for-a-schema-in-the-collection"></a><span data-ttu-id="43f24-112">Koleksiyondaki şemayı denetle</span><span class="sxs-lookup"><span data-stu-id="43f24-112">Check for a Schema in the Collection</span></span>  
 <span data-ttu-id="43f24-113">**Contains** metodunu kullanarak bir şemanın koleksiyonda olup olmadığını kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43f24-113">You can check to see if a schema is in the collection by using the **Contains** method.</span></span> <span data-ttu-id="43f24-114">**Contains** yöntemi bir **XmlSchema** nesnesi (yalnızca XML şemaları için) ya da ŞEMAYLA ilişkili ad alanı URI 'sini temsil eden bir dizeyi (XML şemaları ve XDR şemaları için) alır.</span><span class="sxs-lookup"><span data-stu-id="43f24-114">The **Contains** method takes either an **XmlSchema** object (for XML Schemas only) or a string representing the namespace URI associated with the schema (for XML Schemas and XDR schemas).</span></span>  
  
## <a name="retrieve-a-schema-from-the-collection"></a><span data-ttu-id="43f24-115">Koleksiyondan bir şema alma</span><span class="sxs-lookup"><span data-stu-id="43f24-115">Retrieve a Schema from the Collection</span></span>  
 <span data-ttu-id="43f24-116">**Öğe** özelliğini kullanarak koleksiyondan bir şema alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43f24-116">You can retrieve a schema from the collection by using the **Item** property.</span></span> <span data-ttu-id="43f24-117">**Öğe** özelliği, şemayla ilişkili ad alanı URI 'sini temsil eden bir dize alır, genellikle hedef ad alanı ve bir **XmlSchema** nesnesi döndürür.</span><span class="sxs-lookup"><span data-stu-id="43f24-117">The **Item** property takes a string representing the namespace URI associated with the schema, typically its target namespace, and returns an **XmlSchema** object.</span></span> <span data-ttu-id="43f24-118">**Öğe** ÖZELLIĞI yalnızca XML şemaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="43f24-118">The **Item** property applies to XML Schemas only.</span></span> <span data-ttu-id="43f24-119">Bir nesne modeli mevcut olmadığından, dönüş değeri her zaman XDR şemaları için bir null başvurudur.</span><span class="sxs-lookup"><span data-stu-id="43f24-119">The return value is always a null reference for XDR schemas because they do not have an object model available.</span></span>  
  
## <a name="validate-xml-documents-using-xmlschemacollection"></a><span data-ttu-id="43f24-120">XmlSchemaCollection kullanarak XML belgelerini doğrulama</span><span class="sxs-lookup"><span data-stu-id="43f24-120">Validate XML Documents Using XmlSchemaCollection</span></span>  
 <span data-ttu-id="43f24-121">**XmlSchemaCollection nesnesini oluşturarak** , şemalarınızı koleksiyona ekleyerek ve **XmlValidatingReader** üzerinde oluşturulan **XmlSchemaCollection** 'ı atamak için, XmlValidatingReader üzerinde **şemalar** özelliğini ayarlayarak bir **XmlSchemaCollection** kullanarak bir XML örnek belgesini **doğrulayabilirsiniz.**</span><span class="sxs-lookup"><span data-stu-id="43f24-121">You can validate an XML instance document using an **XmlSchemaCollection** by creating the **XmlSchemaCollection** object, adding your schemas to the collection, and setting the **Schemas** property on the **XmlValidatingReader** to assign the created **XmlSchemaCollection** to the **XmlValidatingReader**.</span></span>  
  
### <a name="improved-performance"></a><span data-ttu-id="43f24-122">İyileştirilmiş performans</span><span class="sxs-lookup"><span data-stu-id="43f24-122">Improved Performance</span></span>  
 <span data-ttu-id="43f24-123">Aynı şemaya karşı birden fazla belge doğrulmanız önerilir, bu, bir şemayı bellekte önbelleğe alarak daha iyi performans sağladığından, **XmlSchemaCollection** 'ı kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="43f24-123">It is recommended, if you are validating more than one document against the same schema, that you use the **XmlSchemaCollection** because it provides better performance by caching schemas in memory.</span></span>  
  
 <span data-ttu-id="43f24-124">Aşağıdaki kod örneği, **XmlSchemaCollection** nesnesini oluşturur, koleksiyona şemalar ekler ve **şemalar** özelliğini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="43f24-124">The following code example creates the **XmlSchemaCollection** object, adds schemas to the collection, and sets the **Schemas** property.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43f24-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43f24-125">See also</span></span>

- [<span data-ttu-id="43f24-126">XmlSchemaCollection ile XDR Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="43f24-126">XDR Validation with XmlSchemaCollection</span></span>](xdr-validation-with-xmlschemacollection.md)
- [<span data-ttu-id="43f24-127">XmlSchemaCollection ile XML Şeması (XSD) Doğrulaması</span><span class="sxs-lookup"><span data-stu-id="43f24-127">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>](xml-schema-xsd-validation-with-xmlschemacollection.md)
