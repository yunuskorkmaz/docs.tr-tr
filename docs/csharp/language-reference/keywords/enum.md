---
title: "enum (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f3ba82eb3fd1832a3d57090c9dc6941f962cb837
ms.sourcegitcommit: c3ebb11a66e85a465c9ba2c42592222630b7ff9e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2018
---
# <a name="enum-c-reference"></a><span data-ttu-id="6865b-102">enum (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6865b-102">enum (C# Reference)</span></span>
<span data-ttu-id="6865b-103">`enum` Anahtar sözcüğü bir numaralandırma, numaralandırıcı listesi adlı adlandırılmış sabitler kümesinden oluşur farklı bir tür bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6865b-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>  
  
 <span data-ttu-id="6865b-104">Genellikle ad alanındaki tüm sınıflar, ile eşit kolaylık erişebilmesi için doğrudan bir ad alanı içinde bir enum tanımlamak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="6865b-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="6865b-105">Ancak, bir enum da bir sınıf veya yapı içinde iç içe.</span><span class="sxs-lookup"><span data-stu-id="6865b-105">However, an enum can also be nested within a class or struct.</span></span>  
  
 <span data-ttu-id="6865b-106">Varsayılan olarak, ilk Numaralandırıcı 0 değerine sahip ve art arda gelen her Numaralandırıcı değerinin 1 ile artar.</span><span class="sxs-lookup"><span data-stu-id="6865b-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="6865b-107">Örneğin, aşağıdaki numaralandırma içinde `Sat` olan `0`, `Sun` olan `1`, `Mon` olan `2`, vb.</span><span class="sxs-lookup"><span data-stu-id="6865b-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>  
  
