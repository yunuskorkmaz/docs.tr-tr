---
title: enum anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: 57043963640f3c384b1e1a9aa7aeb65114689e9f
ms.sourcegitcommit: 4a3c95e91289d16c38979575a245a4f76b0da147
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67569531"
---
# <a name="enum-c-reference"></a><span data-ttu-id="f4b19-102">enum (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f4b19-102">enum (C# Reference)</span></span>

<span data-ttu-id="f4b19-103">`enum` Anahtar sözcüğü bir numaralandırma, numaralandırıcı listesi olarak adlandırılan sabitler kümesinden oluşan ayrı bir türü bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4b19-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>

<span data-ttu-id="f4b19-104">Genellikle ad alanındaki tüm sınıflar ile eşit kolaylık erişebilmeleri doğrudan bir ad alanındaki bir numaralandırma tanımlamak idealdir.</span><span class="sxs-lookup"><span data-stu-id="f4b19-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="f4b19-105">Ancak, bir sabit listesi bir sınıf veya yapı içinde yuvalanabilir.</span><span class="sxs-lookup"><span data-stu-id="f4b19-105">However, an enum can also be nested within a class or struct.</span></span>

<span data-ttu-id="f4b19-106">Varsayılan olarak, ilk Numaralandırıcı değeri 0 olan ve art arda gelen her Numaralandırıcı değeri 1 artar.</span><span class="sxs-lookup"><span data-stu-id="f4b19-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="f4b19-107">Örneğin, aşağıdaki sabit listesi içinde `Sat` olduğu `0`, `Sun` olduğu `1`, `Mon` olduğu `2`vb.</span><span class="sxs-lookup"><span data-stu-id="f4b19-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="f4b19-108">Numaralandırıcılar başlatıcılar varsayılan değerlerini geçersiz kılması için aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4b19-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="f4b19-109">Bu sabit listesi öğeleri dizisi başlangıç zorlanır `1` yerine `0`.</span><span class="sxs-lookup"><span data-stu-id="f4b19-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="f4b19-110">Ancak, 0 değerine sahip bir sabit dahil olmak üzere önerilir.</span><span class="sxs-lookup"><span data-stu-id="f4b19-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="f4b19-111">Daha fazla bilgi için [Numaralandırma türleri](../../programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="f4b19-111">For more information, see [Enumeration Types](../../programming-guide/enumeration-types.md).</span></span>

<span data-ttu-id="f4b19-112">Herhangi bir temel türü her sabit listesi türünde [sayısal bir tamsayı türü](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="f4b19-112">Every enumeration type has an underlying type, which can be any [integral numeric type](../builtin-types/integral-numeric-types.md).</span></span> <span data-ttu-id="f4b19-113">[Char](char.md) bir sabit listesi türünü temel türü olamaz.</span><span class="sxs-lookup"><span data-stu-id="f4b19-113">The [char](char.md) type cannot be an underlying type of an enum.</span></span> <span data-ttu-id="f4b19-114">Sabit listesi öğeleri listesinin temel alınan türü varsayılandır [int](../builtin-types/integral-numeric-types.md). Bir numaralandırma başka bir integral türü gibi bildirmek için [bayt](../builtin-types/integral-numeric-types.md), aşağıdaki örnekte gösterildiği gibi türü tarafından izlenen tanımlayıcısı sonra bir virgül kullanın.</span><span class="sxs-lookup"><span data-stu-id="f4b19-114">The default underlying type of enumeration elements is [int](../builtin-types/integral-numeric-types.md). To declare an enum of another integral type, such as [byte](../builtin-types/integral-numeric-types.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="f4b19-115">Bir değişken bir numaralandırma türünün temel türü aralığındaki herhangi bir değer atanabilir; değerleri için adlandırılmış sabitler sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="f4b19-115">A variable of an enumeration type can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>

<span data-ttu-id="f4b19-116">Varsayılan değer olan bir `enum E` ifade tarafından üretilen değer `(E)0`.</span><span class="sxs-lookup"><span data-stu-id="f4b19-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>

> [!NOTE]
> <span data-ttu-id="f4b19-117">Bir numaralandırıcı adı boşluk içeremez.</span><span class="sxs-lookup"><span data-stu-id="f4b19-117">An enumerator cannot contain white space in its name.</span></span>

<span data-ttu-id="f4b19-118">Her Numaralandırıcı için ne kadar depolama alanı ayrılır, temel alınan türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4b19-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="f4b19-119">Ancak, bir açık tür dönüştürme dönüştürmek gerekli `enum` türü için bir tamsayı türü.</span><span class="sxs-lookup"><span data-stu-id="f4b19-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="f4b19-120">Örneğin aşağıdaki deyim, numaralandırıcı atar `Sun` türünde bir değişkene [int](../builtin-types/integral-numeric-types.md) dönüştürmek için bir tür dönüştürme kullanılarak `enum` için `int`.</span><span class="sxs-lookup"><span data-stu-id="f4b19-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../builtin-types/integral-numeric-types.md) by using a cast to convert from `enum` to `int`.</span></span>

```csharp
int x = (int)Day.Sun;
```

<span data-ttu-id="f4b19-121">Uyguladığınızda <xref:System.FlagsAttribute?displayProperty=nameWithType> bit ile birleştirilebilir öğeleri içeren bir sabit listesi `OR` işlemi, öznitelik davranışını etkileyen `enum` bazı araçlarla kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="f4b19-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="f4b19-122">Gibi araçları kullanın, bu değişiklikler fark <xref:System.Console> sınıfı yöntemleri ve ifade değerlendiricisi.</span><span class="sxs-lookup"><span data-stu-id="f4b19-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="f4b19-123">(Üçüncü örneğe bakın.)</span><span class="sxs-lookup"><span data-stu-id="f4b19-123">(See the third example.)</span></span>

## <a name="robust-programming"></a><span data-ttu-id="f4b19-124">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="f4b19-124">Robust programming</span></span>

<span data-ttu-id="f4b19-125">Tek tek bir sabit listesi değerlerinin tüm başvurular olduğu herhangi bir sabit olduğu gibi sayısal değişmez değerleri için derleme zamanında dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="f4b19-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="f4b19-126">Bu sürüm ile ilgili olası sorunları açıklandığı gibi oluşturabilirsiniz [sabitleri](../../programming-guide/classes-and-structs/constants.md).</span><span class="sxs-lookup"><span data-stu-id="f4b19-126">This can create potential versioning issues as described in [Constants](../../programming-guide/classes-and-structs/constants.md).</span></span>

<span data-ttu-id="f4b19-127">Sabit listeleri yeni sürümleri için ek değerler atama veya yeni bir sürümünde, sabit listesi üyelerinin değerlerini değiştirmek için bağımlı kaynak kodunuz için sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4b19-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="f4b19-128">Sabit listesi değerlerinin sık sık kullanılır [geçiş](switch.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="f4b19-128">Enum values often are used in [switch](switch.md) statements.</span></span> <span data-ttu-id="f4b19-129">Ek öğeler için eklenip eklenmediğini `enum` varsayılan bölümün switch ifadesinin türü beklenmedik bir şekilde seçilebilir.</span><span class="sxs-lookup"><span data-stu-id="f4b19-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>

<span data-ttu-id="f4b19-130">Diğer geliştiricilerin kodunuzu kullanırsanız, yeni öğeler için eklenirse kodlarını nasıl yanıt vermesini hakkında yönergeleri sağlamalıdır `enum` türleri.</span><span class="sxs-lookup"><span data-stu-id="f4b19-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>

## <a name="example"></a><span data-ttu-id="f4b19-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4b19-131">Example</span></span>

<span data-ttu-id="f4b19-132">Aşağıdaki örnekte, bir numaralandırma `Day`, bildirilir.</span><span class="sxs-lookup"><span data-stu-id="f4b19-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="f4b19-133">İki numaralandırıcılar açıkça tamsayıya dönüştürülüp ve tamsayı değişkenine atanır.</span><span class="sxs-lookup"><span data-stu-id="f4b19-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a><span data-ttu-id="f4b19-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4b19-134">Example</span></span>

<span data-ttu-id="f4b19-135">Aşağıdaki örnekte, temel türünde seçenek bildirmek için kullanılan bir `enum` üyeleri, tür `long`.</span><span class="sxs-lookup"><span data-stu-id="f4b19-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="f4b19-136">Sabit listesi türünü temel olsa bile dikkat `long`, numaralandırma üyelerini hala açıkça türüne dönüştürülmesi gerekir `long` kullanarak bir cast.</span><span class="sxs-lookup"><span data-stu-id="f4b19-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a><span data-ttu-id="f4b19-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="f4b19-137">Example</span></span>

<span data-ttu-id="f4b19-138">Aşağıdaki kod örneği kullanım ve etkisini gösterir <xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliği bir `enum` bildirimi.</span><span class="sxs-lookup"><span data-stu-id="f4b19-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a><span data-ttu-id="f4b19-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f4b19-139">Comments</span></span>

<span data-ttu-id="f4b19-140">Kaldırırsanız `Flags`, örnek aşağıdaki değerleri görüntüler:</span><span class="sxs-lookup"><span data-stu-id="f4b19-140">If you remove `Flags`, the example displays the following values:</span></span>

`5`

`5`

## <a name="c-language-specification"></a><span data-ttu-id="f4b19-141">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f4b19-141">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f4b19-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4b19-142">See also</span></span>

- [<span data-ttu-id="f4b19-143">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f4b19-143">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f4b19-144">Sabit Listesi Türleri</span><span class="sxs-lookup"><span data-stu-id="f4b19-144">Enumeration Types</span></span>](../../programming-guide/enumeration-types.md)
- [<span data-ttu-id="f4b19-145">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="f4b19-145">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f4b19-146">Tam sayı türleri</span><span class="sxs-lookup"><span data-stu-id="f4b19-146">Integral types</span></span>](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="f4b19-147">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="f4b19-147">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="f4b19-148">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="f4b19-148">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="f4b19-149">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="f4b19-149">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="f4b19-150">Enum adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="f4b19-150">Enum Naming Conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
