---
title: Ayrıntılı Sözdizimi (F#)
description: 'F # programlama dilinin ayrıntılı ve basit söz dizimi arasındaki fark hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: e697c6fe619df7ffe12f7d4e2a234a5a5cb401ff
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "50196771"
---
# <a name="verbose-syntax"></a><span data-ttu-id="82f63-103">Ayrıntılı Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82f63-103">Verbose Syntax</span></span>

<span data-ttu-id="82f63-104">F # Dili içinde birçok yapıları için kullanılabilir iki tür sözdizimi vardır: *ayrıntılı sözdizimi* ve *basit söz dizimi*.</span><span class="sxs-lookup"><span data-stu-id="82f63-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="82f63-105">Ayrıntılı sözdizimi gibi yaygın olarak kullanılmaz, ancak için girinti daha az duyarlı olan, avantajına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="82f63-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="82f63-106">Basit sözdizimi daha kısadır ve girinti başlangıcını ve bitişini yapıları göstermek için kullandığı yerine ek anahtar sözcükler gibi `begin`, `end`, `in`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="82f63-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="82f63-107">Basit sözdizimi varsayılan sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="82f63-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="82f63-108">Basit sözdizimi etkinleştirilmediğinde Bu konu, F # yapılarını sözdizimi açıklar.</span><span class="sxs-lookup"><span data-stu-id="82f63-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="82f63-109">Basit sözdizimi etkinleştirseniz bile bazı yapıları için ayrıntılı sözdizimi hala kullanabilmeniz için ayrıntılı sözdizimi her zaman etkindir.</span><span class="sxs-lookup"><span data-stu-id="82f63-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="82f63-110">Kullanarak basit söz dizimi devre dışı bırakabilirsiniz `#light "off"` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="82f63-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="82f63-111">Yapıları tablosu</span><span class="sxs-lookup"><span data-stu-id="82f63-111">Table of Constructs</span></span>

<span data-ttu-id="82f63-112">Aşağıdaki tabloda, F # dil yapılarının basit ve ayrıntılı sözdizimi bağlamlarda gösterilmektedir. iki biçim arasında bir fark olduğunda.</span><span class="sxs-lookup"><span data-stu-id="82f63-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="82f63-113">Bu tabloda, açı köşeli ayraçlar (&lt;&gt;) kullanıcı tarafından sağlanan söz dizimi öğeleri alın.</span><span class="sxs-lookup"><span data-stu-id="82f63-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="82f63-114">Her dil yapısı içinde bu yapıları kullanılan söz dizimi hakkında daha ayrıntılı bilgi için belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="82f63-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="82f63-115">Dil yapısı</span><span class="sxs-lookup"><span data-stu-id="82f63-115">Language construct</span></span></th>
<th><span data-ttu-id="82f63-116">Basit sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82f63-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="82f63-117">Ayrıntılı sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82f63-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="82f63-118">Bileşik deyimler</span><span class="sxs-lookup"><span data-stu-id="82f63-118">compound expressions</span></span>
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

<span data-ttu-id="82f63-119">iç içe geçmiş `let` bağlamaları</span><span class="sxs-lookup"><span data-stu-id="82f63-119">nested `let` bindings</span></span>

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
<span data-ttu-id="82f63-120">kod bloğu</span><span class="sxs-lookup"><span data-stu-id="82f63-120">code block</span></span>
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
<tr><td><span data-ttu-id="82f63-121">Kaydı</span><span class="sxs-lookup"><span data-stu-id="82f63-121">record</span></span>
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
<tr><td><span data-ttu-id="82f63-122">sınıf</span><span class="sxs-lookup"><span data-stu-id="82f63-122">class</span></span>
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
<tr><td><span data-ttu-id="82f63-123">yapı</span><span class="sxs-lookup"><span data-stu-id="82f63-123">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="82f63-124">ayrılmış birleşim</span><span class="sxs-lookup"><span data-stu-id="82f63-124">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="82f63-125">arabirim</span><span class="sxs-lookup"><span data-stu-id="82f63-125">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="82f63-126">nesne ifadesi</span><span class="sxs-lookup"><span data-stu-id="82f63-126">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="82f63-127">arabirim uygulaması</span><span class="sxs-lookup"><span data-stu-id="82f63-127">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="82f63-128">tür uzantısı</span><span class="sxs-lookup"><span data-stu-id="82f63-128">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="82f63-129">modül</span><span class="sxs-lookup"><span data-stu-id="82f63-129">module</span></span></td><td>

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

## <a name="see-also"></a><span data-ttu-id="82f63-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82f63-130">See also</span></span>

- [<span data-ttu-id="82f63-131">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="82f63-131">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="82f63-132">Derleyici Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="82f63-132">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="82f63-133">Kod Biçimlendirme Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="82f63-133">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
