---
title: "Boş Değer Atanabilir Türleri Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c8a42392bbcd2e53c54ff4c13bf98c048262ae4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="add34-102">Boş Değer Atanabilir Türleri Kullanma (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="add34-102">Using Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="add34-103">Boş değer atanabilir türleri bir temel alınan tür ve ek bir tüm değerleri temsil eden [null](../../../csharp/language-reference/keywords/null.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="add34-103">Nullable types can represent all the values of an underlying type, and an additional [null](../../../csharp/language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="add34-104">Boş değer atanabilir türler iki yoldan biriyle bildirilir:</span><span class="sxs-lookup"><span data-stu-id="add34-104">Nullable types are declared in one of two ways:</span></span>  
  
 `System.Nullable<T> variable`  
  
 <span data-ttu-id="add34-105">veya</span><span class="sxs-lookup"><span data-stu-id="add34-105">-or-</span></span>  
  
 `T? variable`  
  
 <span data-ttu-id="add34-106">`T`boş değer atanabilir tür temel türde değil.</span><span class="sxs-lookup"><span data-stu-id="add34-106">`T` is the underlying type of the nullable type.</span></span> <span data-ttu-id="add34-107">`T`olması dahil herhangi bir değer türü `struct`; bir başvuru türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="add34-107">`T` can be any value type including `struct`; it cannot be a reference type.</span></span>  
  
 <span data-ttu-id="add34-108">Boş değer atanabilir bir tür kullandığınızda, bir örnek için nasıl sıradan bir Boolean değişken iki değerlere sahip olabilir göz önünde bulundurun: true ve false.</span><span class="sxs-lookup"><span data-stu-id="add34-108">For an example of when you might use a nullable type, consider how an ordinary Boolean variable can have two values: true and false.</span></span> <span data-ttu-id="add34-109">"Tanımsız" belirten değer yoktur.</span><span class="sxs-lookup"><span data-stu-id="add34-109">There is no value that signifies "undefined".</span></span> <span data-ttu-id="add34-110">Birçok programlama uygulamalarda değişkenleri tanımlanmamış bir durumda oluşabilir etkileşimleri, özellikle veritabanı.</span><span class="sxs-lookup"><span data-stu-id="add34-110">In many programming applications, most notably database interactions, variables can occur in an undefined state.</span></span> <span data-ttu-id="add34-111">Örneğin, bir veritabanında bir alan true veya false değerleri içerebilir, ancak hiçbir değer hiç ayrıca içerebilir.</span><span class="sxs-lookup"><span data-stu-id="add34-111">For example, a field in a database may contain the values true or false, but it may also contain no value at all.</span></span> <span data-ttu-id="add34-112">Başvuru türleri benzer şekilde, ayarlanabilir `null` bunlar başlatılmaz belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="add34-112">Similarly, reference types can be set to `null` to indicate that they are not initialized.</span></span>  
  
 <span data-ttu-id="add34-113">Bu farklılığa fazladan programlama iş durumu bilgileri, özel değerler ve benzeri kullanımını depolamak için kullanılan ek değişkenlerle oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="add34-113">This disparity can create extra programming work, with additional variables used to store state information, the use of special values, and so on.</span></span> <span data-ttu-id="add34-114">Boş değer atanabilir tür değiştiricisi tanımlanmamış bir değere gösteren değer türü değişkenleri oluşturmak üzere C# sağlar.</span><span class="sxs-lookup"><span data-stu-id="add34-114">The nullable type modifier enables C# to create value-type variables that indicate an undefined value.</span></span>  
  
## <a name="examples-of-nullable-types"></a><span data-ttu-id="add34-115">Boş değer atanabilir türler örnekleri</span><span class="sxs-lookup"><span data-stu-id="add34-115">Examples of Nullable Types</span></span>  
 <span data-ttu-id="add34-116">Herhangi bir değer türü null olabilir bir tür için temel olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="add34-116">Any value type may be used as the basis for a nullable type.</span></span> <span data-ttu-id="add34-117">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="add34-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## <a name="the-members-of-nullable-types"></a><span data-ttu-id="add34-118">Boş değer atanabilir türler üyeleri</span><span class="sxs-lookup"><span data-stu-id="add34-118">The Members of Nullable Types</span></span>  
 <span data-ttu-id="add34-119">Boş değer atanabilir bir tür her örneğinin iki genel salt okunur özellikler vardır:</span><span class="sxs-lookup"><span data-stu-id="add34-119">Each instance of a nullable type has two public read-only properties:</span></span>  
  
