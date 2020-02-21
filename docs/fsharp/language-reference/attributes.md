---
title: Öznitelikler
description: Özniteliklerin bir F# programlama yapısına nasıl uygulanacağını nasıl etkinleştirebileceğinizi öğrenin.
ms.date: 02/19/2020
ms.openlocfilehash: 77b84713ab9360166b3634d406993cf209c8a623
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543644"
---
# <a name="attributes"></a><span data-ttu-id="2b072-103">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="2b072-103">Attributes</span></span>

<span data-ttu-id="2b072-104">Öznitelikler meta verilerin bir programlama yapısına uygulanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b072-104">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b072-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b072-105">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="2b072-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b072-106">Remarks</span></span>

<span data-ttu-id="2b072-107">Önceki sözdiziminde, *hedef* isteğe bağlıdır ve varsa, özniteliğin uygulandığı program varlığının türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="2b072-107">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="2b072-108">*Target* için geçerli değerler, bu belgenin ilerleyen kısımlarında görüntülenen tabloda gösteriliyor.</span><span class="sxs-lookup"><span data-stu-id="2b072-108">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="2b072-109">*Öznitelik adı* , genellikle öznitelik türü adlarında kullanılan `Attribute` sonek olan veya olmayan geçerli bir öznitelik türünün adı (ad alanları ile nitelenme) anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="2b072-109">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="2b072-110">Örneğin `ObsoleteAttribute` tür bu bağlamda yalnızca `Obsolete` kısaltılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="2b072-110">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="2b072-111">*Bağımsız değişkenler* öznitelik türü için oluşturucunun bağımsız değişkenidir.</span><span class="sxs-lookup"><span data-stu-id="2b072-111">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="2b072-112">Bir özniteliğin parametresiz oluşturucusu varsa, bağımsız değişken listesi ve parantezleri atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="2b072-112">If an attribute has a parameterless constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="2b072-113">Öznitelikler hem Konumsal bağımsız değişkenleri hem de adlandırılmış bağımsız değişkenleri destekler.</span><span class="sxs-lookup"><span data-stu-id="2b072-113">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="2b072-114">*Konumsal bağımsız değişkenler* göründükleri sırada kullanılan bağımsız değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="2b072-114">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="2b072-115">Adlandırılmış bağımsız değişkenler, özniteliğinde ortak özellikler varsa kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2b072-115">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="2b072-116">Bunları, bağımsız değişken listesinde aşağıdaki sözdizimini kullanarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b072-116">You can set these by using the following syntax in the argument list.</span></span>

```fsharp
property-name = property-value
```

