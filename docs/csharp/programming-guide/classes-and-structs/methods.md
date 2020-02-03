---
title: Yöntemler- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: 8c90f06bfadc528bd9575ead30e6b01263055fe8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743910"
---
# <a name="methods-c-programming-guide"></a><span data-ttu-id="84577-102">Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="84577-102">Methods (C# Programming Guide)</span></span>

<span data-ttu-id="84577-103">Yöntemi, bir dizi deyim içeren bir kod bloğudur.</span><span class="sxs-lookup"><span data-stu-id="84577-103">A method is a code block that contains a series of statements.</span></span> <span data-ttu-id="84577-104">Program, metodu çağırarak ve gerekli Yöntem bağımsız değişkenlerini belirterek deyimlerin yürütülmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="84577-104">A program causes the statements to be executed by calling the method and specifying any required method arguments.</span></span> <span data-ttu-id="84577-105">' C#De, her yürütülen yönerge bir yöntem bağlamında gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="84577-105">In C#, every executed instruction is performed in the context of a method.</span></span> <span data-ttu-id="84577-106">`Main` yöntemi her C# uygulamanın giriş noktasıdır ve program başlatıldığında ortak dil çalışma zamanı (CLR) tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="84577-106">The `Main` method is the entry point for every C# application and it's called by the common language runtime (CLR) when the program is started.</span></span>

> [!NOTE]
> <span data-ttu-id="84577-107">Bu makalede adlandırılmış yöntemler ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="84577-107">This article discusses named methods.</span></span> <span data-ttu-id="84577-108">Anonim işlevler hakkında daha fazla bilgi için bkz. [Anonim işlevler](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="84577-108">For information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>

## <a name="method-signatures"></a><span data-ttu-id="84577-109">Yöntem imzaları</span><span class="sxs-lookup"><span data-stu-id="84577-109">Method signatures</span></span>

<span data-ttu-id="84577-110">Yöntemler, `public` veya `private`, `abstract` veya `sealed`, dönüş değeri, yöntemin adı ve herhangi bir yöntem parametresi gibi erişim düzeyi belirtilerek bir [sınıf](../../language-reference/keywords/class.md) veya [Yapı](../../language-reference/keywords/struct.md) içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="84577-110">Methods are declared in a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/keywords/struct.md) by specifying the access level such as `public` or `private`, optional modifiers such as `abstract` or `sealed`, the return value, the name of the method, and any method parameters.</span></span> <span data-ttu-id="84577-111">Bu parçalar, yönteminin imzasıdır.</span><span class="sxs-lookup"><span data-stu-id="84577-111">These parts together are the signature of the method.</span></span>

> [!NOTE]
> <span data-ttu-id="84577-112">Bir yöntemin dönüş türü, yöntem aşırı yüklemesi amaçları için yöntemin imzasının bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="84577-112">A return type of a method is not part of the signature of the method for the purposes of method overloading.</span></span> <span data-ttu-id="84577-113">Ancak, bir temsilci ve işaret ettiği yöntem arasındaki uyumluluğun belirlenmesi sırasında yönteminin imzasının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="84577-113">However, it is part of the signature of the method when determining the compatibility between a delegate and the method that it points to.</span></span>

<span data-ttu-id="84577-114">Yöntem parametreleri parantez içine alınır ve virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="84577-114">Method parameters are enclosed in parentheses and are separated by commas.</span></span> <span data-ttu-id="84577-115">Boş parantezler, yöntemin hiçbir parametre gerektirmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="84577-115">Empty parentheses indicate that the method requires no parameters.</span></span> <span data-ttu-id="84577-116">Bu sınıf dört yöntem içerir:</span><span class="sxs-lookup"><span data-stu-id="84577-116">This class contains four methods:</span></span>

