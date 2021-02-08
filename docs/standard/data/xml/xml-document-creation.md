---
description: 'Daha fazla bilgi edinin: XML belgesi oluşturma'
title: XML Belgesi Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
ms.openlocfilehash: 825c616fc6c0f7216248ae71e7d7630383d9cfea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782786"
---
# <a name="xml-document-creation"></a><span data-ttu-id="e900b-103">XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e900b-103">XML Document Creation</span></span>

<span data-ttu-id="e900b-104">XML belgesi oluşturmanın iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="e900b-104">There are two ways to create an XML document.</span></span> <span data-ttu-id="e900b-105">Bir yol, parametresiz bir **XmlDocument** oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="e900b-105">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="e900b-106">Diğer bir deyişle, bir **XmlDocument** oluşturmak ve bunu bir XmlNameTable parametresi olarak iletmektir.</span><span class="sxs-lookup"><span data-stu-id="e900b-106">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="e900b-107">Aşağıdaki örnek, parametresiz yeni, boş bir **XmlDocument** oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e900b-107">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="e900b-108">Bir belge oluşturulduktan sonra, **Load** metodunu kullanarak bir dize, AKıŞ, URL, metin okuyucusu veya bir **XmlReader** türetilmiş sınıftan verilerle yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e900b-108">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="e900b-109">Ayrıca, bir dizeden XML okuyan bir Load yöntemi olan **LoadXml** yöntemi de vardır.</span><span class="sxs-lookup"><span data-stu-id="e900b-109">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="e900b-110">Çeşitli **yükleme** yöntemleri hakkında daha fazla bilgi için bkz. [Dom 'Da XML belgesi okuma](reading-an-xml-document-into-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="e900b-110">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="e900b-111">**XmlNameTable** adlı bir sınıf vardır.</span><span class="sxs-lookup"><span data-stu-id="e900b-111">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="e900b-112">Bu sınıf, atomlanmış dize nesnelerinin bir tablosudur.</span><span class="sxs-lookup"><span data-stu-id="e900b-112">This class is a table of atomized string objects.</span></span> <span data-ttu-id="e900b-113">Bu tablo, XML ayrıştırıcısının bir XML belgesindeki tüm yinelenen öğe ve öznitelik adları için aynı dize nesnesini kullanması için etkili bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="e900b-113">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="e900b-114">Bir belge, yukarıda gösterildiği gibi oluşturulduğunda ve belge yüklendiğinde öznitelik ve öğe adlarıyla yüklendiğinde, otomatik olarak bir **XmlNameTable** oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e900b-114">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="e900b-115">Zaten bir ad tablosu olan bir belgeniz varsa ve bu adlar başka bir belgede yararlı olacaksa, parametre olarak **XmlNameTable** alan **Load** metodunu kullanarak yeni bir belge oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e900b-115">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="e900b-116">Belge bu yöntemle oluşturulduğunda, var olan **XmlNameTable** , diğer belgeden daha önce yüklenmiş olan tüm öznitelikleri ve öğeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="e900b-116">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="e900b-117">Öğe ve öznitelik adlarını verimli bir şekilde karşılaştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e900b-117">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="e900b-118">**XmlNameTable** hakkında daha fazla bilgi için bkz. [XmlNameTable kullanılarak nesne karşılaştırması](object-comparison-using-xmlnametable.md).</span><span class="sxs-lookup"><span data-stu-id="e900b-118">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="e900b-119">Başvuru için bkz <xref:System.Xml.XmlNameTable> ..</span><span class="sxs-lookup"><span data-stu-id="e900b-119">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e900b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e900b-120">See also</span></span>

- [<span data-ttu-id="e900b-121">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="e900b-121">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
