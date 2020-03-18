---
title: Nesnelere LINQ (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: ae4389aa1ce049edc71bff42c38f66fb328ba034
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344777"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="3cb06-102">Nesnelere LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="3cb06-102">LINQ to Objects (C#)</span></span>
<span data-ttu-id="3cb06-103">"LinQ to Objects" terimi, linq sorgularının doğrudan <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> herhangi bir veya koleksiyona sahip, bir ara LINQ sağlayıcısı veya [LINQ'dan SQL'e](../../../../framework/data/adonet/sql/linq/index.md) veya [LINQ'dan XML'e](./linq-to-xml-overview.md)API kullanmadan kullanılması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3cb06-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](./linq-to-xml-overview.md).</span></span> <span data-ttu-id="3cb06-104">Linq'i kullanarak <xref:System.Collections.Generic.List%601>, <xref:System.Array>, veya <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="3cb06-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="3cb06-105">Koleksiyon kullanıcı tarafından tanımlanabilir veya .NET Framework API tarafından döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="3cb06-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="3cb06-106">Temel anlamda LINQ to Objects koleksiyonlara yeni bir yaklaşımı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3cb06-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="3cb06-107">Eski şekilde, bir koleksiyondan `foreach` veri alma nın nasıl olduğunu belirten karmaşık döngüler yazmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="3cb06-107">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="3cb06-108">LINQ yaklaşımında, ne almak istediğinizi açıklayan bildirim kodu yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="3cb06-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="3cb06-109">Buna ek olarak, LINQ sorguları `foreach` geleneksel döngülere göre üç ana avantaj sunar:</span><span class="sxs-lookup"><span data-stu-id="3cb06-109">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
1. <span data-ttu-id="3cb06-110">Özellikle birden çok koşulu filtrelerken daha kısa ve okunabilirdirler.</span><span class="sxs-lookup"><span data-stu-id="3cb06-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="3cb06-111">En az uygulama koduyla güçlü filtreleme, sıralama ve gruplandırma özellikleri sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="3cb06-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="3cb06-112">Çok az değişiklik olmadan veya hiç değişiklik olmadan diğer veri kaynaklarına taşınabilirler.</span><span class="sxs-lookup"><span data-stu-id="3cb06-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="3cb06-113">Genel olarak, veriler üzerinde gerçekleştirmek istediğiniz işlem ne kadar karmaşıksa, geleneksel yineleme teknikleri yerine LINQ'u kullanarak o kadar çok fayda elde elabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cb06-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="3cb06-114">Bu bölümün amacı, LINQ yaklaşımını bazı belirli örneklerle göstermektir.</span><span class="sxs-lookup"><span data-stu-id="3cb06-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="3cb06-115">Bu ayrıntılı olması amaçlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="3cb06-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3cb06-116">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3cb06-116">In This Section</span></span>  
 [<span data-ttu-id="3cb06-117">LINQ ve Dizeleri (C#)</span><span class="sxs-lookup"><span data-stu-id="3cb06-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)  
 <span data-ttu-id="3cb06-118">LINQ dizeleri ve dizeleri koleksiyonları sorgulamak ve dönüştürmek için nasıl kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="3cb06-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="3cb06-119">Ayrıca bu ilkeleri gösteren konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="3cb06-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="3cb06-120">LINQ ve Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="3cb06-120">LINQ and Reflection (C#)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 <span data-ttu-id="3cb06-121">LINQ'un yansımayı nasıl kullandığını gösteren bir örneğe bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="3cb06-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="3cb06-122">LINQ ve Dosya Dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="3cb06-122">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)  
 <span data-ttu-id="3cb06-123">LINQ'nin dosya sistemleriyle etkileşimde bulunmak için nasıl kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="3cb06-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="3cb06-124">Ayrıca bu kavramları gösteren konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="3cb06-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="3cb06-125">LINQ (C#) ile ArrayList nasıl sorgulanır?</span><span class="sxs-lookup"><span data-stu-id="3cb06-125">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="3cb06-126">C#'da bir ArrayList'in nasıl sorgulanır olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3cb06-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="3cb06-127">LINQ sorguları için özel yöntemler ekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="3cb06-127">How to add custom methods for LINQ queries (C#)</span></span>](./how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="3cb06-128">Arabirime uzantı yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz yöntem <xref:System.Collections.Generic.IEnumerable%601> kümesini nasıl genişletebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="3cb06-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="3cb06-129">Dil-Tümleşik Sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3cb06-129">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)  
 <span data-ttu-id="3cb06-130">LINQ açıklayan ve sorguları gerçekleştiren kod örnekleri sağlayan konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cb06-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