[!code-csharp[csProgGuideObjects#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#40)]

## <a name="method-access"></a><span data-ttu-id="84577-117">Yöntem erişimi</span><span class="sxs-lookup"><span data-stu-id="84577-117">Method access</span></span>

<span data-ttu-id="84577-118">Bir nesne üzerinde bir yöntemi çağırmak, bir alana erişme gibidir.</span><span class="sxs-lookup"><span data-stu-id="84577-118">Calling a method on an object is like accessing a field.</span></span> <span data-ttu-id="84577-119">Nesne adından sonra bir nokta, yöntemin adı ve parantez ekleyin.</span><span class="sxs-lookup"><span data-stu-id="84577-119">After the object name, add a period, the name of the method, and parentheses.</span></span> <span data-ttu-id="84577-120">Bağımsız değişkenler parantez içinde listelenir ve virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="84577-120">Arguments are listed within the parentheses, and are separated by commas.</span></span> <span data-ttu-id="84577-121">`Motorcycle` sınıfının yöntemleri, bu nedenle aşağıdaki örnekte olduğu gibi çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="84577-121">The methods of the `Motorcycle` class can therefore be called as in the following example:</span></span>

[!code-csharp[csProgGuideObjects#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#41)]

## <a name="method-parameters-vs-arguments"></a><span data-ttu-id="84577-122">Yöntem parametreleri ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="84577-122">Method parameters vs. arguments</span></span>

<span data-ttu-id="84577-123">Yöntem tanımı, gerekli parametrelerin adlarını ve türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="84577-123">The method definition specifies the names and types of any parameters that are required.</span></span> <span data-ttu-id="84577-124">Kodu çağırırken yöntemi çağırdığında, her parametre için bağımsız değişkenler olarak adlandırılan somut değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="84577-124">When calling code calls the method, it provides concrete values called arguments for each parameter.</span></span> <span data-ttu-id="84577-125">Bağımsız değişkenlerin parametre türüyle uyumlu olması gerekir, ancak çağıran kodda kullanılan bağımsız değişken adı (varsa) yöntemde tanımlanan parametre ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="84577-125">The arguments must be compatible with the parameter type but the argument name (if any) used in the calling code doesn't have to be the same as the parameter named defined in the method.</span></span> <span data-ttu-id="84577-126">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="84577-126">For example:</span></span>

[!code-csharp[csProgGuideObjects#74](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#74)]

## <a name="passing-by-reference-vs-passing-by-value"></a><span data-ttu-id="84577-127">Başvuruya göre geçirme-değere göre geçirme</span><span class="sxs-lookup"><span data-stu-id="84577-127">Passing by reference vs. passing by value</span></span>

<span data-ttu-id="84577-128">Varsayılan olarak, bir [değer türü](../../language-reference/builtin-types/value-types.md) örneği bir yönteme geçirildiğinde, kopyasının kendisi yerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="84577-128">By default, when an instance of a [value type](../../language-reference/builtin-types/value-types.md) is passed to a method, its copy is passed instead of the instance itself.</span></span> <span data-ttu-id="84577-129">Bu nedenle, bağımsız değişkende yapılan değişikliklerin, çağırma yönteminde orijinal örnek üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="84577-129">Therefore, changes to the argument have no effect on the original instance in the calling method.</span></span> <span data-ttu-id="84577-130">Değer türü örneği başvuruya göre geçirmek için `ref` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="84577-130">To pass a value-type instance by reference, use the `ref` keyword.</span></span> <span data-ttu-id="84577-131">Daha fazla bilgi için bkz. [değer türü parametrelerini geçirme](./passing-value-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="84577-131">For more information, see [Passing Value-Type Parameters](./passing-value-type-parameters.md).</span></span>

<span data-ttu-id="84577-132">Başvuru türündeki bir nesne yöntemine geçirildiğinde, nesnesine bir başvuru geçirilir.</span><span class="sxs-lookup"><span data-stu-id="84577-132">When an object of a reference type is passed to a method, a reference to the object is passed.</span></span> <span data-ttu-id="84577-133">Diğer bir deyişle, yöntem nesnenin kendisini değil, nesnenin konumunu gösteren bir bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="84577-133">That is, the method receives not the object itself but an argument that indicates the location of the object.</span></span> <span data-ttu-id="84577-134">Bu başvuruyu kullanarak nesnesinin bir üyesini değiştirirseniz, nesneyi değere göre iletseniz bile, değişiklik çağırma yöntemindeki bağımsız değişkende yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="84577-134">If you change a member of the object by using this reference, the change is reflected in the argument in the calling method, even if you pass the object by value.</span></span>

<span data-ttu-id="84577-135">Aşağıdaki örnekte gösterildiği gibi, `class` anahtar sözcüğünü kullanarak bir başvuru türü oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="84577-135">You create a reference type by using the `class` keyword, as the following example shows:</span></span>

[!code-csharp[csProgGuideObjects#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#42)]

<span data-ttu-id="84577-136">Artık, bu türü temel alan bir nesneyi bir yönteme geçirirseniz, nesnesine bir başvuru geçirilir.</span><span class="sxs-lookup"><span data-stu-id="84577-136">Now, if you pass an object that is based on this type to a method, a reference to the object is passed.</span></span> <span data-ttu-id="84577-137">Aşağıdaki örnek, `SampleRefType` `ModifyObject`yöntemine bir nesne geçirir:</span><span class="sxs-lookup"><span data-stu-id="84577-137">The following example passes an object of type `SampleRefType` to method `ModifyObject`:</span></span>

[!code-csharp[csProgGuideObjects#75](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#75)]

<span data-ttu-id="84577-138">Örnek temelde bir yönteme değere göre bir bağımsız değişken geçirdiğinden önceki örnekle aynı şeyi yapar.</span><span class="sxs-lookup"><span data-stu-id="84577-138">The example does essentially the same thing as the previous example in that it passes an argument by value to a method.</span></span> <span data-ttu-id="84577-139">Ancak, bir başvuru türü kullanıldığından, sonuç farklıdır.</span><span class="sxs-lookup"><span data-stu-id="84577-139">But, because a reference type is used, the result is different.</span></span> <span data-ttu-id="84577-140">`ModifyObject` ' de, parametresinin `value` alanına yapılan değişiklik `obj`, `rt`yönteminde `TestRefType` bağımsız değişkeninin `value` alanını da değiştirir.</span><span class="sxs-lookup"><span data-stu-id="84577-140">The modification that is made in `ModifyObject` to the `value` field of the parameter, `obj`, also changes the `value` field of the argument, `rt`, in the `TestRefType` method.</span></span> <span data-ttu-id="84577-141">`TestRefType` yöntemi çıkış olarak 33 görüntüler.</span><span class="sxs-lookup"><span data-stu-id="84577-141">The `TestRefType` method displays 33 as the output.</span></span>

<span data-ttu-id="84577-142">Başvuru türlerini başvuruya ve değere göre geçirme hakkında daha fazla bilgi için bkz. [başvuru türü parametrelerini](./passing-reference-type-parameters.md) ve [başvuru türlerini](../../language-reference/keywords/reference-types.md)geçirme.</span><span class="sxs-lookup"><span data-stu-id="84577-142">For more information about how to pass reference types by reference and by value, see [Passing Reference-Type Parameters](./passing-reference-type-parameters.md) and [Reference Types](../../language-reference/keywords/reference-types.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="84577-143">Döndürülen değerler</span><span class="sxs-lookup"><span data-stu-id="84577-143">Return values</span></span>

<span data-ttu-id="84577-144">Yöntemler çağırana bir değer döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="84577-144">Methods can return a value to the caller.</span></span> <span data-ttu-id="84577-145">Dönüş türü, yöntem adından önce listelenen tür `void`değilse, yöntemi `return` anahtar sözcüğünü kullanarak değeri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="84577-145">If the return type, the type listed before the method name, is not `void`, the method can return the value by using the `return` keyword.</span></span> <span data-ttu-id="84577-146">Dönüş türüyle eşleşen bir değer gelen `return` anahtar sözcüğünü içeren bir ifade, bu değeri çağıran metoda döndürür.</span><span class="sxs-lookup"><span data-stu-id="84577-146">A statement with the `return` keyword followed by a value that matches the return type will return that value to the method caller.</span></span>

<span data-ttu-id="84577-147">Değer, çağırarak değere göre veya 7,0 ile C# başlayarak [başvuruya göre](ref-returns.md)döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="84577-147">The value can be returned to the caller by value or, starting with C# 7.0, [by reference](ref-returns.md).</span></span> <span data-ttu-id="84577-148">Değer, yöntem imzasında `ref` anahtar sözcüğü kullanılıyorsa ve her bir `return` anahtar sözcüğünü takip eden başvuruya göre çağırana döndürülür.</span><span class="sxs-lookup"><span data-stu-id="84577-148">Values are returned to the caller by reference if the `ref` keyword is used in the method signature and it follows each `return` keyword.</span></span> <span data-ttu-id="84577-149">Örneğin, aşağıdaki yöntem imzası ve Return deyimleri, yöntemin çağırana başvuruya göre `estDistance` bir değişken adları döndürdüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="84577-149">For example, the following method signature and return statement indicate that the method returns a variable names `estDistance` by reference to the caller.</span></span>

```csharp
public ref double GetEstimatedDistance()
{
    return ref estDistance;
}
```

<span data-ttu-id="84577-150">`return` anahtar sözcüğü, yöntemin yürütülmesini de durduruyor.</span><span class="sxs-lookup"><span data-stu-id="84577-150">The `return` keyword also stops the execution of the method.</span></span> <span data-ttu-id="84577-151">Dönüş türü `void`ise, değer içermeyen bir `return` deyimin, metodun yürütülmesini durdurmak için yine de yararlı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="84577-151">If the return type is `void`, a `return` statement without a value is still useful to stop the execution of the method.</span></span> <span data-ttu-id="84577-152">`return` anahtar sözcüğü olmadan Yöntem, kod bloğunun sonuna ulaştığında yürütmeyi durdurur.</span><span class="sxs-lookup"><span data-stu-id="84577-152">Without the `return` keyword, the method will stop executing when it reaches the end of the code block.</span></span> <span data-ttu-id="84577-153">Void olmayan bir dönüş türüne sahip metotlar, bir değer döndürmek için `return` anahtar sözcüğünü kullanmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="84577-153">Methods with a non-void return type are required to use the `return` keyword to return a value.</span></span> <span data-ttu-id="84577-154">Örneğin, bu iki yöntem tamsayılar döndürmek için `return` anahtar sözcüğünü kullanır:</span><span class="sxs-lookup"><span data-stu-id="84577-154">For example, these two methods use the `return` keyword to return integers:</span></span>

[!code-csharp[csProgGuideObjects#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#44)]

<span data-ttu-id="84577-155">Bir yöntemden döndürülen bir değer kullanmak için, çağırma yöntemi yöntemi tek bir değer olan her yerde, aynı türde bir değer yeterli olacak şekilde kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="84577-155">To use a value returned from a method, the calling method can use the method call itself anywhere a value of the same type would be sufficient.</span></span> <span data-ttu-id="84577-156">Dönüş değerini bir değişkene de atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84577-156">You can also assign the return value to a variable.</span></span> <span data-ttu-id="84577-157">Örneğin, aşağıdaki iki kod örneği aynı hedefi yerine getirmektedir:</span><span class="sxs-lookup"><span data-stu-id="84577-157">For example, the following two code examples accomplish the same goal:</span></span>

[!code-csharp[csProgGuideObjects#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#45)]

[!code-csharp[csProgGuideObjects#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#46)]

<span data-ttu-id="84577-158">Bu durumda, bir değeri depolamak için `result`, yerel bir değişken kullanmak isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="84577-158">Using a local variable, in this case, `result`, to store a value is optional.</span></span> <span data-ttu-id="84577-159">Kodun okunabilirliğini yardımcı olabilir veya metodun tüm kapsamı için bağımsız değişkenin özgün değerini depolamanız gerekirse gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="84577-159">It may help the readability of the code, or it may be necessary if you need to store the original value of the argument for the entire scope of the method.</span></span>

<span data-ttu-id="84577-160">Bir yöntemden başvuruya göre döndürülen bir değeri kullanmak için, değerini değiştirmek istiyorsanız bir [ref yerel](ref-returns.md#ref-locals) değişkeni bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="84577-160">To use a value returned by reference from a method, you must declare a [ref local](ref-returns.md#ref-locals) variable if you intend to modify its value.</span></span> <span data-ttu-id="84577-161">Örneğin, `Planet.GetEstimatedDistance` yöntemi başvuruya göre bir <xref:System.Double> değeri döndürürse, bunu aşağıdaki gibi kodla bir ref yerel değişkeni olarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="84577-161">For example, if the `Planet.GetEstimatedDistance` method returns a <xref:System.Double> value by reference, you can define it as a ref local variable with code like the following:</span></span>

```csharp
ref int distance = plant
```

<span data-ttu-id="84577-162">Çağırma işlevi diziyi `M`geçirse, dizinin içeriğini değiştiren `M`bir yöntemden çok boyutlu bir dizi döndürmektir.</span><span class="sxs-lookup"><span data-stu-id="84577-162">Returning a multi-dimensional array from a method, `M`, that modifies the array's contents is not necessary if the calling function passed the array into `M`.</span></span>  <span data-ttu-id="84577-163">`M` elde edilen diziyi, iyi stil veya işlevsel akış için döndürebilir, ancak gerekli değildir çünkü C# tüm başvuru türlerini değere göre geçirir ve dizi başvurusunun değeri dizi işaretçisidir.</span><span class="sxs-lookup"><span data-stu-id="84577-163">You may return the resulting array from `M` for good style or functional flow of values, but it is not necessary because C# passes all reference types by value, and the value of an array reference is the pointer to the array.</span></span> <span data-ttu-id="84577-164">Yöntem `M`, dizideki içeriklerinde yapılan tüm değişiklikler, aşağıdaki örnekte gösterildiği gibi diziye başvuran herhangi bir kod tarafından Observable ' tır:</span><span class="sxs-lookup"><span data-stu-id="84577-164">In the method `M`, any changes to the array's contents are observable by any code that has a reference to the array, as shown in the following example:</span></span>

```csharp
static void Main(string[] args)
{
    int[,] matrix = new int[2, 2];
    FillMatrix(matrix);
    // matrix is now full of -1
}

public static void FillMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            matrix[i, j] = -1;
        }
    }
}
```

<span data-ttu-id="84577-165">Daha fazla bilgi için bkz. [Return](../../language-reference/keywords/return.md).</span><span class="sxs-lookup"><span data-stu-id="84577-165">For more information, see [return](../../language-reference/keywords/return.md).</span></span>

## <a name="async-methods"></a><span data-ttu-id="84577-166">Zaman uyumsuz yöntemler</span><span class="sxs-lookup"><span data-stu-id="84577-166">Async methods</span></span>

<span data-ttu-id="84577-167">Async özelliğini kullanarak, açık geri çağırmaları kullanmadan zaman uyumsuz yöntemleri çağırabilir veya kodunuzu birden çok yöntemde veya Lambda ifadelerinde el ile böedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84577-167">By using the async feature, you can invoke asynchronous methods without using explicit callbacks or manually splitting your code across multiple methods or lambda expressions.</span></span>

<span data-ttu-id="84577-168">[Zaman uyumsuz](../../language-reference/keywords/async.md) değiştiriciyle bir yöntemi işaretlerseniz, yönteminde [await](../../language-reference/operators/await.md) işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="84577-168">If you mark a method with the [async](../../language-reference/keywords/async.md) modifier, you can use the [await](../../language-reference/operators/await.md) operator in the method.</span></span> <span data-ttu-id="84577-169">Denetim zaman uyumsuz yöntemde bir await ifadesine ulaştığında denetim çağırana döner ve beklenen görev tamamlanana kadar yöntemdeki ilerleme durumu askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="84577-169">When control reaches an await expression in the async method, control returns to the caller, and progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="84577-170">Görev tamamlandığında, yürütme yöntemi içinde çalışmaya çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="84577-170">When the task is complete, execution can resume in the method.</span></span>

> [!NOTE]
> <span data-ttu-id="84577-171">Zaman uyumsuz bir yöntem, henüz tamamlanmamış olan ilk beklemiş nesneyle karşılaştığında çağırana döner veya zaman uyumsuz yöntemin sonuna kadar, hangisi önce gerçekleşiyorsa.</span><span class="sxs-lookup"><span data-stu-id="84577-171">An async method returns to the caller when either it encounters the first awaited object that’s not yet complete or it gets to the end of the async method, whichever occurs first.</span></span>

<span data-ttu-id="84577-172">Zaman uyumsuz bir yöntem <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>veya void dönüş türüne sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="84577-172">An async method can have a return type of <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, or void.</span></span> <span data-ttu-id="84577-173">Void dönüş türü birincil olarak, bir void dönüş türünün gerekli olduğu olay işleyicilerini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84577-173">The void return type is used primarily to define event handlers, where a void return type is required.</span></span> <span data-ttu-id="84577-174">Void döndüren zaman uyumsuz bir yöntem beklenemez ve void döndüren bir yöntemi çağıran yöntemin aldığı özel durumları yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="84577-174">An async method that returns void can't be awaited, and the caller of a void-returning method can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="84577-175">Aşağıdaki örnekte `DelayAsync`, dönüş türü <xref:System.Threading.Tasks.Task%601>olan zaman uyumsuz bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="84577-175">In the following example, `DelayAsync` is an async method that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="84577-176">`DelayAsync`, bir tamsayı döndüren bir `return` bildirimine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="84577-176">`DelayAsync` has a `return` statement that returns an integer.</span></span> <span data-ttu-id="84577-177">Bu nedenle `DelayAsync` yöntemi bildirimi `Task<int>`dönüş türüne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="84577-177">Therefore the method declaration of `DelayAsync` must have a return type of `Task<int>`.</span></span> <span data-ttu-id="84577-178">Dönüş türü `Task<int>`olduğundan, aşağıdaki deyimde gösterildiği gibi, `DoSomethingAsync` `await` ifadenin değerlendirmesi bir tamsayı üretir: `int result = await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="84577-178">Because the return type is `Task<int>`, the evaluation of the `await` expression in `DoSomethingAsync` produces an integer as the following statement demonstrates: `int result = await delayTask`.</span></span>

<span data-ttu-id="84577-179">`startButton_Click` yöntemi, void dönüş türüne sahip bir zaman uyumsuz metoda bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="84577-179">The `startButton_Click` method is an example of an async method that has a return type of void.</span></span> <span data-ttu-id="84577-180">`DoSomethingAsync` zaman uyumsuz bir yöntem olduğundan, aşağıdaki bildirimde gösterildiği gibi, `DoSomethingAsync` çağrısının görevi beklenmelidir: `await DoSomethingAsync();`.</span><span class="sxs-lookup"><span data-stu-id="84577-180">Because `DoSomethingAsync` is an async method, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `await DoSomethingAsync();`.</span></span> <span data-ttu-id="84577-181">Metodun bir `await` ifadesi olduğundan `startButton_Click` yöntemi `async` değiştiricisiyle tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="84577-181">The `startButton_Click` method must be defined with the `async` modifier because the method has an `await` expression.</span></span>

[!code-csharp[csAsyncMethod#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncmethod/cs/mainwindow.xaml.cs#2)]

<span data-ttu-id="84577-182">Zaman uyumsuz bir yöntem herhangi bir [ref](../../language-reference/keywords/ref.md) veya [Out](../../language-reference/keywords/out-parameter-modifier.md) parametresi bildiremez, ancak bu parametrelere sahip yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="84577-182">An async method can't declare any [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameters, but it can call methods that have such parameters.</span></span>

<span data-ttu-id="84577-183">Zaman uyumsuz yöntemler hakkında daha fazla bilgi için bkz. [Async ve await Ile zaman uyumsuz programlama](../concepts/async/index.md), [zaman uyumsuz programlarda denetim akışı](../concepts/async/control-flow-in-async-programs.md)ve [zaman uyumsuz dönüş türleri](../concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="84577-183">For more information about async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md), [Control Flow in Async Programs](../concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../concepts/async/async-return-types.md).</span></span>

## <a name="expression-body-definitions"></a><span data-ttu-id="84577-184">İfade gövdesi tanımları</span><span class="sxs-lookup"><span data-stu-id="84577-184">Expression body definitions</span></span>

<span data-ttu-id="84577-185">Yalnızca bir ifadenin sonucuyla hemen dönen veya yöntemin gövdesi olarak tek bir deyimi olan yöntem tanımlarının olması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="84577-185">It is common to have method definitions that simply return immediately with the result of an expression, or that have a single statement as the body of the method.</span></span> <span data-ttu-id="84577-186">`=>`kullanarak bu tür yöntemleri tanımlamaya yönelik bir sözdizimi kısayolu vardır:</span><span class="sxs-lookup"><span data-stu-id="84577-186">There is a syntax shortcut for defining such methods using `=>`:</span></span>

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

<span data-ttu-id="84577-187">Yöntem `void` döndürürse veya zaman uyumsuz bir yöntem ise, yöntemin gövdesi bir deyim ifadesi olmalıdır (Lambdalar ile aynı).</span><span class="sxs-lookup"><span data-stu-id="84577-187">If the method returns `void` or is an async method, then the body of the method must be a statement expression (same as with lambdas).</span></span> <span data-ttu-id="84577-188">Özellikler ve Dizin oluşturucular için, bunların salt okunmaları gerekir ve `get` erişimci anahtar sözcüğünü kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="84577-188">For properties and indexers, they must be read only, and you don't use the `get` accessor keyword.</span></span>

## <a name="iterators"></a><span data-ttu-id="84577-189">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="84577-189">Iterators</span></span>

<span data-ttu-id="84577-190">Yineleyici, bir koleksiyon üzerinde liste veya dizi gibi özel bir yineleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="84577-190">An iterator performs a custom iteration over a collection, such as a list or an array.</span></span> <span data-ttu-id="84577-191">Bir yineleyici, her öğeyi birer birer döndürmek için [yield return](../../language-reference/keywords/yield.md) ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="84577-191">An iterator uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="84577-192">Bir [yield return](../../language-reference/keywords/yield.md) ifadesine ulaşıldığında, koddaki geçerli konum hatırlanır.</span><span class="sxs-lookup"><span data-stu-id="84577-192">When a [yield return](../../language-reference/keywords/yield.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="84577-193">Yineleyici bir sonraki sefer çağrıldığında, yürütme o konumdan yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="84577-193">Execution is restarted from that location when the iterator is called the next time.</span></span>

<span data-ttu-id="84577-194">Bir [foreach](../../language-reference/keywords/foreach-in.md) ifadesi kullanarak istemci kodundan bir yineleyici çağırın.</span><span class="sxs-lookup"><span data-stu-id="84577-194">You call an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

<span data-ttu-id="84577-195">Yineleyicinin dönüş türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>veya <xref:System.Collections.Generic.IEnumerator%601>olabilir.</span><span class="sxs-lookup"><span data-stu-id="84577-195">The return type of an iterator can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="84577-196">Daha fazla bilgi için bkz. [yineleyiciler](../concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="84577-196">For more information, see [Iterators](../concepts/iterators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="84577-197">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="84577-197">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="84577-198">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84577-198">See also</span></span>

- [<span data-ttu-id="84577-199">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="84577-199">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="84577-200">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="84577-200">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="84577-201">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="84577-201">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="84577-202">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="84577-202">Static Classes and Static Class Members</span></span>](static-classes-and-static-class-members.md)
- [<span data-ttu-id="84577-203">Devralma</span><span class="sxs-lookup"><span data-stu-id="84577-203">Inheritance</span></span>](inheritance.md)
- [<span data-ttu-id="84577-204">Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="84577-204">Abstract and Sealed Classes and Class Members</span></span>](abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="84577-205">params</span><span class="sxs-lookup"><span data-stu-id="84577-205">params</span></span>](../../language-reference/keywords/params.md)
- [<span data-ttu-id="84577-206">return</span><span class="sxs-lookup"><span data-stu-id="84577-206">return</span></span>](../../language-reference/keywords/return.md)
- [<span data-ttu-id="84577-207">out</span><span class="sxs-lookup"><span data-stu-id="84577-207">out</span></span>](../../language-reference/keywords/out.md)
- [<span data-ttu-id="84577-208">ref</span><span class="sxs-lookup"><span data-stu-id="84577-208">ref</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="84577-209">Parametreleri Geçirme</span><span class="sxs-lookup"><span data-stu-id="84577-209">Passing Parameters</span></span>](passing-parameters.md)