-   `HasValue`  
  
     <span data-ttu-id="add34-120">`HasValue`tür `bool`.</span><span class="sxs-lookup"><span data-stu-id="add34-120">`HasValue` is of type `bool`.</span></span> <span data-ttu-id="add34-121">Ayarlanır `true` değişkeni boş olmayan bir değer içerdiğinde.</span><span class="sxs-lookup"><span data-stu-id="add34-121">It is set to `true` when the variable contains a non-null value.</span></span>  
  
-   `Value`  
  
     <span data-ttu-id="add34-122">`Value`temel alınan türü olarak aynı türde değil.</span><span class="sxs-lookup"><span data-stu-id="add34-122">`Value` is of the same type as the underlying type.</span></span> <span data-ttu-id="add34-123">Varsa `HasValue` olan `true`, `Value` anlamlı bir değer içeriyor.</span><span class="sxs-lookup"><span data-stu-id="add34-123">If `HasValue` is `true`, `Value` contains a meaningful value.</span></span> <span data-ttu-id="add34-124">Varsa `HasValue` olan `false`, erişilirken `Value` özel durum oluşturacak bir <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="add34-124">If `HasValue` is `false`, accessing `Value` will throw a <xref:System.InvalidOperationException>.</span></span>  
  
 <span data-ttu-id="add34-125">Bu örnekte, `HasValue` üye değişkeni bir değeri içerip görüntülenecek denemeden önce test etmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="add34-125">In this example, the `HasValue` member is used to test whether the variable contains a value before it tries to display it.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 <span data-ttu-id="add34-126">İçin bir değer sınama aşağıdaki örnekteki yapılabilir:</span><span class="sxs-lookup"><span data-stu-id="add34-126">Testing for a value can also be done as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## <a name="explicit-conversions"></a><span data-ttu-id="add34-127">Açık dönüşümler</span><span class="sxs-lookup"><span data-stu-id="add34-127">Explicit Conversions</span></span>  
 <span data-ttu-id="add34-128">Açıkça bir cast veya kullanarak normal bir türe boş değer atanabilir bir tür atanabilecek `Value` özelliği.</span><span class="sxs-lookup"><span data-stu-id="add34-128">A nullable type can be cast to a regular type, either explicitly with a cast, or by using the `Value` property.</span></span> <span data-ttu-id="add34-129">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="add34-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 <span data-ttu-id="add34-130">İki veri türleri arasında kullanıcı tanımlı bir dönüştürme tanımlanmışsa, bu veri türlerini boş değer atanabilir sürümleriyle aynı dönüştürme de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="add34-130">If a user-defined conversion is defined between two data types, the same conversion can also be used with the nullable versions of these data types.</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="add34-131">Örtük dönüşümler</span><span class="sxs-lookup"><span data-stu-id="add34-131">Implicit Conversions</span></span>  
 <span data-ttu-id="add34-132">Boş değer atanabilir türde bir değişken ayarlanabilir null ile `null` anahtar sözcüğü, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="add34-132">A variable of nullable type can be set to null with the `null` keyword, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 <span data-ttu-id="add34-133">Bir sıradan türünden null olabilir bir tür dönüştürme örtük.</span><span class="sxs-lookup"><span data-stu-id="add34-133">The conversion from an ordinary type to a nullable type, is implicit.</span></span>  
  
 [!code-csharp[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## <a name="operators"></a><span data-ttu-id="add34-134">İşleçler</span><span class="sxs-lookup"><span data-stu-id="add34-134">Operators</span></span>  
 <span data-ttu-id="add34-135">Ayrıca önceden tanımlanmış birli ve ikili işleç ve değer türleri için mevcut kullanıcı tanımlı işleçler boş değer atanabilir türleri tarafından kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="add34-135">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="add34-136">Bu işleçlere işlenenler null bir null değer oluşturmaz; Aksi takdirde işleci sonucu hesaplamak için kapsanan değeri kullanır.</span><span class="sxs-lookup"><span data-stu-id="add34-136">These operators produce a null value if the operands are null; otherwise, the operator uses the contained value to calculate the result.</span></span> <span data-ttu-id="add34-137">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="add34-137">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 <span data-ttu-id="add34-138">Boş değer atanabilir türler birinin değeri null ise ve diğeri değilse boş değer atanabilir türler ile karşılaştırmaları gerçekleştirdiğinizde, tüm karşılaştırmaları için değerlendirin `false` dışında `!=` (eşit değildir).</span><span class="sxs-lookup"><span data-stu-id="add34-138">When you perform comparisons with nullable types, if the value of one of the nullable types is null and the other is not, all comparisons evaluate to `false` except for `!=` (not equal).</span></span> <span data-ttu-id="add34-139">Belirli bir karşılaştırma döndürdüğünden varsayımında değil önemlidir `false`, aksi durumda döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="add34-139">It is important not to assume that because a particular comparison returns `false`, the opposite case returns `true`.</span></span> <span data-ttu-id="add34-140">Aşağıdaki örnekte, 10 değerinden daha büyük değildir ve null değerine eşit.</span><span class="sxs-lookup"><span data-stu-id="add34-140">In the following example, 10 is not greater than, less than, nor equal to null.</span></span> <span data-ttu-id="add34-141">Yalnızca `num1 != num2` değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="add34-141">Only `num1 != num2` evaluates to `true`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 <span data-ttu-id="add34-142">Her ikisi de null iki boş değer atanabilir türler bir eşitlik karşılaştırması değerlendiren `true`.</span><span class="sxs-lookup"><span data-stu-id="add34-142">An equality comparison of two nullable types that are both null evaluates to `true`.</span></span>  
  
## <a name="the--operator"></a><span data-ttu-id="add34-143">??</span><span class="sxs-lookup"><span data-stu-id="add34-143">The ??</span></span> <span data-ttu-id="add34-144">İşleç</span><span class="sxs-lookup"><span data-stu-id="add34-144">Operator</span></span>  
 <span data-ttu-id="add34-145">`??` İşleci, null atanabilir bir tür null türüne atandığında, döndürülen varsayılan bir değer tanımlar.</span><span class="sxs-lookup"><span data-stu-id="add34-145">The `??` operator defines a default value that is returned when a nullable type is assigned to a non-nullable type.</span></span>  
  
 [!code-csharp[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 <span data-ttu-id="add34-146">Bu işleç birden çok boş değer atanabilir türler ile de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="add34-146">This operator can also be used with multiple nullable types.</span></span> <span data-ttu-id="add34-147">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="add34-147">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## <a name="the-bool-type"></a><span data-ttu-id="add34-148">Bool? türü</span><span class="sxs-lookup"><span data-stu-id="add34-148">The bool? type</span></span>  
 <span data-ttu-id="add34-149">`bool?` Boş değer atanabilir tür üç farklı değerler içerebilir: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) ve [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="add34-149">The `bool?` nullable type can contain three different values: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) and [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="add34-150">Bool atama hakkında daha fazla bilgi için? bool için bkz: [nasıl yapılır: güvenli bir şekilde bool dönüştürme? değerinden bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span><span class="sxs-lookup"><span data-stu-id="add34-150">For information about how to cast from a bool? to a bool, see [How to: Safely Cast from bool? to bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span></span>  
  
 <span data-ttu-id="add34-151">Boş değer atanabilir Boole değerlerini SQL'de kullanılan Boole değişken türü gibidir.</span><span class="sxs-lookup"><span data-stu-id="add34-151">Nullable Booleans are like the Boolean variable type that is used in SQL.</span></span> <span data-ttu-id="add34-152">Tarafından üretilen sonuçları emin olmak için `&` ve `|` işleçleri üç değerli Boole türü ile tutarlı SQL'de aşağıdaki önceden tanımlanmış işleçleri sağlanır:</span><span class="sxs-lookup"><span data-stu-id="add34-152">To ensure that the results produced by the `&` and `|` operators are consistent with the three-valued Boolean type in SQL, the following predefined operators are provided:</span></span>  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
 <span data-ttu-id="add34-153">Bu işleçlere sonuçları aşağıdaki tabloda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="add34-153">The results of these operators are listed in the following table:</span></span>  
  
|<span data-ttu-id="add34-154">X</span><span class="sxs-lookup"><span data-stu-id="add34-154">X</span></span>|<span data-ttu-id="add34-155">y</span><span class="sxs-lookup"><span data-stu-id="add34-155">y</span></span>|<span data-ttu-id="add34-156">x ve y</span><span class="sxs-lookup"><span data-stu-id="add34-156">x&y</span></span>|<span data-ttu-id="add34-157">x &#124; y</span><span class="sxs-lookup"><span data-stu-id="add34-157">x&#124;y</span></span>|  
|-------|-------|---------|--------------|  
|<span data-ttu-id="add34-158">true</span><span class="sxs-lookup"><span data-stu-id="add34-158">true</span></span>|<span data-ttu-id="add34-159">true</span><span class="sxs-lookup"><span data-stu-id="add34-159">true</span></span>|<span data-ttu-id="add34-160">true</span><span class="sxs-lookup"><span data-stu-id="add34-160">true</span></span>|<span data-ttu-id="add34-161">true</span><span class="sxs-lookup"><span data-stu-id="add34-161">true</span></span>|  
|<span data-ttu-id="add34-162">true</span><span class="sxs-lookup"><span data-stu-id="add34-162">true</span></span>|<span data-ttu-id="add34-163">false</span><span class="sxs-lookup"><span data-stu-id="add34-163">false</span></span>|<span data-ttu-id="add34-164">false</span><span class="sxs-lookup"><span data-stu-id="add34-164">false</span></span>|<span data-ttu-id="add34-165">true</span><span class="sxs-lookup"><span data-stu-id="add34-165">true</span></span>|  
|<span data-ttu-id="add34-166">true</span><span class="sxs-lookup"><span data-stu-id="add34-166">true</span></span>|<span data-ttu-id="add34-167">null</span><span class="sxs-lookup"><span data-stu-id="add34-167">null</span></span>|<span data-ttu-id="add34-168">null</span><span class="sxs-lookup"><span data-stu-id="add34-168">null</span></span>|<span data-ttu-id="add34-169">true</span><span class="sxs-lookup"><span data-stu-id="add34-169">true</span></span>|  
|<span data-ttu-id="add34-170">false</span><span class="sxs-lookup"><span data-stu-id="add34-170">false</span></span>|<span data-ttu-id="add34-171">true</span><span class="sxs-lookup"><span data-stu-id="add34-171">true</span></span>|<span data-ttu-id="add34-172">false</span><span class="sxs-lookup"><span data-stu-id="add34-172">false</span></span>|<span data-ttu-id="add34-173">true</span><span class="sxs-lookup"><span data-stu-id="add34-173">true</span></span>|  
|<span data-ttu-id="add34-174">false</span><span class="sxs-lookup"><span data-stu-id="add34-174">false</span></span>|<span data-ttu-id="add34-175">false</span><span class="sxs-lookup"><span data-stu-id="add34-175">false</span></span>|<span data-ttu-id="add34-176">false</span><span class="sxs-lookup"><span data-stu-id="add34-176">false</span></span>|<span data-ttu-id="add34-177">false</span><span class="sxs-lookup"><span data-stu-id="add34-177">false</span></span>|  
|<span data-ttu-id="add34-178">false</span><span class="sxs-lookup"><span data-stu-id="add34-178">false</span></span>|<span data-ttu-id="add34-179">null</span><span class="sxs-lookup"><span data-stu-id="add34-179">null</span></span>|<span data-ttu-id="add34-180">false</span><span class="sxs-lookup"><span data-stu-id="add34-180">false</span></span>|<span data-ttu-id="add34-181">null</span><span class="sxs-lookup"><span data-stu-id="add34-181">null</span></span>|  
|<span data-ttu-id="add34-182">null</span><span class="sxs-lookup"><span data-stu-id="add34-182">null</span></span>|<span data-ttu-id="add34-183">true</span><span class="sxs-lookup"><span data-stu-id="add34-183">true</span></span>|<span data-ttu-id="add34-184">null</span><span class="sxs-lookup"><span data-stu-id="add34-184">null</span></span>|<span data-ttu-id="add34-185">true</span><span class="sxs-lookup"><span data-stu-id="add34-185">true</span></span>|  
|<span data-ttu-id="add34-186">null</span><span class="sxs-lookup"><span data-stu-id="add34-186">null</span></span>|<span data-ttu-id="add34-187">false</span><span class="sxs-lookup"><span data-stu-id="add34-187">false</span></span>|<span data-ttu-id="add34-188">false</span><span class="sxs-lookup"><span data-stu-id="add34-188">false</span></span>|<span data-ttu-id="add34-189">null</span><span class="sxs-lookup"><span data-stu-id="add34-189">null</span></span>|  
|<span data-ttu-id="add34-190">null</span><span class="sxs-lookup"><span data-stu-id="add34-190">null</span></span>|<span data-ttu-id="add34-191">null</span><span class="sxs-lookup"><span data-stu-id="add34-191">null</span></span>|<span data-ttu-id="add34-192">null</span><span class="sxs-lookup"><span data-stu-id="add34-192">null</span></span>|<span data-ttu-id="add34-193">null</span><span class="sxs-lookup"><span data-stu-id="add34-193">null</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="add34-194">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="add34-194">See Also</span></span>  
 [<span data-ttu-id="add34-195">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="add34-195">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="add34-196">Boş değer atanabilir türler</span><span class="sxs-lookup"><span data-stu-id="add34-196">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="add34-197">Boş değer atanabilir türleri kutulama</span><span class="sxs-lookup"><span data-stu-id="add34-197">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
 [<span data-ttu-id="add34-198">Boş değer atanabilen değer türleri</span><span class="sxs-lookup"><span data-stu-id="add34-198">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
