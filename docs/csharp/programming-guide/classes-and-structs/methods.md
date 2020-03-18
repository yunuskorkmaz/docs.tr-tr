---
title: Yöntemler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: 114fa2973c50be9a4199db9729e3cd9ea6122866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626535"
---
# <a name="methods-c-programming-guide"></a><span data-ttu-id="6794c-102">Yöntemler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6794c-102">Methods (C# Programming Guide)</span></span>

<span data-ttu-id="6794c-103">Yöntem, bir dizi deyim içeren bir kod bloğudur.</span><span class="sxs-lookup"><span data-stu-id="6794c-103">A method is a code block that contains a series of statements.</span></span> <span data-ttu-id="6794c-104">Program, yöntem çağırArak ve gerekli yöntem bağımsız değişkenlerini belirterek deyimlerin yürütülmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="6794c-104">A program causes the statements to be executed by calling the method and specifying any required method arguments.</span></span> <span data-ttu-id="6794c-105">C#'da, çalıştırılan her yönerge bir yöntem bağlamında gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6794c-105">In C#, every executed instruction is performed in the context of a method.</span></span> <span data-ttu-id="6794c-106">Yöntem, `Main` her C# uygulamasının giriş noktasıdır ve program başlatıldığında ortak dil çalışma süresi (CLR) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6794c-106">The `Main` method is the entry point for every C# application and it's called by the common language runtime (CLR) when the program is started.</span></span>

> [!NOTE]
> <span data-ttu-id="6794c-107">Bu makalede, adlandırılmış yöntemler anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6794c-107">This article discusses named methods.</span></span> <span data-ttu-id="6794c-108">Anonim işlevler hakkında bilgi için [Bkz. Anonim Fonksiyonlar.](../statements-expressions-operators/anonymous-functions.md)</span><span class="sxs-lookup"><span data-stu-id="6794c-108">For information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>

## <a name="method-signatures"></a><span data-ttu-id="6794c-109">Yöntem imzaları</span><span class="sxs-lookup"><span data-stu-id="6794c-109">Method signatures</span></span>

<span data-ttu-id="6794c-110">Yöntemler, bir [sınıf,](../../language-reference/keywords/class.md) [yapı](../../language-reference/builtin-types/struct.md)veya [arabirim](../interfaces/index.md) gibi erişim düzeyi `public` veya `private`, iade değeri, `abstract` `sealed`yöntemin adı ve herhangi bir yöntem parametreleri gibi isteğe bağlı değiştiriciler belirterek bildirilir.</span><span class="sxs-lookup"><span data-stu-id="6794c-110">Methods are declared in a [class](../../language-reference/keywords/class.md), [struct](../../language-reference/builtin-types/struct.md), or [interface](../interfaces/index.md) by specifying the access level such as `public` or `private`, optional modifiers such as `abstract` or `sealed`, the return value, the name of the method, and any method parameters.</span></span> <span data-ttu-id="6794c-111">Bu parçalar birlikte yöntemin imzasıdır.</span><span class="sxs-lookup"><span data-stu-id="6794c-111">These parts together are the signature of the method.</span></span>

> [!NOTE]
> <span data-ttu-id="6794c-112">Yöntemin dönüş türü, yöntem aşırı yükleme amacıyla yöntemin imzasının bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="6794c-112">A return type of a method is not part of the signature of the method for the purposes of method overloading.</span></span> <span data-ttu-id="6794c-113">Ancak, bir temsilci ve işaret ettiği yöntem arasındaki uyumluluğu belirlerken yöntemin imzasının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="6794c-113">However, it is part of the signature of the method when determining the compatibility between a delegate and the method that it points to.</span></span>

<span data-ttu-id="6794c-114">Yöntem parametreleri parantez içinde eklenir ve virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="6794c-114">Method parameters are enclosed in parentheses and are separated by commas.</span></span> <span data-ttu-id="6794c-115">Boş parantezler yöntemin parametre gerektirmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6794c-115">Empty parentheses indicate that the method requires no parameters.</span></span> <span data-ttu-id="6794c-116">Bu sınıf dört yöntem içerir:</span><span class="sxs-lookup"><span data-stu-id="6794c-116">This class contains four methods:</span></span>

