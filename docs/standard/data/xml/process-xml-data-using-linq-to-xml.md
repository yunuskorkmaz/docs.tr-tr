---
title: LINQ to XML Kullanarak XML Verilerini İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
ms.openlocfilehash: 5afa9fc84b7f41023eceb5c0734b0667dc55514e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556505"
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="e2d89-102">LINQ to XML Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="e2d89-102">Process XML Data Using LINQ to XML</span></span>
<span data-ttu-id="e2d89-103">LINQ to XML, XML verilerini işlemek için .NET Framework sürüm 3,5 ' deki yeni bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="e2d89-103">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="e2d89-104">LINQ to XML, geliştiricilerin XML verileri ile bekledikleri her şeyi yapmasına izin verir: XML belgelerini sorgulama, değiştirme, oluşturma, kaydetme ve serileştirme.</span><span class="sxs-lookup"><span data-stu-id="e2d89-104">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="e2d89-105">Gerçek avantajlar sorgu ve oluşturma özellikleri ' nde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="e2d89-105">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="e2d89-106">LINQ to XML sorguları, SQL 'e daha benzer bir sözdizimi kullanılarak XPath veya XQuery ile kısa ve ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="e2d89-106">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="e2d89-107">Sorgu sonuçları öğe veya özniteliklerin koleksiyonları olarak döndürülebildiğinden ve XElement nesneleri için parametre olarak kullanılabileceği için, XML ağaçları bir şekilden diğerine kolayca dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="e2d89-107">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="e2d89-108">LINQ to XML, .NET Framework sürüm 3,5 ' de dil tümleşik sorgu (LINQ) teknolojisinden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="e2d89-108">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="e2d89-109">LINQ, büyük olasılıkla herhangi bir veri deposuna genişletilebilen güçlü sorgu özellikleri sağlamak için C# ve Visual Basic dil sözdizimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="e2d89-109">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="e2d89-110">Kullanımıyla ilgili ayrıntılı bir tartışma için bkz. [LINQ to XML (C#)](../../linq/linq-xml-overview.md) ve [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e2d89-110">For a detailed discussion of its use, see [LINQ to XML (C#)](../../linq/linq-xml-overview.md) and [LINQ to XML (Visual Basic)](../../linq/linq-xml-overview.md).</span></span> <span data-ttu-id="e2d89-111">LINQ Framework 'e genel bir bakış için bkz. [dil Ile tümleşik sorgu (LINQ)-C#](../../../csharp/programming-guide/concepts/linq/index.md) veya [dil ile TÜMLEŞIK sorgu (lınq)-Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="e2d89-111">For an overview of the LINQ framework, see [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2d89-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2d89-112">See also</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Linq>
- [<span data-ttu-id="e2d89-113">LINQ to XML vs. DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="e2d89-113">LINQ to XML vs. DOM (C#)</span></span>](../../linq/linq-xml-vs-dom.md)
- [<span data-ttu-id="e2d89-114">LINQ to XML vs DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2d89-114">LINQ to XML vs. DOM (Visual Basic)</span></span>](../../linq/linq-xml-vs-dom.md)
- [<span data-ttu-id="e2d89-115">LINQ to XML ile diğer XML Teknolojileri (C#)</span><span class="sxs-lookup"><span data-stu-id="e2d89-115">LINQ to XML vs. Other XML Technologies (C#)</span></span>](../../linq/linq-xml-vs-xml-technologies.md)
- [<span data-ttu-id="e2d89-116">LINQ to XML ile diğer XML Teknolojileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2d89-116">LINQ to XML vs. Other XML Technologies (Visual Basic)</span></span>](../../linq/linq-xml-vs-xml-technologies.md)
