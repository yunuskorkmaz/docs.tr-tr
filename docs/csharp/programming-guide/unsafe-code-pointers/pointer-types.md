---
title: İşaretçi türleri (C# Programlama Kılavuzu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- unsafe code [C#], pointers
- pointers [C#]
ms.assetid: 3319faf9-336d-4148-9af2-1da2579cdd1e
caps.latest.revision: ''
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fe7b926bdf9f662d25f2fe960b51fc8254b7aa3a
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="pointer-types-c-programming-guide"></a><span data-ttu-id="ecfd5-102">İşaretçi türleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ecfd5-102">Pointer types (C# Programming Guide)</span></span>
<span data-ttu-id="ecfd5-103">Güvensiz bir bağlamda, bir işaretçi türü, bir değer türü veya bir başvuru türü bir tür olabilir.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-103">In an unsafe context, a type may be a pointer type, a value type, or a reference type.</span></span> <span data-ttu-id="ecfd5-104">Bir işaretçi türü bildirimi, aşağıdaki biçimlerden birini alır:</span><span class="sxs-lookup"><span data-stu-id="ecfd5-104">A pointer type declaration takes one of the following forms:</span></span>  
  
```  
type* identifier;  
void* identifier; //allowed but not recommended  
```  
  
 <span data-ttu-id="ecfd5-105">Aşağıdaki türlerden herhangi birisi bir işaretçi türü olabilir:</span><span class="sxs-lookup"><span data-stu-id="ecfd5-105">Any of the following types may be a pointer type:</span></span>  
  
-   <span data-ttu-id="ecfd5-106">[sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bayt](../../../csharp/language-reference/keywords/byte.md), [kısa](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [ uzun](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [çift](../../../csharp/language-reference/keywords/double.md), [ondalık](../../../csharp/language-reference/keywords/decimal.md), veya [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="ecfd5-106">[sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [char](../../../csharp/language-reference/keywords/char.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), [decimal](../../../csharp/language-reference/keywords/decimal.md), or [bool](../../../csharp/language-reference/keywords/bool.md).</span></span>  
  
-   <span data-ttu-id="ecfd5-107">Tüm [enum](../../../csharp/language-reference/keywords/enum.md) türü.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-107">Any [enum](../../../csharp/language-reference/keywords/enum.md) type.</span></span>  
  
-   <span data-ttu-id="ecfd5-108">Herhangi bir işaretçi türü.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-108">Any pointer type.</span></span>  
  
-   <span data-ttu-id="ecfd5-109">Yalnızca yönetilmeyen türlerde alanlar içeren, kullanıcı tarafından tanımlanmış herhangi bir yapı türü.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-109">Any user-defined struct type that contains fields of unmanaged types only.</span></span>  
  
 <span data-ttu-id="ecfd5-110">İşaretçi türleri devralmaz gelen [nesne](../../../csharp/language-reference/keywords/object.md) ve işaretçi türleri arasında hiçbir dönüşümleri var ve `object`.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-110">Pointer types do not inherit from [object](../../../csharp/language-reference/keywords/object.md) and no conversions exist between pointer types and `object`.</span></span> <span data-ttu-id="ecfd5-111">Ayrıca, kutulama ve kutudan çıkarma işaretçileri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-111">Also, boxing and unboxing do not support pointers.</span></span> <span data-ttu-id="ecfd5-112">Ancak, farklı işaretçi türleri ve işaretçi türleri ve tamsayı türleri arasında dönüştürme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-112">However, you can convert between different pointer types and between pointer types and integral types.</span></span>  
  
 <span data-ttu-id="ecfd5-113">Aynı bildirimde birden çok işaretçi bildirdiğinizde, yıldız işareti (\*) yalnızca altı çizili türle birlikte yazılır; her bir işaretçi adı için önek olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-113">When you declare multiple pointers in the same declaration, the asterisk (\*) is written together with the underlying type only; it is not used as a prefix to each pointer name.</span></span> <span data-ttu-id="ecfd5-114">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ecfd5-114">For example:</span></span>  
  
```  
int* p1, p2, p3;   // Ok  
int *p1, *p2, *p3;   // Invalid in C#  
```  
  
 <span data-ttu-id="ecfd5-115">Bir işaretçi bir başvuru ya da çok işaret edemez bir [yapısı](../../../csharp/language-reference/keywords/struct.md) nesne başvurusu bir işaretçi işaret olsa bile toplanacak olabileceğinden başvuruları içeren.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-115">A pointer cannot point to a reference or to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains references, because an object reference can be garbage collected even if a pointer is pointing to it.</span></span> <span data-ttu-id="ecfd5-116">Çöp toplayıcı, bir nesneye herhangi bir işaretçi türü tarafından işaret edilip edilmediğini izlemez.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-116">The garbage collector does not keep track of whether an object is being pointed to by any pointer types.</span></span>  
  
 <span data-ttu-id="ecfd5-117">Tür işaretçi değişkeninin değerini `myType*` türünde bir değişken adresidir `myType`.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-117">The value of the pointer variable of type `myType*` is the address of a variable of type `myType`.</span></span> <span data-ttu-id="ecfd5-118">Aşağıda, işaretçi türü bildirimi örnekleri verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ecfd5-118">The following are examples of pointer type declarations:</span></span>  
  
|<span data-ttu-id="ecfd5-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="ecfd5-119">Example</span></span>|<span data-ttu-id="ecfd5-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ecfd5-120">Description</span></span>|  
|-------------|-----------------|  
|`int* p`|<span data-ttu-id="ecfd5-121">`p` tamsayıya bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-121">`p` is a pointer to an integer.</span></span>|  
|`int** p`|<span data-ttu-id="ecfd5-122">`p` tamsayı gösteren bir işaretçi bir işaretçi var.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-122">`p` is a pointer to a pointer to an integer.</span></span>|  
|`int*[] p`|<span data-ttu-id="ecfd5-123">`p` bir tek boyutlu tamsayı işaretçiler dizisidir.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-123">`p` is a single-dimensional array of pointers to integers.</span></span>|  
|`char* p`|<span data-ttu-id="ecfd5-124">`p` bir karakter için bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-124">`p` is a pointer to a char.</span></span>|  
|`void* p`|<span data-ttu-id="ecfd5-125">`p` Bilinmeyen bir tür için bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-125">`p` is a pointer to an unknown type.</span></span>|  
  
 <span data-ttu-id="ecfd5-126">İşaretçi yöneltme işleci \*, işaretçi değişkeninin işaret ettiği yerdeki içeriğe erişebilir.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-126">The pointer indirection operator \* can be used to access the contents at the location pointed to by the pointer variable.</span></span> <span data-ttu-id="ecfd5-127">Örneğin, aşağıdaki bildirimi ele alalım:</span><span class="sxs-lookup"><span data-stu-id="ecfd5-127">For example, consider the following declaration:</span></span>  
  
```  
int* myVariable;  
```  
  
 <span data-ttu-id="ecfd5-128">İfade `*myVariable` gösterir `int` içinde yer alan adresinde bulunan değişkeni `myVariable`.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-128">The expression `*myVariable` denotes the `int` variable found at the address contained in `myVariable`.</span></span>  
  
 <span data-ttu-id="ecfd5-129">Bazı işaretçiler konulardaki örnekleri vardır [deyimi sabit](../../../csharp/language-reference/keywords/fixed-statement.md) ve [işaretçi dönüşümleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="ecfd5-129">There are several examples of pointers in the topics [fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) and [Pointer Conversions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md).</span></span>  <span data-ttu-id="ecfd5-130">Aşağıdaki örnek, gereksinimini gösterir `unsafe` anahtar sözcüğü ve `fixed` deyimi ve iç işaretçi artırmak nasıl.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-130">The following example shows the need for the `unsafe` keyword and the `fixed` statement, and how to increment an interior pointer.</span></span>  <span data-ttu-id="ecfd5-131">Bu kodu çalıştırmak için bir konsolun Ana işlevine yapıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-131">You can paste this code into the Main function of a console application to run it.</span></span> <span data-ttu-id="ecfd5-132">(Güvenli olmayan kod içinde etkinleştirmeyi unutmayın **Proje Tasarımcısı**; seçin **proje**, **özellikleri** menüsünde çubuğu ve ardından **güvenli olmayan kodizinver** içinde **yapı** sekmesi.)</span><span class="sxs-lookup"><span data-stu-id="ecfd5-132">(Remember to enable unsafe code in the **Project Designer**; choose **Project**, **Properties** on the menu bar, and then select **Allow unsafe code** in the **Build** tab.)</span></span>  
  
```  
// Normal pointer to an object.  
int[] a = new int[5] {10, 20, 30, 40, 50};  
// Must be in unsafe code to use interior pointers.  
unsafe  
{  
    // Must pin object on heap so that it doesn't move while using interior pointers.  
    fixed (int* p = &a[0])  
    {  
        // p is pinned as well as object, so create another pointer to show incrementing it.  
        int* p2 = p;  
        Console.WriteLine(*p2);  
        // Incrementing p2 bumps the pointer by four bytes due to its type ...  
        p2 += 1;  
        Console.WriteLine(*p2);  
        p2 += 1;  
        Console.WriteLine(*p2);  
        Console.WriteLine("--------");  
        Console.WriteLine(*p);  
        // Deferencing p and incrementing changes the value of a[0] ...  
        *p += 1;  
        Console.WriteLine(*p);  
        *p += 1;  
        Console.WriteLine(*p);  
    }  
}  
  
Console.WriteLine("--------");  
Console.WriteLine(a[0]);  
Console.ReadLine();  
  
// Output:  
//10  
//20  
//30  
//--------  
//10  
//11  
//12  
//--------  
//12  
```  
  
 <span data-ttu-id="ecfd5-133">İndirection işleci gösteren bir işaretçi türü uygulanamıyor `void*`.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-133">You cannot apply the indirection operator to a pointer of type `void*`.</span></span> <span data-ttu-id="ecfd5-134">Ancak, boş bir işaretçiyi başka herhangi bir türü dönüştürmek veya bunun tersini yapmak için bir yayın kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-134">However, you can use a cast to convert a void pointer to any other pointer type, and vice versa.</span></span>  
  
 <span data-ttu-id="ecfd5-135">Bir işaretçi olabilir `null`.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-135">A pointer can be `null`.</span></span> <span data-ttu-id="ecfd5-136">Yönlendirme işlecini bir null işaretçiye uygulamak, uygulama tarafından tanımlanan bir davranışa neden olur.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-136">Applying the indirection operator to a null pointer causes an implementation-defined behavior.</span></span>  
  
 <span data-ttu-id="ecfd5-137">İşaretçilerin yöntemler arasında aktarılmasının tanımlanmamış davranışa neden olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-137">Be aware that passing pointers between methods can cause undefined behavior.</span></span> <span data-ttu-id="ecfd5-138">Yerel bir değişken için bir işaretçi döndüren bir yöntem göz önünde bulundurun bir `in`, `out` veya `ref` parametresi ya da işlevin sonucu olarak.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-138">Consider a method that returns a pointer to a local variable through an `in`, `out` or `ref` parameter or as the function result.</span></span> <span data-ttu-id="ecfd5-139">İşaretçi sabit bir blokta ayarlandıysa, işaret ettiği değişken artık sabit olamaz.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-139">If the pointer was set in a fixed block, the variable to which it points may no longer be fixed.</span></span>  
  
 <span data-ttu-id="ecfd5-140">Aşağıdaki tabloda, güvenli olmayan bir bağlamda işaretçiler üzerinde işlem yapabilecek işleçler ve deyimler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="ecfd5-140">The following table lists the operators and statements that can operate on pointers in an unsafe context:</span></span>  
  
|<span data-ttu-id="ecfd5-141">İşleç/Deyim</span><span class="sxs-lookup"><span data-stu-id="ecfd5-141">Operator/Statement</span></span>|<span data-ttu-id="ecfd5-142">Bir yönetim grubuna bağlanmak veya bağlı bir yönetim grubunun özelliklerini düzenlemek için Yönetim çalışma alanında</span><span class="sxs-lookup"><span data-stu-id="ecfd5-142">Use</span></span>|  
|-------------------------|---------|  
|*|<span data-ttu-id="ecfd5-143">İşaretçi yöneltmesi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-143">Performs pointer indirection.</span></span>|  
|->|<span data-ttu-id="ecfd5-144">Bir yapının bir üyesine bir işaretçi yoluyla erişir.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-144">Accesses a member of a struct through a pointer.</span></span>|  
|<span data-ttu-id="ecfd5-145">[]</span><span class="sxs-lookup"><span data-stu-id="ecfd5-145">[]</span></span>|<span data-ttu-id="ecfd5-146">Bir işaretçiyi dizine ekler.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-146">Indexes a pointer.</span></span>|  
|`&`|<span data-ttu-id="ecfd5-147">Bir değişkenin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-147">Obtains the address of a variable.</span></span>|  
|<span data-ttu-id="ecfd5-148">++ ve --</span><span class="sxs-lookup"><span data-stu-id="ecfd5-148">++ and --</span></span>|<span data-ttu-id="ecfd5-149">İşaretçileri artırır ve azaltır.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-149">Increments and decrements pointers.</span></span>|  
|<span data-ttu-id="ecfd5-150">+ ve -</span><span class="sxs-lookup"><span data-stu-id="ecfd5-150">+ and -</span></span>|<span data-ttu-id="ecfd5-151">İşaretçi aritmetiği gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-151">Performs pointer arithmetic.</span></span>|  
|<span data-ttu-id="ecfd5-152">==,! =, \<, >, \<= ve > =</span><span class="sxs-lookup"><span data-stu-id="ecfd5-152">==, !=, \<, >, \<=, and >=</span></span>|<span data-ttu-id="ecfd5-153">İşaretçileri karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-153">Compares pointers.</span></span>|  
|`stackalloc`|<span data-ttu-id="ecfd5-154">Yığında bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-154">Allocates memory on the stack.</span></span>|  
|<span data-ttu-id="ecfd5-155">`fixed` Deyimi</span><span class="sxs-lookup"><span data-stu-id="ecfd5-155">`fixed` statement</span></span>|<span data-ttu-id="ecfd5-156">Adresinin bulunamaması için bir değişkeni geçici olarak sabitler.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-156">Temporarily fixes a variable so that its address may be found.</span></span>|  
  
## <a name="c-language-specification"></a><span data-ttu-id="ecfd5-157">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="ecfd5-157">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ecfd5-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ecfd5-158">See Also</span></span>  
 [<span data-ttu-id="ecfd5-159">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ecfd5-159">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ecfd5-160">Güvenli Olmayan Kod ve İşaretçiler</span><span class="sxs-lookup"><span data-stu-id="ecfd5-160">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="ecfd5-161">İşaretçi Dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="ecfd5-161">Pointer Conversions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md)  
 [<span data-ttu-id="ecfd5-162">İşaretçi İfadeleri</span><span class="sxs-lookup"><span data-stu-id="ecfd5-162">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="ecfd5-163">Türler</span><span class="sxs-lookup"><span data-stu-id="ecfd5-163">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="ecfd5-164">unsafe</span><span class="sxs-lookup"><span data-stu-id="ecfd5-164">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="ecfd5-165">fixed Deyimi</span><span class="sxs-lookup"><span data-stu-id="ecfd5-165">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="ecfd5-166">stackalloc</span><span class="sxs-lookup"><span data-stu-id="ecfd5-166">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)  
 [<span data-ttu-id="ecfd5-167">Kutulama ve Kutudan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="ecfd5-167">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
