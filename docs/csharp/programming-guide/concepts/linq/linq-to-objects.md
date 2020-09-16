---
title: LINQ to Objects (C#)
description: <T>Bir ara LINQ sağlayıcısı veya API olmadan herhangi bir IEnumerable veya IEnumerable KOLEKSIYONUYLA LINQ sorguları kullanan C# ' de LINQ to Objects hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: f8e65f129dc002d9615b01e3a3a123514754b886
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557012"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="8afbd-103">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="8afbd-103">LINQ to Objects (C#)</span></span>

<span data-ttu-id="8afbd-104">"LINQ to Objects" terimi, <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> bır ara LINQ sağlayıcısı veya [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) veya [LINQ to XML](../../../../standard/linq/linq-xml-overview.md)gibi API KULLANıLMADAN doğrudan herhangi bir veya koleksiyonuyla LINQ sorgularının kullanımını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="8afbd-104">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](../../../../standard/linq/linq-xml-overview.md).</span></span> <span data-ttu-id="8afbd-105">, Veya gibi tüm sıralanabilir koleksiyonları sorgulamak için LINQ kullanabilirsiniz <xref:System.Collections.Generic.List%601> <xref:System.Array> <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="8afbd-105">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="8afbd-106">Koleksiyon Kullanıcı tanımlı olabilir veya bir .NET API 'SI tarafından döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="8afbd-106">The collection may be user-defined or may be returned by a .NET API.</span></span>  
  
 <span data-ttu-id="8afbd-107">Temel anlamda, LINQ to Objects koleksiyonlara yönelik yeni bir yaklaşımı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8afbd-107">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="8afbd-108">Eski şekilde, `foreach` bir koleksiyondan verilerin nasıl alınacağını belirtilen karmaşık döngüler yazmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="8afbd-108">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="8afbd-109">LINQ yaklaşımında, almak istediklerinizi açıklayan bildirim kodu yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="8afbd-109">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="8afbd-110">Ayrıca, LINQ sorguları geleneksel Döngülerde üç temel avantaj sunar `foreach` :</span><span class="sxs-lookup"><span data-stu-id="8afbd-110">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
- <span data-ttu-id="8afbd-111">Özellikle birden fazla koşula filtre uygulanırken bunlar daha kısa ve okunabilir.</span><span class="sxs-lookup"><span data-stu-id="8afbd-111">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
- <span data-ttu-id="8afbd-112">En az uygulama kodu ile güçlü filtreleme, sıralama ve gruplama özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8afbd-112">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
- <span data-ttu-id="8afbd-113">Bunlar, çok az değişiklik yapmadan diğer veri kaynaklarına da eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8afbd-113">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="8afbd-114">Genel olarak, veriler üzerinde gerçekleştirmek istediğiniz işlem daha karmaşıktır, geleneksel yineleme teknikleri yerine LINQ kullanarak bunu daha fazla avantaj elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="8afbd-114">In general, the more complex the operation you want to perform on the data, the more benefit you'll realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="8afbd-115">Bu bölümün amacı, bazı Select örnekleri ile LINQ yaklaşımını göstermektir.</span><span class="sxs-lookup"><span data-stu-id="8afbd-115">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="8afbd-116">Bu, kapsamlı olmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="8afbd-116">It's not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8afbd-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8afbd-117">In This Section</span></span>  
 [<span data-ttu-id="8afbd-118">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="8afbd-118">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)  
 <span data-ttu-id="8afbd-119">LINQ 'in dizeleri ve dize koleksiyonlarını sorgulamak ve dönüştürmek için nasıl kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8afbd-119">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="8afbd-120">Ayrıca, bu ilkeleri gösteren makalelerin bağlantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="8afbd-120">Also includes links to articles that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="8afbd-121">LINQ ve yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="8afbd-121">LINQ and Reflection (C#)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 <span data-ttu-id="8afbd-122">LINQ 'in yansıma kullanımını gösteren bir örneğe bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="8afbd-122">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="8afbd-123">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="8afbd-123">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)  
 <span data-ttu-id="8afbd-124">LINQ 'in dosya sistemleriyle etkileşime geçmek için nasıl kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8afbd-124">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="8afbd-125">Ayrıca, bu kavramları gösteren makalelerin bağlantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="8afbd-125">Also includes links to articles that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="8afbd-126">LINQ ile ArrayList 'i sorgulama (C#)</span><span class="sxs-lookup"><span data-stu-id="8afbd-126">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="8afbd-127">C# içinde ArrayList 'in nasıl sorgulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8afbd-127">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="8afbd-128">LINQ sorguları için özel yöntemler ekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="8afbd-128">How to add custom methods for LINQ queries (C#)</span></span>](./how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="8afbd-129">Arabirime uzantı yöntemleri ekleyerek, LINQ sorguları için kullanabileceğiniz yöntemlerin kümesinin nasıl genişletileceğini açıklar <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="8afbd-129">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="8afbd-130">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="8afbd-130">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)  
 <span data-ttu-id="8afbd-131">LINQ ' i açıklayan ve sorgu gerçekleştiren koda örnek sağlayan makalelere bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="8afbd-131">Provides links to articles that explain LINQ and provide examples of code that perform queries.</span></span>
