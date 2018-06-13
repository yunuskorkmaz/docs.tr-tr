---
title: Çalışma zamanında koşul filtrelerini dinamik olarak belirtme
description: Çalışma zamanında koşul filtrelerini dinamik olarak belirleme konusunda.
ms.date: 12/1/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: fa3426a513758d8c30bf381ec480b9b8d12a5f81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33287946"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a><span data-ttu-id="5802e-103">Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="5802e-103">Dynamically specify predicate filters at runtime</span></span>

<span data-ttu-id="5802e-104">Bazı durumlarda, çalışma zamanına kadar sahip kaynak öğelerine uygulamak kaç tane doğrulamaları bilmiyorsanız `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="5802e-104">In some cases you do not know until run time how many predicates you have to apply to source elements in the `where` clause.</span></span> <span data-ttu-id="5802e-105">Birden çok koşul filtrelerini dinamik olarak belirtmek için bir yol kullanmaktır <xref:System.Linq.Enumerable.Contains%2A> aşağıdaki örnekte gösterildiği gibi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5802e-105">One way to dynamically specify multiple predicate filters is to use the <xref:System.Linq.Enumerable.Contains%2A> method, as shown in the following example.</span></span> <span data-ttu-id="5802e-106">Örneğin, iki şekilde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5802e-106">The example is constructed in two ways.</span></span> <span data-ttu-id="5802e-107">İlk olarak, projeyi programa sağlanan değerleri üzerinde filtreleme yaparak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="5802e-107">First, the project is run by filtering on values that are provided in the program.</span></span> <span data-ttu-id="5802e-108">Daha sonra projeyi yeniden çalışma zamanında sağlanan giriş kullanarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="5802e-108">Then the project is run again by using input provided at run time.</span></span>  
  
## <a name="to-filter-by-using-the-contains-method"></a><span data-ttu-id="5802e-109">Contains yöntemi kullanarak filtre uygulamak için</span><span class="sxs-lookup"><span data-stu-id="5802e-109">To filter by using the Contains method</span></span>  
  
1.  <span data-ttu-id="5802e-110">Yeni bir konsol uygulaması açın ve adını `PredicateFilters`.</span><span class="sxs-lookup"><span data-stu-id="5802e-110">Open a new console application and name it `PredicateFilters`.</span></span>  
  
2.  <span data-ttu-id="5802e-111">Kopya `StudentClass` sınıfıyla [nesneler koleksiyonunu sorgulama](query-a-collection-of-objects.md) ve ad alanına yapıştırın `PredicateFilters` sınıfı altında `Program`.</span><span class="sxs-lookup"><span data-stu-id="5802e-111">Copy the `StudentClass` class from [Query a collection of objects](query-a-collection-of-objects.md) and paste it into namespace `PredicateFilters` underneath class `Program`.</span></span> <span data-ttu-id="5802e-112">`StudentClass` bir listesini sağlar `Student` nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5802e-112">`StudentClass` provides a list of `Student` objects.</span></span>  
  
3.  <span data-ttu-id="5802e-113">Out açıklama `Main` yönteminde `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="5802e-113">Comment out the `Main` method in `StudentClass`.</span></span>  
  
