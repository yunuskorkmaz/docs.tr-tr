---
title: LINQ to nesneler (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c2a48e792c656a84c07730b67f734f6b539ab97d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="linq-to-objects-visual-basic"></a><span data-ttu-id="b2e2f-102">LINQ to nesneler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2e2f-102">LINQ to Objects (Visual Basic)</span></span>
<span data-ttu-id="b2e2f-103">"Nesnelere LINQ" başvuruyor LINQ kullanımını terim tüm sorgular <xref:System.Collections.IEnumerable> veya <xref:System.Collections.Generic.IEnumerable%601> koleksiyonu veya bir ara LINQ sağlayıcısı gibi API kullanmadan, doğrudan [LINQ-SQL](../../../../framework/data/adonet/sql/linq/index.md) veya [LINQ-XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span><span class="sxs-lookup"><span data-stu-id="b2e2f-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span> <span data-ttu-id="b2e2f-104">LINQ numaralandırılabilir tüm koleksiyonlar gibi sorgulamak için kullanabileceğiniz <xref:System.Collections.Generic.List%601>, <xref:System.Array>, veya <xref:System.Collections.Generic.Dictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="b2e2f-105">Koleksiyon, kullanıcı tanımlı olabilir veya bir .NET Framework API tarafından döndürülen.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-105">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="b2e2f-106">Bir temel anlamda nesnelere LINQ koleksiyonlar için yeni bir yaklaşım temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="b2e2f-107">Karmaşık yazma gerekiyordu eski biçimde `For Each` koleksiyondan verileri almak üzere nasıl belirtilen döngüler.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-107">In the old way, you had to write complex `For Each` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="b2e2f-108">LINQ yaklaşımda, almak istediğiniz açıklar bildirim temelli bir kod yazın.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="b2e2f-109">Ayrıca, üç ana avantajları geleneksel LINQ sorgularını teklif `For Each` döngüler:</span><span class="sxs-lookup"><span data-stu-id="b2e2f-109">In addition, LINQ queries offer three main advantages over traditional `For Each` loops:</span></span>  
  
1.  <span data-ttu-id="b2e2f-110">Bunlar özellikle birden çok koşul filtre uygularken daha kısa ve okunabilir,.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2.  <span data-ttu-id="b2e2f-111">Güçlü filtreleme, sıralama ve uygulama kodu en az özellikleriyle gruplandırma sağlarlar.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3.  <span data-ttu-id="b2e2f-112">Bunlar çok az kayıpla veya hiç değişiklik ile diğer veri kaynakları için bağlantı noktası kurulmuş.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="b2e2f-113">Genel olarak, daha karmaşık hayata geçirmek yerine geleneksel yineleme teknikleri LINQ kullanarak daha fazla avantajı, veriler üzerinde gerçekleştirmek istediğiniz işlem.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-113">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="b2e2f-114">Bu bölümün amacı select bazı örnekler LINQ yaklaşımda göstermektir.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="b2e2f-115">Kapsamlı olması amaçlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-115">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2e2f-116">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b2e2f-116">In This Section</span></span>  
 [<span data-ttu-id="b2e2f-117">LINQ ve dizeler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2e2f-117">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)  
 <span data-ttu-id="b2e2f-118">LINQ Sorgu ve dizeler ve koleksiyonları dizeleri dönüştürmek için nasıl kullanılabileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="b2e2f-119">Ayrıca bu ilkeler göstermek konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-119">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="b2e2f-120">LINQ ve yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2e2f-120">LINQ and Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-reflection.md)  
 <span data-ttu-id="b2e2f-121">LINQ yansıma nasıl kullandığını gösteren bir örnek bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="b2e2f-122">LINQ ve dosya dizinleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2e2f-122">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)  
 <span data-ttu-id="b2e2f-123">LINQ dosya sistemleri ile etkileşim kurmak için nasıl kullanılabileceği açıklanır.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="b2e2f-124">Ayrıca bu kavramları göstermeye konulara bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-124">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="b2e2f-125">Nasıl yapılır: LINQ (Visual Basic) ile ArrayList sorgulama</span><span class="sxs-lookup"><span data-stu-id="b2e2f-125">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="b2e2f-126">C# ArrayList sorgulama gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="b2e2f-127">Nasıl yapılır: özel yöntemler ekleme LINQ sorgularını (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2e2f-127">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="b2e2f-128">İçin genişletme yöntemleri ekleyerek LINQ sorguları için kullanabileceğiniz yöntemler kümesi genişletmek açıklanmaktadır <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="b2e2f-129">Dil ile tümleşik sorgu (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2e2f-129">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="b2e2f-130">LINQ açıklayan ve sorgular gerçekleştirebilir kod örnekleri sağlayın konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2e2f-130">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
