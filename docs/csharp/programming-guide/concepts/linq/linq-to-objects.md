---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: 8c0eb71fffdd29d9599d74c789a66ec7caf1faeb
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418172"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="b3a28-102">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="b3a28-102">LINQ to Objects (C#)</span></span>
<span data-ttu-id="b3a28-103">"LINQ to Objects" terimi, bir ara LINQ sağlayıcısının veya [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) veya [LINQ to XML](./linq-to-xml-overview.md)gibi API kullanılmadan doğrudan herhangi bir <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601> koleksiyonuyla LINQ sorgularının kullanımını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="b3a28-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](./linq-to-xml-overview.md).</span></span> <span data-ttu-id="b3a28-104"><xref:System.Collections.Generic.List%601>, <xref:System.Array>veya <xref:System.Collections.Generic.Dictionary%602>gibi herhangi bir sıralanabilir koleksiyonu sorgulamak için LINQ 'i kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3a28-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="b3a28-105">Koleksiyon Kullanıcı tanımlı olabilir veya bir .NET Framework API 'SI tarafından döndürülen olabilir.</span><span class="sxs-lookup"><span data-stu-id="b3a28-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="b3a28-106">Temel anlamda, LINQ to Objects koleksiyonlara yönelik yeni bir yaklaşımı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b3a28-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="b3a28-107">Eski şekilde, bir koleksiyondan verilerin nasıl alınacağını belirtilen karmaşık `foreach` döngüleri yazmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="b3a28-107">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="b3a28-108">LINQ yaklaşımında, almak istediklerinizi açıklayan bildirim kodu yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="b3a28-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="b3a28-109">Ayrıca, LINQ sorguları geleneksel `foreach` döngülerine göre üç temel avantaj sunar:</span><span class="sxs-lookup"><span data-stu-id="b3a28-109">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
1. <span data-ttu-id="b3a28-110">Özellikle birden fazla koşula filtre uygulanırken bunlar daha kısa ve okunabilir.</span><span class="sxs-lookup"><span data-stu-id="b3a28-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="b3a28-111">En az uygulama kodu ile güçlü filtreleme, sıralama ve gruplama özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3a28-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="b3a28-112">Bunlar, çok az değişiklik yapmadan diğer veri kaynaklarına da eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="b3a28-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="b3a28-113">Genel olarak, veriler üzerinde gerçekleştirmek istediğiniz işlem daha karmaşıktır, geleneksel yineleme teknikleri yerine LINQ kullanarak bunu daha fazla avantaj elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="b3a28-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="b3a28-114">Bu bölümün amacı, bazı Select örnekleri ile LINQ yaklaşımını göstermektir.</span><span class="sxs-lookup"><span data-stu-id="b3a28-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="b3a28-115">Bu, kapsamlı olmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="b3a28-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3a28-116">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b3a28-116">In This Section</span></span>  
 [<span data-ttu-id="b3a28-117">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="b3a28-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)  
 <span data-ttu-id="b3a28-118">LINQ 'in dizeleri ve dize koleksiyonlarını sorgulamak ve dönüştürmek için nasıl kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b3a28-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="b3a28-119">Ayrıca, bu ilkeleri gösteren konuların bağlantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b3a28-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="b3a28-120">LINQ ve yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="b3a28-120">LINQ and Reflection (C#)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 <span data-ttu-id="b3a28-121">LINQ 'in yansıma kullanımını gösteren bir örneğe bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="b3a28-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="b3a28-122">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="b3a28-122">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)  
 <span data-ttu-id="b3a28-123">LINQ 'in dosya sistemleriyle etkileşime geçmek için nasıl kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b3a28-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="b3a28-124">Ayrıca, bu kavramları gösteren konuların bağlantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="b3a28-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="b3a28-125">Nasıl yapılır: LINQ (C#) ile ArrayList 'i sorgulama</span><span class="sxs-lookup"><span data-stu-id="b3a28-125">How to: Query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="b3a28-126">İçinde C#ArrayList 'in nasıl sorgulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3a28-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="b3a28-127">Nasıl yapılır: LINQ sorguları için özel yöntemler ekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="b3a28-127">How to: Add Custom Methods for LINQ Queries (C#)</span></span>](./how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="b3a28-128"><xref:System.Collections.Generic.IEnumerable%601> arabirimine uzantı yöntemleri ekleyerek, LINQ sorguları için kullanabileceğiniz yöntemlerin kümesinin nasıl genişletileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b3a28-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="b3a28-129">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b3a28-129">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)  
 <span data-ttu-id="b3a28-130">LINQ ' i açıklayan ve sorguları gerçekleştiren koda örnek sağlayan konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3a28-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
