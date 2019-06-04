---
title: LINQ to Objects'in (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: c66a818d48316279817fdc6b7919a7667b6b8eb8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484470"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="b4924-102">LINQ to Objects'in (C#)</span><span class="sxs-lookup"><span data-stu-id="b4924-102">LINQ to Objects (C#)</span></span>
<span data-ttu-id="b4924-103">Tüm sorgular "LINQ için nesneler" LINQ kullanımı ifade eder <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601> koleksiyon Ara LINQ sağlayıcısı veya API gibi kullanmadan, doğrudan [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md) veya [LINQ to XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b4924-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md) or [LINQ to XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md).</span></span> <span data-ttu-id="b4924-104">LINQ gibi herhangi bir sıralanabilir koleksiyonu sorgulamak için kullanabileceğiniz <xref:System.Collections.Generic.List%601>, <xref:System.Array>, veya <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="b4924-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="b4924-105">Koleksiyon veya bir .NET Framework API tarafından döndürülen kullanıcı tanımlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b4924-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="b4924-106">Temel bir anlamda, LINQ to Objects'in koleksiyonları yeni bir yaklaşımı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b4924-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="b4924-107">Karmaşık yazmanız gerekirdi eski biçimde `foreach` belirtilen bir koleksiyondaki verileri alma döngüleri.</span><span class="sxs-lookup"><span data-stu-id="b4924-107">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="b4924-108">LINQ yaklaşımda almak istediğiniz açıklayan bildirim temelli bir kod yazın.</span><span class="sxs-lookup"><span data-stu-id="b4924-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="b4924-109">Ayrıca, LINQ sorguları üç ana avantajları geleneksel teklif `foreach` döngüleri:</span><span class="sxs-lookup"><span data-stu-id="b4924-109">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
1. <span data-ttu-id="b4924-110">Özellikle birden çok koşulu filtrelerken daha kısa süren ve okunabilir, değildirler.</span><span class="sxs-lookup"><span data-stu-id="b4924-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="b4924-111">Güçlü filtreleme, sıralama ve Gruplama yetenekler uygulama kodu en az sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="b4924-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="b4924-112">Bunlar çok az kayıpla veya hiç değişiklik diğer veri kaynaklarıyla için unity'nin.</span><span class="sxs-lookup"><span data-stu-id="b4924-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="b4924-113">Genel olarak, daha karmaşık fark geleneksel yineleme teknikleri yerine LINQ kullanarak daha fazla avantaj, verilerle ilgili gerçekleştirmek istediğiniz işlem.</span><span class="sxs-lookup"><span data-stu-id="b4924-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="b4924-114">Bu bölümün amacı, select bazı örnekler LINQ yaklaşımıyla göstermektir.</span><span class="sxs-lookup"><span data-stu-id="b4924-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="b4924-115">Testin daha kapsamlı olmasını sağlamak için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="b4924-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4924-116">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b4924-116">In This Section</span></span>  
 [<span data-ttu-id="b4924-117">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="b4924-117">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 <span data-ttu-id="b4924-118">LINQ Sorgu dizeleri ve dizelerden oluşan koleksiyonları dönüştürmek için nasıl kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b4924-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="b4924-119">Ayrıca, bu ilkeyi gösteren konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="b4924-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="b4924-120">LINQ ve yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="b4924-120">LINQ and Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-reflection.md)  
 <span data-ttu-id="b4924-121">LINQ yansıma nasıl kullandığını gösteren bir örnek bağlar.</span><span class="sxs-lookup"><span data-stu-id="b4924-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="b4924-122">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b4924-122">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 <span data-ttu-id="b4924-123">Dosya sistemleri ile etkileşimde bulunmak için LINQ'ın nasıl kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b4924-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="b4924-124">Ayrıca bu kavramları göstermeye konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="b4924-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="b4924-125">Nasıl yapılır: LINQ ile ArrayList sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="b4924-125">How to: Query an ArrayList with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="b4924-126">C# ArrayList sorgulama işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b4924-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="b4924-127">Nasıl yapılır: LINQ sorguları için özel yöntemler ekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="b4924-127">How to: Add Custom Methods for LINQ Queries (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="b4924-128">İçin genişletme yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz yöntemler kümesi genişletmek açıklanmaktadır <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b4924-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="b4924-129">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b4924-129">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="b4924-130">LINQ açıklamak ve sorguları gerçekleştirme kod örnekleri sağlayan konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b4924-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
