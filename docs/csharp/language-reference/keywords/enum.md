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
ms.openlocfilehash: f2439bb955f821b58acc818ede308c379d5b68a6
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243562"
---
# <a name="enum-c-reference"></a><span data-ttu-id="ecbee-102">enum (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ecbee-102">enum (C# Reference)</span></span>

<span data-ttu-id="ecbee-103">`enum` Anahtar sözcüğü bir numaralandırma, numaralandırıcı listesi olarak adlandırılan sabitler kümesinden oluşan ayrı bir türü bildirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ecbee-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>  

<span data-ttu-id="ecbee-104">Genellikle ad alanındaki tüm sınıflar ile eşit kolaylık erişebilmeleri doğrudan bir ad alanındaki bir numaralandırma tanımlamak idealdir.</span><span class="sxs-lookup"><span data-stu-id="ecbee-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="ecbee-105">Ancak, bir sabit listesi bir sınıf veya yapı içinde yuvalanabilir.</span><span class="sxs-lookup"><span data-stu-id="ecbee-105">However, an enum can also be nested within a class or struct.</span></span>

<span data-ttu-id="ecbee-106">Varsayılan olarak, ilk Numaralandırıcı değeri 0 olan ve art arda gelen her Numaralandırıcı değeri 1 artar.</span><span class="sxs-lookup"><span data-stu-id="ecbee-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="ecbee-107">Örneğin, aşağıdaki sabit listesi içinde `Sat` olduğu `0`, `Sun` olduğu `1`, `Mon` olduğu `2`vb.</span><span class="sxs-lookup"><span data-stu-id="ecbee-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="ecbee-108">Numaralandırıcılar başlatıcılar varsayılan değerlerini geçersiz kılması için aşağıdaki örnekte gösterildiği gibi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ecbee-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="ecbee-109">Bu sabit listesi öğeleri dizisi başlangıç zorlanır `1` yerine `0`.</span><span class="sxs-lookup"><span data-stu-id="ecbee-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="ecbee-110">Ancak, 0 değerine sahip bir sabit dahil olmak üzere önerilir.</span><span class="sxs-lookup"><span data-stu-id="ecbee-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="ecbee-111">Daha fazla bilgi için [Numaralandırma türleri](../../programming-guide/enumeration-types.md).</span><span class="sxs-lookup"><span data-stu-id="ecbee-111">For more information, see [Enumeration Types](../../programming-guide/enumeration-types.md).</span></span>

