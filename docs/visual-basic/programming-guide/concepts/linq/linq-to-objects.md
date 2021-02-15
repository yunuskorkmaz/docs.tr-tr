---
description: 'Hakkında daha fazla bilgi edinin: LINQ to Objects (Visual Basic)'
title: Nesnelere LINQ
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: 50f04c77579595cc78ed43d04e0547eb15f91dc3
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464774"
---
# <a name="linq-to-objects-visual-basic"></a><span data-ttu-id="8311d-103">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8311d-103">LINQ to Objects (Visual Basic)</span></span>

<span data-ttu-id="8311d-104">"LINQ to Objects" terimi, <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> bır ara LINQ sağlayıcısı veya [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) veya [LINQ to XML](../../../../standard/linq/linq-xml-overview.md)gibi API KULLANıLMADAN doğrudan herhangi bir veya koleksiyonuyla LINQ sorgularının kullanımını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="8311d-104">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](../../../../standard/linq/linq-xml-overview.md).</span></span> <span data-ttu-id="8311d-105">, Veya gibi tüm sıralanabilir koleksiyonları sorgulamak için LINQ kullanabilirsiniz <xref:System.Collections.Generic.List%601> <xref:System.Array> <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="8311d-105">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="8311d-106">Koleksiyon Kullanıcı tanımlı olabilir veya bir .NET Framework API 'SI tarafından döndürülen olabilir.</span><span class="sxs-lookup"><span data-stu-id="8311d-106">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="8311d-107">Temel anlamda, LINQ to Objects koleksiyonlara yönelik yeni bir yaklaşımı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8311d-107">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="8311d-108">Eski şekilde, `For Each` bir koleksiyondan verilerin nasıl alınacağını belirtilen karmaşık döngüler yazmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="8311d-108">In the old way, you had to write complex `For Each` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="8311d-109">LINQ yaklaşımında, almak istediklerinizi açıklayan bildirim kodu yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="8311d-109">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="8311d-110">Ayrıca, LINQ sorguları geleneksel Döngülerde üç temel avantaj sunar `For Each` :</span><span class="sxs-lookup"><span data-stu-id="8311d-110">In addition, LINQ queries offer three main advantages over traditional `For Each` loops:</span></span>  
  
1. <span data-ttu-id="8311d-111">Özellikle birden fazla koşula filtre uygulanırken bunlar daha kısa ve okunabilir.</span><span class="sxs-lookup"><span data-stu-id="8311d-111">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="8311d-112">En az uygulama kodu ile güçlü filtreleme, sıralama ve gruplama özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="8311d-112">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="8311d-113">Bunlar, çok az değişiklik yapmadan diğer veri kaynaklarına da eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8311d-113">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="8311d-114">Genel olarak, veriler üzerinde gerçekleştirmek istediğiniz işlem daha karmaşıktır, geleneksel yineleme teknikleri yerine LINQ kullanarak bunu daha fazla avantaj elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="8311d-114">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="8311d-115">Bu bölümün amacı, bazı Select örnekleri ile LINQ yaklaşımını göstermektir.</span><span class="sxs-lookup"><span data-stu-id="8311d-115">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="8311d-116">Bu, kapsamlı olmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="8311d-116">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8311d-117">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8311d-117">In This Section</span></span>  

 [<span data-ttu-id="8311d-118">LINQ ve dizeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8311d-118">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)  
 <span data-ttu-id="8311d-119">LINQ 'in dizeleri ve dize koleksiyonlarını sorgulamak ve dönüştürmek için nasıl kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8311d-119">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="8311d-120">Ayrıca, bu ilkeleri gösteren konuların bağlantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="8311d-120">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="8311d-121">LINQ ve yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8311d-121">LINQ and Reflection (Visual Basic)</span></span>](linq-and-reflection.md)  
 <span data-ttu-id="8311d-122">LINQ 'in yansıma kullanımını gösteren bir örneğe bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="8311d-122">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="8311d-123">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8311d-123">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)  
 <span data-ttu-id="8311d-124">LINQ 'in dosya sistemleriyle etkileşime geçmek için nasıl kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8311d-124">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="8311d-125">Ayrıca, bu kavramları gösteren konuların bağlantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="8311d-125">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="8311d-126">Nasıl yapılır: LINQ ile ArrayList 'i sorgulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8311d-126">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="8311d-127">C# içinde ArrayList 'in nasıl sorgulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8311d-127">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="8311d-128">Nasıl yapılır: LINQ sorguları için özel yöntemler ekleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8311d-128">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>](how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="8311d-129">Arabirime uzantı yöntemleri ekleyerek, LINQ sorguları için kullanabileceğiniz yöntemlerin kümesinin nasıl genişletileceğini açıklar <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="8311d-129">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="8311d-130">Dil ile tümleşik sorgu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8311d-130">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)  
 <span data-ttu-id="8311d-131">LINQ ' i açıklayan ve sorguları gerçekleştiren koda örnek sağlayan konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="8311d-131">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
