---
title: Atama ve tür dönüştürmeleri - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- type conversion [C#]
- data type conversion [C#]
- numeric conversions [C#]
- conversions [C#], type
- casting [C#]
- converting types [C#]
ms.assetid: 568df58a-d292-4b55-93ba-601578722878
ms.openlocfilehash: 2aee15443172e753846574806565f7804f1716d1
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423685"
---
# <a name="casting-and-type-conversions-c-programming-guide"></a><span data-ttu-id="c0dfa-102">Atama ve tür dönüştürmeleri (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c0dfa-102">Casting and type conversions (C# Programming Guide)</span></span>

<span data-ttu-id="c0dfa-103">Bir değişken bildirildikten sonra C# türü statik belirlenmiştir derleme zamanında olduğundan, yeniden bildirilen veya bu tür değişkenin türüne örtük olarak dönüştürülebilir olmadığı sürece başka bir türde bir değer atanır.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-103">Because C# is statically-typed at compile time, after a variable is declared, it cannot be declared again or assigned a value of another type unless that type is implicitly convertible to the variable's type.</span></span> <span data-ttu-id="c0dfa-104">Örneğin, `string` için örtük olarak dönüştürülemez `int`.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-104">For example, the `string` cannot be implicitly converted to `int`.</span></span> <span data-ttu-id="c0dfa-105">Bu nedenle, sonra bildirdiğiniz `i` olarak bir `int`, ", aşağıdaki kodun gösterdiği gibi Hello" dizesi atanamaz:</span><span class="sxs-lookup"><span data-stu-id="c0dfa-105">Therefore, after you declare `i` as an `int`, you cannot assign the string "Hello" to it, as the following code shows:</span></span>
  
```csharp  
int i;  
i = "Hello"; // error CS0029: Cannot implicitly convert type 'string' to 'int'
```  
  
 <span data-ttu-id="c0dfa-106">Ancak, bazen bir değişken veya yöntem türünden parametreye başka bir değeri kopyalama gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-106">However, you might sometimes need to copy a value into a variable or method parameter of another type.</span></span> <span data-ttu-id="c0dfa-107">Örneğin, bir yöntem parametresi olarak yazıldığında geçirmek için gereken tamsayı değişkenini olabilir `double`.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-107">For example, you might have an integer variable that you need to pass to a method whose parameter is typed as `double`.</span></span> <span data-ttu-id="c0dfa-108">Veya bir sınıf değişkeni bir arabirim türü bir değişkene atayın gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-108">Or you might need to assign a class variable to a variable of an interface type.</span></span> <span data-ttu-id="c0dfa-109">Bu tür işlemler adlı *tür dönüştürmeleri*.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-109">These kinds of operations are called *type conversions*.</span></span> <span data-ttu-id="c0dfa-110">C# ' ta, aşağıdaki tür dönüştürmeleri gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="c0dfa-110">In C#, you can perform the following kinds of conversions:</span></span>  
  
- <span data-ttu-id="c0dfa-111">**Örtük dönüştürmeleri**: Hiçbir özel sözdizimi, dönüştürme tür bakımından güvenli olduğundan ve hiçbir veri kaybı olmayacağını gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-111">**Implicit conversions**: No special syntax is required because the conversion is type safe and no data will be lost.</span></span> <span data-ttu-id="c0dfa-112">Daha küçük Dönüştürmelere daha büyük bir tam sayı türleri için ve temel sınıf için türetilmiş sınıflardan dönüştürmeler verilebilir.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-112">Examples include conversions from smaller to larger integral types, and conversions from derived classes to base classes.</span></span>  
  
- <span data-ttu-id="c0dfa-113">**Açık dönüştürmeler (yayınları)** : Açık dönüştürmeler bir atama işleci gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-113">**Explicit conversions (casts)**: Explicit conversions require a cast operator.</span></span> <span data-ttu-id="c0dfa-114">Atama, bilgi dönüştürme sırasında kaybedilen veya diğer nedenlerle dönüştürme başarılı olmayabilir gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-114">Casting is required when information might be lost in the conversion, or when the conversion might not succeed for other reasons.</span></span>  <span data-ttu-id="c0dfa-115">Daha az duyarlılık ya da daha küçük bir aralığı olan bir türü sayısal dönüştürme ve türetilmiş bir sınıf bir taban sınıfı örneğini dönüştürme Bunun tipik örneklerindendir.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-115">Typical examples include numeric conversion to a type that has less precision or a smaller range, and conversion of a base-class instance to a derived class.</span></span>  
  
- <span data-ttu-id="c0dfa-116">**Kullanıcı tanımlı dönüşümler**: Bir türetilmiş sınıf – temel sınıf ilişkisi olmayan özel türler arasında açık ve örtük dönüştürme etkinleştirmek için tanımlayabileceğiniz özel yöntemler kullanıcı tanımlı dönüştürmeler gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-116">**User-defined conversions**: User-defined conversions are performed by special methods that you can define to enable explicit and implicit conversions between custom types that do not have a base class–derived class relationship.</span></span> <span data-ttu-id="c0dfa-117">Daha fazla bilgi için [dönüştürme işleçleri](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="c0dfa-117">For more information, see [Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md).</span></span>  
  
- <span data-ttu-id="c0dfa-118">**Yardımcı sınıfları dönüştürmeler**: Tam sayılar gibi uyumlu olmayan türleri arasında dönüştürme yapma ve <xref:System.DateTime?displayProperty=nameWithType> nesneleri veya onaltılık dizeler ve bayt dizileri kullanabilirsiniz <xref:System.BitConverter?displayProperty=nameWithType> sınıfı <xref:System.Convert?displayProperty=nameWithType> sınıfı ve `Parse` gibi yerleşik sayısal yöntemlerinin türleri <xref:System.Int32.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-118">**Conversions with helper classes**: To convert between non-compatible types, such as integers and <xref:System.DateTime?displayProperty=nameWithType> objects, or hexadecimal strings and byte arrays, you can use the <xref:System.BitConverter?displayProperty=nameWithType> class, the <xref:System.Convert?displayProperty=nameWithType> class, and the `Parse` methods of the built-in numeric types, such as <xref:System.Int32.Parse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c0dfa-119">Daha fazla bilgi için [nasıl yapılır: Byte dizisini int'e dönüştürme](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [nasıl yapılır: Bir dizeyi sayıya dönüştürme](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), ve [nasıl yapılır: Onaltılık dizeler ve sayısal türler arasında dönüştürme](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="c0dfa-119">For more information, see [How to: Convert a byte Array to an int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md), [How to: Convert a String to a Number](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md), and [How to: Convert Between Hexadecimal Strings and Numeric Types](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md).</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="c0dfa-120">Örtük dönüşümler</span><span class="sxs-lookup"><span data-stu-id="c0dfa-120">Implicit conversions</span></span>

 <span data-ttu-id="c0dfa-121">Depolanacak değer kısaltılır veya yuvarlanır olmadan değişkene uygun olduğunda yerleşik sayısal türler için örtük bir dönüştürme yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-121">For built-in numeric types, an implicit conversion can be made when the value to be stored can fit into the variable without being truncated or rounded off.</span></span> <span data-ttu-id="c0dfa-122">Tam sayı türleri için bu aralığın hedef türü için uygun bir alt kümesi kaynak türü aralığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-122">For integral types, this means the range of the source type is a proper subset of the range for the target type.</span></span> <span data-ttu-id="c0dfa-123">Örneğin, bir değişken türü [uzun](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) (64-bit tamsayı) depolayabileceğiniz değerine herhangi bir [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) (32-bit tamsayı) depolayabilir.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-123">For example, a variable of type [long](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) (64-bit integer) can store any value that an [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) (32-bit integer) can store.</span></span> <span data-ttu-id="c0dfa-124">Aşağıdaki örnekte, derleyici değeri örtük olarak dönüştürür `num` türüne sağ taraftaki `long` giderek önce `bigNum`.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-124">In the following example, the compiler implicitly converts the value of `num` on the right to a type `long` before assigning it to `bigNum`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#34)]  
  
 <span data-ttu-id="c0dfa-125">Tüm örtük sayısal dönüşümler tam bir listesi için bkz. [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="c0dfa-125">For a complete list of all implicit numeric conversions, see [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="c0dfa-126">Başvuru türleri için örtük bir dönüştürme her zaman bir sınıftan herhangi biri, doğrudan veya dolaylı temel sınıfların veya arabirimleri bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-126">For reference types, an implicit conversion always exists from a class to any one of its direct or indirect base classes or interfaces.</span></span> <span data-ttu-id="c0dfa-127">Hiçbir özel sözdizimi, türetilmiş bir sınıf her zaman temel sınıfın tüm üyeleri içerdiği için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-127">No special syntax is necessary because a derived class always contains all the members of a base class.</span></span>  
  
```  
Derived d = new Derived();  
Base b = d; // Always OK.  
```  
  
## <a name="explicit-conversions"></a><span data-ttu-id="c0dfa-128">Açık dönüştürmeler</span><span class="sxs-lookup"><span data-stu-id="c0dfa-128">Explicit conversions</span></span>

 <span data-ttu-id="c0dfa-129">Dönüştürme bilgileri kaybetme riski yapılamazsa, ancak derleyici çağrılır açık bir dönüştürme gerçekleştirmek gerektirir bir *atama*.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-129">However, if a conversion cannot be made without a risk of losing information, the compiler requires that you perform an explicit conversion, which is called a *cast*.</span></span> <span data-ttu-id="c0dfa-130">Bir yayın derleyici, dönüştürme yapmak istediğiniz ve veri kaybı oluşabilir haberdar olduğunuzu açıkça bildiren bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-130">A cast is a way of explicitly informing the compiler that you intend to make the conversion and that you are aware that data loss might occur.</span></span> <span data-ttu-id="c0dfa-131">Bir dönüştürme gerçekleştirmek için değişkeni ve değer dönüştürülecek önünde parantez içinde için atama türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-131">To perform a cast, specify the type that you are casting to in parentheses in front of the value or variable to be converted.</span></span> <span data-ttu-id="c0dfa-132">Aşağıdaki program yayınları bir [çift](../../../csharp/language-reference/keywords/double.md) için bir [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md). Program yayın olmadan derlemeyecektir.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-132">The following program casts a [double](../../../csharp/language-reference/keywords/double.md) to an [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md). The program will not compile without the cast.</span></span>  
  
 [!code-csharp[csProgGuideTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#2)]  
  
 <span data-ttu-id="c0dfa-133">İzin verilen açık sayısal dönüşümler listesi için bkz. [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="c0dfa-133">For a list of the explicit numeric conversions that are allowed, see [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).</span></span>  
  
 <span data-ttu-id="c0dfa-134">Başvuru türleri için açık bir tür dönüştürme temel türünden türetilmiş bir tür dönüştürmek istiyorsanız gereklidir:</span><span class="sxs-lookup"><span data-stu-id="c0dfa-134">For reference types, an explicit cast is required if you need to convert from a base type to a derived type:</span></span>  
  
```csharp  
// Create a new derived type.  
Giraffe g = new Giraffe();  
  
// Implicit conversion to base type is safe.  
Animal a = g;  
  
// Explicit conversion is required to cast back  
// to derived type. Note: This will compile but will  
// throw an exception at run time if the right-side  
// object is not in fact a Giraffe.  
Giraffe g2 = (Giraffe) a;  
```  
  
 <span data-ttu-id="c0dfa-135">Başvuru türleri arasındaki bir tür dönüştürme işlemi, temel alınan nesnenin çalışma zamanı türünü değiştirmez. yalnızca bu nesneye bir başvuru olarak kullanılan değerin türünü değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-135">A cast operation between reference types does not change the run-time type of the underlying object; it only changes the type of the value that is being used as a reference to that object.</span></span> <span data-ttu-id="c0dfa-136">Daha fazla bilgi için [çok biçimlilik](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span><span class="sxs-lookup"><span data-stu-id="c0dfa-136">For more information, see [Polymorphism](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span></span>  
  
## <a name="type-conversion-exceptions-at-run-time"></a><span data-ttu-id="c0dfa-137">Tür dönüştürme özel durumlar çalışma zamanında</span><span class="sxs-lookup"><span data-stu-id="c0dfa-137">Type conversion exceptions at run time</span></span>

 <span data-ttu-id="c0dfa-138">Bazı başvuru türü dönüşümleri, derleyici bir tür dönüştürme geçerli olup olmayacağını belirlenemiyor.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-138">In some reference type conversions, the compiler cannot determine whether a cast will be valid.</span></span> <span data-ttu-id="c0dfa-139">Çalışma zamanında başarısız için doğru derleyen bir dönüştürme işlemi mümkündür.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-139">It is possible for a cast operation that compiles correctly to fail at run time.</span></span> <span data-ttu-id="c0dfa-140">Aşağıdaki örnekte gösterildiği gibi çalışma zamanında başarısız neden olacak bir tür cast bir <xref:System.InvalidCastException> oluşturulması için.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-140">As shown in the following example, a type cast that fails at run time will cause an <xref:System.InvalidCastException> to be thrown.</span></span>  
  
 [!code-csharp[csProgGuideTypes#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#41)]  
  
 <span data-ttu-id="c0dfa-141">C#sağlar [olduğu](../../language-reference/operators/type-testing-and-conversion-operators.md#is-operator) işleci, bir atama gerçekleştirmeden önce uyumluluğu test etmek sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-141">C# provides the [is](../../language-reference/operators/type-testing-and-conversion-operators.md#is-operator) operator to enable you to test for compatibility before actually performing a cast.</span></span> <span data-ttu-id="c0dfa-142">Daha fazla bilgi için [nasıl yapılır: güvenli bir şekilde desen eşleştirme ve olarak kullanarak AS ve is işleçlerini](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).</span><span class="sxs-lookup"><span data-stu-id="c0dfa-142">For more information, see [How to: safely cast using pattern matching and the as and is operators](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c0dfa-143">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c0dfa-143">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

## <a name="see-also"></a><span data-ttu-id="c0dfa-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0dfa-144">See also</span></span>

- [<span data-ttu-id="c0dfa-145">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c0dfa-145">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c0dfa-146">Türler</span><span class="sxs-lookup"><span data-stu-id="c0dfa-146">Types</span></span>](../../../csharp/programming-guide/types/index.md)
- [<span data-ttu-id="c0dfa-147">() İşleci</span><span class="sxs-lookup"><span data-stu-id="c0dfa-147">() Operator</span></span>](../../../csharp/language-reference/operators/type-testing-and-conversion-operators.md#cast-operator-)
- [<span data-ttu-id="c0dfa-148">explicit</span><span class="sxs-lookup"><span data-stu-id="c0dfa-148">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)
- [<span data-ttu-id="c0dfa-149">implicit</span><span class="sxs-lookup"><span data-stu-id="c0dfa-149">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)
- [<span data-ttu-id="c0dfa-150">Dönüştürme İşleçleri</span><span class="sxs-lookup"><span data-stu-id="c0dfa-150">Conversion Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/conversion-operators.md)
- <span data-ttu-id="c0dfa-151">[Genelleşmiş tür dönüştürme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="c0dfa-151">[Generalized Type Conversion](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/yy580hbd(v=vs.120))</span></span>
- [<span data-ttu-id="c0dfa-152">Nasıl yapılır: Bir dizeyi sayıya dönüştürme</span><span class="sxs-lookup"><span data-stu-id="c0dfa-152">How to: Convert a String to a Number</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