<span data-ttu-id="ecbee-112">Her sabit listesi türünde herhangi bir Entegral türü olabilir bir temel türü dışında [char](char.md).</span><span class="sxs-lookup"><span data-stu-id="ecbee-112">Every enumeration type has an underlying type, which can be any integral type except [char](char.md).</span></span> <span data-ttu-id="ecbee-113">Sabit listesi öğeleri listesinin temel alınan türü varsayılandır [int](int.md). Bir numaralandırma başka bir integral türü gibi bildirmek için [bayt](byte.md), aşağıdaki örnekte gösterildiği gibi türü tarafından izlenen tanımlayıcısı sonra bir virgül kullanın.</span><span class="sxs-lookup"><span data-stu-id="ecbee-113">The default underlying type of enumeration elements is [int](int.md). To declare an enum of another integral type, such as [byte](byte.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="ecbee-114">Enum için onaylanan türler [bayt](byte.md), [sbyte](sbyte.md), [kısa](short.md), [ushort](ushort.md), [int](int.md), [uint](uint.md), [uzun](long.md), veya [ulong](ulong.md).</span><span class="sxs-lookup"><span data-stu-id="ecbee-114">The approved types for an enum are [byte](byte.md), [sbyte](sbyte.md), [short](short.md), [ushort](ushort.md), [int](int.md), [uint](uint.md), [long](long.md), or [ulong](ulong.md).</span></span>

<span data-ttu-id="ecbee-115">Bir değişken bir numaralandırma türünün temel türü aralığındaki herhangi bir değer atanabilir; değerleri için adlandırılmış sabitler sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="ecbee-115">A variable of an enumeration type can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>

<span data-ttu-id="ecbee-116">Varsayılan değer olan bir `enum E` ifade tarafından üretilen değer `(E)0`.</span><span class="sxs-lookup"><span data-stu-id="ecbee-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>

> [!NOTE]
> <span data-ttu-id="ecbee-117">Bir numaralandırıcı adı boşluk içeremez.</span><span class="sxs-lookup"><span data-stu-id="ecbee-117">An enumerator cannot contain white space in its name.</span></span>

<span data-ttu-id="ecbee-118">Her Numaralandırıcı için ne kadar depolama alanı ayrılır, temel alınan türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="ecbee-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="ecbee-119">Ancak, bir açık tür dönüştürme dönüştürmek gerekli `enum` türü için bir tamsayı türü.</span><span class="sxs-lookup"><span data-stu-id="ecbee-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="ecbee-120">Örneğin aşağıdaki deyim, numaralandırıcı atar `Sun` türünde bir değişkene [int](int.md) dönüştürmek için bir tür dönüştürme kullanılarak `enum` için `int`.</span><span class="sxs-lookup"><span data-stu-id="ecbee-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](int.md) by using a cast to convert from `enum` to `int`.</span></span>

```csharp
int x = (int)Day.Sun;
```

<span data-ttu-id="ecbee-121">Uyguladığınızda <xref:System.FlagsAttribute?displayProperty=nameWithType> bit ile birleştirilebilir öğeleri içeren bir sabit listesi `OR` işlemi, öznitelik davranışını etkileyen `enum` bazı araçlarla kullanıldığında.</span><span class="sxs-lookup"><span data-stu-id="ecbee-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="ecbee-122">Gibi araçları kullanın, bu değişiklikler fark <xref:System.Console> sınıfı yöntemleri ve ifade değerlendiricisi.</span><span class="sxs-lookup"><span data-stu-id="ecbee-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="ecbee-123">(Üçüncü örneğe bakın.)</span><span class="sxs-lookup"><span data-stu-id="ecbee-123">(See the third example.)</span></span>

## <a name="robust-programming"></a><span data-ttu-id="ecbee-124">Güçlü programlama</span><span class="sxs-lookup"><span data-stu-id="ecbee-124">Robust programming</span></span>

<span data-ttu-id="ecbee-125">Tek tek bir sabit listesi değerlerinin tüm başvurular olduğu herhangi bir sabit olduğu gibi sayısal değişmez değerleri için derleme zamanında dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="ecbee-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="ecbee-126">Bu sürüm ile ilgili olası sorunları açıklandığı gibi oluşturabilirsiniz [sabitleri](../../programming-guide/classes-and-structs/constants.md).</span><span class="sxs-lookup"><span data-stu-id="ecbee-126">This can create potential versioning issues as described in [Constants](../../programming-guide/classes-and-structs/constants.md).</span></span>

<span data-ttu-id="ecbee-127">Sabit listeleri yeni sürümleri için ek değerler atama veya yeni bir sürümünde, sabit listesi üyelerinin değerlerini değiştirmek için bağımlı kaynak kodunuz için sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ecbee-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="ecbee-128">Sabit listesi değerlerinin sık sık kullanılır [geçiş](switch.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="ecbee-128">Enum values often are used in [switch](switch.md) statements.</span></span> <span data-ttu-id="ecbee-129">Ek öğeler için eklenip eklenmediğini `enum` varsayılan bölümün switch ifadesinin türü beklenmedik bir şekilde seçilebilir.</span><span class="sxs-lookup"><span data-stu-id="ecbee-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>

<span data-ttu-id="ecbee-130">Diğer geliştiricilerin kodunuzu kullanırsanız, yeni öğeler için eklenirse kodlarını nasıl yanıt vermesini hakkında yönergeleri sağlamalıdır `enum` türleri.</span><span class="sxs-lookup"><span data-stu-id="ecbee-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>

## <a name="example"></a><span data-ttu-id="ecbee-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="ecbee-131">Example</span></span>

<span data-ttu-id="ecbee-132">Aşağıdaki örnekte, bir numaralandırma `Day`, bildirilir.</span><span class="sxs-lookup"><span data-stu-id="ecbee-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="ecbee-133">İki numaralandırıcılar açıkça tamsayıya dönüştürülüp ve tamsayı değişkenine atanır.</span><span class="sxs-lookup"><span data-stu-id="ecbee-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a><span data-ttu-id="ecbee-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="ecbee-134">Example</span></span>

<span data-ttu-id="ecbee-135">Aşağıdaki örnekte, temel türünde seçenek bildirmek için kullanılan bir `enum` üyeleri, tür `long`.</span><span class="sxs-lookup"><span data-stu-id="ecbee-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="ecbee-136">Sabit listesi türünü temel olsa bile dikkat `long`, numaralandırma üyelerini hala açıkça türüne dönüştürülmesi gerekir `long` kullanarak bir cast.</span><span class="sxs-lookup"><span data-stu-id="ecbee-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a><span data-ttu-id="ecbee-137">Örnek</span><span class="sxs-lookup"><span data-stu-id="ecbee-137">Example</span></span>

<span data-ttu-id="ecbee-138">Aşağıdaki kod örneği kullanım ve etkisini gösterir <xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliği bir `enum` bildirimi.</span><span class="sxs-lookup"><span data-stu-id="ecbee-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a><span data-ttu-id="ecbee-139">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ecbee-139">Comments</span></span>

<span data-ttu-id="ecbee-140">Kaldırırsanız `Flags`, örnek aşağıdaki değerleri görüntüler:</span><span class="sxs-lookup"><span data-stu-id="ecbee-140">If you remove `Flags`, the example displays the following values:</span></span>

`5`

`5`

## <a name="c-language-specification"></a><span data-ttu-id="ecbee-141">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ecbee-141">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ecbee-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecbee-142">See also</span></span>

- [<span data-ttu-id="ecbee-143">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="ecbee-143">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="ecbee-144">Sabit Listesi Türleri</span><span class="sxs-lookup"><span data-stu-id="ecbee-144">Enumeration Types</span></span>](../../programming-guide/enumeration-types.md)  
- [<span data-ttu-id="ecbee-145">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="ecbee-145">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="ecbee-146">Tam Sayı Türleri Tablosu</span><span class="sxs-lookup"><span data-stu-id="ecbee-146">Integral Types Table</span></span>](integral-types-table.md)  
- [<span data-ttu-id="ecbee-147">Yerleşik Türler Tablosu</span><span class="sxs-lookup"><span data-stu-id="ecbee-147">Built-In Types Table</span></span>](built-in-types-table.md)  
- [<span data-ttu-id="ecbee-148">Örtük Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="ecbee-148">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="ecbee-149">Açık Sayısal Dönüştürmeler Tablosu</span><span class="sxs-lookup"><span data-stu-id="ecbee-149">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)  
- [<span data-ttu-id="ecbee-150">Enum adlandırma kuralları</span><span class="sxs-lookup"><span data-stu-id="ecbee-150">Enum Naming Conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
