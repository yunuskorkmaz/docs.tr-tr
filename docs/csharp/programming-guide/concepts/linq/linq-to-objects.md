---
title: LINQ to nesneler (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 089db6be5163b9da34dae89229abeb9ca7144e76
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="86ccd-102">LINQ to nesneler (C#)</span><span class="sxs-lookup"><span data-stu-id="86ccd-102">LINQ to Objects (C#)</span></span>
<span data-ttu-id="86ccd-103">"Nesnelere LINQ" başvuruyor LINQ kullanımını terim tüm sorgular <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601> koleksiyonu veya bir ara LINQ sağlayıcısı gibi API kullanmadan, doğrudan [LINQ-SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md) veya [LINQ-XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span><span class="sxs-lookup"><span data-stu-id="86ccd-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md) or [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span> <span data-ttu-id="86ccd-104">LINQ numaralandırılabilir tüm koleksiyonlar gibi sorgulamak için kullanabileceğiniz <xref:System.Collections.Generic.List%601>, <xref:System.Array>, veya <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="86ccd-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="86ccd-105">Koleksiyon, kullanıcı tanımlı olabilir veya bir .NET Framework API tarafından döndürülen.</span><span class="sxs-lookup"><span data-stu-id="86ccd-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="86ccd-106">Bir temel anlamda nesnelere LINQ koleksiyonlar için yeni bir yaklaşım temsil eder.</span><span class="sxs-lookup"><span data-stu-id="86ccd-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="86ccd-107">Karmaşık yazma gerekiyordu eski biçimde `foreach` koleksiyondan verileri almak üzere nasıl belirtilen döngüler.</span><span class="sxs-lookup"><span data-stu-id="86ccd-107">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="86ccd-108">LINQ yaklaşımda, almak istediğiniz açıklar bildirim temelli bir kod yazın.</span><span class="sxs-lookup"><span data-stu-id="86ccd-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="86ccd-109">Ayrıca, üç ana avantajları geleneksel LINQ sorgularını teklif `foreach` döngüler:</span><span class="sxs-lookup"><span data-stu-id="86ccd-109">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
1.  <span data-ttu-id="86ccd-110">Bunlar özellikle birden çok koşul filtre uygularken daha kısa ve okunabilir,.</span><span class="sxs-lookup"><span data-stu-id="86ccd-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2.  <span data-ttu-id="86ccd-111">Güçlü filtreleme, sıralama ve uygulama kodu en az özellikleriyle gruplandırma sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="86ccd-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3.  <span data-ttu-id="86ccd-112">Bunlar çok az kayıpla veya hiç değişiklik ile diğer veri kaynakları için bağlantı noktası kurulmuş.</span><span class="sxs-lookup"><span data-stu-id="86ccd-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="86ccd-113">Genel olarak, daha karmaşık hayata geçirmek yerine geleneksel yineleme teknikleri LINQ kullanarak daha fazla avantajı, veriler üzerinde gerçekleştirmek istediğiniz işlem.</span><span class="sxs-lookup"><span data-stu-id="86ccd-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="86ccd-114">Bu bölümün amacı select bazı örnekler LINQ yaklaşımda göstermektir.</span><span class="sxs-lookup"><span data-stu-id="86ccd-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="86ccd-115">Kapsamlı olması amaçlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="86ccd-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86ccd-116">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="86ccd-116">In This Section</span></span>  
 [<span data-ttu-id="86ccd-117">LINQ ve dizeler (C#)</span><span class="sxs-lookup"><span data-stu-id="86ccd-117">LINQ and Strings (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-strings.md)  
 <span data-ttu-id="86ccd-118">LINQ Sorgu ve dizeler ve koleksiyonları dizeleri dönüştürmek için nasıl kullanılabileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="86ccd-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="86ccd-119">Ayrıca bu ilkeler göstermek konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="86ccd-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="86ccd-120">LINQ ve yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="86ccd-120">LINQ and Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-reflection.md)  
 <span data-ttu-id="86ccd-121">LINQ yansıma nasıl kullandığını gösteren bir örnek bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="86ccd-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="86ccd-122">LINQ ve dosya dizinleri (C#)</span><span class="sxs-lookup"><span data-stu-id="86ccd-122">LINQ and File Directories (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-file-directories.md)  
 <span data-ttu-id="86ccd-123">LINQ dosya sistemleri ile etkileşim kurmak için nasıl kullanılabileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="86ccd-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="86ccd-124">Ayrıca bu kavramları göstermeye konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="86ccd-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="86ccd-125">Nasıl yapılır: LINQ (C#) ile ArrayList sorgulama</span><span class="sxs-lookup"><span data-stu-id="86ccd-125">How to: Query an ArrayList with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="86ccd-126">C# ArrayList sorgulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="86ccd-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="86ccd-127">Nasıl yapılır: LINQ sorguları için (C#) özel yöntemler ekleme</span><span class="sxs-lookup"><span data-stu-id="86ccd-127">How to: Add Custom Methods for LINQ Queries (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="86ccd-128">İçin genişletme yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz yöntemler kümesi genişletmek açıklanmaktadır <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="86ccd-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="86ccd-129">Dil ile tümleşik sorgu (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="86ccd-129">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="86ccd-130">LINQ açıklayan ve sorgular gerçekleştirebilir kod örnekleri sağlayın konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="86ccd-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
