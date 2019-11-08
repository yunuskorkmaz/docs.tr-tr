---
title: Ref dönüş değerleri ve ref YerellerC# (kılavuz)
description: Ref return ve ref yerel değerlerini tanımlama ve kullanma hakkında bilgi edinin
ms.date: 04/04/2018
ms.openlocfilehash: 7ade422b5b3805ef2e1f487252a98fb85cdfe70c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736826"
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="1bcfa-103">Ref dönüşler ve ref yerel ayarlar</span><span class="sxs-lookup"><span data-stu-id="1bcfa-103">Ref returns and ref locals</span></span>

<span data-ttu-id="1bcfa-104">7,0 ile C# başlayarak, C# başvuru dönüş değerlerini (Ref dönüşler) destekler.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-104">Starting with C# 7.0, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="1bcfa-105">Bir başvuru dönüş değeri, bir yöntemin bir değer yerine bir değişkene geri dönmesi için bir başvuru döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="1bcfa-106">Çağıran, döndürülen değişkeni değere veya başvuruya göre döndürülmüş gibi kabul edebilir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="1bcfa-107">Çağıran, başvuru yerel olarak adlandırılan döndürülen değere bir başvuru olan yeni bir değişken oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="1bcfa-108">Başvuru dönüş değeri nedir?</span><span class="sxs-lookup"><span data-stu-id="1bcfa-108">What is a reference return value?</span></span>

<span data-ttu-id="1bcfa-109">Çoğu geliştirici, bir bağımsız değişkeni *başvuruya göre*çağrılan bir yönteme geçirmeyi öğrenmektir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="1bcfa-110">Çağrılan yöntemin bağımsız değişken listesi, başvuruya göre geçirilmiş bir değişken içerir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-110">A called method's argument list includes a variable passed by reference.</span></span> <span data-ttu-id="1bcfa-111">Çağrılan yönteme göre değerinde yapılan tüm değişiklikler arayan tarafından izlenir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-111">Any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="1bcfa-112">Bir *Başvuru dönüş değeri* , bir yöntemin bazı değişkene bir *başvuru* (veya diğer ad) döndürdüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-112">A *reference return value* means that a method returns a *reference* (or an alias) to some variable.</span></span> <span data-ttu-id="1bcfa-113">Bu değişkenin kapsamı yöntemi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-113">That variable's scope must include the method.</span></span> <span data-ttu-id="1bcfa-114">Bu değişkenin yaşam süresi yöntemin geri dönüşlerinin ötesinde genişlemelidir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-114">That variable's lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="1bcfa-115">Metodun dönüş değerindeki çağıran tarafından yapılan değişiklikler, yöntemi tarafından döndürülen değişkene yapılır.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-115">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="1bcfa-116">Bir yöntemin bir *Başvuru dönüş değeri* döndürdüğünü bildirmek, yöntemin bir değişkene bir diğer ad döndürdüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-116">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="1bcfa-117">Tasarım amacı, genellikle çağıran kodun, diğer ad üzerinden bu değişkene, değiştirmek de dahil olmak üzere erişim sahibi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-117">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="1bcfa-118">Başvuruya göre döndüren yöntemlerin dönüş türü `void`olamaz.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-118">It follows that methods returning by reference can't have the return type `void`.</span></span>

<span data-ttu-id="1bcfa-119">İfadede bir yöntemin başvuru dönüş değeri olarak döndürebilen bazı kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-119">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="1bcfa-120">Sınırlamalar şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="1bcfa-120">Restrictions include:</span></span>

- <span data-ttu-id="1bcfa-121">Dönüş değeri, yönteminin yürütülmesini aşan bir yaşam süresine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-121">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="1bcfa-122">Diğer bir deyişle, bu, döndüren yöntemde yerel bir değişken olamaz.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-122">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="1bcfa-123">Bir sınıfın örneği veya statik alanı olabilir veya yöntemine geçirilen bir bağımsız değişken olabilir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-123">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="1bcfa-124">Yerel bir değişken döndürme girişimi, "yerel ' obj" bir ref yerel olmadığından, "yerel ' obj ' başvuru ile döndürülemiyor."</span><span class="sxs-lookup"><span data-stu-id="1bcfa-124">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="1bcfa-125">Dönüş değeri `null`sabit değer olamaz.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-125">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="1bcfa-126">`null` derleyici hatası CS8156, "bir ifade başvuru ile döndürülmeyebilir çünkü bu bağlamda kullanılamaz."</span><span class="sxs-lookup"><span data-stu-id="1bcfa-126">Returning `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="1bcfa-127">Ref Return içeren bir yöntem, değeri şu anda null (örneklenmiş) değeri olan bir değişkene veya bir değer türü için null [yapılabilir değer türüne](../../language-reference/builtin-types/nullable-value-types.md) sahip bir diğer ad döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-127">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable value type](../../language-reference/builtin-types/nullable-value-types.md) for a value type.</span></span>

