---
title: "Çalışma zamanında koşul filtrelerini dinamik olarak belirtme"
description: "Çalışma zamanında koşul filtrelerini dinamik olarak belirleme konusunda."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 06bc594ac1357e7dca6c182fa28310559a79875c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a><span data-ttu-id="9ecb4-104">Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="9ecb4-104">Dynamically specify predicate filters at runtime</span></span>

<span data-ttu-id="9ecb4-105">Bazı durumlarda, çalışma zamanına kadar sahip kaynak öğelerine uygulamak kaç tane doğrulamaları bilmiyorsanız `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-105">In some cases you do not know until run time how many predicates you have to apply to source elements in the `where` clause.</span></span> <span data-ttu-id="9ecb4-106">Birden çok koşul filtrelerini dinamik olarak belirtmek için bir yol kullanmaktır <xref:System.Linq.Enumerable.Contains%2A> aşağıdaki örnekte gösterildiği gibi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-106">One way to dynamically specify multiple predicate filters is to use the <xref:System.Linq.Enumerable.Contains%2A> method, as shown in the following example.</span></span> <span data-ttu-id="9ecb4-107">Örneğin, iki şekilde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-107">The example is constructed in two ways.</span></span> <span data-ttu-id="9ecb4-108">İlk olarak, projeyi programa sağlanan değerleri üzerinde filtreleme yaparak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-108">First, the project is run by filtering on values that are provided in the program.</span></span> <span data-ttu-id="9ecb4-109">Daha sonra projeyi yeniden çalışma zamanında sağlanan giriş kullanarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-109">Then the project is run again by using input provided at run time.</span></span>  
  
## <a name="to-filter-by-using-the-contains-method"></a><span data-ttu-id="9ecb4-110">Contains yöntemi kullanarak filtre uygulamak için</span><span class="sxs-lookup"><span data-stu-id="9ecb4-110">To filter by using the Contains method</span></span>  
  
1.  <span data-ttu-id="9ecb4-111">Yeni bir konsol uygulaması açın ve adını `PredicateFilters`.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-111">Open a new console application and name it `PredicateFilters`.</span></span>  
  
2.  <span data-ttu-id="9ecb4-112">Kopya `StudentClass` sınıfıyla [nesneler koleksiyonunu sorgulama](query-a-collection-of-objects.md) ve ad alanına yapıştırın `PredicateFilters` sınıfı altında `Program`.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-112">Copy the `StudentClass` class from [Query a collection of objects](query-a-collection-of-objects.md) and paste it into namespace `PredicateFilters` underneath class `Program`.</span></span> <span data-ttu-id="9ecb4-113">`StudentClass`bir listesini sağlar `Student` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-113">`StudentClass` provides a list of `Student` objects.</span></span>  
  
3.  <span data-ttu-id="9ecb4-114">Out açıklama `Main` yönteminde `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-114">Comment out the `Main` method in `StudentClass`.</span></span>  
  
