---
title: Yapılar- C# kılavuz
description: Yapı türü ve bunları nasıl oluşturacağınız hakkında bilgi edinin
ms.date: 10/12/2016
ms.technology: csharp-fundamentals
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 39bf44dc187fbbc7aac71a1d5c5f3a4d7f446eb8
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739182"
---
# <a name="structs"></a><span data-ttu-id="bb5b5-103">Yapılar</span><span class="sxs-lookup"><span data-stu-id="bb5b5-103">Structs</span></span>

<span data-ttu-id="bb5b5-104">*Struct* bir değer türüdür.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-104">A *struct* is a value type.</span></span> <span data-ttu-id="bb5b5-105">Bir struct oluşturulduğunda, yapının atandığı değişken yapının gerçek verilerini barındırır.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-105">When a struct is created, the variable to which the struct is assigned holds the struct's actual data.</span></span> <span data-ttu-id="bb5b5-106">Yapı yeni bir değişkene atandığında, kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-106">When the struct is assigned to a new variable, it is copied.</span></span> <span data-ttu-id="bb5b5-107">Bu nedenle, yeni değişken ve özgün değişken aynı verilerin iki ayrı kopyasını içerir.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-107">The new variable and the original variable therefore contain two separate copies of the same data.</span></span> <span data-ttu-id="bb5b5-108">Bir kopyada yapılan değişiklikler diğer kopyayı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-108">Changes made to one copy do not affect the other copy.</span></span>

<span data-ttu-id="bb5b5-109">Değer türü değişkenleri doğrudan değerlerini içerir, bu da belleğin, değişkenin bildirildiği bağlamda satır içi olarak ayrıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-109">Value type variables directly contain their values, which means that the memory is allocated inline in whatever context the variable is declared.</span></span> <span data-ttu-id="bb5b5-110">Değer türü değişkenler için ayrı bir yığın ayırma veya çöp toplama ek yükü yoktur.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-110">There is no separate heap allocation or garbage collection overhead for value-type variables.</span></span>  
  
