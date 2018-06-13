---
title: Ayrıntılı Sözdizimi (F#)
description: 'F # programlama dili ayrıntılı ve basit sözdizimi arasındaki fark hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: b0bed66b4a76c5ab11e6c9e7aaf695f864e74ca0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563790"
---
# <a name="verbose-syntax"></a><span data-ttu-id="fdcf4-103">Ayrıntılı Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdcf4-103">Verbose Syntax</span></span>

<span data-ttu-id="fdcf4-104">F # dilinde birçok yapıları için kullanılabilen iki tür sözdizimi vardır: *ayrıntılı sözdizimi* ve *basit sözdizimi*.</span><span class="sxs-lookup"><span data-stu-id="fdcf4-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="fdcf4-105">Ayrıntılı sözdizimi gibi yaygın olarak kullanılmaz, ancak girintileme için daha az hassas olma avantajına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fdcf4-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="fdcf4-106">Basit sözdizimi daha kısadır ve girinti başlangıcını ve bitişini yapıları sinyal kullanmasını yerine ek anahtar sözcükler gibi `begin`, `end`, `in`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="fdcf4-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="fdcf4-107">Varsayılan sözdizimi basit sözdizimi şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="fdcf4-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="fdcf4-108">Bu konuda, basit sözdizimi etkinleştirilmediğinde F # yapılarını sözdizimi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fdcf4-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="fdcf4-109">Basit sözdizimi bile etkinleştirirseniz, ayrıntılı sözdizimi için bazı yapılar hala kullanabilmeniz için ayrıntılı sözdizimi her zaman etkindir.</span><span class="sxs-lookup"><span data-stu-id="fdcf4-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="fdcf4-110">Kullanarak basit sözdizimi devre dışı bırakabilirsiniz `#light "off"` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="fdcf4-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>


## <a name="table-of-constructs"></a><span data-ttu-id="fdcf4-111">Yapıları tablosu</span><span class="sxs-lookup"><span data-stu-id="fdcf4-111">Table of Constructs</span></span>
<span data-ttu-id="fdcf4-112">Aşağıdaki tabloda, bağlamlarda F # dil yapıları için basit ve ayrıntılı sözdizimi gösterilmektedir iki biçim arasında bir fark olduğu.</span><span class="sxs-lookup"><span data-stu-id="fdcf4-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="fdcf4-113">Bu tabloda, açı köşeli ayraçlar (&lt;&gt;) kullanıcı tarafından sağlanan söz dizimi öğeleri alın.</span><span class="sxs-lookup"><span data-stu-id="fdcf4-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="fdcf4-114">Bu yapıları içinde kullanılan sözdizimi hakkında daha ayrıntılı bilgi için her dil yapısı belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="fdcf4-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>



<table>
<tr>
<th><span data-ttu-id="fdcf4-115">Dil yapısı</span><span class="sxs-lookup"><span data-stu-id="fdcf4-115">Language construct</span></span></th>
<th><span data-ttu-id="fdcf4-116">Basit sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdcf4-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="fdcf4-117">Ayrıntılı sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fdcf4-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="fdcf4-118">Bileşik deyimler</span><span class="sxs-lookup"><span data-stu-id="fdcf4-118">compound expressions</span></span>
</td>
<td>

```xml
<expression1>
<expression2>
```
</td><td>

```
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>


<span data-ttu-id="fdcf4-119">iç içe geçmiş `let` bağlamaları</span><span class="sxs-lookup"><span data-stu-id="fdcf4-119">nested `let` bindings</span></span>

</td><td>
```
let f x =
    let a = 1
    let b = 2
    x + a + b
```

</td><td>

```
let f x =
    let a = 1 in
    let b = 2 in
    x + a + b
```

</td>
</tr>
<tr><td>
<span data-ttu-id="fdcf4-120">kod bloğu</span><span class="sxs-lookup"><span data-stu-id="fdcf4-120">code block</span></span>
</td><td>

```
(
    <expression1>
    <expression2>
)
```

</td><td>

```
begin
    <expression1>;
    <expression2>;
end
```
</td>
</tr>
<tr><td>
`for...do`
</td><td>

```
for counter = start to finish do
    ...
```

</td><td>

```
for counter = start to finish do
    ...
done
```

</td>
</tr>
<tr><td>
`while...do`
</td><td>

```
while <condition> do
    ...
```

</td><td>

```
while <condition> do
    ...
done
```

</td>
</tr>
<tr><td>
`for...in`
</td><td>

```
for var in start .. finish do
    ...
```

</td><td>

```
for var in start .. finish do
    ...
done
```

</td>
</tr>
<tr><td>
`do`
</td><td>

```
do
    ...
```

</td><td>

```
do
    ...
in
```

</td>
</tr>
<tr><td><span data-ttu-id="fdcf4-121">Kayıt</span><span class="sxs-lookup"><span data-stu-id="fdcf4-121">record</span></span>
</td><td>

```
type <record-name> =
    {
        <field-declarations>
    }
    <value-or-member-definitions>
```

</td><td>

```
type <record-name> =
    {
        <field-declarations>
    }
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="fdcf4-122">sınıf</span><span class="sxs-lookup"><span data-stu-id="fdcf4-122">class</span></span>
</td><td><span data-ttu-id="fdcf4-123">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="fdcf4-123">
```
type <class-name>(<params>) = ... ```

</span></span></td><td>

```
type <class-name>(<params>) =
    class
        ...
    end
```
</td>
</tr>
<tr><td><span data-ttu-id="fdcf4-124">yapı</span><span class="sxs-lookup"><span data-stu-id="fdcf4-124">structure</span></span></td><td>

```
[<StructAttribute>]
type <structure-name> =
    ...
```
</td><td>

```
type <structure-name> =
    struct
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="fdcf4-125">ayrılmış birleşim</span><span class="sxs-lookup"><span data-stu-id="fdcf4-125">discriminated union</span></span></td><td>

```
type <union-name> =
    | ...
    | ...
    ...
    <value-or-member definitions>
```
</td><td>

```
type <union-name> =
    | ...
    | ...
    ...
    with
        <value-or-member-definitions>
    end    
```

</td>
</tr>
<tr><td><span data-ttu-id="fdcf4-126">arabirim</span><span class="sxs-lookup"><span data-stu-id="fdcf4-126">interface</span></span></td><td>

```
type <interface-name> =
    ...
```
</td><td>

```
type <interface-name> =
    interface
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="fdcf4-127">nesne ifadesi</span><span class="sxs-lookup"><span data-stu-id="fdcf4-127">object expression</span></span></td><td>

```
{ new <type-name>
    with
        <value-or-member-definitions>
        <interface-implementations>
}
```

</td><td>

```
{ new <type-name>
    with
        <value-or-member-definitions>
    end
    <interface-implementations>
}
```

</td>
</tr>
<tr><td><span data-ttu-id="fdcf4-128">arabirim uygulaması</span><span class="sxs-lookup"><span data-stu-id="fdcf4-128">interface implementation</span></span></td><td>

```
interface <interface-name>
    with
        <value-or-member-definitions>
```

</td><td>

```
interface <interface-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="fdcf4-129">türü uzantısı</span><span class="sxs-lookup"><span data-stu-id="fdcf4-129">type extension</span></span></td><td>

```
type <type-name>
    with
        <value-or-member-definitions>
```

</td><td>

```
type <type-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="fdcf4-130">modül</span><span class="sxs-lookup"><span data-stu-id="fdcf4-130">module</span></span></td><td>

```
module <module-name> =
    ...
```

</td><td>

```
module <module-name> =
    begin
        ...
    end
```

</td>
</tr>
</table>



## <a name="see-also"></a><span data-ttu-id="fdcf4-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fdcf4-131">See Also</span></span>
[<span data-ttu-id="fdcf4-132">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="fdcf4-132">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="fdcf4-133">Derleyici Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="fdcf4-133">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="fdcf4-134">Kod Biçimlendirme Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="fdcf4-134">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
