---
title: Ref iade değerleri ve ref yerlileri (C# Guide)
description: Ref return ve ref local değerlerini nasıl tanımlayıp kullanacağınızı öğrenin
ms.date: 04/04/2018
ms.openlocfilehash: 87a9538db60d69062f0fb48ed9683a9d4f972b91
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170079"
---
# <a name="ref-returns-and-ref-locals"></a><span data-ttu-id="40276-103">Ref dönüşler ve ref yerel ayarlar</span><span class="sxs-lookup"><span data-stu-id="40276-103">Ref returns and ref locals</span></span>

<span data-ttu-id="40276-104">C# 7.0 ile başlayarak, C# referans iade değerlerini (ref döner) destekler.</span><span class="sxs-lookup"><span data-stu-id="40276-104">Starting with C# 7.0, C# supports reference return values (ref returns).</span></span> <span data-ttu-id="40276-105">Başvuru iade değeri, bir yöntemin bir başvurucuzun bir değer yerine bir değişkene geri dönmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="40276-105">A reference return value allows a method to return a reference to a variable, rather than a value, back to a caller.</span></span> <span data-ttu-id="40276-106">Arayan daha sonra döndürülen değişkeni değer veya başvuru yla döndürülmüş gibi ele almayı seçebilir.</span><span class="sxs-lookup"><span data-stu-id="40276-106">The caller can then choose to treat the returned variable as if it were returned by value or by reference.</span></span> <span data-ttu-id="40276-107">Arayan, döndürülen değere bir başvuru olan ve ref yerel olarak adlandırılan yeni bir değişken oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="40276-107">The caller can create a new variable that is itself a reference to the returned value, called a ref local.</span></span>

## <a name="what-is-a-reference-return-value"></a><span data-ttu-id="40276-108">Referans iade değeri nedir?</span><span class="sxs-lookup"><span data-stu-id="40276-108">What is a reference return value?</span></span>

<span data-ttu-id="40276-109">Çoğu geliştirici, bir bağımsız değişkeni *başvuru yla*çağrılan yönteme geçirmeye aşinadır.</span><span class="sxs-lookup"><span data-stu-id="40276-109">Most developers are familiar with passing an argument to a called method *by reference*.</span></span> <span data-ttu-id="40276-110">Çağrılan yöntemin bağımsız değişken listesi, başvuru tarafından geçirilen bir değişken içerir.</span><span class="sxs-lookup"><span data-stu-id="40276-110">A called method's argument list includes a variable passed by reference.</span></span> <span data-ttu-id="40276-111">Çağrılan yöntemle değerinde yapılan değişiklikler arayan tarafından gözlenir.</span><span class="sxs-lookup"><span data-stu-id="40276-111">Any changes made to its value by the called method are observed by the caller.</span></span> <span data-ttu-id="40276-112">*Başvuru iade değeri,* yöntemin bazı değişkenlere *bir başvuru* (veya diğer ad) döndürdüğü anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="40276-112">A *reference return value* means that a method returns a *reference* (or an alias) to some variable.</span></span> <span data-ttu-id="40276-113">Bu değişkenin kapsamı yöntemi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="40276-113">That variable's scope must include the method.</span></span> <span data-ttu-id="40276-114">Bu değişkenin ömrü yöntemin geri dönüşünden öteye uzanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="40276-114">That variable's lifetime must extend beyond the return of the method.</span></span> <span data-ttu-id="40276-115">Arayanın yöntemin geri dönüş değerinde yaptığı değişiklikler, yöntem tarafından döndürülen değişkene yapılır.</span><span class="sxs-lookup"><span data-stu-id="40276-115">Modifications to the method's return value by the caller are made to the variable that is returned by the method.</span></span>

<span data-ttu-id="40276-116">Bir yöntemin bir *başvuru iade değeri* döndürüğünün beyan ı, yöntemin bir diğer adı bir değişkene döndürüğünu gösterir.</span><span class="sxs-lookup"><span data-stu-id="40276-116">Declaring that a method returns a *reference return value* indicates that the method returns an alias to a variable.</span></span> <span data-ttu-id="40276-117">Tasarım amacı genellikle arama kodunun bu değişkene diğer ad aracılığıyla erişmesi gerektiğidir.</span><span class="sxs-lookup"><span data-stu-id="40276-117">The design intent is often that the calling code should have access to that variable through the alias, including to modify it.</span></span> <span data-ttu-id="40276-118">Başvuruyla dönen yöntemlerin return türüne `void`sahip olamamayacağı izsini izler.</span><span class="sxs-lookup"><span data-stu-id="40276-118">It follows that methods returning by reference can't have the return type `void`.</span></span>

<span data-ttu-id="40276-119">Bir yöntemin başvuru iade değeri olarak döndürülebileceği ifadeüzerinde bazı kısıtlamalar vardır.</span><span class="sxs-lookup"><span data-stu-id="40276-119">There are some restrictions on the expression that a method can return as a reference return value.</span></span> <span data-ttu-id="40276-120">Kısıtlamalar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="40276-120">Restrictions include:</span></span>

- <span data-ttu-id="40276-121">İade değerinin, yöntemin yürütülmesinin ötesine uzanan bir ömrü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="40276-121">The return value must have a lifetime that extends beyond the execution of the method.</span></span> <span data-ttu-id="40276-122">Başka bir deyişle, döndüren yöntemde yerel bir değişken olamaz.</span><span class="sxs-lookup"><span data-stu-id="40276-122">In other words, it cannot be a local variable in the method that returns it.</span></span> <span data-ttu-id="40276-123">Bir sınıfın örnek veya statik alanı olabilir veya yönteme geçirilen bir bağımsız değişken olabilir.</span><span class="sxs-lookup"><span data-stu-id="40276-123">It can be an instance or static field of a class, or it can be an argument passed to the method.</span></span> <span data-ttu-id="40276-124">Yerel bir değişkeni döndürmeye çalışırken derleyici hatası CS8168 oluşturur, "Ref local olmadığı için başvuru yla yerel 'obj' döndüremez."</span><span class="sxs-lookup"><span data-stu-id="40276-124">Attempting to return a local variable generates compiler error CS8168, "Cannot return local 'obj' by reference because it is not a ref local."</span></span>

- <span data-ttu-id="40276-125">İade değeri gerçek `null`olamaz.</span><span class="sxs-lookup"><span data-stu-id="40276-125">The return value cannot be the literal `null`.</span></span> <span data-ttu-id="40276-126">Returning `null` derleyici hatası CS8156 oluşturur, "Bir ifade başvuru yla döndürülemeyebilir, çünkü bu bağlamda kullanılamaz."</span><span class="sxs-lookup"><span data-stu-id="40276-126">Returning `null` generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

   <span data-ttu-id="40276-127">Ref iadesi olan bir yöntem, değeri şu anda null (instantiated) değeri olan bir değişkene veya bir değer türü için [nullable değer türüne](../../language-reference/builtin-types/nullable-value-types.md) bir diğer ad döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="40276-127">A method with a ref return can return an alias to a variable whose value is currently the null (uninstantiated) value or a [nullable value type](../../language-reference/builtin-types/nullable-value-types.md) for a value type.</span></span>

- <span data-ttu-id="40276-128">İade değeri sabit, numaralandırma üyesi, bir özellikten gelen yan değer dönüş değeri veya `class` bir `struct`veya .</span><span class="sxs-lookup"><span data-stu-id="40276-128">The return value cannot be a constant, an enumeration member, the by-value return value from a property, or a method of a `class` or `struct`.</span></span> <span data-ttu-id="40276-129">Bu kuralı ihlal etmek derleyici hatası CS8156 oluşturur, "Bir ifade başvuruyla döndürülemeyebilir, çünkü bu bağlamda kullanılamaz."</span><span class="sxs-lookup"><span data-stu-id="40276-129">Violating this rule generates compiler error CS8156, "An expression cannot be used in this context because it may not be returned by reference."</span></span>

<span data-ttu-id="40276-130">Buna ek olarak, async yöntemleri referans dönüş değerleri izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="40276-130">In addition, reference return values are not allowed on async methods.</span></span> <span data-ttu-id="40276-131">Adsız bir yöntem yürütme tamamlanmadan önce dönebilir, ancak geri dönüş değeri hala bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="40276-131">An asynchronous method may return before it has finished execution, while its return value is still unknown.</span></span>

## <a name="defining-a-ref-return-value"></a><span data-ttu-id="40276-132">Ref iade değerinin tanımlanması</span><span class="sxs-lookup"><span data-stu-id="40276-132">Defining a ref return value</span></span>

<span data-ttu-id="40276-133">*Başvuru iade değerini* döndüren bir yöntem aşağıdaki iki koşulu karşılamalıdır:</span><span class="sxs-lookup"><span data-stu-id="40276-133">A method that returns a *reference return value* must satisfy the following two conditions:</span></span>

- <span data-ttu-id="40276-134">Yöntem imzası, iade türünün önündeki [ref](../../language-reference/keywords/ref.md) anahtar sözcüğüiçerir.</span><span class="sxs-lookup"><span data-stu-id="40276-134">The method signature includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the return type.</span></span>
- <span data-ttu-id="40276-135">Yöntem gövdesindeki her [iade](../../language-reference/keywords/return.md) deyimi, döndürülen örneğin adının önündeki [ref](../../language-reference/keywords/ref.md) anahtar sözcüğüiçerir.</span><span class="sxs-lookup"><span data-stu-id="40276-135">Each [return](../../language-reference/keywords/return.md) statement in the method body includes the [ref](../../language-reference/keywords/ref.md) keyword in front of the name of the returned instance.</span></span>

<span data-ttu-id="40276-136">Aşağıdaki örnek, bu koşulları karşılayan ve bir başvuruyu adlı `Person` `p`nesneye döndüren bir yöntem gösterir:</span><span class="sxs-lookup"><span data-stu-id="40276-136">The following example shows a method that satisfies those conditions and returns a reference to a `Person` object named `p`:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
{
    // ...method implementation...
    return ref p;
}
```

## <a name="consuming-a-ref-return-value"></a><span data-ttu-id="40276-137">Ref iade değerini tüketme</span><span class="sxs-lookup"><span data-stu-id="40276-137">Consuming a ref return value</span></span>

<span data-ttu-id="40276-138">Ref dönüş değeri, çağrılan yöntemin kapsamındaki başka bir değişkenin diğer adıdır.</span><span class="sxs-lookup"><span data-stu-id="40276-138">The ref return value is an alias to another variable in the called method's scope.</span></span> <span data-ttu-id="40276-139">Ref iadesinin herhangi bir kullanımını diğer adlar değişkenini kullanarak yorumlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="40276-139">You can interpret any use of the ref return as using the variable it aliases:</span></span>

- <span data-ttu-id="40276-140">Değerini atadığınızda, diğer adlarına bir değer atarsınız.</span><span class="sxs-lookup"><span data-stu-id="40276-140">When you assign its value, you are assigning a value to the variable it aliases.</span></span>
- <span data-ttu-id="40276-141">Değerini okuduğunuzda, diğer adlarının değişkeninin değerini okuyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="40276-141">When you read its value, you are reading the value of the variable it aliases.</span></span>
- <span data-ttu-id="40276-142">*Başvuruyla*döndürerseniz, aynı değişkene bir diğer ad döndürebilirsin.</span><span class="sxs-lookup"><span data-stu-id="40276-142">If you return it *by reference*, you are returning an alias to that same variable.</span></span>
- <span data-ttu-id="40276-143">*Başvuru yla*başka bir yönteme geçerseniz, diğer adlarına bir başvuru aktarırsınız.</span><span class="sxs-lookup"><span data-stu-id="40276-143">If you pass it to another method *by reference*, you are passing a reference to the variable it aliases.</span></span>
- <span data-ttu-id="40276-144">Bir ref [yerel](#ref-locals) takma ad yaptığınızda, aynı değişkene yeni bir takma ad yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="40276-144">When you make a [ref local](#ref-locals) alias, you make a new alias to the same variable.</span></span>

## <a name="ref-locals"></a><span data-ttu-id="40276-145">Ref yerlileri</span><span class="sxs-lookup"><span data-stu-id="40276-145">Ref locals</span></span>

<span data-ttu-id="40276-146">Yöntemin `GetContactInformation` ref iadesi olarak beyan edildiği varsayalım:</span><span class="sxs-lookup"><span data-stu-id="40276-146">Assume the `GetContactInformation` method is declared as a ref return:</span></span>

```csharp
public ref Person GetContactInformation(string fname, string lname)
```

<span data-ttu-id="40276-147">Bir yan değer ataması bir değişkenin değerini okur ve onu yeni bir değişkene atar:</span><span class="sxs-lookup"><span data-stu-id="40276-147">A by-value assignment reads the value of a variable and assigns it to a new variable:</span></span>

```csharp
Person p = contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="40276-148">Önceki atama yerel `p` değişken olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="40276-148">The preceding assignment declares `p` as a local variable.</span></span> <span data-ttu-id="40276-149">İlk değeri, döndürülen değerin okunmasından `GetContactInformation`kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="40276-149">Its initial value is copied from reading the value returned by `GetContactInformation`.</span></span> <span data-ttu-id="40276-150">Gelecekteki atamalar `p` tarafından döndürülen değişkenin değerini `GetContactInformation`değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="40276-150">Any future assignments to `p` will not change the value of the variable returned by `GetContactInformation`.</span></span> <span data-ttu-id="40276-151">Değişken `p` artık döndürülen değişkenin diğer adı değildir.</span><span class="sxs-lookup"><span data-stu-id="40276-151">The variable `p` is no longer an alias to the variable returned.</span></span>

<span data-ttu-id="40276-152">Diğer adı özgün değere kopyalamak için *ref yerel* değişkeni beyan esiniz.</span><span class="sxs-lookup"><span data-stu-id="40276-152">You declare a *ref local* variable to copy the alias to the original value.</span></span> <span data-ttu-id="40276-153">Aşağıdaki atamada, `p` 'den `GetContactInformation`döndürülen değişkenin diğer adıdır.</span><span class="sxs-lookup"><span data-stu-id="40276-153">In the following assignment, `p` is an alias to the variable returned from `GetContactInformation`.</span></span>

```csharp
ref Person p = ref contacts.GetContactInformation("Brandie", "Best");
```

<span data-ttu-id="40276-154">Sonraki `p` kullanım, bu değişkenin diğer `GetContactInformation` adı `p` olduğu için döndürülen değişkeni kullanmakla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="40276-154">Subsequent usage of `p` is the same as using the variable returned by `GetContactInformation` because `p` is an alias for that variable.</span></span> <span data-ttu-id="40276-155">Döndürülen `p` değişkeni değiştirmek `GetContactInformation`için yapılan değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="40276-155">Changes to `p` also change the variable returned from `GetContactInformation`.</span></span>

<span data-ttu-id="40276-156">`ref` Anahtar kelime hem yerel değişken bildiriminden önce *hem* de yöntem çağrısından önce kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40276-156">The `ref` keyword is used both before the local variable declaration *and* before the method call.</span></span>

<span data-ttu-id="40276-157">Bir değere aynı şekilde başvuru yla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40276-157">You can access a value by reference in the same way.</span></span> <span data-ttu-id="40276-158">Bazı durumlarda, bir değere referans la erişmek, pahalı olabilecek bir kopyalama işleminden kaçınarak performansı artırır.</span><span class="sxs-lookup"><span data-stu-id="40276-158">In some cases, accessing a value by reference increases performance by avoiding a potentially expensive copy operation.</span></span> <span data-ttu-id="40276-159">Örneğin, aşağıdaki deyim, bir değere başvurmak için kullanılan bir ref yerel değerini nasıl tanımlayabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="40276-159">For example, the following statement shows how one can define a ref local value that is used to reference a value.</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct;
```

<span data-ttu-id="40276-160">`ref` Anahtar kelime hem yerel değişken bildiriminden önce *hem* de ikinci örnekteki değerden önce kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40276-160">The `ref` keyword is used both before the local variable declaration *and* before the value in the second example.</span></span> <span data-ttu-id="40276-161">Değişken bildirimi `ref` ve atama her iki örnekte her iki anahtar kelime dahil edilmemesi derleyici hatası CS8172 sonuçlanır, "Bir değer ile bir by-referans değişken başlatılması olamaz."</span><span class="sxs-lookup"><span data-stu-id="40276-161">Failure to include both `ref` keywords in the variable declaration and assignment in both examples results in compiler error CS8172, "Cannot initialize a by-reference variable with a value."</span></span>

<span data-ttu-id="40276-162">C# 7.3'ten önce, ref yerel değişkenleri baş harfe batandıktan sonra farklı depolama alanına başvurmak üzere yeniden atanamadı.</span><span class="sxs-lookup"><span data-stu-id="40276-162">Prior to C# 7.3, ref local variables couldn't be reassigned to refer to different storage after being initialized.</span></span> <span data-ttu-id="40276-163">Bu kısıtlama kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="40276-163">That restriction has been removed.</span></span> <span data-ttu-id="40276-164">Aşağıdaki örnekte yeniden atama gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="40276-164">The following example shows a reassignment:</span></span>

```csharp
ref VeryLargeStruct reflocal = ref veryLargeStruct; // initialization
refLocal = ref anotherVeryLargeStruct; // reassigned, refLocal refers to different storage.
```

 <span data-ttu-id="40276-165">Ref yerel değişkenler, beyan edildiklerinde hala başharfe alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="40276-165">Ref local variables must still be initialized when they are declared.</span></span>

## <a name="ref-returns-and-ref-locals-an-example"></a><span data-ttu-id="40276-166">Ref döner ve ref yerliler: bir örnek</span><span class="sxs-lookup"><span data-stu-id="40276-166">Ref returns and ref locals: an example</span></span>

<span data-ttu-id="40276-167">Aşağıdaki örnek, bir `NumberStore` tamsayı değerleri dizisini depolayan bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="40276-167">The following example defines a `NumberStore` class that stores an array of integer values.</span></span> <span data-ttu-id="40276-168">Yöntem, `FindNumber` bağımsız değişken olarak geçirilen sayıdan daha büyük veya eşit olan ilk sayıyı referans la döndürür.</span><span class="sxs-lookup"><span data-stu-id="40276-168">The `FindNumber` method returns by reference the first number that is greater than or equal to the number passed as an argument.</span></span> <span data-ttu-id="40276-169">Hiçbir sayı bağımsız değişkenden büyük veya eşit değilse, yöntem dizin 0'daki sayıyı döndürür.</span><span class="sxs-lookup"><span data-stu-id="40276-169">If no number is greater than or equal to the argument, the method returns the number in index 0.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#1)]

<span data-ttu-id="40276-170">Aşağıdaki örnek, `NumberStore.FindNumber` 16'dan büyük veya eşit olan ilk değeri almak için yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="40276-170">The following example calls the `NumberStore.FindNumber` method to retrieve the first value that is greater than or equal to 16.</span></span> <span data-ttu-id="40276-171">Arayan daha sonra yöntem tarafından döndürülen değeri iki katına çıkar.</span><span class="sxs-lookup"><span data-stu-id="40276-171">The caller then doubles the value returned by the method.</span></span> <span data-ttu-id="40276-172">Örnekteki çıktı, `NumberStore` örneğin dizi öğelerinin değerine yansıyan değişikliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="40276-172">The output from the example shows the change reflected in the value of the array elements of the `NumberStore` instance.</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStore.cs#2)]

<span data-ttu-id="40276-173">Referans döndürücü değerler desteği olmadan, bu tür bir işlem değeri ile birlikte dizi öğesidizini döndürülerek gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="40276-173">Without support for reference return values, such an operation is performed by returning the index of the array element along with its value.</span></span> <span data-ttu-id="40276-174">Arayan daha sonra ayrı bir yöntem çağrısında değeri değiştirmek için bu dizini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40276-174">The caller can then use this index to modify the value in a separate method call.</span></span> <span data-ttu-id="40276-175">Ancak, arayan dizin erişmek ve büyük olasılıkla diğer dizi değerlerini değiştirmek için de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40276-175">However, the caller can also modify the index to access and possibly modify other array values.</span></span>  

<span data-ttu-id="40276-176">Aşağıdaki örnek, yöntemin `FindNumber` ref yerel yeniden atamasını kullanmak için C# 7.3'ten sonra nasıl yeniden yazılabileceğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="40276-176">The following example shows how the `FindNumber` method could be rewritten after C# 7.3 to use ref local reassignment:</span></span>

[!code-csharp[ref-returns](../../../../samples/snippets/csharp/programming-guide/ref-returns/NumberStoreUpdated.cs#1)]

<span data-ttu-id="40276-177">Bu ikinci sürüm, aranan sayının dizinin sonuna daha yakın olduğu senaryolarda daha uzun dizilerle daha verimlidir.</span><span class="sxs-lookup"><span data-stu-id="40276-177">This second version is more efficient with longer sequences in scenarios where the number sought is closer to the end of the array.</span></span>

## <a name="see-also"></a><span data-ttu-id="40276-178">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40276-178">See also</span></span>

- [<span data-ttu-id="40276-179">ref anahtar kelime</span><span class="sxs-lookup"><span data-stu-id="40276-179">ref keyword</span></span>](../../language-reference/keywords/ref.md)
- [<span data-ttu-id="40276-180">Güvenli verimli kod yazın</span><span class="sxs-lookup"><span data-stu-id="40276-180">Write safe efficient code</span></span>](../../write-safe-efficient-code.md)