4.  <span data-ttu-id="9ecb4-115">Sınıf Değiştir `Program` aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-115">Replace class `Program` with the following code.</span></span>  
  
     [!code-csharp[csProgGuideLINQ#26](../../../samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]  
  
5.  <span data-ttu-id="9ecb4-116">Aşağıdaki satırı ekleyin `Main` sınıfında yöntemi `DynamicPredicates`, bildirimi altında `ids`.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-116">Add the following line to the `Main` method in class `DynamicPredicates`, under the declaration of `ids`.</span></span>  
  
     ```csharp
     QueryById(ids);
     ```

6.  <span data-ttu-id="9ecb4-117">Projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-117">Run the project.</span></span>  
  
7.  <span data-ttu-id="9ecb4-118">Aşağıdaki çıkış konsol penceresinde görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="9ecb4-118">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="9ecb4-119">Garcia: 114</span><span class="sxs-lookup"><span data-stu-id="9ecb4-119">Garcia: 114</span></span>  
  
     <span data-ttu-id="9ecb4-120">O'Donnell: 112</span><span class="sxs-lookup"><span data-stu-id="9ecb4-120">O'Donnell: 112</span></span>  
  
     <span data-ttu-id="9ecb4-121">Omelchenko: 111</span><span class="sxs-lookup"><span data-stu-id="9ecb4-121">Omelchenko: 111</span></span>  
  
8.  <span data-ttu-id="9ecb4-122">Sonraki adım projeyi yeniden çalıştırmak için dizi yerine çalışma zamanında giriş kullanarak bu saati girildi. `ids`.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-122">The next step is to run the project again, this time by using input entered at run time instead of array `ids`.</span></span> <span data-ttu-id="9ecb4-123">Değişiklik `QueryByID(ids)` için `QueryByID(args)` içinde `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-123">Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.</span></span>  
  
9. <span data-ttu-id="9ecb4-124">Komut satırı bağımsız değişkenleri ile projeyi çalıştırın `122 117 120 115`.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-124">Run the project with the command line arguments `122 117 120 115`.</span></span> <span data-ttu-id="9ecb4-125">Projeyi çalıştırdığınızda bu değerleri öğeleri hale `args`, parametresinin `Main` yöntemi...</span><span class="sxs-lookup"><span data-stu-id="9ecb4-125">When the project is run, those values become elements of `args`, the parameter of the `Main` method..</span></span>  
  
10. <span data-ttu-id="9ecb4-126">Aşağıdaki çıkış konsol penceresinde görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="9ecb4-126">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="9ecb4-127">Adams: 120</span><span class="sxs-lookup"><span data-stu-id="9ecb4-127">Adams: 120</span></span>  
  
     <span data-ttu-id="9ecb4-128">Feng: 117</span><span class="sxs-lookup"><span data-stu-id="9ecb4-128">Feng: 117</span></span>  
  
     <span data-ttu-id="9ecb4-129">Garcia: 115</span><span class="sxs-lookup"><span data-stu-id="9ecb4-129">Garcia: 115</span></span>  
  
     <span data-ttu-id="9ecb4-130">Tucker: 122</span><span class="sxs-lookup"><span data-stu-id="9ecb4-130">Tucker: 122</span></span>  
  
## <a name="to-filter-by-using-a-switch-statement"></a><span data-ttu-id="9ecb4-131">Switch deyimi kullanarak filtre uygulamak için</span><span class="sxs-lookup"><span data-stu-id="9ecb4-131">To filter by using a switch statement</span></span>  
  
1.  <span data-ttu-id="9ecb4-132">Kullanabileceğiniz bir `switch` arasından seçim yapmak deyimi önceden alternatif sorgular.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-132">You can use a `switch` statement to select among predetermined alternative queries.</span></span> <span data-ttu-id="9ecb4-133">Aşağıdaki örnekte, `studentQuery` farklı bir kullanan `where` bağlı olarak hangi düzeyde düzeyini yılı, belirtilmişse, veya çalışma zamanında yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-133">In the following example, `studentQuery` uses a different `where` clause depending on which grade level, or year, is specified at run time.</span></span>  
  
2.  <span data-ttu-id="9ecb4-134">Aşağıdaki yöntem kopyalayın ve sınıfına yapıştırın `DynamicPredicates`.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-134">Copy the following method and paste it into class `DynamicPredicates`.</span></span>  
  
     [!code-csharp[csProgGuideLINQ#27](../../../samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]  
  
3.  <span data-ttu-id="9ecb4-135">İçinde `Main` yöntemi çağrısı Değiştir `QueryByID` aşağıdaki çağrısı ile gönderdiği ilk öğeden `args` bağımsız değişkeni olarak bir dizi: `QueryByYear(args[0])`.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-135">In the `Main` method, replace the call to `QueryByID` with the following call, which sends the first element from the `args` array as its argument: `QueryByYear(args[0])`.</span></span>  
  
4.  <span data-ttu-id="9ecb4-136">Proje, 1 ile 4 arasında bir tamsayı değeri bir komut satırı bağımsız değişkeni ile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-136">Run the project with a command line argument of an integer value between 1 and 4.</span></span>  
  
 
## <a name="see-also"></a><span data-ttu-id="9ecb4-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9ecb4-137">See Also</span></span>  
 [<span data-ttu-id="9ecb4-138">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="9ecb4-138">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="9ecb4-139">Burada yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="9ecb4-139">where clause</span></span>](../language-reference/keywords/where-clause.md)
