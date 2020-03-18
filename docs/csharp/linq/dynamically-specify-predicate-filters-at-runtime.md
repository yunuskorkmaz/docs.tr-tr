---
title: Çalışma zamanında yüklem filtrelerini dinamik olarak belirtin (C#'da LINQ)
description: C#'da LINQ kullanarak çalışma zamanında yüklem filtrelerini dinamik olarak nasıl belirtebilirsiniz öğrenin.
ms.date: 12/01/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: 314be8f98b9ff014f14bef11a1f3581eff8574b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659949"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a><span data-ttu-id="e9584-103">Çalışma zamanında koşul filtrelerini dinamik olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="e9584-103">Dynamically specify predicate filters at runtime</span></span>

<span data-ttu-id="e9584-104">Bazı durumlarda, `where` çalışma süresine kadar yan tümcedeki kaynak öğelere kaç yüklem uygulamanız gerektiğini bilemezsin.</span><span class="sxs-lookup"><span data-stu-id="e9584-104">In some cases, you don't know until run time how many predicates you have to apply to source elements in the `where` clause.</span></span> <span data-ttu-id="e9584-105">Birden çok yüklem filtresini dinamik olarak belirtmenin <xref:System.Linq.Enumerable.Contains%2A> bir yolu, aşağıdaki örnekte gösterildiği gibi yöntemi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="e9584-105">One way to dynamically specify multiple predicate filters is to use the <xref:System.Linq.Enumerable.Contains%2A> method, as shown in the following example.</span></span> <span data-ttu-id="e9584-106">Örnek iki şekilde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="e9584-106">The example is constructed in two ways.</span></span> <span data-ttu-id="e9584-107">İlk olarak, proje programda sağlanan değerlere filtre uygulanarak çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="e9584-107">First, the project is run by filtering on values that are provided in the program.</span></span> <span data-ttu-id="e9584-108">Daha sonra proje, çalışma zamanında sağlanan giriş kullanılarak yeniden çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="e9584-108">Then the project is run again by using input provided at run time.</span></span>

## <a name="to-filter-by-using-the-contains-method"></a><span data-ttu-id="e9584-109">İçle yöntemini kullanarak filtrelemek için</span><span class="sxs-lookup"><span data-stu-id="e9584-109">To filter by using the Contains method</span></span>

1. <span data-ttu-id="e9584-110">Yeni bir konsol uygulaması `PredicateFilters`açın ve adlandırın.</span><span class="sxs-lookup"><span data-stu-id="e9584-110">Open a new console application and name it `PredicateFilters`.</span></span>

2. <span data-ttu-id="e9584-111">Sınıfı `StudentClass` Sorgula'dan [nesnelerin bir koleksiyonunu](query-a-collection-of-objects.md) kopyalayın ve `PredicateFilters` sınıfın `Program`altındaki ad alanına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="e9584-111">Copy the `StudentClass` class from [Query a collection of objects](query-a-collection-of-objects.md) and paste it into namespace `PredicateFilters` underneath class `Program`.</span></span> <span data-ttu-id="e9584-112">`StudentClass``Student` nesnelerin bir listesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9584-112">`StudentClass` provides a list of `Student` objects.</span></span>

3. <span data-ttu-id="e9584-113">Yöntemi ' `Main` de `StudentClass`yorumla.</span><span class="sxs-lookup"><span data-stu-id="e9584-113">Comment out the `Main` method in `StudentClass`.</span></span>

4. <span data-ttu-id="e9584-114">Sınıfı `Program` aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="e9584-114">Replace class `Program` with the following code:</span></span>

     [!code-csharp[csProgGuideLINQ#26](~/samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]

5. <span data-ttu-id="e9584-115">Sınıftaki `Main` `DynamicPredicates`yönteme aşağıdaki satırı ekleyin, `ids`.</span><span class="sxs-lookup"><span data-stu-id="e9584-115">Add the following line to the `Main` method in class `DynamicPredicates`, under the declaration of `ids`.</span></span>

     ```csharp
     QueryById(ids);
     ```

6. <span data-ttu-id="e9584-116">Projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e9584-116">Run the project.</span></span>

7. <span data-ttu-id="e9584-117">Aşağıdaki çıktı konsol penceresinde görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="e9584-117">The following output is displayed in a console window:</span></span>

     <span data-ttu-id="e9584-118">Garcia: 114</span><span class="sxs-lookup"><span data-stu-id="e9584-118">Garcia: 114</span></span>

     <span data-ttu-id="e9584-119">O'Donnell: 112</span><span class="sxs-lookup"><span data-stu-id="e9584-119">O'Donnell: 112</span></span>

     <span data-ttu-id="e9584-120">Omelchenko: 111</span><span class="sxs-lookup"><span data-stu-id="e9584-120">Omelchenko: 111</span></span>

8. <span data-ttu-id="e9584-121">Bir sonraki adım, bu kez dizi `ids`yerine çalışma zamanında girilen girişi kullanarak projeyi yeniden çalıştırmaktır.</span><span class="sxs-lookup"><span data-stu-id="e9584-121">The next step is to run the project again, this time by using input entered at run time instead of array `ids`.</span></span> <span data-ttu-id="e9584-122">Yöntemde değiştirin. `Main` `QueryByID(ids)` `QueryByID(args)`</span><span class="sxs-lookup"><span data-stu-id="e9584-122">Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.</span></span>

9. <span data-ttu-id="e9584-123">Komut satırı bağımsız değişkenleriyle `122 117 120 115`projeyi çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e9584-123">Run the project with the command line arguments `122 117 120 115`.</span></span> <span data-ttu-id="e9584-124">Proje çalıştırıldığında, bu değerler `args` `Main` yöntemin parametresi olan öğeler haline gelir.</span><span class="sxs-lookup"><span data-stu-id="e9584-124">When the project is run, those values become elements of `args`, the parameter of the `Main` method.</span></span>

10. <span data-ttu-id="e9584-125">Aşağıdaki çıktı konsol penceresinde görüntülenir:</span><span class="sxs-lookup"><span data-stu-id="e9584-125">The following output is displayed in a console window:</span></span>

     <span data-ttu-id="e9584-126">Adam sayısı: 120</span><span class="sxs-lookup"><span data-stu-id="e9584-126">Adams: 120</span></span>

     <span data-ttu-id="e9584-127">Feng: 117</span><span class="sxs-lookup"><span data-stu-id="e9584-127">Feng: 117</span></span>

     <span data-ttu-id="e9584-128">Garcia: 115</span><span class="sxs-lookup"><span data-stu-id="e9584-128">Garcia: 115</span></span>

     <span data-ttu-id="e9584-129">Tucker: 122</span><span class="sxs-lookup"><span data-stu-id="e9584-129">Tucker: 122</span></span>

## <a name="to-filter-by-using-a-switch-statement"></a><span data-ttu-id="e9584-130">Anahtar deyimi kullanarak filtre lemek için</span><span class="sxs-lookup"><span data-stu-id="e9584-130">To filter by using a switch statement</span></span>

1. <span data-ttu-id="e9584-131">Önceden belirlenmiş `switch` alternatif sorgular arasından seçim yapmak için bir deyim kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9584-131">You can use a `switch` statement to select among predetermined alternative queries.</span></span> <span data-ttu-id="e9584-132">Aşağıdaki örnekte, `studentQuery` çalışma `where` zamanında hangi sınıf düzeyine veya yıla bağlı olarak farklı bir tümce kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9584-132">In the following example, `studentQuery` uses a different `where` clause depending on which grade level, or year, is specified at run time.</span></span>

2. <span data-ttu-id="e9584-133">Aşağıdaki yöntemi kopyalayın ve sınıfa `DynamicPredicates`yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="e9584-133">Copy the following method and paste it into class `DynamicPredicates`.</span></span>

     [!code-csharp[csProgGuideLINQ#27](~/samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]

3. <span data-ttu-id="e9584-134">`Main` Yöntemde, çağrıyı `QueryByID` aşağıdaki çağrıyla değiştirin, bu da `args` diziden ilk `QueryByYear(args[0])`öğeyi bağımsız değişken olarak gönderir: .</span><span class="sxs-lookup"><span data-stu-id="e9584-134">In the `Main` method, replace the call to `QueryByID` with the following call, which sends the first element from the `args` array as its argument: `QueryByYear(args[0])`.</span></span>

4. <span data-ttu-id="e9584-135">Projeyi, 1 ile 4 arasında bir tamsayı değerinin komut satırı bağımsız değişkeniyle çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e9584-135">Run the project with a command line argument of an integer value between 1 and 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9584-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9584-136">See also</span></span>

- [<span data-ttu-id="e9584-137">Dil ile Tümleşik Sorgu (LINQ)</span><span class="sxs-lookup"><span data-stu-id="e9584-137">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="e9584-138">where tümcesi</span><span class="sxs-lookup"><span data-stu-id="e9584-138">where clause</span></span>](../language-reference/keywords/where-clause.md)