- <span data-ttu-id="1bcfa-128">Dönüş değeri bir sabit, bir numaralandırma üyesi, bir özellikten değere göre dönüş değeri veya `class` ya da `struct`bir yöntem olamaz.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-128">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="1bcfa-129">Bu kuralın ihlal edildiğinde derleyici hatası CS8156, "bir ifade başvuru ile döndürülmeyebilir çünkü bu bağlamda kullanılamaz."</span><span class="sxs-lookup"><span data-stu-id="1bcfa-129">Violating this rule generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="1bcfa-130">Buna ek olarak, zaman uyumsuz metotlarda başvuru dönüş değerlerine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-130">In addition, reference return values are not allowed on async methods.</span></span> <span data-ttu-id="1bcfa-131">Zaman uyumsuz bir yöntem yürütmeyi bitmeden önce dönebilir, ancak dönüş değeri hala bilinmez.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-131">An asynchronous method may return before it has finished execution, while its return value is still unknown.</span></span>

## <a name="defining-a-ref-return-value"></a><span data-ttu-id="1bcfa-132">Başvuru dönüş değeri tanımlama</span><span class="sxs-lookup"><span data-stu-id="1bcfa-132">Defining a ref return value</span></span>

<span data-ttu-id="1bcfa-133">*Başvuru dönüş değeri* döndüren bir yöntem aşağıdaki iki koşulu karşılamalıdır:</span><span class="sxs-lookup"><span data-stu-id="1bcfa-133">A method that returns a *reference return value* must satisfy the following two conditions:</span></span>

- <span data-ttu-id="1bcfa-134">Yöntem imzası, dönüş türünün önünde [ref](../../language-reference/keywords/ref.md) anahtar sözcüğünü içerir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-134">The method signature includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the return type.</span></span>
- <span data-ttu-id="1bcfa-135">Yöntem gövdesindeki her [dönüş](../../language-reference/keywords/return.md) ifadesinde, döndürülen örnek adının önünde [başvuru](../../language-reference/keywords/ref.md) anahtar sözcüğü bulunur.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-135">Each [return](../../language-reference/keywords/return.md) statement in the method body includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the name of the returned instance.</span></span>

<span data-ttu-id="1bcfa-136">Aşağıdaki örnek, bu koşulları karşılayan bir yöntemi gösterir ve `p`adlı `Person` nesnesine bir başvuru döndürür:</span><span class="sxs-lookup"><span data-stu-id="1bcfa-136">The following example shows a method that satisfies those conditions and returns a reference to a `Person` object named `p`:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="1bcfa-137">Ref dönüş değeri kullanma</span><span class="sxs-lookup"><span data-stu-id="1bcfa-137">Consuming a ref return value</span></span>