<span data-ttu-id="2b072-117">Bu tür özellik başlatmaları herhangi bir sırada olabilir, ancak bunların herhangi bir Konumsal bağımsız değişkeni izlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2b072-117">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="2b072-118">Aşağıda Konumsal bağımsız değişkenleri ve özellik başlatmaları kullanan bir özniteliğe örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2b072-118">The following is an example of an attribute that uses positional arguments and property initializations:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="2b072-119">Bu örnekte, öznitelik `DllImportAttribute`, kısaltılmış biçimde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2b072-119">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="2b072-120">İlk bağımsız değişken bir Konumsal parametredir ve ikincisi bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="2b072-120">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="2b072-121">Öznitelikler, bir *öznitelik* olarak bilinen bir nesnenin bir tür veya diğer program öğesiyle ilişkilendirilmesi için bir .NET programlama yapısıdır.</span><span class="sxs-lookup"><span data-stu-id="2b072-121">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="2b072-122">Bir özniteliğin uygulandığı program öğesi *öznitelik hedefi*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="2b072-122">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="2b072-123">Özniteliği genellikle hedefi hakkında meta veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="2b072-123">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="2b072-124">Bu bağlamda meta veriler, alanları ve üyeleri dışındaki türle ilgili herhangi bir veri olabilir.</span><span class="sxs-lookup"><span data-stu-id="2b072-124">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="2b072-125">İçindeki F# öznitelikler şu programlama yapılarına uygulanabilir: işlevler, Yöntemler, derlemeler, modüller, türler (sınıflar, kayıtlar, yapılar, arabirimler, temsilciler, numaralandırmalar, birleşimler, vb.), oluşturucular, özellikler, alanlar, parametreler, tür parametreleri ve dönüş değerleri.</span><span class="sxs-lookup"><span data-stu-id="2b072-125">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="2b072-126">Sınıfların, ifadelerin veya iş akışı ifadelerinin içindeki `let` bağlamalarda özniteliklere izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="2b072-126">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="2b072-127">Genellikle, öznitelik bildirimi doğrudan öznitelik hedefinin bildiriminden önce görünür.</span><span class="sxs-lookup"><span data-stu-id="2b072-127">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="2b072-128">Birden çok öznitelik bildirimi, aşağıdaki gibi birlikte kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="2b072-128">Multiple attribute declarations can be used together, as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="2b072-129">.NET Reflection kullanarak çalışma zamanında öznitelikleri sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b072-129">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="2b072-130">Bir önceki kod örneğinde olduğu gibi birden çok özniteliği ayrı ayrı bildirebilir veya bağımsız öznitelikleri ve oluşturucuları ayırmak için noktalı virgül kullanırsanız, bunları bir parantez kümesinde bildirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2b072-130">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="2b072-131">Tipik olarak, `Obsolete` özniteliği, güvenlik konuları için öznitelikler, COM desteği öznitelikleri, kod sahipliğiyle ilgili öznitelikler ve bir türün seri hale getirilebilir olup olmadığını belirten öznitelikler bulunur.</span><span class="sxs-lookup"><span data-stu-id="2b072-131">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="2b072-132">Aşağıdaki örnek `Obsolete` özniteliğinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b072-132">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="2b072-133">`assembly` ve `module`öznitelik hedefleri için, öznitelikleri derlemeinizdeki en üst düzey `do` bağlamaya uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="2b072-133">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="2b072-134">Öznitelik bildiriminde `assembly` veya `module` sözcüğünü aşağıdaki gibi ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2b072-134">You can include the word `assembly` or `module` in the attribute declaration, as follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="2b072-135">`do` bağlamaya uygulanan bir özniteliğin öznitelik hedefini atlarsanız, F# derleyici bu öznitelik için anlamlı olan öznitelik hedefini saptamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="2b072-135">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="2b072-136">Birçok öznitelik sınıfı, bu öznitelik için desteklenen olası hedefler hakkında bilgi içeren `System.AttributeUsageAttribute` türünde bir özniteliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2b072-136">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="2b072-137">`System.AttributeUsageAttribute` özniteliğin işlevleri hedef olarak desteklediğini gösteriyorsa, öznitelik programın ana giriş noktasına uygulanacak şekilde alınır.</span><span class="sxs-lookup"><span data-stu-id="2b072-137">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="2b072-138">`System.AttributeUsageAttribute` özniteliğin derlemeleri hedef olarak desteklediğini gösteriyorsa, derleyici özniteliği derlemeye uygulanacak şekilde alır.</span><span class="sxs-lookup"><span data-stu-id="2b072-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="2b072-139">Çoğu öznitelik hem işlevler hem de derlemeler için geçerlidir, ancak oldukları durumlarda özniteliği programın ana işlevine uygulanacak şekilde alınır.</span><span class="sxs-lookup"><span data-stu-id="2b072-139">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="2b072-140">Öznitelik hedefi açıkça belirtilirse, öznitelik belirtilen hedefe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2b072-140">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="2b072-141">Genellikle öznitelik hedefini açıkça belirtmeniz gerekmese de, bir öznitelikte *target* için geçerli değerler, kullanım örnekleri ile birlikte aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2b072-141">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute along with examples of usage are shown in the following table:</span></span>

<table>
  <tr>
    <th><span data-ttu-id="2b072-142">Öznitelik hedefi</span><span class="sxs-lookup"><span data-stu-id="2b072-142">Attribute target</span></span></td>
    <th><span data-ttu-id="2b072-143">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b072-143">Example</span></span></td>
  </tr>
  <tr>
    <td><span data-ttu-id="2b072-144">derleme</span><span class="sxs-lookup"><span data-stu-id="2b072-144">assembly</span></span></td>
    <td><pre><code class="lang-fsharp">[&lt;assembly: AssemblyVersion("1.0.0.0")&gt;]</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="2b072-145">return</span><span class="sxs-lookup"><span data-stu-id="2b072-145">return</span></span></td>
    <td><pre><code class="lang-fsharp">let function1 x : [&lt;return: MyCustomAttributeThatWorksOnReturns&gt;] int = x + 1</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="2b072-146">alan</span><span class="sxs-lookup"><span data-stu-id="2b072-146">field</span></span></td>
    <td><pre><code class="lang-fsharp">[&lt;DefaultValue&gt;] val mutable x: int</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="2b072-147">özellik</span><span class="sxs-lookup"><span data-stu-id="2b072-147">property</span></span></td>
    <td><pre><code class="lang-fsharp">[&lt;Obsolete&gt;] this.MyProperty = x</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="2b072-148">larına</span><span class="sxs-lookup"><span data-stu-id="2b072-148">param</span></span></td>
    <td><pre><code class="lang-fsharp">member this.MyMethod([&lt;Out&gt;] x : ref&lt;int&gt;) = x := 10</code></pre></td>
  </tr>
  <tr>
    <td><span data-ttu-id="2b072-149">tür</span><span class="sxs-lookup"><span data-stu-id="2b072-149">type</span></span></td>
    <td>
        <pre><code class="lang-fsharp">
[&lt;type: StructLayout(LayoutKind.Sequential)&gt;]
type MyStruct =
  struct
    val x : byte
    val y : int
  end</code></pre>
    </td>
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="2b072-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b072-150">See also</span></span>

- [<span data-ttu-id="2b072-151">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="2b072-151">F# Language Reference</span></span>](index.md)
