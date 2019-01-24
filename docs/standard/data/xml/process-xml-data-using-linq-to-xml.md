---
title: LINQ to XML kullanarak XML verilerini işleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 059d6b9d-63f7-4011-9ba8-8406f0bbae7d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 634c76c3510d594584f06ea14bed84b1b0423c31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502188"
---
# <a name="process-xml-data-using-linq-to-xml"></a><span data-ttu-id="d7dd4-102">LINQ to XML kullanarak XML verilerini işleme</span><span class="sxs-lookup"><span data-stu-id="d7dd4-102">Process XML Data Using LINQ to XML</span></span>
<span data-ttu-id="d7dd4-103">LINQ to XML, .NET Framework sürüm 3.5 XML verilerini işlemek için yeni modelidir.</span><span class="sxs-lookup"><span data-stu-id="d7dd4-103">LINQ to XML is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="d7dd4-104">LINQ to XML XML verileri ile beklediği her şeyi yapmak geliştiricilerinin sağlayan: sorgulama, değiştirme, oluşturma, kaydetme ve XML belgeleri seri hale getirme.</span><span class="sxs-lookup"><span data-stu-id="d7dd4-104">LINQ to XML allows developers to do everything they would expect with XML data: querying, modifying, creating, saving, and serializing XML documents.</span></span> <span data-ttu-id="d7dd4-105">Gerçek avantajları, sorgu ve oluşturma özellikleri yer.</span><span class="sxs-lookup"><span data-stu-id="d7dd4-105">The real advantages lie in the query and creation capabilities.</span></span>  
  
 <span data-ttu-id="d7dd4-106">LINQ to XML sorgularında birleştiren ve ifadesel XPath veya XQuery SQL'e benzeyen daha söz dizimini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="d7dd4-106">Queries in LINQ to XML are succinct and expressive, using syntax more similar to SQL than to XPath or XQuery.</span></span> <span data-ttu-id="d7dd4-107">Sorgu sonuçları öğeler veya öznitelikleri koleksiyonu döndürülür ve XElement nesneleri için parametre olarak kullanılabilir olduğundan, XML ağaçlarını kolayca bir şekilden diğerine dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="d7dd4-107">Because query results can be returned as collections of elements or attributes and can be used as parameters for XElement objects, XML trees can be easily transformed from one shape to another.</span></span>  
  
 <span data-ttu-id="d7dd4-108">LINQ to XML .NET Framework sürüm 3.5 için dil ile tümleşik sorgu (LINQ) teknolojileri yararlanır.</span><span class="sxs-lookup"><span data-stu-id="d7dd4-108">LINQ to XML leverages the language-integrated query (LINQ) technology in the .NET Framework version 3.5.</span></span> <span data-ttu-id="d7dd4-109">LINQ dili söz dizimini C# ve Visual Basic potansiyel olarak tüm veri deposuna ilave güçlü sorgu özellikleri sağlamak üzere genişletir.</span><span class="sxs-lookup"><span data-stu-id="d7dd4-109">LINQ extends the language syntax of C# and Visual Basic to provide powerful query capabilities that can be extended to potentially any data store.</span></span>  
  
 <span data-ttu-id="d7dd4-110">Bkz: [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) bakın ve kullanımı hakkında ayrıntılı bilgi için [LINQ (dil ile tümleşik sorgu)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) LINQ framework genel bakış.</span><span class="sxs-lookup"><span data-stu-id="d7dd4-110">See [LINQ to XML](https://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) for a detailed discussion of its use, and see [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) for an overview of the LINQ framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7dd4-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7dd4-111">See also</span></span>

- <xref:System.Xml.Linq>
- <xref:System.Linq>
- [<span data-ttu-id="d7dd4-112">LINQ to XML ile DOM Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="d7dd4-112">LINQ to XML vs. DOM</span></span>](https://msdn.microsoft.com/library/19b5ed02-feb2-455a-8897-f7f0fd76aca3)
- [<span data-ttu-id="d7dd4-113">LINQ to XML ile Diğer XML Teknolojileri Karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="d7dd4-113">LINQ to XML vs. Other XML Technologies</span></span>](https://msdn.microsoft.com/library/7ba1eecf-f09a-42de-bc80-22ca5b2e42d3)
