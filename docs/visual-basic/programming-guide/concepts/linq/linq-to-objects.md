---
title: Nesnelere LINQ
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: cb277a255151bf7db9d0fb0a50605ee07ba1423f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075297"
---
# <a name="linq-to-objects-visual-basic"></a><span data-ttu-id="c4115-102">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4115-102">LINQ to Objects (Visual Basic)</span></span>

<span data-ttu-id="c4115-103">"LINQ to Objects" terimi, <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> bır ara LINQ sağlayıcısı veya [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) veya [LINQ to XML](../../../../standard/linq/linq-xml-overview.md)gibi API KULLANıLMADAN doğrudan herhangi bir veya koleksiyonuyla LINQ sorgularının kullanımını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="c4115-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](../../../../standard/linq/linq-xml-overview.md).</span></span> <span data-ttu-id="c4115-104">, Veya gibi tüm sıralanabilir koleksiyonları sorgulamak için LINQ kullanabilirsiniz <xref:System.Collections.Generic.List%601> <xref:System.Array> <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="c4115-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="c4115-105">Koleksiyon Kullanıcı tanımlı olabilir veya bir .NET Framework API 'SI tarafından döndürülen olabilir.</span><span class="sxs-lookup"><span data-stu-id="c4115-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="c4115-106">Temel anlamda, LINQ to Objects koleksiyonlara yönelik yeni bir yaklaşımı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c4115-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="c4115-107">Eski şekilde, `For Each` bir koleksiyondan verilerin nasıl alınacağını belirtilen karmaşık döngüler yazmanız gerekiyordu.</span><span class="sxs-lookup"><span data-stu-id="c4115-107">In the old way, you had to write complex `For Each` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="c4115-108">LINQ yaklaşımında, almak istediklerinizi açıklayan bildirim kodu yazarsınız.</span><span class="sxs-lookup"><span data-stu-id="c4115-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="c4115-109">Ayrıca, LINQ sorguları geleneksel Döngülerde üç temel avantaj sunar `For Each` :</span><span class="sxs-lookup"><span data-stu-id="c4115-109">In addition, LINQ queries offer three main advantages over traditional `For Each` loops:</span></span>  
  
1. <span data-ttu-id="c4115-110">Özellikle birden fazla koşula filtre uygulanırken bunlar daha kısa ve okunabilir.</span><span class="sxs-lookup"><span data-stu-id="c4115-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="c4115-111">En az uygulama kodu ile güçlü filtreleme, sıralama ve gruplama özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4115-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="c4115-112">Bunlar, çok az değişiklik yapmadan diğer veri kaynaklarına da eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="c4115-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="c4115-113">Genel olarak, veriler üzerinde gerçekleştirmek istediğiniz işlem daha karmaşıktır, geleneksel yineleme teknikleri yerine LINQ kullanarak bunu daha fazla avantaj elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="c4115-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="c4115-114">Bu bölümün amacı, bazı Select örnekleri ile LINQ yaklaşımını göstermektir.</span><span class="sxs-lookup"><span data-stu-id="c4115-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="c4115-115">Bu, kapsamlı olmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="c4115-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c4115-116">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c4115-116">In This Section</span></span>  

 [<span data-ttu-id="c4115-117">LINQ ve dizeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4115-117">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)  
 <span data-ttu-id="c4115-118">LINQ 'in dizeleri ve dize koleksiyonlarını sorgulamak ve dönüştürmek için nasıl kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c4115-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="c4115-119">Ayrıca, bu ilkeleri gösteren konuların bağlantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="c4115-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="c4115-120">LINQ ve yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4115-120">LINQ and Reflection (Visual Basic)</span></span>](linq-and-reflection.md)  
 <span data-ttu-id="c4115-121">LINQ 'in yansıma kullanımını gösteren bir örneğe bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="c4115-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="c4115-122">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4115-122">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)  
 <span data-ttu-id="c4115-123">LINQ 'in dosya sistemleriyle etkileşime geçmek için nasıl kullanılabileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c4115-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="c4115-124">Ayrıca, bu kavramları gösteren konuların bağlantılarını içerir.</span><span class="sxs-lookup"><span data-stu-id="c4115-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="c4115-125">Nasıl yapılır: LINQ ile ArrayList 'i sorgulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4115-125">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="c4115-126">C# içinde ArrayList 'in nasıl sorgulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4115-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="c4115-127">Nasıl yapılır: LINQ sorguları için özel yöntemler ekleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4115-127">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>](how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="c4115-128">Arabirime uzantı yöntemleri ekleyerek, LINQ sorguları için kullanabileceğiniz yöntemlerin kümesinin nasıl genişletileceğini açıklar <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="c4115-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="c4115-129">Dil ile tümleşik sorgu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4115-129">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)  
 <span data-ttu-id="c4115-130">LINQ ' i açıklayan ve sorguları gerçekleştiren koda örnek sağlayan konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="c4115-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