[!code-csharp[csProgGuideObjects#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#40)]

## <a name="method-access"></a><span data-ttu-id="6794c-117">Yöntem erişimi</span><span class="sxs-lookup"><span data-stu-id="6794c-117">Method access</span></span>

<span data-ttu-id="6794c-118">Bir nesne üzerinde yöntem çağırmak, bir alana erişmek gibidir.</span><span class="sxs-lookup"><span data-stu-id="6794c-118">Calling a method on an object is like accessing a field.</span></span> <span data-ttu-id="6794c-119">Nesne adından sonra, bir nokta, yöntemin adını ekleyin ve parantez.</span><span class="sxs-lookup"><span data-stu-id="6794c-119">After the object name, add a period, the name of the method, and parentheses.</span></span> <span data-ttu-id="6794c-120">Bağımsız değişkenler parantez içinde listelenir ve virgülle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="6794c-120">Arguments are listed within the parentheses, and are separated by commas.</span></span> <span data-ttu-id="6794c-121">Bu nedenle `Motorcycle` sınıfın yöntemleri aşağıdaki örnekte olduğu gibi çağrılabilir:</span><span class="sxs-lookup"><span data-stu-id="6794c-121">The methods of the `Motorcycle` class can therefore be called as in the following example:</span></span>

[!code-csharp[csProgGuideObjects#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#41)]

## <a name="method-parameters-vs-arguments"></a><span data-ttu-id="6794c-122">Yöntem parametreleri ve bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="6794c-122">Method parameters vs. arguments</span></span>

<span data-ttu-id="6794c-123">Yöntem tanımı, gerekli parametrelerin adlarını ve türlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6794c-123">The method definition specifies the names and types of any parameters that are required.</span></span> <span data-ttu-id="6794c-124">Kod çağırıldığında yöntem çağırır, her parametre için bağımsız değişken adı verilen somut değerler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6794c-124">When calling code calls the method, it provides concrete values called arguments for each parameter.</span></span> <span data-ttu-id="6794c-125">Bağımsız değişkenler parametre türüyle uyumlu olmalıdır, ancak çağrı kodunda kullanılan bağımsız değişken adı (varsa) yöntemde tanımlanan parametreyle aynı olmak zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="6794c-125">The arguments must be compatible with the parameter type but the argument name (if any) used in the calling code doesn't have to be the same as the parameter named defined in the method.</span></span> <span data-ttu-id="6794c-126">Örnek:</span><span class="sxs-lookup"><span data-stu-id="6794c-126">For example:</span></span>

[!code-csharp[csProgGuideObjects#74](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#74)]

## <a name="passing-by-reference-vs-passing-by-value"></a><span data-ttu-id="6794c-127">Referansa göre geçiş ve değere göre geçme</span><span class="sxs-lookup"><span data-stu-id="6794c-127">Passing by reference vs. passing by value</span></span>

<span data-ttu-id="6794c-128">Varsayılan olarak, bir [değer türü](../../language-reference/builtin-types/value-types.md) örneği bir yönteme geçirildiğinde, kopya örneği kendisi yerine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="6794c-128">By default, when an instance of a [value type](../../language-reference/builtin-types/value-types.md) is passed to a method, its copy is passed instead of the instance itself.</span></span> <span data-ttu-id="6794c-129">Bu nedenle, bağımsız değişkendeğişiklikleri arama yönteminde özgün örnek üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6794c-129">Therefore, changes to the argument have no effect on the original instance in the calling method.</span></span> <span data-ttu-id="6794c-130">Başvuru yla değer türü örneği geçmek `ref` için anahtar sözcüğü kullanın.</span><span class="sxs-lookup"><span data-stu-id="6794c-130">To pass a value-type instance by reference, use the `ref` keyword.</span></span> <span data-ttu-id="6794c-131">Daha fazla bilgi için [Bkz. Değer Türü Parametreleri Geçme.](./passing-value-type-parameters.md)</span><span class="sxs-lookup"><span data-stu-id="6794c-131">For more information, see [Passing Value-Type Parameters](./passing-value-type-parameters.md).</span></span>

<span data-ttu-id="6794c-132">Başvuru türünden bir nesne bir yönteme geçirildiğinde, nesneye bir başvuru geçirilir.</span><span class="sxs-lookup"><span data-stu-id="6794c-132">When an object of a reference type is passed to a method, a reference to the object is passed.</span></span> <span data-ttu-id="6794c-133">Diğer bir zamanda, yöntem nesnenin kendisini değil, nesnenin konumunu gösteren bir bağımsız değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="6794c-133">That is, the method receives not the object itself but an argument that indicates the location of the object.</span></span> <span data-ttu-id="6794c-134">Bu başvuruyu kullanarak nesnenin bir üyesini değiştirirseniz, nesneyi değere göre geçirseniz bile değişiklik arama yöntemindeki bağımsız değişkene yansıtılır.</span><span class="sxs-lookup"><span data-stu-id="6794c-134">If you change a member of the object by using this reference, the change is reflected in the argument in the calling method, even if you pass the object by value.</span></span>

<span data-ttu-id="6794c-135">Aşağıdaki örnekte görüldüğü `class` gibi, anahtar kelimeyi kullanarak bir başvuru türü oluşturursunuz:</span><span class="sxs-lookup"><span data-stu-id="6794c-135">You create a reference type by using the `class` keyword, as the following example shows:</span></span>

[!code-csharp[csProgGuideObjects#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#42)]

<span data-ttu-id="6794c-136">Şimdi, bu türe dayalı bir nesneyi bir yönteme geçirirseniz, nesneye bir başvuru geçirilir.</span><span class="sxs-lookup"><span data-stu-id="6794c-136">Now, if you pass an object that is based on this type to a method, a reference to the object is passed.</span></span> <span data-ttu-id="6794c-137">Aşağıdaki örnek, yönteme `SampleRefType` `ModifyObject`bir tür nesnesi geçer:</span><span class="sxs-lookup"><span data-stu-id="6794c-137">The following example passes an object of type `SampleRefType` to method `ModifyObject`:</span></span>

[!code-csharp[csProgGuideObjects#75](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#75)]

<span data-ttu-id="6794c-138">Örnek, bir bağımsız değişkeni bir yönteme değer olarak geçirmesinde önceki örnekle temelde aynı şeyi yapar.</span><span class="sxs-lookup"><span data-stu-id="6794c-138">The example does essentially the same thing as the previous example in that it passes an argument by value to a method.</span></span> <span data-ttu-id="6794c-139">Ancak, bir başvuru türü kullanıldığından, sonuç farklıdır.</span><span class="sxs-lookup"><span data-stu-id="6794c-139">But, because a reference type is used, the result is different.</span></span> <span data-ttu-id="6794c-140">Parametre `ModifyObject` `value` alanında yapılan değişiklik, `obj`aynı zamanda yöntemde `value` `rt` `TestRefType` bağımsız değişkenalanını değiştirir.</span><span class="sxs-lookup"><span data-stu-id="6794c-140">The modification that is made in `ModifyObject` to the `value` field of the parameter, `obj`, also changes the `value` field of the argument, `rt`, in the `TestRefType` method.</span></span> <span data-ttu-id="6794c-141">Yöntem `TestRefType` çıktı olarak 33 görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6794c-141">The `TestRefType` method displays 33 as the output.</span></span>

<span data-ttu-id="6794c-142">Referans türlerinin başvuru ve değere göre nasıl geçirilen hakkında [Reference Types](../../language-reference/keywords/reference-types.md)daha fazla bilgi için [bkz.](./passing-reference-type-parameters.md)</span><span class="sxs-lookup"><span data-stu-id="6794c-142">For more information about how to pass reference types by reference and by value, see [Passing Reference-Type Parameters](./passing-reference-type-parameters.md) and [Reference Types](../../language-reference/keywords/reference-types.md).</span></span>

## <a name="return-values"></a><span data-ttu-id="6794c-143">Döndürülen değerler</span><span class="sxs-lookup"><span data-stu-id="6794c-143">Return values</span></span>

<span data-ttu-id="6794c-144">Yöntemler arayana bir değer döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="6794c-144">Methods can return a value to the caller.</span></span> <span data-ttu-id="6794c-145">İade türü, yöntem adından önce listelenen tür, değilse, `void`yöntem `return` anahtar sözcüğü kullanarak değeri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="6794c-145">If the return type, the type listed before the method name, is not `void`, the method can return the value by using the `return` keyword.</span></span> <span data-ttu-id="6794c-146">Anahtar kelimenin `return` ardından gelen bir değerin ardından gelen bir ifade, bu değeri yöntem arayana döndürecektir.</span><span class="sxs-lookup"><span data-stu-id="6794c-146">A statement with the `return` keyword followed by a value that matches the return type will return that value to the method caller.</span></span>

<span data-ttu-id="6794c-147">Değer, arayana değer veya C# 7.0 ile başlayarak [referans olarak](ref-returns.md)döndürülebilir.</span><span class="sxs-lookup"><span data-stu-id="6794c-147">The value can be returned to the caller by value or, starting with C# 7.0, [by reference](ref-returns.md).</span></span> <span data-ttu-id="6794c-148">`ref` Anahtar kelime yöntem imzasında kullanılıyorsa ve her `return` anahtar kelimeyi izliyorsa, değerler başvuru tarafından arayanın döndürülür.</span><span class="sxs-lookup"><span data-stu-id="6794c-148">Values are returned to the caller by reference if the `ref` keyword is used in the method signature and it follows each `return` keyword.</span></span> <span data-ttu-id="6794c-149">Örneğin, aşağıdaki yöntem imza ve return deyimi, yöntemin `estDistance` arayana atıfta bulunarak bir değişken adlarını döndürür olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6794c-149">For example, the following method signature and return statement indicate that the method returns a variable names `estDistance` by reference to the caller.</span></span>

```csharp
public ref double GetEstimatedDistance()
{
    return ref estDistance;
}
```

<span data-ttu-id="6794c-150">Anahtar `return` kelime de yöntemin yürütülmesini durdurur.</span><span class="sxs-lookup"><span data-stu-id="6794c-150">The `return` keyword also stops the execution of the method.</span></span> <span data-ttu-id="6794c-151">İade türü ise, `void` `return` değeri olmayan bir deyim, yöntemin yürütülmesini durdurmak için yine de yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="6794c-151">If the return type is `void`, a `return` statement without a value is still useful to stop the execution of the method.</span></span> <span data-ttu-id="6794c-152">`return` Anahtar kelime olmadan, yöntem kod bloğunun sonuna ulaştığında yürütmeyi durdurur.</span><span class="sxs-lookup"><span data-stu-id="6794c-152">Without the `return` keyword, the method will stop executing when it reaches the end of the code block.</span></span> <span data-ttu-id="6794c-153">Geçersiz olmayan bir iade türüne sahip `return` yöntemlerin, bir değeri döndürmek için anahtar sözcüğü kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6794c-153">Methods with a non-void return type are required to use the `return` keyword to return a value.</span></span> <span data-ttu-id="6794c-154">Örneğin, bu iki yöntem, sonlu ları döndürmek için `return` anahtar sözcüğü kullanır:</span><span class="sxs-lookup"><span data-stu-id="6794c-154">For example, these two methods use the `return` keyword to return integers:</span></span>

[!code-csharp[csProgGuideObjects#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#44)]

<span data-ttu-id="6794c-155">Bir yöntemden döndürülen bir değeri kullanmak için, arama yöntemi nin kendisini her yerde aynı türde bir değerin yeterli olduğu her yerde çağırın yöntemini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="6794c-155">To use a value returned from a method, the calling method can use the method call itself anywhere a value of the same type would be sufficient.</span></span> <span data-ttu-id="6794c-156">İade değerini bir değişkene de atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6794c-156">You can also assign the return value to a variable.</span></span> <span data-ttu-id="6794c-157">Örneğin, aşağıdaki iki kod örneği aynı amacı gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="6794c-157">For example, the following two code examples accomplish the same goal:</span></span>

[!code-csharp[csProgGuideObjects#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#45)]

[!code-csharp[csProgGuideObjects#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#46)]

<span data-ttu-id="6794c-158">Yerel bir değişkenkullanarak, bu `result`durumda, bir değeri depolamak için isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6794c-158">Using a local variable, in this case, `result`, to store a value is optional.</span></span> <span data-ttu-id="6794c-159">Kodun okunabilirliğine yardımcı olabilir veya yöntemin tüm kapsamı için bağımsız değişkenin özgün değerini depolamanız gerekiyorsa gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="6794c-159">It may help the readability of the code, or it may be necessary if you need to store the original value of the argument for the entire scope of the method.</span></span>

<span data-ttu-id="6794c-160">Bir yöntemden referans la döndürülen bir değeri kullanmak için, değerini değiştirmek istiyorsanız [bir ref yerel](ref-returns.md#ref-locals) değişkeni bildirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6794c-160">To use a value returned by reference from a method, you must declare a [ref local](ref-returns.md#ref-locals) variable if you intend to modify its value.</span></span> <span data-ttu-id="6794c-161">Örneğin, `Planet.GetEstimatedDistance` yöntem başvuru yla <xref:System.Double> bir değer döndürürse, onu aşağıdaki gibi kodlu bir ref yerel değişkenolarak tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6794c-161">For example, if the `Planet.GetEstimatedDistance` method returns a <xref:System.Double> value by reference, you can define it as a ref local variable with code like the following:</span></span>

```csharp
ref int distance = plant
```

<span data-ttu-id="6794c-162">Bir yöntemden çok boyutlu bir `M`dizi döndürme, arama işlevi dizi geçti `M`eğer dizinin içeriğini değiştiren gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6794c-162">Returning a multi-dimensional array from a method, `M`, that modifies the array's contents is not necessary if the calling function passed the array into `M`.</span></span>  <span data-ttu-id="6794c-163">İyi stil veya işlevsel `M` değerler akışı için elde edilen diziyi döndürebilirsiniz, ancak C# tüm başvuru türlerini değere göre geçtiği ve dizi referansının değeri diziişaretçisi olduğundan bu gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6794c-163">You may return the resulting array from `M` for good style or functional flow of values, but it is not necessary because C# passes all reference types by value, and the value of an array reference is the pointer to the array.</span></span> <span data-ttu-id="6794c-164">Yöntemde, `M`dizinin içeriğindeki herhangi bir değişiklik, aşağıdaki örnekte gösterildiği gibi, diziye başvuru olan herhangi bir kod tarafından gözlemlenebilir:</span><span class="sxs-lookup"><span data-stu-id="6794c-164">In the method `M`, any changes to the array's contents are observable by any code that has a reference to the array, as shown in the following example:</span></span>

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

<span data-ttu-id="6794c-165">Daha fazla bilgi için [return'e](../../language-reference/keywords/return.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="6794c-165">For more information, see [return](../../language-reference/keywords/return.md).</span></span>

## <a name="async-methods"></a><span data-ttu-id="6794c-166">Async yöntemleri</span><span class="sxs-lookup"><span data-stu-id="6794c-166">Async methods</span></span>

<span data-ttu-id="6794c-167">Async özelliğini kullanarak, açık geri aramalar kullanmadan veya kodunuzu birden çok yöntem veya lambda ifadeleri arasında el ile bölmeden eşzamanlı yöntemler çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6794c-167">By using the async feature, you can invoke asynchronous methods without using explicit callbacks or manually splitting your code across multiple methods or lambda expressions.</span></span>

<span data-ttu-id="6794c-168">Bir yöntemi [async](../../language-reference/keywords/async.md) değiştirici ile işaretlerseniz, yöntemde [bekleme](../../language-reference/operators/await.md) işlecini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6794c-168">If you mark a method with the [async](../../language-reference/keywords/async.md) modifier, you can use the [await](../../language-reference/operators/await.md) operator in the method.</span></span> <span data-ttu-id="6794c-169">Denetim async yönteminde bir bekleme ifadesine ulaştığında, denetim arayana döndürür ve beklenen görev tamamlanana kadar yöntemdeki ilerleme askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="6794c-169">When control reaches an await expression in the async method, control returns to the caller, and progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="6794c-170">Görev tamamlandığında, yürütme yöntemde devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="6794c-170">When the task is complete, execution can resume in the method.</span></span>

> [!NOTE]
> <span data-ttu-id="6794c-171">Async yöntemi, henüz tamamlanmamış ilk beklenen nesneyle karşılaştığında veya önce hangisi gerçekleşirse async yönteminin sonuna geldiğinde arayanın karşısına geçer.</span><span class="sxs-lookup"><span data-stu-id="6794c-171">An async method returns to the caller when either it encounters the first awaited object that’s not yet complete or it gets to the end of the async method, whichever occurs first.</span></span>

<span data-ttu-id="6794c-172">Bir async yöntemi <xref:System.Threading.Tasks.Task%601>, , <xref:System.Threading.Tasks.Task>veya geçersiz bir dönüş türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="6794c-172">An async method can have a return type of <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, or void.</span></span> <span data-ttu-id="6794c-173">Geçersiz dönüş türü öncelikle geçersiz dönüş türünün gerekli olduğu olay işleyicilerini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6794c-173">The void return type is used primarily to define event handlers, where a void return type is required.</span></span> <span data-ttu-id="6794c-174">Geçersiz liği döndüren bir async yöntemi beklenebilir ve boşluk döndüren bir yöntemin arayan ı, yöntemin attığı özel durumları yakalayamaz.</span><span class="sxs-lookup"><span data-stu-id="6794c-174">An async method that returns void can't be awaited, and the caller of a void-returning method can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="6794c-175">Aşağıdaki örnekte, `DelayAsync` bir dönüş türü olan bir <xref:System.Threading.Tasks.Task%601>async yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="6794c-175">In the following example, `DelayAsync` is an async method that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="6794c-176">`DelayAsync`bir `return` tamsayı döndüren bir ifadesi vardır.</span><span class="sxs-lookup"><span data-stu-id="6794c-176">`DelayAsync` has a `return` statement that returns an integer.</span></span> <span data-ttu-id="6794c-177">Bu nedenle yöntem `DelayAsync` bildirimibir `Task<int>`dönüş türü olmalıdır .</span><span class="sxs-lookup"><span data-stu-id="6794c-177">Therefore the method declaration of `DelayAsync` must have a return type of `Task<int>`.</span></span> <span data-ttu-id="6794c-178">İade türü `Task<int>`olduğundan, aşağıdaki ifadenin gösterdiği gibi bir insalı `await` `DoSomethingAsync` üretir `int result = await delayTask`ifadenin değerlendirilmesi: .</span><span class="sxs-lookup"><span data-stu-id="6794c-178">Because the return type is `Task<int>`, the evaluation of the `await` expression in `DoSomethingAsync` produces an integer as the following statement demonstrates: `int result = await delayTask`.</span></span>

<span data-ttu-id="6794c-179">Yöntem, `startButton_Click` bir boşluk dönüş türü olan bir async yönteminin bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="6794c-179">The `startButton_Click` method is an example of an async method that has a return type of void.</span></span> <span data-ttu-id="6794c-180">Async yöntemi `DoSomethingAsync` olduğundan, aşağıdaki ifadede `DoSomethingAsync` görüldüğü gibi, çağrı için görev `await DoSomethingAsync();`in beklenmesi gerekir: .</span><span class="sxs-lookup"><span data-stu-id="6794c-180">Because `DoSomethingAsync` is an async method, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `await DoSomethingAsync();`.</span></span> <span data-ttu-id="6794c-181">`startButton_Click` Yöntem bir `await` ifade olduğundan yöntem `async` değiştirici ile tanımlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6794c-181">The `startButton_Click` method must be defined with the `async` modifier because the method has an `await` expression.</span></span>

[!code-csharp[csAsyncMethod#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncmethod/cs/mainwindow.xaml.cs#2)]

<span data-ttu-id="6794c-182">Bir async yöntemi herhangi bir [ref](../../language-reference/keywords/ref.md) veya [çıkış](../../language-reference/keywords/out-parameter-modifier.md) parametreleri bildiremez, ancak bu tür parametrelere sahip yöntemleri çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="6794c-182">An async method can't declare any [ref](../../language-reference/keywords/ref.md) or [out](../../language-reference/keywords/out-parameter-modifier.md) parameters, but it can call methods that have such parameters.</span></span>

<span data-ttu-id="6794c-183">Async yöntemleri hakkında daha fazla bilgi için, [async ile Asynchronous Programlama](../concepts/async/index.md)bakın ve bekliyor , [Async Programları Kontrol Akışı](../concepts/async/control-flow-in-async-programs.md), ve [Async İade Türleri](../concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="6794c-183">For more information about async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md), [Control Flow in Async Programs](../concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../concepts/async/async-return-types.md).</span></span>

## <a name="expression-body-definitions"></a><span data-ttu-id="6794c-184">İfade gövdesi tanımları</span><span class="sxs-lookup"><span data-stu-id="6794c-184">Expression body definitions</span></span>

<span data-ttu-id="6794c-185">Yalnızca bir ifadenin sonucuyla hemen dönen veya yöntemin gövdesi olarak tek bir ifadeye sahip yöntem tanımlarına sahip olması yaygındır.</span><span class="sxs-lookup"><span data-stu-id="6794c-185">It is common to have method definitions that simply return immediately with the result of an expression, or that have a single statement as the body of the method.</span></span> <span data-ttu-id="6794c-186">Bu tür yöntemleri tanımlamak için bir sözdizimi kısayolu vardır: `=>`</span><span class="sxs-lookup"><span data-stu-id="6794c-186">There is a syntax shortcut for defining such methods using `=>`:</span></span>

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

<span data-ttu-id="6794c-187">Yöntem döndürür `void` veya bir async yöntemi ise, o zaman yöntemin gövdesi bir deyim ifadesi olmalıdır (lambdas ile aynı).</span><span class="sxs-lookup"><span data-stu-id="6794c-187">If the method returns `void` or is an async method, then the body of the method must be a statement expression (same as with lambdas).</span></span> <span data-ttu-id="6794c-188">Özellikler ve dizin leyiciler için yalnızca okunması gerekir ve `get` erişimci anahtar sözcüğü kullanmazsınız.</span><span class="sxs-lookup"><span data-stu-id="6794c-188">For properties and indexers, they must be read only, and you don't use the `get` accessor keyword.</span></span>

## <a name="iterators"></a><span data-ttu-id="6794c-189">Yineleyiciler</span><span class="sxs-lookup"><span data-stu-id="6794c-189">Iterators</span></span>

<span data-ttu-id="6794c-190">Yineleyici, liste veya dizi gibi bir koleksiyon üzerinde özel bir yineleme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="6794c-190">An iterator performs a custom iteration over a collection, such as a list or an array.</span></span> <span data-ttu-id="6794c-191">Bir yineleyici, her öğeyi birer birer döndürmek için [verim iade](../../language-reference/keywords/yield.md) deyimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6794c-191">An iterator uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="6794c-192">Bir [verim iade](../../language-reference/keywords/yield.md) deyimine ulaşıldığında, koddaki geçerli konum hatırlanır.</span><span class="sxs-lookup"><span data-stu-id="6794c-192">When a [yield return](../../language-reference/keywords/yield.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="6794c-193">Yineleyici bir sonraki seferde çağrıldığında yürütme bu konumdan yeniden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="6794c-193">Execution is restarted from that location when the iterator is called the next time.</span></span>

<span data-ttu-id="6794c-194">[Her](../../language-reference/keywords/foreach-in.md) bir deyim kullanarak istemci kodundan bir yineleyici çağırırsınız.</span><span class="sxs-lookup"><span data-stu-id="6794c-194">You call an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement.</span></span>

<span data-ttu-id="6794c-195">Bir yineleyicinin dönüş türü <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, <xref:System.Collections.Generic.IEnumerator%601>veya .</span><span class="sxs-lookup"><span data-stu-id="6794c-195">The return type of an iterator can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="6794c-196">Daha fazla bilgi için [bkz.](../concepts/iterators.md)</span><span class="sxs-lookup"><span data-stu-id="6794c-196">For more information, see [Iterators](../concepts/iterators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6794c-197">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6794c-197">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6794c-198">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6794c-198">See also</span></span>

- [<span data-ttu-id="6794c-199">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6794c-199">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6794c-200">Sınıflar ve Structs</span><span class="sxs-lookup"><span data-stu-id="6794c-200">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="6794c-201">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="6794c-201">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="6794c-202">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="6794c-202">Static Classes and Static Class Members</span></span>](static-classes-and-static-class-members.md)
- [<span data-ttu-id="6794c-203">Devralma</span><span class="sxs-lookup"><span data-stu-id="6794c-203">Inheritance</span></span>](inheritance.md)
- [<span data-ttu-id="6794c-204">Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="6794c-204">Abstract and Sealed Classes and Class Members</span></span>](abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="6794c-205">params</span><span class="sxs-lookup"><span data-stu-id="6794c-205">params</span></span>](../../language-reference/keywords/params.md)
- [<span data-ttu-id="6794c-206">return</span><span class="sxs-lookup"><span data-stu-id="6794c-206">return</span></span>](../../language-reference/keywords/return.md)
- [<span data-ttu-id="6794c-207">çıkış</span><span class="sxs-lookup"><span data-stu-id="6794c-207">out</span></span>](../../language-reference/keywords/out.md)
- [<span data-ttu-id="6794c-208">Referans</span><span class="sxs-lookup"><span data-stu-id="6794c-208">ref</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="6794c-209">Parametreleri Geçirme</span><span class="sxs-lookup"><span data-stu-id="6794c-209">Passing Parameters</span></span>](passing-parameters.md)
