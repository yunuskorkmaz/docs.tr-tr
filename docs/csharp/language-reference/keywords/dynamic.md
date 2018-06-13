---
title: dynamic (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- dynamic_CSharpKeyword
helpviewer_keywords:
- dynamic [C#]
- dynamic keyword [C#]
ms.assetid: 9e797102-cc83-4964-bf58-afe4f54d16bc
ms.openlocfilehash: 59957ce6b2a26c1d24dc1178630eef8551db3340
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217145"
---
# <a name="dynamic-c-reference"></a><span data-ttu-id="fd424-102">dynamic (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fd424-102">dynamic (C# Reference)</span></span>
<span data-ttu-id="fd424-103">`dynamic` Türü içinde gerçekleşir derleme zamanı tür denetimi atlayacak işlemleri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="fd424-103">The `dynamic` type enables the operations in which it occurs to bypass compile-time type checking.</span></span> <span data-ttu-id="fd424-104">Bunun yerine, bu işlemlerin çalışma zamanında çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="fd424-104">Instead, these operations are resolved at run time.</span></span> <span data-ttu-id="fd424-105">`dynamic` Türü Office Automation API'leri gibi COM API'leri ve ayrıca IronPython kitaplıklarına gibi dinamik API'lere ve erişim HTML belge nesne modeli (DOM) basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="fd424-105">The `dynamic` type simplifies access to COM APIs such as the Office Automation APIs, and also to dynamic APIs such as IronPython libraries, and to the HTML Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="fd424-106">Tür `dynamic` türü gibi davranır `object` çoğu durumda.</span><span class="sxs-lookup"><span data-stu-id="fd424-106">Type `dynamic` behaves like type `object` in most circumstances.</span></span> <span data-ttu-id="fd424-107">Ancak, türünde ifadeler içeren operations `dynamic` değil çözülen veya derleyici tarafından teslim türü.</span><span class="sxs-lookup"><span data-stu-id="fd424-107">However, operations that contain expressions of type `dynamic` are not resolved or type checked by the compiler.</span></span> <span data-ttu-id="fd424-108">Çalışma zamanı derleyici paketleri işlemi birlikte bilgilerini ve bu bilgileri daha sonra işlemi tekrar değerlendirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fd424-108">The compiler packages together information about the operation, and that information is later used to evaluate the operation at run time.</span></span> <span data-ttu-id="fd424-109">Türündeki değişkenler işleminin bir parçası olarak `dynamic` türündeki değişkenler derlenmiş `object`.</span><span class="sxs-lookup"><span data-stu-id="fd424-109">As part of the process, variables of type `dynamic` are compiled into variables of type `object`.</span></span> <span data-ttu-id="fd424-110">Bu nedenle, yazın `dynamic` yalnızca derleme zamanında değil çalışma zamanında bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fd424-110">Therefore, type `dynamic` exists only at compile time, not at run time.</span></span>  
  
 <span data-ttu-id="fd424-111">Aşağıdaki örnek türünde bir değişken karşılaştırır `dynamic` türünde bir değişken için `object`.</span><span class="sxs-lookup"><span data-stu-id="fd424-111">The following example contrasts a variable of type `dynamic` to a variable of type `object`.</span></span> <span data-ttu-id="fd424-112">Derleme zamanında her bir değişken türünü doğrulamak için üzerine fare işaretçisini getirin `dyn` veya `obj` içinde `WriteLine` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="fd424-112">To verify the type of each variable at compile time, place the mouse pointer over `dyn` or `obj` in the `WriteLine` statements.</span></span> <span data-ttu-id="fd424-113">IntelliSense gösterir **dinamik** için `dyn` ve **nesne** için `obj`.</span><span class="sxs-lookup"><span data-stu-id="fd424-113">IntelliSense shows **dynamic** for `dyn` and **object** for `obj`.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_1.cs)]  
  
 <span data-ttu-id="fd424-114">`WriteLine` Deyimlerini görüntülemek çalışma zamanı tür `dyn` ve `obj`.</span><span class="sxs-lookup"><span data-stu-id="fd424-114">The `WriteLine` statements display the run-time types of `dyn` and `obj`.</span></span> <span data-ttu-id="fd424-115">Bu noktada, her ikisi de aynı türe sahip tamsayı.</span><span class="sxs-lookup"><span data-stu-id="fd424-115">At that point, both have the same type, integer.</span></span> <span data-ttu-id="fd424-116">Şu çıktı üretilir:</span><span class="sxs-lookup"><span data-stu-id="fd424-116">The following output is produced:</span></span>  
  
 `System.Int32`  
  
 `System.Int32`  
  
 <span data-ttu-id="fd424-117">Arasındaki farkı görmek için `dyn` ve `obj` derleme zamanında bildirimler arasında aşağıdaki iki satırı ekleyin ve `WriteLine` deyimleri önceki örnekte.</span><span class="sxs-lookup"><span data-stu-id="fd424-117">To see the difference between `dyn` and `obj` at compile time, add the following two lines between the declarations and the `WriteLine` statements in the previous example.</span></span>  
  
```csharp  
dyn = dyn + 3;  
obj = obj + 3;  
```  
  
 <span data-ttu-id="fd424-118">Derleyici Hatası bir tamsayı ve bir nesne ifadesinde denenen eklenmesi için bildirilen `obj + 3`.</span><span class="sxs-lookup"><span data-stu-id="fd424-118">A compiler error is reported for the attempted addition of an integer and an object in expression `obj + 3`.</span></span> <span data-ttu-id="fd424-119">Ancak, herhangi bir hata için bildirilen `dyn + 3`.</span><span class="sxs-lookup"><span data-stu-id="fd424-119">However, no error is reported for `dyn + 3`.</span></span> <span data-ttu-id="fd424-120">İçeren ifade `dyn` derleme zamanında çünkü işaretlenmediği türünü `dyn` olan `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="fd424-120">The expression that contains `dyn` is not checked at compile time because the type of `dyn` is `dynamic`.</span></span>  
  
## <a name="context"></a><span data-ttu-id="fd424-121">Bağlam</span><span class="sxs-lookup"><span data-stu-id="fd424-121">Context</span></span>  
 <span data-ttu-id="fd424-122">`dynamic` Anahtar sözcüğü, doğrudan veya bir bileşen aşağıdaki durumlarda yapılandırılmış bir tür olarak görünebilir:</span><span class="sxs-lookup"><span data-stu-id="fd424-122">The `dynamic` keyword can appear directly or as a component of a constructed type in the following situations:</span></span>  
  
-   <span data-ttu-id="fd424-123">Bir özellik, alan, dizin oluşturucu, parametre türü olarak bildirimlerden dönüş değeri, yerel değişken veya kısıtlama yazın.</span><span class="sxs-lookup"><span data-stu-id="fd424-123">In declarations, as the type of a property, field, indexer, parameter, return value, local variable, or type constraint.</span></span> <span data-ttu-id="fd424-124">Aşağıdaki sınıf tanımı kullanır `dynamic` birkaç farklı bildirimlerden.</span><span class="sxs-lookup"><span data-stu-id="fd424-124">The following class definition uses `dynamic` in several different declarations.</span></span>  
  
     [!code-csharp[csrefKeywordsTypes#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_2.cs)]  
  
-   <span data-ttu-id="fd424-125">Açık tür dönüşümleri içinde bir dönüştürme hedef türü.</span><span class="sxs-lookup"><span data-stu-id="fd424-125">In explicit type conversions, as the target type of a conversion.</span></span>  
  
     [!code-csharp[csrefKeywordsTypes#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_3.cs)]  
  
-   <span data-ttu-id="fd424-126">Burada türleri hizmet değerler olarak gibi sağ tarafında bağlamında bir `is` işleci veya bir `as` işleci veya bağımsız değişken olarak `typeof` oluşturulan türü bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="fd424-126">In any context where types serve as values, such as on the right side of an `is` operator or an `as` operator, or as the argument to `typeof` as part of a constructed type.</span></span> <span data-ttu-id="fd424-127">Örneğin, `dynamic` aşağıdaki ifadelerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fd424-127">For example, `dynamic` can be used in the following expressions.</span></span>  
  
     [!code-csharp[csrefKeywordsTypes#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="fd424-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd424-128">Example</span></span>  
 <span data-ttu-id="fd424-129">Aşağıdaki örnek kullanır `dynamic` birkaç bildirimlerden.</span><span class="sxs-lookup"><span data-stu-id="fd424-129">The following example uses `dynamic` in several declarations.</span></span> <span data-ttu-id="fd424-130">`Main` Yöntemi de derleme zamanı tür denetimi çalışma zamanı tür denetimi ile karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="fd424-130">The `Main` method also contrasts compile-time type checking with run-time type checking.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#25](../../../csharp/language-reference/keywords/codesnippet/CSharp/dynamic_5.cs)]  
  
 <span data-ttu-id="fd424-131">Daha fazla bilgi ve örnekler için bkz: [türünü kullanarak dinamik](../../../csharp/programming-guide/types/using-type-dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="fd424-131">For more information and examples, see [Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd424-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd424-132">See Also</span></span>  
 <xref:System.Dynamic.ExpandoObject?displayProperty=nameWithType>  
 <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>  
 [<span data-ttu-id="fd424-133">Tür dinamiği kullanma</span><span class="sxs-lookup"><span data-stu-id="fd424-133">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [<span data-ttu-id="fd424-134">object</span><span class="sxs-lookup"><span data-stu-id="fd424-134">object</span></span>](../../../csharp/language-reference/keywords/object.md)  
 [<span data-ttu-id="fd424-135">is</span><span class="sxs-lookup"><span data-stu-id="fd424-135">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="fd424-136">as</span><span class="sxs-lookup"><span data-stu-id="fd424-136">as</span></span>](../../../csharp/language-reference/keywords/as.md)  
 [<span data-ttu-id="fd424-137">typeof</span><span class="sxs-lookup"><span data-stu-id="fd424-137">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
 [<span data-ttu-id="fd424-138">Nasıl yapılır: as ve is İşleçlerini Kullanarak Güvenli Bir Şekilde Atama</span><span class="sxs-lookup"><span data-stu-id="fd424-138">How to: Safely Cast by Using as and is Operators</span></span>](../../../csharp/programming-guide/types/how-to-safely-cast-by-using-as-and-is-operators.md)  
 [<span data-ttu-id="fd424-139">İzlenecek yol: Oluşturma ve dinamik nesneler kullanma</span><span class="sxs-lookup"><span data-stu-id="fd424-139">Walkthrough: Creating and Using Dynamic Objects</span></span>](../../../csharp/programming-guide/types/walkthrough-creating-and-using-dynamic-objects.md)