```  
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="6865b-108">Numaralandırmalar başlatıcıları varsayılan değerleri geçersiz kılmak için aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6865b-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>  
  
```  
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="6865b-109">Bu numaralandırma, öğelerin sırasını başlangıç zorlanır `1` yerine `0`.</span><span class="sxs-lookup"><span data-stu-id="6865b-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="6865b-110">Ancak, değeri 0 olan bir sabit dahil olmak üzere önerilir.</span><span class="sxs-lookup"><span data-stu-id="6865b-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="6865b-111">Daha fazla bilgi için bkz: [Numaralandırma türleri](../../../csharp/programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-111">For more information, see [Enumeration Types](../../../csharp/programming-guide/enumeration-types.md).</span></span>  
  
 <span data-ttu-id="6865b-112">Her numaralandırma türü, herhangi bir tam sayı türü olabilecek bir temel türünde dışında [char](../../../csharp/language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-112">Every enumeration type has an underlying type, which can be any integral type except [char](../../../csharp/language-reference/keywords/char.md).</span></span> <span data-ttu-id="6865b-113">Temel alınan tür numaralandırma öğelerinin varsayılan [int](../../../csharp/language-reference/keywords/int.md). Başka bir tam sayı türü, bir numaralandırma gibi bildirmek için [bayt](../../../csharp/language-reference/keywords/byte.md), aşağıdaki örnekte gösterildiği gibi türü, izlemelidir tanımlayıcı sonra iki nokta kullanın.</span><span class="sxs-lookup"><span data-stu-id="6865b-113">The default underlying type of enumeration elements is [int](../../../csharp/language-reference/keywords/int.md). To declare an enum of another integral type, such as [byte](../../../csharp/language-reference/keywords/byte.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>  
  
```  
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};  
```  
  
 <span data-ttu-id="6865b-114">Bir numaralandırma için onaylanan türleri `byte`, [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [kısa](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [uzun](../../../csharp/language-reference/keywords/long.md), veya [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-114">The approved types for an enum are `byte`, [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
 <span data-ttu-id="6865b-115">Türünde bir değişken `Day` temel alınan tür; aralığındaki hiçbir değer atanabilir değerlerin adlandırılmış sabitler sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="6865b-115">A variable of type `Day` can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>  
  
 <span data-ttu-id="6865b-116">Varsayılan değer olan bir `enum E` ifade tarafından üretilen değer `(E)0`.</span><span class="sxs-lookup"><span data-stu-id="6865b-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6865b-117">Bir numaralandırıcı adında boşluk içeremez.</span><span class="sxs-lookup"><span data-stu-id="6865b-117">An enumerator cannot contain white space in its name.</span></span>  
  
 <span data-ttu-id="6865b-118">Temel alınan tür, ne kadar depolama alanı için her Numaralandırıcı ayrılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="6865b-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="6865b-119">Ancak, bir açık atama dönüştürmek gerekli olan `enum` türü olarak bir tam sayı tür.</span><span class="sxs-lookup"><span data-stu-id="6865b-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="6865b-120">Örneğin, aşağıdaki deyim Numaralandırıcı atar `Sun` türünde bir değişken için [int](../../../csharp/language-reference/keywords/int.md) dönüştürmek için bir atama kullanarak `enum` için `int`.</span><span class="sxs-lookup"><span data-stu-id="6865b-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../../../csharp/language-reference/keywords/int.md) by using a cast to convert from `enum` to `int`.</span></span>  
  
```  
int x = (int)Day.Sun;  
```  
  
 <span data-ttu-id="6865b-121">Uyguladığınızda <xref:System.FlagsAttribute?displayProperty=nameWithType> bit ile birleştirilebilir öğeleri içeren bir sabit `OR` işlemi, öznitelik davranışını etkileyen `enum` bazı araçları ile kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="6865b-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="6865b-122">Araçları gibi kullandığınızda bu değişiklikler fark <xref:System.Console> sınıfı yöntemleri ve ifade değerlendiricisi.</span><span class="sxs-lookup"><span data-stu-id="6865b-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="6865b-123">(Üçüncü örneğe bakın.)</span><span class="sxs-lookup"><span data-stu-id="6865b-123">(See the third example.)</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6865b-124">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="6865b-124">Robust Programming</span></span>  
 <span data-ttu-id="6865b-125">Herhangi bir sabit olduğu gibi yalnızca ile tek tek enum değerlerinin tüm başvurularını derleme zamanında sayısal değişmez değerleri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="6865b-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="6865b-126">Bu sürüm ile ilgili olası sorunları açıklandığı gibi oluşturabilirsiniz [sabitleri](../../../csharp/programming-guide/classes-and-structs/constants.md).</span><span class="sxs-lookup"><span data-stu-id="6865b-126">This can create potential versioning issues as described in [Constants](../../../csharp/programming-guide/classes-and-structs/constants.md).</span></span>  
  
 <span data-ttu-id="6865b-127">Numaralandırmalar yeni sürümleri için ek değerler atama veya yeni bir sürümünde enum üyelerinin değerlerini değiştirme bağımlı kaynak kodu için sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6865b-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="6865b-128">Enum değerleri sıklıkla kullanıldığı [geçiş](../../../csharp/language-reference/keywords/switch.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="6865b-128">Enum values often are used in [switch](../../../csharp/language-reference/keywords/switch.md) statements.</span></span> <span data-ttu-id="6865b-129">Ek öğeler için eklenip eklenmediğini `enum` türü, varsayılan bölümünü switch deyimi, beklenmedik biçimde seçilebilir.</span><span class="sxs-lookup"><span data-stu-id="6865b-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>  
  
 <span data-ttu-id="6865b-130">Diğer geliştiriciler kodunuzu kullanırsanız, yeni öğeler hiçbirine eklenirse, kodu nasıl tepki vermelidir hakkında yönergeler sağlamalıdır `enum` türleri.</span><span class="sxs-lookup"><span data-stu-id="6865b-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6865b-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="6865b-131">Example</span></span>  
 <span data-ttu-id="6865b-132">Aşağıdaki örnekte, bir numaralandırma `Day`, bildirilmedi.</span><span class="sxs-lookup"><span data-stu-id="6865b-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="6865b-133">İki numaralandırıcılar açıkça tamsayıya dönüştürülüp ve tamsayı değişkenlere atanır.</span><span class="sxs-lookup"><span data-stu-id="6865b-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="6865b-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="6865b-134">Example</span></span>  
 <span data-ttu-id="6865b-135">Aşağıdaki örnekte, temel türü seçeneği bildirmek için kullanılan bir `enum` üyeleri olan türü `long`.</span><span class="sxs-lookup"><span data-stu-id="6865b-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="6865b-136">Numaralandırma temel alınan türü olsa bile dikkat `long`, numaralandırma üyeleri hala açıkça yazın dönüştürülmelidir `long` bir cast kullanarak.</span><span class="sxs-lookup"><span data-stu-id="6865b-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="6865b-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="6865b-137">Example</span></span>  
 <span data-ttu-id="6865b-138">Aşağıdaki kod örneği kullanım ve etkisini gösterir <xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliği bir `enum` bildirimi.</span><span class="sxs-lookup"><span data-stu-id="6865b-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/enum_3.cs)]  
  
## <a name="comments"></a><span data-ttu-id="6865b-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6865b-139">Comments</span></span>  
 <span data-ttu-id="6865b-140">Kaldırırsanız `Flags`, örnek aşağıdaki değerleri görüntüler:</span><span class="sxs-lookup"><span data-stu-id="6865b-140">If you remove `Flags`, the example displays the following values:</span></span>  
  
 `5`  
  
 `5`  
  
## <a name="c-language-specification"></a><span data-ttu-id="6865b-141">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="6865b-141">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6865b-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6865b-142">See Also</span></span>  
 [<span data-ttu-id="6865b-143">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6865b-143">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6865b-144">Sabit Listesi Türleri</span><span class="sxs-lookup"><span data-stu-id="6865b-144">Enumeration Types</span></span>](../../../csharp/programming-guide/enumeration-types.md)  
 [<span data-ttu-id="6865b-145">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="6865b-145">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6865b-146">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="6865b-146">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="6865b-147">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="6865b-147">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="6865b-148">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="6865b-148">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 <span data-ttu-id="6865b-149">[Açık sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) [Enum adlandırma kuralları](https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces#naming-enumerations)</span><span class="sxs-lookup"><span data-stu-id="6865b-149">[Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) [Enum Naming Conventions](https://docs.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces#naming-enumerations)</span></span>
