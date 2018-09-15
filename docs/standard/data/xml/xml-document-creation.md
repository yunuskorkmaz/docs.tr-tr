---
title: XML belgesi oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b76140fb7d79b1e191c0451cd7556963130d224a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2018
ms.locfileid: "45646187"
---
# <a name="xml-document-creation"></a><span data-ttu-id="838b4-102">XML belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="838b4-102">XML Document Creation</span></span>
<span data-ttu-id="838b4-103">Bir XML belgesi oluşturmak için iki yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="838b4-103">There are two ways to create an XML document.</span></span> <span data-ttu-id="838b4-104">Oluşturmak için bir yolu olan bir **XmlDocument** parametre olmadan.</span><span class="sxs-lookup"><span data-stu-id="838b4-104">One way is to create an **XmlDocument** with no parameters.</span></span> <span data-ttu-id="838b4-105">Oluşturmak için diğer yol ise bir **XmlDocument** ve parametre olarak bir XmlNameTable geçirin.</span><span class="sxs-lookup"><span data-stu-id="838b4-105">The other way is to create an **XmlDocument** and pass it an XmlNameTable as a parameter.</span></span> <span data-ttu-id="838b4-106">Aşağıdaki örnek, yeni, boş oluşturma işlemi gösterilmektedir **XmlDocument** hiçbir parametreleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="838b4-106">The following example shows how to create a new, empty **XmlDocument** using no parameters.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 <span data-ttu-id="838b4-107">Bir belge oluşturulduktan sonra bu verileri bir dizeden ile yükleyebilirsiniz akış URL'si, metin okuyucuyu ya da bir **XmlReader** sınıfını kullanarak türetilmiş **yük** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="838b4-107">Once a document is created, you can load it with data from a string, stream, URL, text reader, or an **XmlReader** derived class using the **Load** method.</span></span> <span data-ttu-id="838b4-108">Ayrıca başka bir yükleme yöntemi vardır **LoadXML** yöntemi XML bir dizeden okur.</span><span class="sxs-lookup"><span data-stu-id="838b4-108">There is also another load method, the **LoadXML** method, which reads XML from a string.</span></span> <span data-ttu-id="838b4-109">Çeşitli hakkında daha fazla bilgi için **yük** yöntemleri bkz [DOM'da XML belgesi okuma](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="838b4-109">For more information on the various **Load** methods, see [Reading an XML Document into the DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).</span></span>  
  
 <span data-ttu-id="838b4-110">Adlı bir sınıf yok **XmlNameTable**.</span><span class="sxs-lookup"><span data-stu-id="838b4-110">There is a class called the **XmlNameTable**.</span></span> <span data-ttu-id="838b4-111">Bu sınıf, parçalara ayrılmış bir dize nesnesi bir tablodur.</span><span class="sxs-lookup"><span data-stu-id="838b4-111">This class is a table of atomized string objects.</span></span> <span data-ttu-id="838b4-112">Bu tabloda tüm yinelenen öğe ve öznitelik adları bir XML belgesi için aynı dize nesnesi kullanılacak XML Ayrıştırıcı için etkili bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="838b4-112">This table provides an efficient means for the XML parser to use the same string object for all repeated element and attribute names in an XML document.</span></span> <span data-ttu-id="838b4-113">Bir **XmlNameTable** belge yukarıda da gösterildiği gibi oluşturulduğunda ve öğeyi ve öznitelik adları ile yüklenen belge yüklendiğinde otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="838b4-113">An **XmlNameTable** is automatically created when a document is created as shown above and is loaded with attribute and element names when the document is loaded.</span></span> <span data-ttu-id="838b4-114">Ad tablosu sahip bir belge zaten varsa ve bu başka bir belgede yararlı olacak adlardır, kullanarak yeni bir belge oluşturabilirsiniz **yük** gereken yöntemini bir **XmlNameTable** bir parametre olarak.</span><span class="sxs-lookup"><span data-stu-id="838b4-114">If you already have a document with a name table, and those names would be useful in another document, you can create a new document using the **Load** method that takes an **XmlNameTable** as a parameter.</span></span> <span data-ttu-id="838b4-115">Belgenin bu yöntemle oluşturulduğunda, varolan kullanır **XmlNameTable** tüm öznitelikleri ve öğeleri içine diğer belgeden zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="838b4-115">When the document is created with this method, it uses the existing **XmlNameTable** with all the attributes and elements already loaded into it from the other document.</span></span> <span data-ttu-id="838b4-116">Öğe ve öznitelik adları verimli bir şekilde karşılaştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="838b4-116">It can be used for efficiently comparing element and attribute names.</span></span> <span data-ttu-id="838b4-117">Daha fazla bilgi için **XmlNameTable**, bkz: [XmlNameTable kullanarak nesne karşılaştırma](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span><span class="sxs-lookup"><span data-stu-id="838b4-117">For more information on the **XmlNameTable**, see [Object Comparison Using XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md).</span></span> <span data-ttu-id="838b4-118">Başvuru için bkz: <xref:System.Xml.XmlNameTable>.</span><span class="sxs-lookup"><span data-stu-id="838b4-118">For reference, see <xref:System.Xml.XmlNameTable>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="838b4-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="838b4-119">See also</span></span>

- [<span data-ttu-id="838b4-120">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="838b4-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