4.  <span data-ttu-id="5802e-114">Sınıf Değiştir `Program` aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="5802e-114">Replace class `Program` with the following code.</span></span>  
  
     [!code-csharp[csProgGuideLINQ#26](../../../samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]  
  
5.  <span data-ttu-id="5802e-115">Aşağıdaki satırı ekleyin `Main` sınıfında yöntemi `DynamicPredicates`, bildirimi altında `ids`.</span><span class="sxs-lookup"><span data-stu-id="5802e-115">Add the following line to the `Main` method in class `DynamicPredicates`, under the declaration of `ids`.</span></span>  
  
     ```csharp
     QueryById(ids);
     ```

6.  <span data-ttu-id="5802e-116">Projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5802e-116">Run the project.</span></span>  
  
7.  <span data-ttu-id="5802e-117">Aşağıdaki çıkış konsol penceresinde görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="5802e-117">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="5802e-118">Garcia: 114</span><span class="sxs-lookup"><span data-stu-id="5802e-118">Garcia: 114</span></span>  
  
     <span data-ttu-id="5802e-119">O'Donnell: 112</span><span class="sxs-lookup"><span data-stu-id="5802e-119">O'Donnell: 112</span></span>  
  
     <span data-ttu-id="5802e-120">Omelchenko: 111</span><span class="sxs-lookup"><span data-stu-id="5802e-120">Omelchenko: 111</span></span>  
  
8.  <span data-ttu-id="5802e-121">Sonraki adım projeyi yeniden çalıştırmak için dizi yerine çalışma zamanında giriş kullanarak bu saati girildi. `ids`.</span><span class="sxs-lookup"><span data-stu-id="5802e-121">The next step is to run the project again, this time by using input entered at run time instead of array `ids`.</span></span> <span data-ttu-id="5802e-122">Değişiklik `QueryByID(ids)` için `QueryByID(args)` içinde `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5802e-122">Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.</span></span>  
  
9. <span data-ttu-id="5802e-123">Komut satırı bağımsız değişkenleri ile projeyi çalıştırın `122 117 120 115`.</span><span class="sxs-lookup"><span data-stu-id="5802e-123">Run the project with the command line arguments `122 117 120 115`.</span></span> <span data-ttu-id="5802e-124">Projeyi çalıştırdığınızda bu değerleri öğeleri hale `args`, parametresinin `Main` yöntemi...</span><span class="sxs-lookup"><span data-stu-id="5802e-124">When the project is run, those values become elements of `args`, the parameter of the `Main` method..</span></span>  
  
10. <span data-ttu-id="5802e-125">Aşağıdaki çıkış konsol penceresinde görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="5802e-125">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="5802e-126">Adams: 120</span><span class="sxs-lookup"><span data-stu-id="5802e-126">Adams: 120</span></span>  
  
     <span data-ttu-id="5802e-127">Feng: 117</span><span class="sxs-lookup"><span data-stu-id="5802e-127">Feng: 117</span></span>  
  
     <span data-ttu-id="5802e-128">Garcia: 115</span><span class="sxs-lookup"><span data-stu-id="5802e-128">Garcia: 115</span></span>  
  
     <span data-ttu-id="5802e-129">Tucker: 122</span><span class="sxs-lookup"><span data-stu-id="5802e-129">Tucker: 122</span></span>  
  
## <a name="to-filter-by-using-a-switch-statement"></a><span data-ttu-id="5802e-130">Switch deyimi kullanarak filtre uygulamak için</span><span class="sxs-lookup"><span data-stu-id="5802e-130">To filter by using a switch statement</span></span>  
  
1.  <span data-ttu-id="5802e-131">Kullanabileceğiniz bir `switch` arasından seçim yapmak deyimi önceden alternatif sorgular.</span><span class="sxs-lookup"><span data-stu-id="5802e-131">You can use a `switch` statement to select among predetermined alternative queries.</span></span> <span data-ttu-id="5802e-132">Aşağıdaki örnekte, `studentQuery` farklı bir kullanan `where` bağlı olarak hangi düzeyde düzeyini yılı, belirtilmişse, veya çalışma zamanında yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="5802e-132">In the following example, `studentQuery` uses a different `where` clause depending on which grade level, or year, is specified at run time.</span></span>  
  
2.  <span data-ttu-id="5802e-133">Aşağıdaki yöntem kopyalayın ve sınıfına yapıştırın `DynamicPredicates`.</span><span class="sxs-lookup"><span data-stu-id="5802e-133">Copy the following method and paste it into class `DynamicPredicates`.</span></span>  
  
     [!code-csharp[csProgGuideLINQ#27](../../../samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]  
  
3.  <span data-ttu-id="5802e-134">İçinde `Main` yöntemi çağrısı Değiştir `QueryByID` aşağıdaki çağrısı ile gönderdiği ilk öğeden `args` bağımsız değişkeni olarak bir dizi: `QueryByYear(args[0])`.</span><span class="sxs-lookup"><span data-stu-id="5802e-134">In the `Main` method, replace the call to `QueryByID` with the following call, which sends the first element from the `args` array as its argument: `QueryByYear(args[0])`.</span></span>  
  
4.  <span data-ttu-id="5802e-135">Proje, 1 ile 4 arasında bir tamsayı değeri bir komut satırı bağımsız değişkeni ile çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5802e-135">Run the project with a command line argument of an integer value between 1 and 4.</span></span>  
  
 
## <a name="see-also"></a><span data-ttu-id="5802e-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5802e-136">See Also</span></span>  
 [<span data-ttu-id="5802e-137">LINQ Sorgu ifadeleri</span><span class="sxs-lookup"><span data-stu-id="5802e-137">LINQ Query Expressions</span></span>](index.md)  
 [<span data-ttu-id="5802e-138">where yan tümcesi</span><span class="sxs-lookup"><span data-stu-id="5802e-138">where clause</span></span>](../language-reference/keywords/where-clause.md)
