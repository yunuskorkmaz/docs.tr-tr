---
title: Ref dönüş değerleri ve ref Yereller (C# Kılavuzu)
description: Ref dönüş ve ref yerel değerleri tanımlayın ve nasıl kullanılacağını öğrenin
author: rpetrusha
ms.author: ronpet
ms.date: 01/23/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: c37c6dd61ae02813bcc467982f3b175da9136e4a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2018
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="e6947-103">Ref döndürür ve ref Yereller</span><span class="sxs-lookup"><span data-stu-id="e6947-103">Ref returns and ref locals</span></span>

<span data-ttu-id="e6947-104">C# 7 ile başlayan, C# başvurusu dönüş değerleri (başvuru dönüşleri) destekler.</span><span class="sxs-lookup"><span data-stu-id="e6947-104">Starting with C# 7, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="e6947-105">Bir başvuru dönüş değeri bir değer yerine bir değişken başvurusu çağırana geri dönmek tek bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="e6947-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="e6947-106">Çağıran, daha sonra döndürülen değişkeni değere veya başvuruya göre döndürülmedi sanki işlemek seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6947-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="e6947-107">Çağıran bir ref yerel olarak adlandırılan döndürülen değer, başvuru kendisi yeni bir değişken oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6947-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="e6947-108">Bir başvuru dönüş değeri nedir?</span><span class="sxs-lookup"><span data-stu-id="e6947-108">What is a reference return value?</span></span>

<span data-ttu-id="e6947-109">Çoğu geliştirici çağrılan yöntemi için bağımsız değişken geçirme ile bilginiz *başvuruya göre*.</span><span class="sxs-lookup"><span data-stu-id="e6947-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="e6947-110">Çağrılan yöntemin bağımsız değişken listesi başvuruya göre geçirilen bir değişken ve değerine çağrılan yöntemi tarafından yapılan değişiklikleri içerir çağıran tarafından gözlenen.</span><span class="sxs-lookup"><span data-stu-id="e6947-110">A called method's argument list includes a variable passed by reference, and any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="e6947-111">A *başvuru dönüş değeri* yöntemi döndürür anlamına gelir bir *başvuru* (veya diğer ad) yöntemin dönüş yöntemi kapsamını içerir ve, yaşam süresi bazı değişkenine genişletmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6947-111">A *reference return value* means that a method returns a *reference* (or an alias) to some variable whose scope includes the method and whose lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="e6947-112">Yöntemin dönüş değeri çağıran tarafından yapılan değişiklikler yöntemi tarafından döndürülen değişkeni yapılır.</span><span class="sxs-lookup"><span data-stu-id="e6947-112">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="e6947-113">Bir yöntem döndüren bildirme bir *başvuru dönüş değeri* yöntemi bir değişkene bir diğer ad döndürdüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6947-113">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="e6947-114">Tasarım hedefi çağıran kodu değişken değiştirmek için de dahil olmak üzere diğer ad üzerinden erişimi olması gerektiğini görülür.</span><span class="sxs-lookup"><span data-stu-id="e6947-114">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="e6947-115">Başvuruya göre döndüren yöntemler dönüş türüne sahip olamaz izleyen `void`.</span><span class="sxs-lookup"><span data-stu-id="e6947-115">It follows that methods returning by reference cannot have the return type `void`.</span></span>

<span data-ttu-id="e6947-116">Bir yöntem başvuru dönüş değeri olarak döndürebilir ifade bazı kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="e6947-116">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="e6947-117">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e6947-117">These include:</span></span>

- <span data-ttu-id="e6947-118">Dönüş değeri yönteminin yürütülmesi genişleten bir yaşam süresi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e6947-118">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="e6947-119">Diğer bir deyişle, onu döndüren yöntemi yerel bir değişkende olamaz.</span><span class="sxs-lookup"><span data-stu-id="e6947-119">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="e6947-120">Bu yönteme geçirilen bağımsız değişken olabilir veya bir örneği veya sınıfının statik alanı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e6947-120">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="e6947-121">Derleyici Hatası CS8168, yerel bir değişken oluşturur dönüş çalışılırken "döndüremiyor yerel 'obj' başvuruya göre yerel bir ref olmadığından."</span><span class="sxs-lookup"><span data-stu-id="e6947-121">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="e6947-122">Dönüş değeri sabit olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="e6947-122">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="e6947-123">Döndürülecek çalışırken `null` derleyici hatası "bir ifade başvuruya göre döndürülemez olduğundan bu bağlamda kullanılamaz." CS8156 oluşturur</span><span class="sxs-lookup"><span data-stu-id="e6947-123">Attempting to return `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="e6947-124">Ref dönüş yöntemiyle bir diğer ad değeri şu anda null (örneklendirilmemiş) değeri bir değişkene döndürebilir ya da bir [boş değer atanabilir tür](../nullable-types/index.md) değer türü.</span><span class="sxs-lookup"><span data-stu-id="e6947-124">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="e6947-125">Dönüş değeri bir sabit bir numaralandırma üyesi olamaz, değer tarafından dönüş değeri bir özelliği veya yöntemi bir `class` veya `struct`.</span><span class="sxs-lookup"><span data-stu-id="e6947-125">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="e6947-126">Derleyici Hatası CS8156 "bir ifade başvuruya göre döndürülemez olduğundan bu bağlamda kullanılamaz.", bunlar döndürülecek çalışırken oluşturur</span><span class="sxs-lookup"><span data-stu-id="e6947-126">Attempting to return these generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="e6947-127">Dönüş değerini bilinmeyen hala durumdayken yürütme bitmeden önce zaman uyumsuz bir yöntem döndürebilir olduğundan, ayrıca, başvuru dönüş değerleri zaman uyumsuz yöntemleri izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="e6947-127">In addition, because an asynchronous method may return before it has finished execution, while its return value is still unknown, reference return values are not allowed on async methods.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="e6947-128">Ref dönüş değeri tanımlama</span><span class="sxs-lookup"><span data-stu-id="e6947-128">Defining a ref return value</span></span>

<span data-ttu-id="e6947-129">Ref dönüş değeri ekleyerek tanımlarsınız [ref](../../language-reference/keywords/ref.md) yöntem imzası dönüş türü için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="e6947-129">You define a ref return value by adding the [ref](../../language-reference/keywords/ref.md) keyword to the return type of the method signature.</span></span> <span data-ttu-id="e6947-130">Örneğin, aşağıdaki imzası belirten `GetContactInformation` özelliği bir başvuru döndürür bir `Person` çağıran nesneye:</span><span class="sxs-lookup"><span data-stu-id="e6947-130">For example, the following signature indicates that the `GetContactInformation` property returns a reference to a `Person` object to the caller:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

<span data-ttu-id="e6947-131">Ayrıca, nesnenin adını döndürülen her tarafından [dönmek](../../language-reference/keywords/return.md) yöntem gövdesi deyiminde öncesinde, tarafından [ref](../../language-reference/keywords/ref.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="e6947-131">In addition, the name of the object returned by each [return](../../language-reference/keywords/return.md) statement in the method body must be preceded by the [ref](../../language-reference/keywords/ref.md) keyword.</span></span> <span data-ttu-id="e6947-132">Örneğin, aşağıdaki `return` deyimi bir başvuru döndürür bir `Person` adlı nesne `p`:</span><span class="sxs-lookup"><span data-stu-id="e6947-132">For example, the following `return` statement returns a reference to a `Person` object named `p`:</span></span>

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="e6947-133">Ref dönüş değeri kullanma</span><span class="sxs-lookup"><span data-stu-id="e6947-133">Consuming a ref return value</span></span>

<span data-ttu-id="e6947-134">Ref dönüş değeri: çağrılan yöntemin kapsamında başka bir değişken için bir diğer ad.</span><span class="sxs-lookup"><span data-stu-id="e6947-134">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="e6947-135">Yorumlaması için herhangi dönüş ref, değişkeni kullanarak, diğer adlar kullanın:</span><span class="sxs-lookup"><span data-stu-id="e6947-135">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="e6947-136">Değerini atadığınızda, değişkene bir değer atadığınız bu diğer adları.</span><span class="sxs-lookup"><span data-stu-id="e6947-136">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="e6947-137">Değerini okurken değişkenin değerini okumakta olduğunuz bu diğer adları.</span><span class="sxs-lookup"><span data-stu-id="e6947-137">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="e6947-138">Bunu dönerseniz *başvuruya* aynı Bu değişken için bir diğer ad döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="e6947-138">If you return it *by reference* you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="e6947-139">Başka bir yönteme geçirirseniz *başvuruya* değişkeni bir başvuru geçtiğiniz bu diğer adları.</span><span class="sxs-lookup"><span data-stu-id="e6947-139">If you pass it to another method *by reference* you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="e6947-140">Yaptığınızda bir [ref yerel](#ref-local) aynı değişken için yeni bir diğer ad yaptığınız diğer ad.</span><span class="sxs-lookup"><span data-stu-id="e6947-140">When you make a [ref local](#ref-local) alias, you make a new alias to the same variable.</span></span>


## <a name="ref-locals"></a><span data-ttu-id="e6947-141">Ref Yereller</span><span class="sxs-lookup"><span data-stu-id="e6947-141">Ref locals</span></span>

<span data-ttu-id="e6947-142">Varsayın `GetContactInformation` yöntemi bildirilen bir başvuru dönüş:</span><span class="sxs-lookup"><span data-stu-id="e6947-142">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="e6947-143">Bir değer tarafından ataması bir değişkenin değeri olarak okur ve yeni bir değişkene atar:</span><span class="sxs-lookup"><span data-stu-id="e6947-143">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="e6947-144">Önceki atama bildirir `p` yerel değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="e6947-144">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="e6947-145">İlk değeri tarafından döndürülen değer okuma kopyalanır `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="e6947-145">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="e6947-146">Gelecekteki tüm atamaları `p` tarafından döndürülen değişkenin değerini değiştirmez `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="e6947-146">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="e6947-147">Değişkeni `p` artık döndürülen değişkenine bir diğer ad değil.</span><span class="sxs-lookup"><span data-stu-id="e6947-147">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="e6947-148">Bildirdiğiniz bir *ref yerel* diğer özgün değerine kopyalamak için değişkeni.</span><span class="sxs-lookup"><span data-stu-id="e6947-148">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="e6947-149">Aşağıdaki atamasında `p` döndürülen değişkenine bir diğer adı `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="e6947-149">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="e6947-150">Sonraki kullanımını `p` tarafından döndürülen değişkenini kullanarak aynı `GetContactInformation` çünkü `p` Bu değişken için bir diğer ad değil.</span><span class="sxs-lookup"><span data-stu-id="e6947-150">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="e6947-151">Değişikliklerini `p` döndürülen değişkeni aynı zamanda değiştirmeniz `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="e6947-151">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="e6947-152">Unutmayın `ref` anahtar sözcüğü kullanılır hem yerel değişken bildirimi önce *ve* yöntemi çağırmadan önce.</span><span class="sxs-lookup"><span data-stu-id="e6947-152">Note that the `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="e6947-153">Başvuruya göre bir değer aynı şekilde erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6947-153">You can access a value by reference in the same way.</span></span> <span data-ttu-id="e6947-154">Bazı durumlarda, bir değer başvuruya göre erişme, performans'potansiyel olarak pahalı kopyalama işlemi kaçınarak artırır.</span><span class="sxs-lookup"><span data-stu-id="e6947-154">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="e6947-155">Örneğin, aşağıdaki deyim bir değer başvurmak için kullanılan bir ref yerel değerin nasıl tanımlayabilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6947-155">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="e6947-156">Unutmayın `ref` anahtar sözcüğü kullanılır hem yerel değişken bildirimi önce *ve* değerin ikinci örnekte önce.</span><span class="sxs-lookup"><span data-stu-id="e6947-156">Note that the `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="e6947-157">Her ikisi de dahil etmek için hata `ref` Değişken bildiriminde anahtar sözcükleri ve atama derleyici hatası CS8172, her iki örnekler sonucu "başlatamıyor bir başvuru tarafından değere sahip bir değişken."</span><span class="sxs-lookup"><span data-stu-id="e6947-157">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 
 
## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="e6947-158">Ref döndürür ve ref Yereller: örneği</span><span class="sxs-lookup"><span data-stu-id="e6947-158">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="e6947-159">Aşağıdaki örnek tanımlayan bir `NumberStore` tamsayı değerleri dizisi depolayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="e6947-159">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="e6947-160">`FindNumber` Yöntemi büyük veya eşit bir bağımsız değişken olarak geçirilen ilk sayı başvuruya göre döndürür.</span><span class="sxs-lookup"><span data-stu-id="e6947-160">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="e6947-161">Büyük veya ona eşit bağımsız değişkeni için herhangi bir sayı ise, yöntem dizin 0 döndürür.</span><span class="sxs-lookup"><span data-stu-id="e6947-161">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#1)]

<span data-ttu-id="e6947-162">Aşağıdaki örnek çağrıları `NumberStore.FindNumber` 16 eşit veya daha büyük olan ilk değer alma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e6947-162">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="e6947-163">Arayan yöntemi tarafından döndürülen değer sonra iki katına çıkar.</span><span class="sxs-lookup"><span data-stu-id="e6947-163">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="e6947-164">Örneğin çıktısını gösterildiği gibi bu değişikliği dizi öğelerinin değeri yansıtılır `NumberStore` örneği.</span><span class="sxs-lookup"><span data-stu-id="e6947-164">As the output from the example shows, this change is reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/ref-returns1.cs#2)]

<span data-ttu-id="e6947-165">Başvuru dönüş değerleri desteği, böyle bir işlem dizin değerini birlikte dizi öğesinin döndürerek genellikle gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e6947-165">Without support for reference return values, such an operation is usually performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="e6947-166">Çağıran, ayrı bir yöntem çağrısı değeri değiştirmek için bu dizini sonra kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6947-166">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="e6947-167">Ancak, çağıran erişmek ve büyük olasılıkla diğer dizi değerlerini değiştirmek için dizini de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6947-167">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="e6947-168">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6947-168">See also</span></span>

[<span data-ttu-id="e6947-169">ref keyword</span><span class="sxs-lookup"><span data-stu-id="e6947-169">ref keyword</span></span>](../../language-reference/keywords/ref.md)  
[<span data-ttu-id="e6947-170">Başvuru semantiği ile değer türleri</span><span class="sxs-lookup"><span data-stu-id="e6947-170">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
