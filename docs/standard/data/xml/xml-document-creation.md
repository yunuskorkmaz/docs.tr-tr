---
title: "XML belgesi oluşturma"
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
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a0806e34cfbf7c8e0b5ba995ca4876b8d10405e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-document-creation"></a><span data-ttu-id="38c3e-102">XML belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="38c3e-102">XML Document Creation</span></span>
<span data-ttu-id="38c3e-103">Bir XML belgesi oluşturmanın iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="38c3e-103">There are two ways to create an XML document.</span></span> <span data-ttu-id="38c3e-104">Tek yönlü oluşturmaktır bir **XmlDocument** hiçbir parametre.</span><span class="sxs-lookup"><span data-stu-id="38c3e-104">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="38c3e-105">Diğer bir yol oluşturmaktır bir **XmlDocument** ve bir XmlNameTable parametre olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="38c3e-105">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="38c3e-106">Aşağıdaki örnek yeni bir boş oluşturulacağını gösterir **XmlDocument** hiçbir parametrelerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="38c3e-106">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="38c3e-107">Bir belge oluşturulduktan sonra onu bir dize verilerle yükleyebilirsiniz akış, URL, metin okuyucu veya bir **XmlReader** sınıfını kullanarak türetilmiş **yük** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="38c3e-107">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="38c3e-108">Ayrıca başka bir yükleme yöntemini olan **LoadXML** bir dizeden XML okur yöntemi.</span><span class="sxs-lookup"><span data-stu-id="38c3e-108">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="38c3e-109">Çeşitli hakkında daha fazla bilgi için **yük** yöntemleri bkz [bir XML belgesi DOM okuma](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="38c3e-109">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="38c3e-110">Adlı bir sınıf yok **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="38c3e-110">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="38c3e-111">Bu sınıf, atomized dize nesnelerin bir tablodur.</span><span class="sxs-lookup"><span data-stu-id="38c3e-111">This class is a table of atomized string objects.</span></span> <span data-ttu-id="38c3e-112">Bu tabloda tüm yinelenen öğe ve öznitelik adları bir XML belgesi aynı dize nesnesi kullanılmak üzere XML Ayrıştırıcı için verimli bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="38c3e-112">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="38c3e-113">Bir **XmlNameTable** bir belge yukarıda gösterildiği gibi oluşturulduğunda ve belge yüklendiğinde özniteliği ve öğesi adlarıyla yüklendi otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="38c3e-113">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="38c3e-114">Bir belge adı tablosu ile zaten varsa ve bu adlardan başka bir belgede yararlı olacaktır, kullanarak yeni bir belge oluşturabilirsiniz **yük** yönteminin alan bir **XmlNameTable** bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="38c3e-114">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="38c3e-115">Belgenin bu yöntemle oluşturulduğunda, varolan kullanan **XmlNameTable** ile tüm öznitelikler ve öğeler içine diğer belgesinden zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="38c3e-115">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="38c3e-116">Verimli bir şekilde öğe ve öznitelik adları karşılaştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="38c3e-116">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="38c3e-117">Daha fazla bilgi için **XmlNameTable**, bkz: [nesne karşılaştırma kullanarak XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span><span class="sxs-lookup"><span data-stu-id="38c3e-117">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="38c3e-118">Başvuru için bkz: <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="38c3e-118">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38c3e-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="38c3e-119">See Also</span></span>  
 [<span data-ttu-id="38c3e-120">XML belge nesne modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="38c3e-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
