---
title: Ref dönüş değerleri ve ref Yereller (C# Kılavuzu)
description: Ref dönüş ve ref yerel değerleri tanımlayın ve nasıl kullanılacağını öğrenin
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 98c58d083cb806a92e28c1c9d27effa1124fd153
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="82618-103">Ref döndürür ve ref Yereller</span><span class="sxs-lookup"><span data-stu-id="82618-103">Ref returns and ref locals</span></span>

<span data-ttu-id="82618-104">C# 7. 0'dan başlayarak, C# başvurusu dönüş değerleri (başvuru dönüşleri) destekler.</span><span class="sxs-lookup"><span data-stu-id="82618-104">Starting with C# 7.0, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="82618-105">Bir başvuru dönüş değeri bir değer yerine bir değişken başvurusu çağırana geri dönmek tek bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="82618-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="82618-106">Çağıran, daha sonra döndürülen değişkeni değere veya başvuruya göre döndürülmedi sanki işlemek seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82618-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="82618-107">Çağıran bir ref yerel olarak adlandırılan döndürülen değer, başvuru kendisi yeni bir değişken oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82618-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="82618-108">Bir başvuru dönüş değeri nedir?</span><span class="sxs-lookup"><span data-stu-id="82618-108">What is a reference return value?</span></span>

<span data-ttu-id="82618-109">Çoğu geliştirici çağrılan yöntemi için bağımsız değişken geçirme ile bilginiz *başvuruya göre*.</span><span class="sxs-lookup"><span data-stu-id="82618-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="82618-110">Çağrılan yöntemin bağımsız değişken listesi başvuruya göre geçirilen bir değişken içerir.</span><span class="sxs-lookup"><span data-stu-id="82618-110">A called method's argument list includes a variable passed by reference.</span></span> <span data-ttu-id="82618-111">Çağrılan yöntemi tarafından değerine yapılan değişiklikler, çağıran tarafından uyulması gereken.</span><span class="sxs-lookup"><span data-stu-id="82618-111">Any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="82618-112">A *başvuru dönüş değeri* yöntemi döndürür anlamına gelir bir *başvuru* (veya diğer ad) bazı değişkenine.</span><span class="sxs-lookup"><span data-stu-id="82618-112">A *reference return value* means that a method returns a *reference* (or an alias) to some variable.</span></span> <span data-ttu-id="82618-113">Bu değişkenin kapsamı yöntemi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="82618-113">That variable's scope must include the method.</span></span> <span data-ttu-id="82618-114">Bu değişkenin ömrü yöntemin dönüş genişletmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="82618-114">That variable's lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="82618-115">Yöntemin dönüş değeri çağıran tarafından yapılan değişiklikler yöntemi tarafından döndürülen değişkeni yapılır.</span><span class="sxs-lookup"><span data-stu-id="82618-115">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="82618-116">Bir yöntem döndüren bildirme bir *başvuru dönüş değeri* yöntemi bir değişkene bir diğer ad döndürdüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="82618-116">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="82618-117">Tasarım hedefi çağıran kodu değişken değiştirmek için de dahil olmak üzere diğer ad üzerinden erişimi olması gerektiğini görülür.</span><span class="sxs-lookup"><span data-stu-id="82618-117">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="82618-118">Başvuruya göre döndüren yöntemler dönüş türüne sahip olamaz izleyen `void`.</span><span class="sxs-lookup"><span data-stu-id="82618-118">It follows that methods returning by reference can't have the return type `void`.</span></span>

<span data-ttu-id="82618-119">Bir yöntem başvuru dönüş değeri olarak döndürebilir ifade bazı kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="82618-119">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="82618-120">Sınırlamaları içerir:</span><span class="sxs-lookup"><span data-stu-id="82618-120">Restrictions include:</span></span>

- <span data-ttu-id="82618-121">Dönüş değeri yönteminin yürütülmesi genişleten bir yaşam süresi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="82618-121">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="82618-122">Diğer bir deyişle, onu döndüren yöntemi yerel bir değişkende olamaz.</span><span class="sxs-lookup"><span data-stu-id="82618-122">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="82618-123">Bu yönteme geçirilen bağımsız değişken olabilir veya bir örneği veya sınıfının statik alanı olabilir.</span><span class="sxs-lookup"><span data-stu-id="82618-123">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="82618-124">Derleyici Hatası CS8168, yerel bir değişken oluşturur dönüş çalışılırken "döndüremiyor yerel 'obj' başvuruya göre yerel bir ref olmadığından."</span><span class="sxs-lookup"><span data-stu-id="82618-124">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="82618-125">Dönüş değeri sabit olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="82618-125">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="82618-126">Döndürme `null` derleyici hatası "bir ifade başvuruya göre döndürülemez olduğundan bu bağlamda kullanılamaz." CS8156 oluşturur</span><span class="sxs-lookup"><span data-stu-id="82618-126">Returning `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="82618-127">Ref dönüş yöntemiyle bir diğer ad değeri şu anda null (örneklendirilmemiş) değeri bir değişkene döndürebilir ya da bir [boş değer atanabilir tür](../nullable-types/index.md) değer türü.</span><span class="sxs-lookup"><span data-stu-id="82618-127">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="82618-128">Dönüş değeri bir sabit bir numaralandırma üyesi olamaz, değer tarafından dönüş değeri bir özelliği veya yöntemi bir `class` veya `struct`.</span><span class="sxs-lookup"><span data-stu-id="82618-128">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="82618-129">Derleyici Hatası CS8156 "bir ifade başvuruya göre döndürülemez olduğundan bu bağlamda kullanılamaz.", bu kural ihlal oluşturur</span><span class="sxs-lookup"><span data-stu-id="82618-129">Violating this rule generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="82618-130">Ayrıca, başvuru döndürmek zaman uyumsuz yöntemleri değerlere izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="82618-130">In addition, reference return values are not allowed on async methods.</span></span> <span data-ttu-id="82618-131">Dönüş değerini bilinmeyen hala durumdayken yürütme bitmeden önce zaman uyumsuz bir yöntem döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="82618-131">An asynchronous method may return before it has finished execution, while its return value is still unknown.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="82618-132">Ref dönüş değeri tanımlama</span><span class="sxs-lookup"><span data-stu-id="82618-132">Defining a ref return value</span></span>

<span data-ttu-id="82618-133">Ref dönüş değeri ekleyerek tanımlarsınız [ref](../../language-reference/keywords/ref.md) yöntem imzası dönüş türü için anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="82618-133">You define a ref return value by adding the [ref](../../language-reference/keywords/ref.md) keyword to the return type of the method signature.</span></span> <span data-ttu-id="82618-134">Örneğin, aşağıdaki imzası belirten `GetContactInformation` özelliği bir başvuru döndürür bir `Person` çağıran nesneye:</span><span class="sxs-lookup"><span data-stu-id="82618-134">For example, the following signature indicates that the `GetContactInformation` property returns a reference to a `Person` object to the caller:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname);
```

<span data-ttu-id="82618-135">Ayrıca, nesnenin adını döndürülen her tarafından [dönmek](../../language-reference/keywords/return.md) yöntem gövdesi deyiminde öncesinde, tarafından [ref](../../language-reference/keywords/ref.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="82618-135">In addition, the name of the object returned by each [return](../../language-reference/keywords/return.md) statement in the method body must be preceded by the [ref](../../language-reference/keywords/ref.md) keyword.</span></span> <span data-ttu-id="82618-136">Örneğin, aşağıdaki `return` deyimi bir başvuru döndürür bir `Person` adlı nesne `p`:</span><span class="sxs-lookup"><span data-stu-id="82618-136">For example, the following `return` statement returns a reference to a `Person` object named `p`:</span></span>

```csharp
return ref p;
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="82618-137">Ref dönüş değeri kullanma</span><span class="sxs-lookup"><span data-stu-id="82618-137">Consuming a ref return value</span></span>

<span data-ttu-id="82618-138">Ref dönüş değeri: çağrılan yöntemin kapsamında başka bir değişken için bir diğer ad.</span><span class="sxs-lookup"><span data-stu-id="82618-138">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="82618-139">Yorumlaması için herhangi dönüş ref, değişkeni kullanarak, diğer adlar kullanın:</span><span class="sxs-lookup"><span data-stu-id="82618-139">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="82618-140">Değerini atadığınızda, değişkene bir değer atadığınız bu diğer adları.</span><span class="sxs-lookup"><span data-stu-id="82618-140">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="82618-141">Değerini okurken değişkenin değerini okumakta olduğunuz bu diğer adları.</span><span class="sxs-lookup"><span data-stu-id="82618-141">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="82618-142">Bunu dönerseniz *başvuruya göre*, bu aynı değişkenine bir diğer ad döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="82618-142">If you return it *by reference*, you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="82618-143">Başka bir yönteme geçirirseniz *başvuruya göre*, değişkeni bir başvuru geçtiğiniz bu diğer adları.</span><span class="sxs-lookup"><span data-stu-id="82618-143">If you pass it to another method *by reference*, you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="82618-144">Yaptığınızda bir [ref yerel](#ref-local) aynı değişken için yeni bir diğer ad yaptığınız diğer ad.</span><span class="sxs-lookup"><span data-stu-id="82618-144">When you make a [ref local](#ref-local) alias, you make a new alias to the same variable.</span></span>


## <a name="ref-locals"></a><span data-ttu-id="82618-145">Ref Yereller</span><span class="sxs-lookup"><span data-stu-id="82618-145">Ref locals</span></span>

<span data-ttu-id="82618-146">Varsayın `GetContactInformation` yöntemi bildirilen bir başvuru dönüş:</span><span class="sxs-lookup"><span data-stu-id="82618-146">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="82618-147">Bir değer tarafından ataması bir değişkenin değeri olarak okur ve yeni bir değişkene atar:</span><span class="sxs-lookup"><span data-stu-id="82618-147">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="82618-148">Önceki atama bildirir `p` yerel değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="82618-148">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="82618-149">İlk değeri tarafından döndürülen değer okuma kopyalanır `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="82618-149">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="82618-150">Gelecekteki tüm atamaları `p` tarafından döndürülen değişkenin değerini değiştirmez `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="82618-150">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="82618-151">Değişkeni `p` artık döndürülen değişkenine bir diğer ad değil.</span><span class="sxs-lookup"><span data-stu-id="82618-151">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="82618-152">Bildirdiğiniz bir *ref yerel* diğer özgün değerine kopyalamak için değişkeni.</span><span class="sxs-lookup"><span data-stu-id="82618-152">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="82618-153">Aşağıdaki atamasında `p` döndürülen değişkenine bir diğer adı `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="82618-153">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="82618-154">Sonraki kullanımını `p` tarafından döndürülen değişkenini kullanarak aynı `GetContactInformation` çünkü `p` Bu değişken için bir diğer ad değil.</span><span class="sxs-lookup"><span data-stu-id="82618-154">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="82618-155">Değişikliklerini `p` döndürülen değişkeni aynı zamanda değiştirmeniz `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="82618-155">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="82618-156">`ref` Anahtar sözcüğü kullanılır hem yerel değişken bildirimi önce *ve* yöntemi çağırmadan önce.</span><span class="sxs-lookup"><span data-stu-id="82618-156">The `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="82618-157">Başvuruya göre bir değer aynı şekilde erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82618-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="82618-158">Bazı durumlarda, bir değer başvuruya göre erişme, performans'potansiyel olarak pahalı kopyalama işlemi kaçınarak artırır.</span><span class="sxs-lookup"><span data-stu-id="82618-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="82618-159">Örneğin, aşağıdaki deyim bir değer başvurmak için kullanılan bir ref yerel değerin nasıl tanımlayabilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="82618-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="82618-160">`ref` Anahtar sözcüğü kullanılır hem yerel değişken bildirimi önce *ve* değerin ikinci örnekte önce.</span><span class="sxs-lookup"><span data-stu-id="82618-160">The `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="82618-161">Her ikisi de dahil etmek için hata `ref` Değişken bildiriminde anahtar sözcükleri ve atama derleyici hatası CS8172, her iki örnekler sonucu "başlatamıyor bir başvuru tarafından değere sahip bir değişken."</span><span class="sxs-lookup"><span data-stu-id="82618-161">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 

<span data-ttu-id="82618-162">Farklı depolama birimine başlatılmış sonra başvurmak için C# 7.3 önce ref yerel değişkenler atanmasını uygulanamadı.</span><span class="sxs-lookup"><span data-stu-id="82618-162">Prior to C# 7.3, ref local variables couldn't be reassigned to refer to different storage after being initialized.</span></span> <span data-ttu-id="82618-163">Bu kısıtlama kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="82618-163">That restriction has been removed.</span></span> <span data-ttu-id="82618-164">Aşağıdaki örnek, bir yeniden atama gösterir:</span><span class="sxs-lookup"><span data-stu-id="82618-164">The following example shows a reassignment:</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 <span data-ttu-id="82618-165">Bunlar bildirirken ref yerel değişkenler hala başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="82618-165">Ref local variables must still be initialized when they are declared.</span></span>

## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="82618-166">Ref döndürür ve ref Yereller: örneği</span><span class="sxs-lookup"><span data-stu-id="82618-166">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="82618-167">Aşağıdaki örnek tanımlayan bir `NumberStore` tamsayı değerleri dizisi depolayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="82618-167">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="82618-168">`FindNumber` Yöntemi büyük veya eşit bir bağımsız değişken olarak geçirilen ilk sayı başvuruya göre döndürür.</span><span class="sxs-lookup"><span data-stu-id="82618-168">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="82618-169">Büyük veya ona eşit bağımsız değişkeni için herhangi bir sayı ise, yöntem dizin 0 döndürür.</span><span class="sxs-lookup"><span data-stu-id="82618-169">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

<span data-ttu-id="82618-170">Aşağıdaki örnek çağrıları `NumberStore.FindNumber` 16 eşit veya daha büyük olan ilk değer alma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="82618-170">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="82618-171">Arayan yöntemi tarafından döndürülen değer sonra iki katına çıkar.</span><span class="sxs-lookup"><span data-stu-id="82618-171">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="82618-172">Dizi öğelerinin değeri yansıtılan değişiklik örnek çıktısını gösterir `NumberStore` örneği.</span><span class="sxs-lookup"><span data-stu-id="82618-172">The output from the example shows the change reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

<span data-ttu-id="82618-173">Başvuru dönüş değerleri için desteği olmadan, dizin değerini birlikte dizi öğesinin döndürerek böyle bir işlem gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="82618-173">Without support for reference return values, such an operation is performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="82618-174">Çağıran, ayrı bir yöntem çağrısı değeri değiştirmek için bu dizini sonra kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82618-174">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="82618-175">Ancak, çağıran erişmek ve büyük olasılıkla diğer dizi değerlerini değiştirmek için dizini de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="82618-175">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  

<span data-ttu-id="82618-176">Aşağıdaki örnekte gösterildiği nasıl `FindNumber` yöntemi C# ref yerel yeniden atama kullanılacak 7.3 sonra yeniden:</span><span class="sxs-lookup"><span data-stu-id="82618-176">The following example shows how the `FindNumber` method could be rewritten after C# 7.3 to use ref local reassignment:</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

<span data-ttu-id="82618-177">Bu ikinci sürümü Aranan numarası dizinin sonuna daha yakın olduğu senaryolarda uzun serileri ile daha verimli olur.</span><span class="sxs-lookup"><span data-stu-id="82618-177">This second version is more efficient with longer sequences in scenarios where the number sought is closer to the end of the array.</span></span>

## <a name="see-also"></a><span data-ttu-id="82618-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82618-178">See also</span></span>

[<span data-ttu-id="82618-179">ref anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="82618-179">ref keyword</span></span>](../../language-reference/keywords/ref.md)  
[<span data-ttu-id="82618-180">Başvuru semantiği ile değer türleri</span><span class="sxs-lookup"><span data-stu-id="82618-180">Reference Semantics with Value Types</span></span>](../../../csharp/reference-semantics-with-value-types.md)
