---
title: Başvuru dönüş değerleri ve ref yerel ayarlar (C# Kılavuzu)
description: Başvuru dönüş ve ref yerel değerlerine tanımlanacağını ve kullanılacağını öğrenin
author: rpetrusha
ms.author: ronpet
ms.date: 04/04/2018
ms.openlocfilehash: fcac162f63438b6cbe54908383467d4b0f227c39
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081856"
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="d0881-103">Ref dönüşler ve ref yerel ayarlar</span><span class="sxs-lookup"><span data-stu-id="d0881-103">Ref returns and ref locals</span></span>

<span data-ttu-id="d0881-104">C# 7.0 ile başlayarak, C# (ref döndürür) başvuru dönüş değerleri destekler.</span><span class="sxs-lookup"><span data-stu-id="d0881-104">Starting with C# 7.0, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="d0881-105">Başvuru dönüş değeri bir değer yerine bir değişken bir başvuru arayana geri döndürmek bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="d0881-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="d0881-106">Çağırana döndürülen değişkeni değere veya başvuruya göre döndürülmedi yokmuş gibi kabul seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0881-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="d0881-107">Arayan, döndürülen değer, bir ref yerel olarak adlandırılan bir başvuru kendisi yeni bir değişken oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0881-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="d0881-108">Başvuru dönüş değeri nedir?</span><span class="sxs-lookup"><span data-stu-id="d0881-108">What is a reference return value?</span></span>

<span data-ttu-id="d0881-109">Çoğu geliştirici için çağrılan bir yöntem bağımsız değişken geçirme ile ilgili bilgi sahibi olduğunuz *başvuruya göre*.</span><span class="sxs-lookup"><span data-stu-id="d0881-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="d0881-110">Çağrılan yöntemin bağımsız değişken listesinin bir değişken başvuruyla geçirildi içerir.</span><span class="sxs-lookup"><span data-stu-id="d0881-110">A called method's argument list includes a variable passed by reference.</span></span> <span data-ttu-id="d0881-111">Tarafından çağrılan yöntem değerine yapılan tüm değişiklikler arayan tarafından gözlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d0881-111">Any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="d0881-112">A *başvuru dönüş değeri* döndüren bir yöntemi gösterir bir *başvuru* (veya diğer ad) bazı değişken.</span><span class="sxs-lookup"><span data-stu-id="d0881-112">A *reference return value* means that a method returns a *reference* (or an alias) to some variable.</span></span> <span data-ttu-id="d0881-113">Bu değişkenin kapsamı yöntemi eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0881-113">That variable's scope must include the method.</span></span> <span data-ttu-id="d0881-114">Değişkenin ömrü yöntemi iadesini genişletmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0881-114">That variable's lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="d0881-115">Yöntem tarafından döndürülen değişkeni yöntemin dönüş değeri çağıran tarafından yapılan değişiklikler yapılır.</span><span class="sxs-lookup"><span data-stu-id="d0881-115">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="d0881-116">Döndüren bir yöntemi bildirmek bir *başvuru dönüş değeri* yöntemi bir değişkene bir diğer ad verdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0881-116">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="d0881-117">Tasarım amacı genellikle çağıran kod değişken değiştirmek için de dahil olmak üzere diğer ad üzerinden erişim gerektiğidir.</span><span class="sxs-lookup"><span data-stu-id="d0881-117">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="d0881-118">Yöntemleri başvuruya göre dönüş türü olamaz takip eden `void`.</span><span class="sxs-lookup"><span data-stu-id="d0881-118">It follows that methods returning by reference can't have the return type `void`.</span></span>

<span data-ttu-id="d0881-119">Başvuru dönüş değeri olarak bir yöntem döndüren bir ifade üzerinde bazı kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="d0881-119">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="d0881-120">Kısıtlamaları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d0881-120">Restrictions include:</span></span>

- <span data-ttu-id="d0881-121">Dönüş değeri, yöntemin yürütülmesi genişletir bir yaşam süresi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0881-121">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="d0881-122">Diğer bir deyişle, bu yöntemin döndürdüğü yerel bir değişkende olamaz.</span><span class="sxs-lookup"><span data-stu-id="d0881-122">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="d0881-123">Bu yönteme geçirilen bağımsız değişken olabilir veya bir örnek veya bir sınıfın statik alanı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d0881-123">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="d0881-124">Derleyici Hatası CS8168, yerel bir değişken oluşturur dönüş çalışılırken "döndüremiyor yerel 'obj' başvuruya göre bir ref yerel öğesi olmadığından."</span><span class="sxs-lookup"><span data-stu-id="d0881-124">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="d0881-125">Dönüş değeri, değişmez değer olamaz `null`.</span><span class="sxs-lookup"><span data-stu-id="d0881-125">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="d0881-126">Döndüren `null` CS8156 "bir ifade başvuru ile döndürülemez olduğundan bu bağlamda kullanılamaz.", derleyici hatası oluşturur</span><span class="sxs-lookup"><span data-stu-id="d0881-126">Returning `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="d0881-127">Bir yöntem dönüş ref ile bir diğer ad değeri şu anda null (örneklenmemiş) değeri bir değişkene döndürebilir veya [boş değer atanabilir tür](../nullable-types/index.md) için bir değer türü.</span><span class="sxs-lookup"><span data-stu-id="d0881-127">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable type](../nullable-types/index.md) for a value type.</span></span>
 
- <span data-ttu-id="d0881-128">Dönüş değeri bir sabit bir numaralandırma üyesine olamaz, değer tarafından dönen değer bir özelliği veya yöntemi bir `class` veya `struct`.</span><span class="sxs-lookup"><span data-stu-id="d0881-128">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="d0881-129">Derleyici Hatası CS8156 "bir ifade başvuru ile döndürülemez olduğundan bu bağlamda kullanılamaz.", bu kuralın ihlali oluşturur</span><span class="sxs-lookup"><span data-stu-id="d0881-129">Violating this rule generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="d0881-130">Ayrıca, başvuru döndürmek zaman uyumsuz yöntemlerde değerlere izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="d0881-130">In addition, reference return values are not allowed on async methods.</span></span> <span data-ttu-id="d0881-131">Zaman uyumsuz bir yöntemin dönüş değerini hala bilinmiyor ancak yürütme bitmeden önce döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="d0881-131">An asynchronous method may return before it has finished execution, while its return value is still unknown.</span></span>
 
## <a name="defining-a-ref-return-value"></a><span data-ttu-id="d0881-132">Başvuru dönüş değeri tanımlama</span><span class="sxs-lookup"><span data-stu-id="d0881-132">Defining a ref return value</span></span>

<span data-ttu-id="d0881-133">Döndüren bir yöntem bir *başvuru dönüş değeri* aşağıdaki iki koşulları karşılaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="d0881-133">A method that returns a *reference return value* must satisfy the following two conditions:</span></span>

- <span data-ttu-id="d0881-134">Yöntem imzası içerir [ref](../../language-reference/keywords/ref.md) önünde dönüş türü anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d0881-134">The method signature includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the return type.</span></span>
- <span data-ttu-id="d0881-135">Her [dönüş](../../language-reference/keywords/return.md) deyimi yöntemin gövdesinde [ref](../../language-reference/keywords/ref.md) döndürülen örneğinin adını önünde anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="d0881-135">Each [return](../../language-reference/keywords/return.md) statement in the method body includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the name of the returned instance.</span></span>

<span data-ttu-id="d0881-136">Aşağıdaki örnek, bir başvuru döndürür ve koşullarını bu karşılayan bir yöntemi gösterir. bir `Person` adlı nesne `p`:</span><span class="sxs-lookup"><span data-stu-id="d0881-136">The following example shows a method that satisfies those conditions and returns a reference to a `Person` object named `p`:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="d0881-137">Başvuru dönüş değeri kullanma</span><span class="sxs-lookup"><span data-stu-id="d0881-137">Consuming a ref return value</span></span>

<span data-ttu-id="d0881-138">Başvuru dönüş değeri çağrılan yöntemin kapsamında başka bir değişkene bir diğer ad:.</span><span class="sxs-lookup"><span data-stu-id="d0881-138">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="d0881-139">Yorumlaması için tüm dönüş başvurusuna sahip değişkeni kullanarak, diğer adları kullanın:</span><span class="sxs-lookup"><span data-stu-id="d0881-139">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="d0881-140">Değişkene bir değer atadığınız değeri atadığınızda, bu diğer adları.</span><span class="sxs-lookup"><span data-stu-id="d0881-140">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="d0881-141">Değerlerini okumak, değişkenin değerini okuyorsanız, diğer adları.</span><span class="sxs-lookup"><span data-stu-id="d0881-141">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="d0881-142">Bu dönüş yaparsa *başvuruya göre*, bir diğer ad, aynı değişkene döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="d0881-142">If you return it *by reference*, you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="d0881-143">Başka bir yönteme geçirdiğinizde *başvuruya göre*, bir değişken başvurusu'nu geçirme, diğer adları.</span><span class="sxs-lookup"><span data-stu-id="d0881-143">If you pass it to another method *by reference*, you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="d0881-144">Yaptığınızda bir [ref yerel](#ref-locals) aynı değişkene yeni bir diğer ad yaptığınız diğer ad.</span><span class="sxs-lookup"><span data-stu-id="d0881-144">When you make a [ref local](#ref-locals) alias, you make a new alias to the same variable.</span></span>

## <a name="ref-locals"></a><span data-ttu-id="d0881-145">Ref yerel ayarlar</span><span class="sxs-lookup"><span data-stu-id="d0881-145">Ref locals</span></span>

<span data-ttu-id="d0881-146">Varsayar `GetContactInformation` yöntemi bildirilen bir başvuru dönüş:</span><span class="sxs-lookup"><span data-stu-id="d0881-146">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="d0881-147">Bir değere göre ataması, bir değişkenin değerini okur ve yeni bir değişkene atar:</span><span class="sxs-lookup"><span data-stu-id="d0881-147">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="d0881-148">Yukarıdaki atamanın bildirir `p` yerel bir değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="d0881-148">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="d0881-149">İlk değeri tarafından döndürülen değer okumasını kopyalanır `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="d0881-149">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="d0881-150">Gelecekteki atamaların `p` tarafından döndürülen değişkenin değerini değiştirmez `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="d0881-150">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="d0881-151">Değişken `p` artık döndürülen değişkenine diğer ad değil.</span><span class="sxs-lookup"><span data-stu-id="d0881-151">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="d0881-152">Bildirdiğiniz bir *ref yerel* değişken özgün değere diğer kopyalamak için.</span><span class="sxs-lookup"><span data-stu-id="d0881-152">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="d0881-153">Aşağıdaki atama `p` döndürüldüğü değişkeni için bir diğer addır `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="d0881-153">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="d0881-154">Sonraki kullanımını `p` tarafından döndürülen değişkenini kullanarak aynı `GetContactInformation` çünkü `p` Bu değişken için bir diğer addır.</span><span class="sxs-lookup"><span data-stu-id="d0881-154">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="d0881-155">Değişikliklerini `p` döndürüldüğü değişkeni de değiştirmeniz `GetContactInformation`.</span><span class="sxs-lookup"><span data-stu-id="d0881-155">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="d0881-156">`ref` Anahtar sözcüğü kullanılır yerel değişken bildiriminde önce her ikisini de *ve* yöntemi çağırmadan önce.</span><span class="sxs-lookup"><span data-stu-id="d0881-156">The `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="d0881-157">Başvuruya göre bir değer aynı şekilde erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0881-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="d0881-158">Bazı durumlarda, bir değere Başvuruya göre erişmeden performansı büyük olasılıkla pahalı kopyalama işlemi tarafından artırır.</span><span class="sxs-lookup"><span data-stu-id="d0881-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="d0881-159">Örneğin, aşağıdaki ifade bir değer başvurmak için kullanılan bir ref yerel değer nasıl tanımlayabilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0881-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="d0881-160">`ref` Anahtar sözcüğü kullanılır yerel değişken bildiriminde önce her ikisini de *ve* değerinden ikinci örnekte önce.</span><span class="sxs-lookup"><span data-stu-id="d0881-160">The `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="d0881-161">Her ikisi de içerecek şekilde hatası `ref` değişken bildirimi anahtar sözcükleri ve derleyici hatası CS8172, her iki örnek sonucu atama "başlatamıyor bir başvuruya göre değişken değeri."</span><span class="sxs-lookup"><span data-stu-id="d0881-161">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 

<span data-ttu-id="d0881-162">C# 7.3 önce ref yerel değişkenleri başlatıldıktan sonra farklı bir depolama alanına başvurmak için başkasına alınamadı.</span><span class="sxs-lookup"><span data-stu-id="d0881-162">Prior to C# 7.3, ref local variables couldn't be reassigned to refer to different storage after being initialized.</span></span> <span data-ttu-id="d0881-163">Bu kısıtlama kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="d0881-163">That restriction has been removed.</span></span> <span data-ttu-id="d0881-164">Aşağıdaki örnek, bir yeniden atama gösterir:</span><span class="sxs-lookup"><span data-stu-id="d0881-164">The following example shows a reassignment:</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 <span data-ttu-id="d0881-165">Bunlar bildirildiğinde ref yerel değişkenleri hala başlatılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d0881-165">Ref local variables must still be initialized when they are declared.</span></span>

## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="d0881-166">Ref dönüşler ve ref yerel ayarlar: örneği</span><span class="sxs-lookup"><span data-stu-id="d0881-166">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="d0881-167">Aşağıdaki örnekte tanımlayan bir `NumberStore` tamsayı değerleri dizisi depolayan sınıf.</span><span class="sxs-lookup"><span data-stu-id="d0881-167">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="d0881-168">`FindNumber` Yöntemi başvuruya göre büyük veya ona eşit bir bağımsız değişken olarak geçirilen ilk sayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0881-168">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="d0881-169">Büyüktür veya eşittir bağımsız değişken numarası yok ise, yöntem dizin 0 döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0881-169">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

<span data-ttu-id="d0881-170">Aşağıdaki örnek çağrıları `NumberStore.FindNumber` büyüktür veya eşittir 16 ilk değerini almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d0881-170">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="d0881-171">Çağıran yöntemi tarafından döndürülen değer ardından iki katına çıkar.</span><span class="sxs-lookup"><span data-stu-id="d0881-171">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="d0881-172">Değişikliğin dizi öğelerinin değerinde yansıtıldığını örneğin çıktısında gösterildiği `NumberStore` örneği.</span><span class="sxs-lookup"><span data-stu-id="d0881-172">The output from the example shows the change reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

<span data-ttu-id="d0881-173">Başvuru dönüş değerleri için desteği olmadan değerini birlikte dizi öğenin dizinini döndüren ve bu tür bir işlem gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d0881-173">Without support for reference return values, such an operation is performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="d0881-174">Çağıran, ayrı yöntem çağrısında değerini değiştirmek için bu dizini sonra kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0881-174">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="d0881-175">Ancak, çağırana erişmek ve büyük olasılıkla diğer dizi değerlerini değiştirmek için dizini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0881-175">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  

<span data-ttu-id="d0881-176">Aşağıdaki örnekte gösterildiği nasıl `FindNumber` yöntemi C# ref yerel yeniden atama kullanılacak 7.3 sonra yeniden:</span><span class="sxs-lookup"><span data-stu-id="d0881-176">The following example shows how the `FindNumber` method could be rewritten after C# 7.3 to use ref local reassignment:</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

<span data-ttu-id="d0881-177">Bu ikinci sürüm numarasını Aranan dizinin sonuna yakın olduğu senaryolarda uzun dizileri ile daha verimli olur.</span><span class="sxs-lookup"><span data-stu-id="d0881-177">This second version is more efficient with longer sequences in scenarios where the number sought is closer to the end of the array.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0881-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0881-178">See also</span></span>

- [<span data-ttu-id="d0881-179">ref anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="d0881-179">ref keyword</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="d0881-180">Güvenli verimli kod yazma</span><span class="sxs-lookup"><span data-stu-id="d0881-180">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
