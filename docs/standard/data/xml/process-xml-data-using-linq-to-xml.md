---
title: LINQ to XML Kullanarak XML Verilerini İşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e4e8e4a826fda20a39576ca78259bb7b389bbf75
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424446"
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="f4c27-102">LINQ to XML Kullanarak XML Verilerini İşleme</span><span class="sxs-lookup"><span data-stu-id="f4c27-102">Process XML Data Using LINQ to XML</span></span>
<span data-ttu-id="f4c27-103">LINQ to XML, XML verilerini işlemek için .NET Framework sürüm 3,5 ' deki yeni bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="f4c27-103">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="f4c27-104">LINQ to XML, geliştiricilerin XML verileri ile bekledikleri her şeyi yapmasına izin verir: XML belgelerini sorgulama, değiştirme, oluşturma, kaydetme ve serileştirme.</span><span class="sxs-lookup"><span data-stu-id="f4c27-104">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="f4c27-105">Gerçek avantajlar sorgu ve oluşturma özellikleri ' nde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="f4c27-105">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="f4c27-106">LINQ to XML sorguları, SQL 'e daha benzer bir sözdizimi kullanılarak XPath veya XQuery ile kısa ve ifade edilir.</span><span class="sxs-lookup"><span data-stu-id="f4c27-106">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="f4c27-107">Sorgu sonuçları öğe veya özniteliklerin koleksiyonları olarak döndürülebildiğinden ve XElement nesneleri için parametre olarak kullanılabileceği için, XML ağaçları bir şekilden diğerine kolayca dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="f4c27-107">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="f4c27-108">LINQ to XML, .NET Framework sürüm 3,5 ' de dil tümleşik sorgu (LINQ) teknolojisinden yararlanır.</span><span class="sxs-lookup"><span data-stu-id="f4c27-108">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="f4c27-109">LINQ, büyük olasılıkla herhangi bir C# veri deposuna genişletilebilen güçlü sorgu özellikleri sağlamak için ve Visual Basic dil sözdizimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="f4c27-109">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="f4c27-110">Kullanımıyla ilgili ayrıntılı bir tartışma için bkz. [LINQ to XMLC#()](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) ve [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f4c27-110">For a detailed discussion of its use, see [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span> <span data-ttu-id="f4c27-111">LINQ Framework 'e genel bir bakış için bkz. [dil ile tümleşik sorgu (LINQ)- C# ](../../../csharp/programming-guide/concepts/linq/index.md) veya [dil ile tümleşik sorgu (LINQ)-Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="f4c27-111">For an overview of the LINQ framework, see [Language-Integrated Query (LINQ) - C#](../../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4c27-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4c27-112">See also</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Linq>
- [<span data-ttu-id="f4c27-113">LINQ to XML vs DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="f4c27-113">LINQ to XML vs. DOM (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="f4c27-114">LINQ to XML vs DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4c27-114">LINQ to XML vs. DOM (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="f4c27-115">LINQ to XML ile diğer XML Teknolojileri (C#)</span><span class="sxs-lookup"><span data-stu-id="f4c27-115">LINQ to XML vs. Other XML Technologies (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
- [<span data-ttu-id="f4c27-116">LINQ to XML ile diğer XML Teknolojileri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4c27-116">LINQ to XML vs. Other XML Technologies (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
