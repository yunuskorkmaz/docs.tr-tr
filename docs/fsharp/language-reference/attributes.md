---
title: Öznitelikler (F#)
description: 'Nasıl F # öznitelikleri bir programlama yapısı uygulanacak meta verilerini etkinleştir öğrenin.'
keywords: 'Visual f #, f # işlevsel programlama'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 95c001e6-3708-4d04-a850-d855f78eb51e
ms.openlocfilehash: 88098e51d19a86f501c35abe3408524378f147b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="attributes"></a><span data-ttu-id="04f7b-104">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="04f7b-104">Attributes</span></span>

<span data-ttu-id="04f7b-105">Öznitelikleri bir programlama yapısı uygulanacak meta verilerini etkinleştir.</span><span class="sxs-lookup"><span data-stu-id="04f7b-105">Attributes enable metadata to be applied to a programming construct.</span></span>

## <a name="syntax"></a><span data-ttu-id="04f7b-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04f7b-106">Syntax</span></span>

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a><span data-ttu-id="04f7b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04f7b-107">Remarks</span></span>

<span data-ttu-id="04f7b-108">Önceki sözdiziminde *hedef* isteğe bağlıdır ve varsa, öznitelik uygulandığı program varlık türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="04f7b-108">In the previous syntax, the *target* is optional and, if present, specifies the kind of program entity that the attribute applies to.</span></span> <span data-ttu-id="04f7b-109">İçin geçerli değerler *hedef* bu belgenin sonraki bölümlerinde görünür tabloda gösterilen.</span><span class="sxs-lookup"><span data-stu-id="04f7b-109">Valid values for *target* are shown in the table that appears later in this document.</span></span>

<span data-ttu-id="04f7b-110">*Öznitelik adı* geçerli öznitelik türü ile veya olmadan soneki (büyük olasılıkla ad alanları ile tam) adının başvurduğu `Attribute` öznitelik türü adları genellikle kullanılan.</span><span class="sxs-lookup"><span data-stu-id="04f7b-110">The *attribute-name* refers to the name (possibly qualified with namespaces) of a valid attribute type, with or without the suffix `Attribute` that is usually used in attribute type names.</span></span> <span data-ttu-id="04f7b-111">Örneğin, türü `ObsoleteAttribute` henüz için kısaltılmış `Obsolete` bu bağlamda.</span><span class="sxs-lookup"><span data-stu-id="04f7b-111">For example, the type `ObsoleteAttribute` can be shortened to just `Obsolete` in this context.</span></span>

<span data-ttu-id="04f7b-112">*Bağımsız değişkenleri* oluşturucuya öznitelik türü bağımsız değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="04f7b-112">The *arguments* are the arguments to the constructor for the attribute type.</span></span> <span data-ttu-id="04f7b-113">Özniteliğin varsayılan bir oluşturucu varsa, bağımsız değişken listesi ve parantez atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="04f7b-113">If an attribute has a default constructor, the argument list and parentheses can be omitted.</span></span> <span data-ttu-id="04f7b-114">Öznitelikler konumsal bağımsız değişkenler ve adlandırılmış bağımsız değişkenler destekler.</span><span class="sxs-lookup"><span data-stu-id="04f7b-114">Attributes support both positional arguments and named arguments.</span></span> <span data-ttu-id="04f7b-115">*Konumsal bağımsız değişkenleri* göründükleri sırada kullanılan bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="04f7b-115">*Positional arguments* are arguments that are used in the order in which they appear.</span></span> <span data-ttu-id="04f7b-116">Adlandırılmış bağımsız değişkenler özniteliği ortak özellikleri varsa kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="04f7b-116">Named arguments can be used if the attribute has public properties.</span></span> <span data-ttu-id="04f7b-117">Bu bağımsız değişken listesinde aşağıdaki sözdizimini kullanarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04f7b-117">You can set these by using the following syntax in the argument list.</span></span>

```
*property-name* = *property-value*
```

<span data-ttu-id="04f7b-118">Bu tür özelliği başlatmaları herhangi bir sırada olabilir, ancak konumsal herhangi bir bağımsız değişken izlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="04f7b-118">Such property initializations can be in any order, but they must follow any positional arguments.</span></span> <span data-ttu-id="04f7b-119">Konumsal bağımsız değişkenleri ve özellik başlatmaları kullanan bir öznitelik örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="04f7b-119">Following is an example of an attribute that uses positional arguments and property initializations.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

<span data-ttu-id="04f7b-120">Bu örnekte, bir özniteliktir `DllImportAttribute`, burada kısaltılmış formunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="04f7b-120">In this example, the attribute is `DllImportAttribute`, here used in shortened form.</span></span> <span data-ttu-id="04f7b-121">İlk bağımsız değişken konumsal bir parametre ve ikinci bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="04f7b-121">The first argument is a positional parameter and the second is a property.</span></span>

<span data-ttu-id="04f7b-122">Öznitelikleridir olarak bilinen bir nesne sağlayan bir .NET programlama yapısı bir *özniteliği* bir tür veya başka bir program öğesi ile ilişkili olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="04f7b-122">Attributes are a .NET programming construct that enables an object known as an *attribute* to be associated with a type or other program element.</span></span> <span data-ttu-id="04f7b-123">Bir öznitelik uygulanan bir program öğesi olarak bilinen *özniteliği hedef*.</span><span class="sxs-lookup"><span data-stu-id="04f7b-123">The program element to which an attribute is applied is known as the *attribute target*.</span></span> <span data-ttu-id="04f7b-124">Öznitelik, genellikle hedefine hakkındaki meta verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="04f7b-124">The attribute usually contains metadata about its target.</span></span> <span data-ttu-id="04f7b-125">Bu bağlamda herhangi bir veri alanları ve üyeleri dışında türü hakkında meta veri olabilir.</span><span class="sxs-lookup"><span data-stu-id="04f7b-125">In this context, metadata could be any data about the type other than its fields and members.</span></span>

<span data-ttu-id="04f7b-126">F # öznitelikleri aşağıdaki programlama yapıları için uygulanabilir: İşlevler, yöntemleri, derlemeleri, modüller, türleri (sınıfları, kayıtları, yapıları, arabirimler, temsilciler, listeleme, birleşimler vb.), Oluşturucular, özellikler, alanları, parametreleri Tür parametreleri ve dönüş değerleri.</span><span class="sxs-lookup"><span data-stu-id="04f7b-126">Attributes in F# can be applied to the following programming constructs: functions, methods, assemblies, modules, types (classes, records, structures, interfaces, delegates, enumerations, unions, and so on), constructors, properties, fields, parameters, type parameters, and return values.</span></span> <span data-ttu-id="04f7b-127">Öznitelikleri yapılamaz `let` bağlamaları sınıfları, ifadeler veya iş akışı ifadeler içinde.</span><span class="sxs-lookup"><span data-stu-id="04f7b-127">Attributes are not allowed on `let` bindings inside classes, expressions, or workflow expressions.</span></span>

<span data-ttu-id="04f7b-128">Genellikle, doğrudan özniteliği hedef bildiriminden önce özniteliği bildirimi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="04f7b-128">Typically, the attribute declaration appears directly before the declaration of the attribute target.</span></span> <span data-ttu-id="04f7b-129">Birden çok öznitelik bildirimleri kullanılabilir birlikte, aşağıdaki gibi.</span><span class="sxs-lookup"><span data-stu-id="04f7b-129">Multiple attribute declarations can be used together, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

<span data-ttu-id="04f7b-130">.NET yansıma kullanarak çalışma zamanında öznitelikleri sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04f7b-130">You can query attributes at run time by using .NET reflection.</span></span>

<span data-ttu-id="04f7b-131">Önceki kod örneğinde olduğu gibi tek tek, birden çok öznitelik bildirebilir veya aşağıda gösterildiği gibi bir noktalı virgül tek tek özniteliklerini ve Oluşturucular, ayırmak için kullanırsanız bunları köşeli bir dizi bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="04f7b-131">You can declare multiple attributes individually, as in the previous code example, or you can declare them in one set of brackets if you use a semicolon to separate the individual attributes and constructors, as shown here.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

<span data-ttu-id="04f7b-132">Genelde karşılaşılan öznitelikleri yer `Obsolete` öznitelik, öznitelikler için güvenlik konuları öznitelikleri COM desteği, kod sahipliği ilgili öznitelikleri ve bir türü seri hale belirten öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="04f7b-132">Typically encountered attributes include the `Obsolete` attribute, attributes for security considerations, attributes for COM support, attributes that relate to ownership of code, and attributes indicating whether a type can be serialized.</span></span> <span data-ttu-id="04f7b-133">Aşağıdaki örnek kullanımını gösteren `Obsolete` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="04f7b-133">The following example demonstrates the use of the `Obsolete` attribute.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

<span data-ttu-id="04f7b-134">Öznitelik hedefleri için `assembly` ve `module`, öznitelikler için üst düzey uygulama `do` bütünleştirilmiş kodunda bağlama.</span><span class="sxs-lookup"><span data-stu-id="04f7b-134">For the attribute targets `assembly` and `module`, you apply the attributes to a top-level `do` binding in your assembly.</span></span> <span data-ttu-id="04f7b-135">Word içerebilir `assembly` veya `module` şekilde öznitelik bildirimi.</span><span class="sxs-lookup"><span data-stu-id="04f7b-135">You can include the word `assembly` or `module` in the attribute declaration, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

<span data-ttu-id="04f7b-136">Uygulanan bir öznitelik için öznitelik hedef atlarsanız, bir `do` bağlama, F # derleyici bu öznitelik için anlamlı özniteliği hedef belirlemeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="04f7b-136">If you omit the attribute target for an attribute applied to a `do` binding, the F# compiler attempts to determine the attribute target that makes sense for that attribute.</span></span> <span data-ttu-id="04f7b-137">Çok sayıda öznitelik sınıfları türünde bir özniteliği bulunması `System.AttributeUsageAttribute` bu öznitelik için desteklenen olası hedefleri hakkında bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="04f7b-137">Many attribute classes have an attribute of type `System.AttributeUsageAttribute` that includes information about the possible targets supported for that attribute.</span></span> <span data-ttu-id="04f7b-138">Varsa `System.AttributeUsageAttribute` öznitelik hedefleri olarak işlevlerini destekleyen, öznitelik programının ana giriş noktası uygulamak için geçen gösterir.</span><span class="sxs-lookup"><span data-stu-id="04f7b-138">If the `System.AttributeUsageAttribute` indicates that the attribute supports functions as targets, the attribute is taken to apply to the main entry point of the program.</span></span> <span data-ttu-id="04f7b-139">Varsa `System.AttributeUsageAttribute` belirten özniteliği derlemeleri hedefleri olarak destekler, derleyicinin derlemeye uygulamak için özniteliğini alır.</span><span class="sxs-lookup"><span data-stu-id="04f7b-139">If the `System.AttributeUsageAttribute` indicates that the attribute supports assemblies as targets, the compiler takes the attribute to apply to the assembly.</span></span> <span data-ttu-id="04f7b-140">Çoğu öznitelikleri işlevler ve derlemeler için geçerli değildir, ancak burada yaptıkları durumlarda, programın main işlevi uygulamak için öznitelik alınır.</span><span class="sxs-lookup"><span data-stu-id="04f7b-140">Most attributes do not apply to both functions and assemblies, but in cases where they do, the attribute is taken to apply to the program's main function.</span></span> <span data-ttu-id="04f7b-141">Öznitelik, öznitelik hedef açıkça belirtilmediği takdirde, belirtilen hedef uygulanır.</span><span class="sxs-lookup"><span data-stu-id="04f7b-141">If the attribute target is specified explicitly, the attribute is applied to the specified target.</span></span>

<span data-ttu-id="04f7b-142">Genellikle belirtmeniz gerekmez ancak öznitelik hedef açıkça için geçerli değerler *hedef* bir öznitelikte aşağıdaki tabloda, kullanım örnekleri ile birlikte gösterilir.</span><span class="sxs-lookup"><span data-stu-id="04f7b-142">Although you do not usually need to specify the attribute target explicitly, valid values for *target* in an attribute are shown in the following table, along with examples of usage.</span></span>

<table>
  <tr>
    <th><span data-ttu-id="04f7b-143">Öznitelik hedef</span><span class="sxs-lookup"><span data-stu-id="04f7b-143">Attribute target</span></span></td>
    <th><span data-ttu-id="04f7b-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="04f7b-144">Example</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="04f7b-145">derleme</span><span class="sxs-lookup"><span data-stu-id="04f7b-145">assembly</span></span></td>
    <td><span data-ttu-id="04f7b-146">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span><span class="sxs-lookup"><span data-stu-id="04f7b-146">`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="04f7b-147">return</span><span class="sxs-lookup"><span data-stu-id="04f7b-147">return</span></span></td>
    <td><span data-ttu-id="04f7b-148">' function1 izin x: [<return: Obsolete>] int = x + 1'</span><span class="sxs-lookup"><span data-stu-id="04f7b-148">`let function1 x : [<return: Obsolete>] int = x + 1`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="04f7b-149">alan</span><span class="sxs-lookup"><span data-stu-id="04f7b-149">field</span></span></td>
    <td><span data-ttu-id="04f7b-150">' [<field: DefaultValue>] val değişebilir x: int'</span><span class="sxs-lookup"><span data-stu-id="04f7b-150">`[<field: DefaultValue>] val mutable x: int`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="04f7b-151">özellik</span><span class="sxs-lookup"><span data-stu-id="04f7b-151">property</span></span></td>
    <td><span data-ttu-id="04f7b-152">' [<property: Obsolete>] Bu. MyProperty = x'</span><span class="sxs-lookup"><span data-stu-id="04f7b-152">`[<property: Obsolete>] this.MyProperty = x`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="04f7b-153">Param</span><span class="sxs-lookup"><span data-stu-id="04f7b-153">param</span></span></td>
    <td><span data-ttu-id="04f7b-154">' üye bu. MyMethod ([<param: Out>] x: ref<int>) = x: = 10'</span><span class="sxs-lookup"><span data-stu-id="04f7b-154">`member this.MyMethod([<param: Out>] x : ref<int>) = x := 10`</span></span></td> 
  </tr>
  <tr>
    <td><span data-ttu-id="04f7b-155">türü</span><span class="sxs-lookup"><span data-stu-id="04f7b-155">type</span></span></td>
    <td><span data-ttu-id="04f7b-156">
        ```
        [<type: StructLayout(Sequential)>] MyStruct yazın yapısı = x: byte y: int bitiş```
    </span><span class="sxs-lookup"><span data-stu-id="04f7b-156">
        ```
        [<type: StructLayout(Sequential)>] type MyStruct = struct x : byte y : int end ```
    </span></span></td> 
  </tr>
</table>

## <a name="see-also"></a><span data-ttu-id="04f7b-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="04f7b-157">See Also</span></span>

[<span data-ttu-id="04f7b-158">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="04f7b-158">F# Language Reference</span></span>](index.md)