<span data-ttu-id="1bcfa-138">Ref dönüş değeri, çağrılan metodun kapsamındaki başka bir değişken için diğer addır.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-138">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="1bcfa-139">Ref Return öğesinin herhangi bir kullanımını, diğer ad olan değişkeni kullanarak yorumlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-139">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="1bcfa-140">Değerini atadığınızda, diğer ad olan değişkene bir değer atarsınız.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-140">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="1bcfa-141">Değerini okurken, diğer adı değişkenin değerini Okuyorda olursunuz.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-141">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="1bcfa-142">*Başvuruya göre*geri döndürülürken, aynı değişkene bir diğer ad döndürürler.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-142">If you return it *by reference*, you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="1bcfa-143">*Başvuruya göre*başka bir yönteme geçirirseniz, diğer ad olan değişkene bir başvuru geçirolursunuz.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-143">If you pass it to another method *by reference*, you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="1bcfa-144">Bir [ref yerel](#ref-locals) diğer adı yaptığınızda aynı değişkene yeni bir diğer ad yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-144">When you make a [ref local](#ref-locals) alias, you make a new alias to the same variable.</span></span>

## <a name="ref-locals"></a><span data-ttu-id="1bcfa-145">Başvuru yerelleri</span><span class="sxs-lookup"><span data-stu-id="1bcfa-145">Ref locals</span></span>

<span data-ttu-id="1bcfa-146">`GetContactInformation` yönteminin bir ref Return olarak bildirildiği varsayılır:</span><span class="sxs-lookup"><span data-stu-id="1bcfa-146">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="1bcfa-147">Değere göre atama bir değişkenin değerini okur ve bunu yeni bir değişkene atar:</span><span class="sxs-lookup"><span data-stu-id="1bcfa-147">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="1bcfa-148">Yukarıdaki atama `p` yerel bir değişken olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-148">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="1bcfa-149">İlk değeri `GetContactInformation`tarafından döndürülen değerin okunmasından kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-149">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="1bcfa-150">`p` gelecekteki tüm atamalar `GetContactInformation`tarafından döndürülen değişkenin değerini değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-150">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="1bcfa-151">`p` değişkeni artık döndürülen değişkenin diğer adı değildir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-151">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="1bcfa-152">Diğer adı özgün değerine kopyalamak için bir *ref yerel* değişkeni bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-152">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="1bcfa-153">Aşağıdaki atamada, `p` `GetContactInformation`döndürülen değişkenin diğer adıdır.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-153">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="1bcfa-154">`p` sonraki kullanımı, bu değişken için bir diğer ad `p` olduğundan, `GetContactInformation` tarafından döndürülen değişkeni kullanmakla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-154">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="1bcfa-155">`p` yapılan değişiklikler `GetContactInformation`döndürülen değişkeni de değiştirir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-155">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="1bcfa-156">`ref` anahtar sözcüğü, hem yerel değişken bildiriminden önce *hem* de yöntem çağrısından önce kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-156">The `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span> 

<span data-ttu-id="1bcfa-157">Başvuruya göre bir değere aynı şekilde erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="1bcfa-158">Bazı durumlarda, başvuruya göre değere erişmek, potansiyel olarak pahalı bir kopyalama işlemini önleyerek performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="1bcfa-159">Örneğin, aşağıdaki ifade bir değere başvurmak için kullanılan bir başvuru yerel değerini nasıl tanımlayacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="1bcfa-160">`ref` anahtar sözcüğü, hem yerel değişken bildiriminden önce *hem* de ikinci örnekteki değerden önce kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-160">The `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="1bcfa-161">Hem değişken bildiriminde hem de atamaya `ref` anahtar sözcükleri dahil etme hatası derleyici hatası CS8172, "bir değere sahip bir başvuru değişkeni başlatılamaz."</span><span class="sxs-lookup"><span data-stu-id="1bcfa-161">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span> 

<span data-ttu-id="1bcfa-162">C# 7,3 ' den önce, ref yerel değişkenleri, başlatıldıktan sonra farklı depolamaya başvuracak şekilde yeniden atanamadı.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-162">Prior to C# 7.3, ref local variables couldn't be reassigned to refer to different storage after being initialized.</span></span> <span data-ttu-id="1bcfa-163">Bu kısıtlama kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-163">That restriction has been removed.</span></span> <span data-ttu-id="1bcfa-164">Aşağıdaki örnekte bir yeniden atama gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="1bcfa-164">The following example shows a reassignment:</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 <span data-ttu-id="1bcfa-165">Ref yerel değişkenlerinin, bildirildiği zaman yine de başlatılmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-165">Ref local variables must still be initialized when they are declared.</span></span>

## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="1bcfa-166">Ref, ve ref yerelleri: bir örnek</span><span class="sxs-lookup"><span data-stu-id="1bcfa-166">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="1bcfa-167">Aşağıdaki örnek, bir tamsayı değerleri dizisini depolayan bir `NumberStore` sınıfını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-167">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="1bcfa-168">`FindNumber` yöntemi, bir bağımsız değişken olarak geçirilen sayıdan büyük veya ona eşit olan ilk sayı başvuru tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-168">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="1bcfa-169">Bir sayı bağımsız değişkenden büyük veya ona eşit değilse, yöntem 0 dizininden sayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-169">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span> 

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

<span data-ttu-id="1bcfa-170">Aşağıdaki örnek, 16 ' dan büyük veya buna eşit ilk değeri almak için `NumberStore.FindNumber` yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-170">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="1bcfa-171">Çağıran, yöntemi tarafından döndürülen değeri iki katına çıkarır.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-171">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="1bcfa-172">Örneğin çıktısı, `NumberStore` örneğinin dizi öğelerinin değerinde yansıtılan değişikliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-172">The output from the example shows the change reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

<span data-ttu-id="1bcfa-173">Başvuru dönüş değerleri için destek olmadan, bu tür bir işlem, dizi öğesinin dizinini değeriyle birlikte döndürerek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-173">Without support for reference return values, such an operation is performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="1bcfa-174">Çağıran, bu dizini kullanarak değeri ayrı bir yöntem çağrısında değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-174">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="1bcfa-175">Bununla birlikte, çağıran dizine erişim için de değişiklik yapabilir ve muhtemelen diğer dizi değerlerini değiştirebilir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-175">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  

<span data-ttu-id="1bcfa-176">Aşağıdaki örnek, `FindNumber` yönteminin, ref yerel yeniden atamasını kullanmak üzere C# 7,3 sonrasında nasıl yeniden yazılabilir olduğunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="1bcfa-176">The following example shows how the `FindNumber` method could be rewritten after C# 7.3 to use ref local reassignment:</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

<span data-ttu-id="1bcfa-177">Bu ikinci sürüm, aranan sayının dizinin sonuna yakın olduğu senaryolarda daha uzun dizileriyle daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-177">This second version is more efficient with longer sequences in scenarios where the number sought is closer to the end of the array.</span></span>

## <a name="see-also"></a><span data-ttu-id="1bcfa-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bcfa-178">See also</span></span>

- [<span data-ttu-id="1bcfa-179">ref anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="1bcfa-179">ref keyword</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="1bcfa-180">Güvenli verimli kod yazma</span><span class="sxs-lookup"><span data-stu-id="1bcfa-180">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
