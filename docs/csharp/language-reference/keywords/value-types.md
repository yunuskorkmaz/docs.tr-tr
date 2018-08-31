---
title: Değer Türleri (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 3bbaea9247d975c27ed6f49dedb749312f675296
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331856"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="dbb2e-102">Değer Türleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="dbb2e-102">Value Types (C# Reference)</span></span>
<span data-ttu-id="dbb2e-103">Değer türleri iki ana kategoride oluşur:</span><span class="sxs-lookup"><span data-stu-id="dbb2e-103">The value types consist of two main categories:</span></span>  
  
-   [<span data-ttu-id="dbb2e-104">Yapılar</span><span class="sxs-lookup"><span data-stu-id="dbb2e-104">Structs</span></span>](../../../csharp/language-reference/keywords/struct.md)  
  
-   [<span data-ttu-id="dbb2e-105">Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="dbb2e-105">Enumerations</span></span>](../../../csharp/language-reference/keywords/enum.md)  
  
 <span data-ttu-id="dbb2e-106">Yapılar, bu kategoriye ayrılır:</span><span class="sxs-lookup"><span data-stu-id="dbb2e-106">Structs fall into these categories:</span></span>  
  
-   <span data-ttu-id="dbb2e-107">Sayısal türler</span><span class="sxs-lookup"><span data-stu-id="dbb2e-107">Numeric types</span></span>  
  
    -   [<span data-ttu-id="dbb2e-108">Tam sayı türleri</span><span class="sxs-lookup"><span data-stu-id="dbb2e-108">Integral types</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
  
    -   [<span data-ttu-id="dbb2e-109">Kayan nokta türleri</span><span class="sxs-lookup"><span data-stu-id="dbb2e-109">Floating-point types</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
  
-   [<span data-ttu-id="dbb2e-110">bool</span><span class="sxs-lookup"><span data-stu-id="dbb2e-110">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)  
  
-   <span data-ttu-id="dbb2e-111">Kullanıcı tanımlı yapılar.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-111">User defined structs.</span></span>  
  
## <a name="main-features-of-value-types"></a><span data-ttu-id="dbb2e-112">Değer türleri'larının temel özellikleri</span><span class="sxs-lookup"><span data-stu-id="dbb2e-112">Main Features of Value Types</span></span>  
 <span data-ttu-id="dbb2e-113">Değer türlerine doğrudan bağlı değişkenleri değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-113">Variables that are based on value types directly contain values.</span></span> <span data-ttu-id="dbb2e-114">Bir değer türü değişken içindeki değeri için başka bir kopya atama.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-114">Assigning one value type variable to another copies the contained value.</span></span> <span data-ttu-id="dbb2e-115">Bu nesne, ancak nesnenin kendisi için bir başvuru kopyalayan atama başvuru türü değişkenlerin farklıdır.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-115">This differs from the assignment of reference type variables, which copies a reference to the object but not the object itself.</span></span>  
  
 <span data-ttu-id="dbb2e-116">Tüm değer türleri örtülü olarak türetilmiş <xref:System.ValueType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-116">All value types are derived implicitly from the <xref:System.ValueType?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="dbb2e-117">Farklı başvuru türleri ile yeni bir tür bir değer türünden türetilemez.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-117">Unlike with reference types, you cannot derive a new type from a value type.</span></span> <span data-ttu-id="dbb2e-118">Ancak, başvuru türleri, ister yapılar, arabirimler uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-118">However, like reference types, structs can implement interfaces.</span></span>  
  
 <span data-ttu-id="dbb2e-119">Başvuru türlerinin aksine, bir değer türü içeremez `null` değeri.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-119">Unlike reference types, a value type cannot contain the `null` value.</span></span> <span data-ttu-id="dbb2e-120">Ancak, [boş değer atanabilir türler](../../../csharp/programming-guide/nullable-types/index.md) özelliğinin izin atanacak değer türleri için `null`.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-120">However, the [nullable types](../../../csharp/programming-guide/nullable-types/index.md) feature does allow for value types to be assigned to `null`.</span></span>  
  
 <span data-ttu-id="dbb2e-121">Her değer türü varsayılan değer türü başlatan örtülü varsayılan bir oluşturucuya sahiptir.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-121">Each value type has an implicit default constructor that initializes the default value of that type.</span></span> <span data-ttu-id="dbb2e-122">Değer türleri varsayılan değerler hakkında daha fazla bilgi için bkz. [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="dbb2e-122">For information about default values of value types, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
## <a name="main-features-of-simple-types"></a><span data-ttu-id="dbb2e-123">Basit türler'larının temel özellikleri</span><span class="sxs-lookup"><span data-stu-id="dbb2e-123">Main Features of Simple Types</span></span>  
 <span data-ttu-id="dbb2e-124">--C# dilinin bu sayıya--basit türlerinin tümü, .NET Framework sistem türleri adlardır.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-124">All of the simple types -- those integral to the C# language -- are aliases of the .NET Framework System types.</span></span> <span data-ttu-id="dbb2e-125">Örneğin, [int](../../../csharp/language-reference/keywords/int.md) bir diğer adıdır <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-125">For example, [int](../../../csharp/language-reference/keywords/int.md) is an alias of <xref:System.Int32?displayProperty=nameWithType>.</span></span> <span data-ttu-id="dbb2e-126">Diğer adlar tam bir listesi için bkz. [yerleşik türler tablosu](../../../csharp/language-reference/keywords/built-in-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="dbb2e-126">For a complete list of aliases, see [Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md).</span></span>  
  
 <span data-ttu-id="dbb2e-127">Sabit ifadeler, işlenenleri tüm basit tür sabit değerlerdir, derleme zamanında değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-127">Constant expressions, whose operands are all simple type constants, are evaluated at compilation time.</span></span>  
  
 <span data-ttu-id="dbb2e-128">Basit türler, değişmez değerleri kullanılarak başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-128">Simple types can be initialized by using literals.</span></span> <span data-ttu-id="dbb2e-129">Örneğin, '' bir sabit değer türü açık `char` ve 2001 bir sabit değer türü `int`.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-129">For example, 'A' is a literal of the type `char` and 2001 is a literal of the type `int`.</span></span>  
  
## <a name="initializing-value-types"></a><span data-ttu-id="dbb2e-130">Değer türleri başlatma</span><span class="sxs-lookup"><span data-stu-id="dbb2e-130">Initializing Value Types</span></span>  
 <span data-ttu-id="dbb2e-131">C# dilinde yerel değişkenler, kullanılmadan önce başlatılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-131">Local variables in C# must be initialized before they are used.</span></span> <span data-ttu-id="dbb2e-132">Örneğin, aşağıdaki örnekte olduğu gibi başlatma olmadan yerel bir değişken bildirmeniz:</span><span class="sxs-lookup"><span data-stu-id="dbb2e-132">For example, you might declare a local variable without initialization as in the following example:</span></span>  
  
```csharp  
int myInt;  
```  
  
 <span data-ttu-id="dbb2e-133">Bunu başlatılmadan önce kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-133">You cannot use it before you initialize it.</span></span> <span data-ttu-id="dbb2e-134">Aşağıdaki deyimi kullanarak başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dbb2e-134">You can initialize it using the following statement:</span></span>  
  
```csharp  
myInt = new int();  // Invoke default constructor for int type.  
```  
  
 <span data-ttu-id="dbb2e-135">Bu ifade, aşağıdaki deyime eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="dbb2e-135">This statement is equivalent to the following statement:</span></span>  
  
```csharp  
myInt = 0;         // Assign an initial value, 0 in this example.  
```  
  
 <span data-ttu-id="dbb2e-136">Elbette, bildirim ve başlatma aşağıdaki örneklerde gösterildiği gibi aynı deyimde olabilir:</span><span class="sxs-lookup"><span data-stu-id="dbb2e-136">You can, of course, have the declaration and the initialization in the same statement as in the following examples:</span></span>  
  
```csharp  
int myInt = new int();  
```  
  
 <span data-ttu-id="dbb2e-137">– veya –</span><span class="sxs-lookup"><span data-stu-id="dbb2e-137">–or–</span></span>  
  
```csharp  
int myInt = 0;  
```  
  
 <span data-ttu-id="dbb2e-138">Kullanarak [yeni](../../../csharp/language-reference/keywords/new.md) işleci belirli türdeki varsayılan oluşturucuyu çağırır ve varsayılan değer değişkenine atar.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-138">Using the [new](../../../csharp/language-reference/keywords/new.md) operator calls the default constructor of the specific type and assigns the default value to the variable.</span></span> <span data-ttu-id="dbb2e-139">Önceki örnekte, varsayılan oluşturucu değer atanmış `0` için `myInt`.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-139">In the preceding example, the default constructor assigned the value `0` to `myInt`.</span></span> <span data-ttu-id="dbb2e-140">Varsayılan Oluşturucu çağırarak atanan değerler hakkında daha fazla bilgi için bkz: [varsayılan değerler tablosu](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="dbb2e-140">For more information about values assigned by calling default constructors, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
 <span data-ttu-id="dbb2e-141">Kullanıcı tanımlı türler ile kullanın [yeni](../../../csharp/language-reference/keywords/new.md) varsayılan oluşturucuyu çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-141">With user-defined types, use [new](../../../csharp/language-reference/keywords/new.md) to invoke the default constructor.</span></span> <span data-ttu-id="dbb2e-142">Örneğin, aşağıdaki deyim olan varsayılan oluşturucusunu çağırır `Point` yapısı:</span><span class="sxs-lookup"><span data-stu-id="dbb2e-142">For example, the following statement invokes the default constructor of the `Point` struct:</span></span>  
  
```csharp  
Point p = new Point(); // Invoke default constructor for the struct.  
```  
  
 <span data-ttu-id="dbb2e-143">Bu çağrıdan sonra kesinlikle atanacak yapı olarak kabul edilir; diğer bir deyişle, tüm üyeleri varsayılan değerlerine başlatılır.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-143">After this call, the struct is considered to be definitely assigned; that is, all its members are initialized to their default values.</span></span>  
  
 <span data-ttu-id="dbb2e-144">New işleci hakkında daha fazla bilgi için bkz: [yeni](../../../csharp/language-reference/keywords/new.md).</span><span class="sxs-lookup"><span data-stu-id="dbb2e-144">For more information about the new operator, see [new](../../../csharp/language-reference/keywords/new.md).</span></span>  
  
 <span data-ttu-id="dbb2e-145">Sayısal türlerin çıktı biçimlendirme hakkında daha fazla bilgi için bkz: [sayısal sonuçlar tablosunu biçimlendirme](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).</span><span class="sxs-lookup"><span data-stu-id="dbb2e-145">For information about formatting the output of numeric types, see [Formatting Numeric Results Table](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbb2e-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dbb2e-146">See Also</span></span>

- [<span data-ttu-id="dbb2e-147">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="dbb2e-147">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="dbb2e-148">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dbb2e-148">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="dbb2e-149">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="dbb2e-149">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="dbb2e-150">Türler</span><span class="sxs-lookup"><span data-stu-id="dbb2e-150">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="dbb2e-151">Türler için Başvuru Tabloları</span><span class="sxs-lookup"><span data-stu-id="dbb2e-151">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
- [<span data-ttu-id="dbb2e-152">Başvuru Türleri</span><span class="sxs-lookup"><span data-stu-id="dbb2e-152">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
- [<span data-ttu-id="dbb2e-153">Boş değer atanabilir türler</span><span class="sxs-lookup"><span data-stu-id="dbb2e-153">Nullable types</span></span>](../../programming-guide/nullable-types/index.md)  
