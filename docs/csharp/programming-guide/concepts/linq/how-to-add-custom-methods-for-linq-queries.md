---
title: LINQ sorguları için özel yöntemler ekleme (C#)
description: C# ' de IEnumerable arabirimine uzantı yöntemleri ekleyerek LINQ sorgularının söz dizimini genişletmeyi öğrenin <T> .
ms.date: 08/26/2020
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: 768882fce40a2fc6e018f24c8928341e7c65bc4b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122433"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a><span data-ttu-id="2053b-103">LINQ sorguları için özel yöntemler ekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="2053b-103">How to add custom methods for LINQ queries (C#)</span></span>

<span data-ttu-id="2053b-104">Arabirime uzantı yöntemleri ekleyerek LINQ sorguları için kullandığınız yöntemlerin kümesini genişletebilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="2053b-104">You extend the set of methods that you use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="2053b-105">Örneğin, standart ortalama veya en yüksek işlemlere ek olarak, bir dizi değerden tek bir değeri hesaplamak için özel bir toplama yöntemi oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="2053b-105">For example, in addition to the standard average or maximum operations, you create a custom aggregate method to compute a single value from a sequence of values.</span></span> <span data-ttu-id="2053b-106">Ayrıca, bir dizi değer için özel bir filtre veya belirli bir veri dönüştürmesi olarak çalışacak bir yöntem oluşturun ve yeni bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="2053b-106">You also create a method that works as a custom filter or a specific data transform for a sequence of values and returns a new sequence.</span></span> <span data-ttu-id="2053b-107">Bu tür yöntemlere örnekler, <xref:System.Linq.Enumerable.Distinct%2A> <xref:System.Linq.Enumerable.Skip%2A> ve ' dir <xref:System.Linq.Enumerable.Reverse%2A> .</span><span class="sxs-lookup"><span data-stu-id="2053b-107">Examples of such methods are <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Skip%2A>, and <xref:System.Linq.Enumerable.Reverse%2A>.</span></span>

<span data-ttu-id="2053b-108"><xref:System.Collections.Generic.IEnumerable%601>Arabirimi genişlettiğinizde, özel yöntemlerinizi herhangi bir sıralanabilir koleksiyona uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2053b-108">When you extend the <xref:System.Collections.Generic.IEnumerable%601> interface, you can apply your custom methods to any enumerable collection.</span></span> <span data-ttu-id="2053b-109">Daha fazla bilgi için bkz. [Uzantı yöntemleri](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="2053b-109">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="adding-an-aggregate-method"></a><span data-ttu-id="2053b-110">Toplama yöntemi ekleme</span><span class="sxs-lookup"><span data-stu-id="2053b-110">Adding an aggregate method</span></span>

<span data-ttu-id="2053b-111">Toplama yöntemi bir değer kümesinden tek bir değeri hesaplar.</span><span class="sxs-lookup"><span data-stu-id="2053b-111">An aggregate method computes a single value from a set of values.</span></span> <span data-ttu-id="2053b-112">LINQ, ve dahil olmak üzere birkaç toplama yöntemi sağlar <xref:System.Linq.Enumerable.Average%2A> <xref:System.Linq.Enumerable.Min%2A> <xref:System.Linq.Enumerable.Max%2A> .</span><span class="sxs-lookup"><span data-stu-id="2053b-112">LINQ provides several aggregate methods, including <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Max%2A>.</span></span> <span data-ttu-id="2053b-113">Arayüze bir genişletme yöntemi ekleyerek kendi toplama yönteminizi oluşturabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="2053b-113">You can create your own aggregate method by adding an extension method to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="2053b-114">Aşağıdaki kod örneği, `Median` bir tür sayı dizisi için ortanca hesaplamak üzere çağrılan bir genişletme yönteminin nasıl oluşturulacağını göstermektedir `double` .</span><span class="sxs-lookup"><span data-stu-id="2053b-114">The following code example shows how to create an extension method called `Median` to compute a median for a sequence of numbers of type `double`.</span></span>

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="LinqExtensionClass":::

<span data-ttu-id="2053b-115">Bu genişletme yöntemini, herhangi bir sıralanabilir koleksiyon için, arabirimden diğer toplama yöntemlerini çağırdığınız şekilde çağırabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="2053b-115">You call this extension method for any enumerable collection in the same way you call other aggregate methods from the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>

<span data-ttu-id="2053b-116">Aşağıdaki kod örneği, `Median` bir dizi türü için yönteminin nasıl kullanılacağını gösterir `double` .</span><span class="sxs-lookup"><span data-stu-id="2053b-116">The following code example shows how to use the `Median` method for an array of type `double`.</span></span>

:::code language="csharp" source="./snippets/Program.cs" ID="MedianUsage":::

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a><span data-ttu-id="2053b-117">Çeşitli türleri kabul etmek için bir toplama yöntemini aşırı yükleme</span><span class="sxs-lookup"><span data-stu-id="2053b-117">Overloading an Aggregate Method to Accept Various Types</span></span>

<span data-ttu-id="2053b-118">Toplama yönteminizi çeşitli türlerde dizileri kabul edecek şekilde aşırı yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2053b-118">You can overload your aggregate method so that it accepts sequences of various types.</span></span> <span data-ttu-id="2053b-119">Standart yaklaşım, her tür için bir aşırı yükleme oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="2053b-119">The standard approach is to create an overload for each type.</span></span> <span data-ttu-id="2053b-120">Başka bir yaklaşım ise genel bir tür alacak ve bir temsilciyi kullanarak belirli bir türe dönüştürecek bir aşırı yükleme oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="2053b-120">Another approach is to create an overload that will take a generic type and convert it to a specific type by using a delegate.</span></span> <span data-ttu-id="2053b-121">Her iki yaklaşımı de birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2053b-121">You can also combine both approaches.</span></span>

#### <a name="to-create-an-overload-for-each-type"></a><span data-ttu-id="2053b-122">Her tür için bir aşırı yükleme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2053b-122">To create an overload for each type</span></span>

<span data-ttu-id="2053b-123">Desteklemek istediğiniz her tür için belirli bir aşırı yükleme oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2053b-123">You can create a specific overload for each type that you want to support.</span></span> <span data-ttu-id="2053b-124">Aşağıdaki kod örneği, türü için yönteminin bir aşırı yüklemesini gösterir `Median` `int` .</span><span class="sxs-lookup"><span data-stu-id="2053b-124">The following code example shows an overload of the `Median` method for the `int` type.</span></span>

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="IntOverload":::

<span data-ttu-id="2053b-125">Artık `Median` `integer` `double` , aşağıdaki kodda gösterildiği gibi, hem hem de türleri için aşırı yüklemeleri çağırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2053b-125">You can now call the `Median` overloads for both `integer` and `double` types, as shown in the following code:</span></span>

:::code language="csharp" source="./snippets/Program.cs" ID="OverloadUsage":::

#### <a name="to-create-a-generic-overload"></a><span data-ttu-id="2053b-126">Genel aşırı yükleme oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="2053b-126">To create a generic overload</span></span>

<span data-ttu-id="2053b-127">Ayrıca, genel nesne dizisini kabul eden bir aşırı yükleme de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2053b-127">You can also create an overload that accepts a sequence of generic objects.</span></span> <span data-ttu-id="2053b-128">Bu aşırı yükleme bir temsilciyi parametre olarak alır ve bir genel türdeki nesne dizisini belirli bir türe dönüştürmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="2053b-128">This overload takes a delegate as a parameter and uses it to convert a sequence of objects of a generic type to a specific type.</span></span>

<span data-ttu-id="2053b-129">Aşağıdaki kod, `Median` <xref:System.Func%602> bir parametresi olarak temsilciyi alan yönteminin bir aşırı yüklemesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2053b-129">The following code shows an overload of the `Median` method that takes the <xref:System.Func%602> delegate as a parameter.</span></span> <span data-ttu-id="2053b-130">Bu temsilci, T genel türünde bir nesne alır ve türünde bir nesne döndürür `double` .</span><span class="sxs-lookup"><span data-stu-id="2053b-130">This delegate takes an object of generic type T and returns an object of type `double`.</span></span>

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="GenericOverload":::

<span data-ttu-id="2053b-131">Artık `Median` herhangi bir türdeki nesne dizisi için yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2053b-131">You can now call the `Median` method for a sequence of objects of any type.</span></span> <span data-ttu-id="2053b-132">Türün kendi yöntem aşırı yüklemesi yoksa, bir temsilci parametresi geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2053b-132">If the type doesn't have its own method overload, you have to pass a delegate parameter.</span></span> <span data-ttu-id="2053b-133">C# dilinde, bu amaçla bir lambda ifadesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2053b-133">In C#, you can use a lambda expression for this purpose.</span></span> <span data-ttu-id="2053b-134">Ayrıca, yalnızca Visual Basic ' de, `Aggregate` `Group By` Yöntem çağrısı yerine OR yan tümcesini kullanırsanız, bu yan tümce kapsamındaki herhangi bir değer veya ifade geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2053b-134">Also, in Visual Basic only, if you use the `Aggregate` or `Group By` clause instead of the method call, you can pass any value or expression that is in the scope this clause.</span></span>

<span data-ttu-id="2053b-135">Aşağıdaki örnek kod, `Median` bir tamsayılar dizisi ve dizeler dizisi için yönteminin nasıl çağrılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2053b-135">The following example code shows how to call the `Median` method for an array of integers and an array of strings.</span></span> <span data-ttu-id="2053b-136">Dizeler için, dizideki dizelerin uzunluklarının ortancası hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="2053b-136">For strings, the median for the lengths of strings in the array is calculated.</span></span> <span data-ttu-id="2053b-137">Örnek, <xref:System.Func%602> her durumda temsilci parametresinin yönteme nasıl geçirileceğini gösterir `Median` .</span><span class="sxs-lookup"><span data-stu-id="2053b-137">The example shows how to pass the <xref:System.Func%602> delegate parameter to the `Median` method for each case.</span></span>

:::code language="csharp" source="./snippets/Program.cs" ID="GenericUsage":::

## <a name="adding-a-method-that-returns-a-sequence"></a><span data-ttu-id="2053b-138">Sıra döndüren bir yöntem ekleme</span><span class="sxs-lookup"><span data-stu-id="2053b-138">Adding a method that returns a sequence</span></span>

<span data-ttu-id="2053b-139"><xref:System.Collections.Generic.IEnumerable%601>Arabirimi bir değer dizisi döndüren özel bir sorgu yöntemiyle genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2053b-139">You can extend the <xref:System.Collections.Generic.IEnumerable%601> interface with a custom query method that returns a sequence of values.</span></span> <span data-ttu-id="2053b-140">Bu durumda, yöntemin türünde bir koleksiyon döndürmesi gerekir <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="2053b-140">In this case, the method must return a collection of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="2053b-141">Bu tür yöntemler, bir değerler dizisine filtre veya veri dönüştürmeleri uygulamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2053b-141">Such methods can be used to apply filters or data transforms to a sequence of values.</span></span>

<span data-ttu-id="2053b-142">Aşağıdaki örnek, `AlternateElements` ilk öğeden başlayarak bir koleksiyondaki her öğeyi döndüren adlı bir genişletme yönteminin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2053b-142">The following example shows how to create an extension method named `AlternateElements` that returns every other element in a collection, starting from the first element.</span></span>

:::code language="csharp" source="./snippets/LinqExtensions.cs" ID="SequenceElement":::

<span data-ttu-id="2053b-143">Aşağıdaki kodda gösterildiği gibi, herhangi bir sayılabilir koleksiyon için bu genişletme yöntemini, arabirimden diğer yöntemleri çağırdığınız gibi çağırabilirsiniz <xref:System.Collections.Generic.IEnumerable%601> :</span><span class="sxs-lookup"><span data-stu-id="2053b-143">You can call this extension method for any enumerable collection just as you would call other methods from the <xref:System.Collections.Generic.IEnumerable%601> interface, as shown in the following code:</span></span>

:::code language="csharp" source="./snippets/Program.cs" ID="SequenceUsage":::

## <a name="see-also"></a><span data-ttu-id="2053b-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2053b-144">See also</span></span>

- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="2053b-145">Uzantı Metotları</span><span class="sxs-lookup"><span data-stu-id="2053b-145">Extension Methods</span></span>](../../classes-and-structs/extension-methods.md)
