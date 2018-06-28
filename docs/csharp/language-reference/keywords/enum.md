---
title: enum anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 634fbd846993d32ae529f87e96fd91857e5c1883
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2018
ms.locfileid: "37028285"
---
# <a name="enum-c-reference"></a><span data-ttu-id="0e58a-102">enum (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="0e58a-102">enum (C# Reference)</span></span>

<span data-ttu-id="0e58a-103">`enum` Anahtar sözcüğü bir numaralandırma, numaralandırıcı listesi adlı adlandırılmış sabitler kümesinden oluşur farklı bir tür bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0e58a-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>  

<span data-ttu-id="0e58a-104">Genellikle ad alanındaki tüm sınıflar, ile eşit kolaylık erişebilmesi için doğrudan bir ad alanı içinde bir enum tanımlamak en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="0e58a-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="0e58a-105">Ancak, bir enum da bir sınıf veya yapı içinde iç içe.</span><span class="sxs-lookup"><span data-stu-id="0e58a-105">However, an enum can also be nested within a class or struct.</span></span>

<span data-ttu-id="0e58a-106">Varsayılan olarak, ilk Numaralandırıcı 0 değerine sahip ve art arda gelen her Numaralandırıcı değerinin 1 ile artar.</span><span class="sxs-lookup"><span data-stu-id="0e58a-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="0e58a-107">Örneğin, aşağıdaki numaralandırma içinde `Sat` olan `0`, `Sun` olan `1`, `Mon` olan `2`, vb.</span><span class="sxs-lookup"><span data-stu-id="0e58a-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="0e58a-108">Numaralandırmalar başlatıcıları varsayılan değerleri geçersiz kılmak için aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e58a-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="0e58a-109">Bu numaralandırma, öğelerin sırasını başlangıç zorlanır `1` yerine `0`.</span><span class="sxs-lookup"><span data-stu-id="0e58a-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="0e58a-110">Ancak, değeri 0 olan bir sabit dahil olmak üzere önerilir.</span><span class="sxs-lookup"><span data-stu-id="0e58a-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="0e58a-111">Daha fazla bilgi için bkz: [Numaralandırma türleri](../../programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="0e58a-111">For more information, see [Enumeration Types](../../programming-guide/enumeration-types.md).</span></span>

<span data-ttu-id="0e58a-112">Her numaralandırma türü, herhangi bir tam sayı türü olabilecek bir temel türünde dışında [char](char.md).</span><span class="sxs-lookup"><span data-stu-id="0e58a-112">Every enumeration type has an underlying type, which can be any integral type except [char](char.md).</span></span> <span data-ttu-id="0e58a-113">Temel alınan tür numaralandırma öğelerinin varsayılan [int](int.md). Başka bir tam sayı türü, bir numaralandırma gibi bildirmek için [bayt](byte.md), aşağıdaki örnekte gösterildiği gibi türü, izlemelidir tanımlayıcı sonra iki nokta kullanın.</span><span class="sxs-lookup"><span data-stu-id="0e58a-113">The default underlying type of enumeration elements is [int](int.md). To declare an enum of another integral type, such as [byte](byte.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="0e58a-114">Bir numaralandırma için onaylanan türleri [bayt](byte.md), [sbyte](sbyte.md), [kısa](short.md), [ushort](ushort.md), [int](int.md), [uint](uint.md), [uzun](long.md), veya [ulong](ulong.md).</span><span class="sxs-lookup"><span data-stu-id="0e58a-114">The approved types for an enum are [byte](byte.md), [sbyte](sbyte.md), [short](short.md), [ushort](ushort.md), [int](int.md), [uint](uint.md), [long](long.md), or [ulong](ulong.md).</span></span>

<span data-ttu-id="0e58a-115">Türünde bir değişken `Day` temel alınan tür; aralığındaki hiçbir değer atanabilir değerlerin adlandırılmış sabitler sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="0e58a-115">A variable of type `Day` can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>

<span data-ttu-id="0e58a-116">Varsayılan değer olan bir `enum E` ifade tarafından üretilen değer `(E)0`.</span><span class="sxs-lookup"><span data-stu-id="0e58a-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>

> [!NOTE]
> <span data-ttu-id="0e58a-117">Bir numaralandırıcı adında boşluk içeremez.</span><span class="sxs-lookup"><span data-stu-id="0e58a-117">An enumerator cannot contain white space in its name.</span></span>

<span data-ttu-id="0e58a-118">Temel alınan tür, ne kadar depolama alanı için her Numaralandırıcı ayrılan belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e58a-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="0e58a-119">Ancak, bir açık atama dönüştürmek gerekli olan `enum` türü olarak bir tam sayı tür.</span><span class="sxs-lookup"><span data-stu-id="0e58a-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="0e58a-120">Örneğin, aşağıdaki deyim Numaralandırıcı atar `Sun` türünde bir değişken için [int](int.md) dönüştürmek için bir atama kullanarak `enum` için `int`.</span><span class="sxs-lookup"><span data-stu-id="0e58a-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](int.md) by using a cast to convert from `enum` to `int`.</span></span>

```csharp
int x = (int)Day.Sun;
```

<span data-ttu-id="0e58a-121">Uyguladığınızda <xref:System.FlagsAttribute?displayProperty=nameWithType> bit ile birleştirilebilir öğeleri içeren bir sabit `OR` işlemi, öznitelik davranışını etkileyen `enum` bazı araçları ile kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="0e58a-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="0e58a-122">Araçları gibi kullandığınızda bu değişiklikler fark <xref:System.Console> sınıfı yöntemleri ve ifade değerlendiricisi.</span><span class="sxs-lookup"><span data-stu-id="0e58a-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="0e58a-123">(Üçüncü örneğe bakın.)</span><span class="sxs-lookup"><span data-stu-id="0e58a-123">(See the third example.)</span></span>

## <a name="robust-programming"></a><span data-ttu-id="0e58a-124">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="0e58a-124">Robust programming</span></span>

<span data-ttu-id="0e58a-125">Herhangi bir sabit olduğu gibi yalnızca ile tek tek enum değerlerinin tüm başvurularını derleme zamanında sayısal değişmez değerleri dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="0e58a-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="0e58a-126">Bu sürüm ile ilgili olası sorunları açıklandığı gibi oluşturabilirsiniz [sabitleri](../../programming-guide/classes-and-structs/constants.md).</span><span class="sxs-lookup"><span data-stu-id="0e58a-126">This can create potential versioning issues as described in [Constants](../../programming-guide/classes-and-structs/constants.md).</span></span>

<span data-ttu-id="0e58a-127">Numaralandırmalar yeni sürümleri için ek değerler atama veya yeni bir sürümünde enum üyelerinin değerlerini değiştirme bağımlı kaynak kodu için sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0e58a-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="0e58a-128">Enum değerleri sıklıkla kullanıldığı [geçiş](switch.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="0e58a-128">Enum values often are used in [switch](switch.md) statements.</span></span> <span data-ttu-id="0e58a-129">Ek öğeler için eklenip eklenmediğini `enum` türü, varsayılan bölümünü switch deyimi, beklenmedik biçimde seçilebilir.</span><span class="sxs-lookup"><span data-stu-id="0e58a-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>

<span data-ttu-id="0e58a-130">Diğer geliştiriciler kodunuzu kullanırsanız, yeni öğeler hiçbirine eklenirse, kodu nasıl tepki vermelidir hakkında yönergeler sağlamalıdır `enum` türleri.</span><span class="sxs-lookup"><span data-stu-id="0e58a-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>

## <a name="example"></a><span data-ttu-id="0e58a-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e58a-131">Example</span></span>

<span data-ttu-id="0e58a-132">Aşağıdaki örnekte, bir numaralandırma `Day`, bildirilmedi.</span><span class="sxs-lookup"><span data-stu-id="0e58a-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="0e58a-133">İki numaralandırıcılar açıkça tamsayıya dönüştürülüp ve tamsayı değişkenlere atanır.</span><span class="sxs-lookup"><span data-stu-id="0e58a-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a><span data-ttu-id="0e58a-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e58a-134">Example</span></span>

<span data-ttu-id="0e58a-135">Aşağıdaki örnekte, temel türü seçeneği bildirmek için kullanılan bir `enum` üyeleri olan türü `long`.</span><span class="sxs-lookup"><span data-stu-id="0e58a-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="0e58a-136">Numaralandırma temel alınan türü olsa bile dikkat `long`, numaralandırma üyeleri hala açıkça yazın dönüştürülmelidir `long` bir cast kullanarak.</span><span class="sxs-lookup"><span data-stu-id="0e58a-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a><span data-ttu-id="0e58a-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e58a-137">Example</span></span>

<span data-ttu-id="0e58a-138">Aşağıdaki kod örneği kullanım ve etkisini gösterir <xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliği bir `enum` bildirimi.</span><span class="sxs-lookup"><span data-stu-id="0e58a-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a><span data-ttu-id="0e58a-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e58a-139">Comments</span></span>

<span data-ttu-id="0e58a-140">Kaldırırsanız `Flags`, örnek aşağıdaki değerleri görüntüler:</span><span class="sxs-lookup"><span data-stu-id="0e58a-140">If you remove `Flags`, the example displays the following values:</span></span>

`5`

`5`

## <a name="c-language-specification"></a><span data-ttu-id="0e58a-141">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="0e58a-141">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0e58a-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e58a-142">See also</span></span>

[<span data-ttu-id="0e58a-143">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="0e58a-143">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="0e58a-144">Sabit Listesi Türleri</span><span class="sxs-lookup"><span data-stu-id="0e58a-144">Enumeration Types</span></span>](../../programming-guide/enumeration-types.md)  
[<span data-ttu-id="0e58a-145">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0e58a-145">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="0e58a-146">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="0e58a-146">Integral Types Table</span></span>](integral-types-table.md)  
[<span data-ttu-id="0e58a-147">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="0e58a-147">Built-In Types Table</span></span>](built-in-types-table.md)  
[<span data-ttu-id="0e58a-148">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="0e58a-148">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)  
[<span data-ttu-id="0e58a-149">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="0e58a-149">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)  
[<span data-ttu-id="0e58a-150">Enum adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="0e58a-150">Enum Naming Conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