<span data-ttu-id="bb5b5-111">Değer türlerinin iki kategorisi vardır: [struct](./language-reference/keywords/struct.md) ve [enum](./language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="bb5b5-111">There are two categories of value types: [struct](./language-reference/keywords/struct.md) and [enum](./language-reference/keywords/enum.md).</span></span>  
  
<span data-ttu-id="bb5b5-112">Yerleşik sayısal türler yapı birimleridir ve erişebileceğiniz özelliklere ve yöntemlere sahiptirler:</span><span class="sxs-lookup"><span data-stu-id="bb5b5-112">The built-in numeric types are structs, and they have properties and methods that you can access:</span></span>  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
<span data-ttu-id="bb5b5-113">Ancak bunları, basit olmayan türler gibi bu değerlere bildirir ve bunlara atanır:</span><span class="sxs-lookup"><span data-stu-id="bb5b5-113">But you declare and assign values to them as if they were simple non-aggregate types:</span></span>  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
<span data-ttu-id="bb5b5-114">Değer türleri *korumalıdır*, yani örneğin, bir türü <xref:System.Int32>türetemezsiniz ve Kullanıcı tanımlı herhangi bir sınıftan veya yapıdan devralacak bir struct tanımlayamazsınız, çünkü bir struct yalnızca <xref:System.ValueType>devralabilir.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-114">Value types are *sealed*, which means, for example, that you cannot derive a type from <xref:System.Int32>, and you cannot define a struct to inherit from any user-defined class or struct because a struct can only inherit from <xref:System.ValueType>.</span></span> <span data-ttu-id="bb5b5-115">Ancak, bir struct bir veya daha fazla arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-115">However, a struct can implement one or more interfaces.</span></span> <span data-ttu-id="bb5b5-116">Bir yapı türünü arabirim türüne çevirebilirsiniz; Bu, bir *kutulama* işleminin yapıyı yönetilen yığında bir başvuru türü nesnesinin içine sarmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-116">You can cast a struct type to an interface type; this causes a *boxing* operation to wrap the struct inside a reference type object on the managed heap.</span></span> <span data-ttu-id="bb5b5-117">Paketleme işlemleri, bir <xref:System.Object> giriş parametresi olarak alan bir yönteme bir değer türü geçirdiğinizde oluşur.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-117">Boxing operations occur when you pass a value type to a method that takes an <xref:System.Object> as an input parameter.</span></span> <span data-ttu-id="bb5b5-118">Daha fazla bilgi için bkz. [kutulama ve kutudan](./programming-guide/types/boxing-and-unboxing.md )çıkarma.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-118">For more information, see [Boxing and Unboxing](./programming-guide/types/boxing-and-unboxing.md ).</span></span>  
  
<span data-ttu-id="bb5b5-119">Kendi özel değer türlerinizi oluşturmak için [struct](./language-reference/keywords/struct.md) anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-119">You use the [struct](./language-reference/keywords/struct.md) keyword to create your own custom value types.</span></span> <span data-ttu-id="bb5b5-120">Genellikle, bir yapı aşağıdaki örnekte gösterildiği gibi küçük bir ilgili değişkenler kümesi için kapsayıcı olarak kullanılır:</span><span class="sxs-lookup"><span data-stu-id="bb5b5-120">Typically, a struct is used as a container for a small set of related variables, as shown in the following example:</span></span>  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
<span data-ttu-id="bb5b5-121">.NET Framework değer türleri hakkında daha fazla bilgi için bkz. [ortak tür sistemi](../standard/common-type-system.md).</span><span class="sxs-lookup"><span data-stu-id="bb5b5-121">For more information about value types in the .NET Framework, see [Common Type System](../standard/common-type-system.md).</span></span>  
    
<span data-ttu-id="bb5b5-122">Yapılar sınıflarla aynı sözdiziminin çoğunu paylaşır, ancak yapılar sınıflardan daha sınırlıdır:</span><span class="sxs-lookup"><span data-stu-id="bb5b5-122">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
- <span data-ttu-id="bb5b5-123">Bir struct bildiriminde, `const` veya `static`olarak belirtilemediği sürece alanlar başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-123">Within a struct declaration, fields cannot be initialized unless they are declared as `const` or `static`.</span></span>  
  
- <span data-ttu-id="bb5b5-124">Struct parametresiz bir Oluşturucu (parametresiz bir Oluşturucu) veya sonlandırıcısı bildiremez.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-124">A struct cannot declare a parameterless constructor (a constructor without parameters) or a finalizer.</span></span>  
  
- <span data-ttu-id="bb5b5-125">Yapılar atamaya kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-125">Structs are copied on assignment.</span></span> <span data-ttu-id="bb5b5-126">Bir yapı yeni bir değişkene atandığında, tüm veriler kopyalanır ve yeni kopyada yapılan değişiklikler özgün kopyanın verilerini değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-126">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="bb5b5-127">Bu, sözlük < dize, myStruct > gibi değer türlerinin koleksiyonlarıyla çalışırken unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-127">This is important to remember when working with collections of value types such as Dictionary<string, myStruct>.</span></span>  
  
- <span data-ttu-id="bb5b5-128">Yapılar, değer türlerdir ve sınıflardır başvuru türleridir.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-128">Structs are value types and classes are reference types.</span></span>  
  
- <span data-ttu-id="bb5b5-129">Sınıfların aksine, yapılar `new` işleci kullanılmadan oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-129">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
- <span data-ttu-id="bb5b5-130">Yapılar, parametreleri olan oluşturucular bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-130">Structs can declare constructors that have parameters.</span></span>  
  
- <span data-ttu-id="bb5b5-131">Yapı, başka bir struct veya sınıftan devralınabilir ve bir sınıfın temeli olamaz.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-131">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="bb5b5-132">Tüm yapılar, <xref:System.Object>devralan <xref:System.ValueType>doğrudan devralır.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-132">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="bb5b5-133">Bir struct, arabirimler uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-133">A struct can implement interfaces.</span></span>

## <a name="nullable-value-types"></a><span data-ttu-id="bb5b5-134">Boş değer atanabilen değer türleri</span><span class="sxs-lookup"><span data-stu-id="bb5b5-134">Nullable value types</span></span>

<span data-ttu-id="bb5b5-135">Sıradan değer türlerinin değeri [null](language-reference/keywords/null.md)olamaz.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-135">Ordinary value types cannot have a value of [null](language-reference/keywords/null.md).</span></span> <span data-ttu-id="bb5b5-136">Ancak, türden sonra bir `?` ekleyerek null yapılabilir değer türleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-136">However, you can create nullable value types by affixing a `?` after the type.</span></span> <span data-ttu-id="bb5b5-137">Örneğin `int?`, [null](./language-reference/keywords/null.md)değeri de olan bir `int` türüdür.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-137">For example, `int?` is an `int` type that can also have the value [null](./language-reference/keywords/null.md).</span></span> <span data-ttu-id="bb5b5-138">Null yapılabilir değer türleri <xref:System.Nullable%601>genel yapı türü örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-138">Nullable value types are instances of the generic struct type <xref:System.Nullable%601>.</span></span> <span data-ttu-id="bb5b5-139">Null olabilen değer türleri, genellikle sayısal değerlerin null veya tanımsız olabileceği veritabanlarına veri geçirirken faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-139">Nullable value types are especially useful when you are passing data to and from databases in which numeric values might be null or undefined.</span></span> <span data-ttu-id="bb5b5-140">Daha fazla bilgi için bkz. [Nullable değer türleri](language-reference/builtin-types/nullable-value-types.md).</span><span class="sxs-lookup"><span data-stu-id="bb5b5-140">For more information, see [Nullable value types](language-reference/builtin-types/nullable-value-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bb5b5-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb5b5-141">See also</span></span>

- [<span data-ttu-id="bb5b5-142">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="bb5b5-142">Classes</span></span>](programming-guide/classes-and-structs/classes.md)
- [<span data-ttu-id="bb5b5-143">Temel Türler</span><span class="sxs-lookup"><span data-stu-id="bb5b5-143">Basic Types</span></span>](basic-types.md)
