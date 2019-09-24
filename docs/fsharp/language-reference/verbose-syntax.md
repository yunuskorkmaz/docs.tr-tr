---
title: Ayrıntılı Sözdizimi
description: F# Programlama dilindeki verbose ve hafif sözdizimi arasındaki farkı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: d2459da60bba5d88bd23615c8bf09ba64f7c22c4
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214042"
---
# <a name="verbose-syntax"></a><span data-ttu-id="6af37-103">Ayrıntılı Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6af37-103">Verbose Syntax</span></span>

<span data-ttu-id="6af37-104">F# Dilde birçok yapı için kullanılabilen iki sözdizimi biçimi vardır: *ayrıntılı sözdizimi* ve *hafif sözdizimi*.</span><span class="sxs-lookup"><span data-stu-id="6af37-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="6af37-105">Ayrıntılı sözdizimi yaygın olarak kullanılmaz, ancak girintide daha az hassas olmasının avantajına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6af37-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="6af37-106">Hafif sözdizimi daha kısadır ve `begin` `in`, `end`,, ve gibi ek anahtar sözcükler yerine yapıların başını ve sonunu bildirmek için girinti kullanır.</span><span class="sxs-lookup"><span data-stu-id="6af37-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="6af37-107">Varsayılan sözdizimi, hafif sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="6af37-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="6af37-108">Bu konu, hafif sözdizimi etkin F# olmadığında yapıların sözdizimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6af37-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="6af37-109">Ayrıntılı sözdizimi her zaman etkindir, bu nedenle basit söz dizimini etkinleştirseniz bile bazı yapılar için ayrıntılı söz dizimi kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6af37-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="6af37-110">`#light "off"` Yönergesini kullanarak hafif sözdizimini devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6af37-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="6af37-111">Yapılar tablosu</span><span class="sxs-lookup"><span data-stu-id="6af37-111">Table of Constructs</span></span>

<span data-ttu-id="6af37-112">Aşağıdaki tabloda, iki form arasında fark olduğu bağlamlarda F# dil yapıları için hafif ve ayrıntılı sözdizimi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6af37-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="6af37-113">Bu tabloda, açılı ayraç (&lt;&gt;) Kullanıcı tarafından sağlanan sözdizimi öğelerini kapsar.</span><span class="sxs-lookup"><span data-stu-id="6af37-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="6af37-114">Bu yapılar içinde kullanılan sözdizimi hakkında daha ayrıntılı bilgi için her dil yapısına yönelik belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="6af37-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="6af37-115">Dil yapısı</span><span class="sxs-lookup"><span data-stu-id="6af37-115">Language construct</span></span></th>
<th><span data-ttu-id="6af37-116">Hafif sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6af37-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="6af37-117">Ayrıntılı sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6af37-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="6af37-118">bileşik ifadeler</span><span class="sxs-lookup"><span data-stu-id="6af37-118">compound expressions</span></span>
</td>
<td>

```xml
<expression1>
<expression2>
```

</td><td>

```fsharp
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>

<span data-ttu-id="6af37-119">iç `let` içe bağlamalar</span><span class="sxs-lookup"><span data-stu-id="6af37-119">nested `let` bindings</span></span>

</td><td>

```fsharp
let f x =
    let a = 1
    let b = 2
    x + a + b
```

</td><td>

```fsharp
let f x =
    let a = 1 in
    let b = 2 in
    x + a + b
```

</td>
</tr>
<tr><td>
<span data-ttu-id="6af37-120">kod bloğu</span><span class="sxs-lookup"><span data-stu-id="6af37-120">code block</span></span>
</td><td>

```fsharp
(
    <expression1>
    <expression2>
)
```

</td><td>

```fsharp
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

```fsharp
for counter = start to finish do
    ...
```

</td><td>

```fsharp
for counter = start to finish do
    ...
done
```

</td>
</tr>
<tr><td>
`while...do`
</td><td>

```fsharp
while <condition> do
    ...
```

</td><td>

```fsharp
while <condition> do
    ...
done
```

</td>
</tr>
<tr><td>
`for...in`
</td><td>

```fsharp
for var in start .. finish do
    ...
```

</td><td>

```fsharp
for var in start .. finish do
    ...
done
```

</td>
</tr>
<tr><td>
`do`
</td><td>

```fsharp
do
    ...
```

</td><td>

```fsharp
do
    ...
in
```

</td>
</tr>
<tr><td><span data-ttu-id="6af37-121">record</span><span class="sxs-lookup"><span data-stu-id="6af37-121">record</span></span>
</td><td>

```fsharp
type <record-name> =
    {
        <field-declarations>
    }
    <value-or-member-definitions>
```

</td><td>

```fsharp
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
<tr><td><span data-ttu-id="6af37-122">sınıf</span><span class="sxs-lookup"><span data-stu-id="6af37-122">class</span></span>
</td><td>

```fsharp
type <class-name>(<params>) =
    ...
```

</td><td>

```fsharp
type <class-name>(<params>) =
    class
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="6af37-123">yapı</span><span class="sxs-lookup"><span data-stu-id="6af37-123">structure</span></span></td><td>

```fsharp
[<StructAttribute>]
type <structure-name> =
    ...
```

</td><td>

```fsharp
type <structure-name> =
    struct
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="6af37-124">ayırt edici bileşim</span><span class="sxs-lookup"><span data-stu-id="6af37-124">discriminated union</span></span></td><td>

```fsharp
type <union-name> =
    | ...
    | ...
    ...
    <value-or-member definitions>
```

</td><td>

```fsharp
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
<tr><td><span data-ttu-id="6af37-125">arabirim</span><span class="sxs-lookup"><span data-stu-id="6af37-125">interface</span></span></td><td>

```fsharp
type <interface-name> =
    ...
```

</td><td>

```fsharp
type <interface-name> =
    interface
        ...
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="6af37-126">nesne ifadesi</span><span class="sxs-lookup"><span data-stu-id="6af37-126">object expression</span></span></td><td>

```fsharp
{ new <type-name>
    with
        <value-or-member-definitions>
        <interface-implementations>
}
```

</td><td>

```fsharp
{ new <type-name>
    with
        <value-or-member-definitions>
    end
    <interface-implementations>
}
```

</td>
</tr>
<tr><td><span data-ttu-id="6af37-127">arabirim uygulaması</span><span class="sxs-lookup"><span data-stu-id="6af37-127">interface implementation</span></span></td><td>

```fsharp
interface <interface-name>
    with
        <value-or-member-definitions>
```

</td><td>

```fsharp
interface <interface-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="6af37-128">tür uzantısı</span><span class="sxs-lookup"><span data-stu-id="6af37-128">type extension</span></span></td><td>

```fsharp
type <type-name>
    with
        <value-or-member-definitions>
```

</td><td>

```fsharp
type <type-name>
    with
        <value-or-member-definitions>
    end
```

</td>
</tr>
<tr><td><span data-ttu-id="6af37-129">modül</span><span class="sxs-lookup"><span data-stu-id="6af37-129">module</span></span></td><td>

```fsharp
module <module-name> =
    ...
```

</td><td>

```fsharp
module <module-name> =
    begin
        ...
    end
```

</td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="6af37-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6af37-130">See also</span></span>

- [<span data-ttu-id="6af37-131">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="6af37-131">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="6af37-132">Derleyici Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6af37-132">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="6af37-133">Kod Biçimlendirme Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6af37-133">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
