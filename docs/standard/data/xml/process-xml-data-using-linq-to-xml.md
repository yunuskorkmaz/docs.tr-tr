---
title: LINQ to XML kullanarak XML verilerini işleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1554c3e2b13dd0ea0d64ccd7e7caee0a1e0dd3f9
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835578"
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="5a821-102">LINQ to XML kullanarak XML verilerini işleme</span><span class="sxs-lookup"><span data-stu-id="5a821-102">Process XML Data Using LINQ to XML</span></span>
<span data-ttu-id="5a821-103">LINQ to XML, .NET Framework sürüm 3.5 XML verilerini işlemek için yeni modelidir.</span><span class="sxs-lookup"><span data-stu-id="5a821-103">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="5a821-104">LINQ to XML XML verileri ile beklediği her şeyi yapmak geliştiricilerinin sağlayan: sorgulama, değiştirme, oluşturma, kaydetme ve XML belgeleri seri hale getirme.</span><span class="sxs-lookup"><span data-stu-id="5a821-104">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="5a821-105">Gerçek avantajları, sorgu ve oluşturma özellikleri yer.</span><span class="sxs-lookup"><span data-stu-id="5a821-105">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="5a821-106">LINQ to XML sorgularında birleştiren ve ifadesel XPath veya XQuery SQL'e benzeyen daha söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="5a821-106">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="5a821-107">Sorgu sonuçları öğeler veya öznitelikleri koleksiyonu döndürülür ve XElement nesneleri için parametre olarak kullanılabilir olduğundan, XML ağaçlarını kolayca bir şekilden diğerine dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="5a821-107">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="5a821-108">LINQ to XML .NET Framework sürüm 3.5 için dil ile tümleşik sorgu (LINQ) teknolojileri yararlanır.</span><span class="sxs-lookup"><span data-stu-id="5a821-108">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="5a821-109">LINQ dili söz dizimini C# ve Visual Basic potansiyel olarak tüm veri deposuna ilave güçlü sorgu özellikleri sağlamak üzere genişletir.</span><span class="sxs-lookup"><span data-stu-id="5a821-109">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="5a821-110">Kullanımı hakkında ayrıntılı bilgi için bkz: [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="5a821-110">For a detailed discussion of its use, see [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="5a821-111">LINQ framework genel bakış için bkz. [dil ile tümleşik sorgu (LINQ) - C# ](../../../csharp/programming-guide/concepts/linq/index.md) veya [dil ile tümleşik sorgu (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="5a821-111">For an overview of the LINQ framework, see [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a821-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a821-112">See also</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Linq>
- [<span data-ttu-id="5a821-113">LINQ to XML ile DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="5a821-113">LINQ to XML vs. DOM (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="5a821-114">LINQ to XML ile DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a821-114">LINQ to XML vs. DOM (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="5a821-115">LINQ to XML ile Diğer XML teknolojileri karşılaştırması (C#)</span><span class="sxs-lookup"><span data-stu-id="5a821-115">LINQ to XML vs. Other XML Technologies (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
- [<span data-ttu-id="5a821-116">LINQ to XML ile Diğer XML teknolojileri karşılaştırması (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a821-116">LINQ to XML vs. Other XML Technologies (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
