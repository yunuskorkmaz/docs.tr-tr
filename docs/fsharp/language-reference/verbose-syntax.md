---
title: Ayrıntılı Sözdizimi (F#)
description: 'F # programlama dilinin ayrıntılı ve basit söz dizimi arasındaki fark hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: b4f2354738da4692cb444e5e7dd9531d80d26664
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45972325"
---
# <a name="verbose-syntax"></a><span data-ttu-id="1a9a9-103">Ayrıntılı Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a9a9-103">Verbose Syntax</span></span>

<span data-ttu-id="1a9a9-104">F # Dili içinde birçok yapıları için kullanılabilir iki tür sözdizimi vardır: *ayrıntılı sözdizimi* ve *basit söz dizimi*.</span><span class="sxs-lookup"><span data-stu-id="1a9a9-104">There are two forms of syntax available for many constructs in the F# language: *verbose syntax* and *lightweight syntax*.</span></span> <span data-ttu-id="1a9a9-105">Ayrıntılı sözdizimi gibi yaygın olarak kullanılmaz, ancak için girinti daha az duyarlı olan, avantajına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="1a9a9-105">The verbose syntax is not as commonly used, but has the advantage of being less sensitive to indentation.</span></span> <span data-ttu-id="1a9a9-106">Basit sözdizimi daha kısadır ve girinti başlangıcını ve bitişini yapıları göstermek için kullandığı yerine ek anahtar sözcükler gibi `begin`, `end`, `in`ve benzeri.</span><span class="sxs-lookup"><span data-stu-id="1a9a9-106">The lightweight syntax is shorter and uses indentation to signal the beginning and end of constructs, rather than additional keywords like `begin`, `end`, `in`, and so on.</span></span> <span data-ttu-id="1a9a9-107">Basit sözdizimi varsayılan sözdizimidir.</span><span class="sxs-lookup"><span data-stu-id="1a9a9-107">The default syntax is the lightweight syntax.</span></span> <span data-ttu-id="1a9a9-108">Basit sözdizimi etkinleştirilmediğinde Bu konu, F # yapılarını sözdizimi açıklar.</span><span class="sxs-lookup"><span data-stu-id="1a9a9-108">This topic describes the syntax for F# constructs when lightweight syntax is not enabled.</span></span> <span data-ttu-id="1a9a9-109">Basit sözdizimi etkinleştirseniz bile bazı yapıları için ayrıntılı sözdizimi hala kullanabilmeniz için ayrıntılı sözdizimi her zaman etkindir.</span><span class="sxs-lookup"><span data-stu-id="1a9a9-109">Verbose syntax is always enabled, so even if you enable lightweight syntax, you can still use verbose syntax for some constructs.</span></span> <span data-ttu-id="1a9a9-110">Kullanarak basit söz dizimi devre dışı bırakabilirsiniz `#light "off"` yönergesi.</span><span class="sxs-lookup"><span data-stu-id="1a9a9-110">You can disable lightweight syntax by using the `#light "off"` directive.</span></span>

## <a name="table-of-constructs"></a><span data-ttu-id="1a9a9-111">Yapıları tablosu</span><span class="sxs-lookup"><span data-stu-id="1a9a9-111">Table of Constructs</span></span>

<span data-ttu-id="1a9a9-112">Aşağıdaki tabloda, F # dil yapılarının basit ve ayrıntılı sözdizimi bağlamlarda gösterilmektedir. iki biçim arasında bir fark olduğunda.</span><span class="sxs-lookup"><span data-stu-id="1a9a9-112">The following table shows the lightweight and verbose syntax for F# language constructs in contexts where there is a difference between the two forms.</span></span> <span data-ttu-id="1a9a9-113">Bu tabloda, açı köşeli ayraçlar (&lt;&gt;) kullanıcı tarafından sağlanan söz dizimi öğeleri alın.</span><span class="sxs-lookup"><span data-stu-id="1a9a9-113">In this table, angle brackets (&lt;&gt;) enclose user-supplied syntax elements.</span></span> <span data-ttu-id="1a9a9-114">Her dil yapısı içinde bu yapıları kullanılan söz dizimi hakkında daha ayrıntılı bilgi için belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="1a9a9-114">Refer to the documentation for each language construct for more detailed information about the syntax used within these constructs.</span></span>

<table>
<tr>
<th><span data-ttu-id="1a9a9-115">Dil yapısı</span><span class="sxs-lookup"><span data-stu-id="1a9a9-115">Language construct</span></span></th>
<th><span data-ttu-id="1a9a9-116">Basit sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a9a9-116">Lightweight syntax</span></span></th>
<th><span data-ttu-id="1a9a9-117">Ayrıntılı sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a9a9-117">Verbose syntax</span></span></th>
</tr>
<tr>
<td>
<span data-ttu-id="1a9a9-118">Bileşik deyimler</span><span class="sxs-lookup"><span data-stu-id="1a9a9-118">compound expressions</span></span>
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


<span data-ttu-id="1a9a9-119">iç içe geçmiş `let` bağlamaları</span><span class="sxs-lookup"><span data-stu-id="1a9a9-119">nested `let` bindings</span></span>

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
<span data-ttu-id="1a9a9-120">kod bloğu</span><span class="sxs-lookup"><span data-stu-id="1a9a9-120">code block</span></span>
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
<tr><td><span data-ttu-id="1a9a9-121">Kaydı</span><span class="sxs-lookup"><span data-stu-id="1a9a9-121">record</span></span>
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
<tr><td><span data-ttu-id="1a9a9-122">sınıf</span><span class="sxs-lookup"><span data-stu-id="1a9a9-122">class</span></span>
</td><td><span data-ttu-id="1a9a9-123">
```
type <class-name>(<params>) = ... ```

</span><span class="sxs-lookup"><span data-stu-id="1a9a9-123">
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
<tr><td><span data-ttu-id="1a9a9-124">yapı</span><span class="sxs-lookup"><span data-stu-id="1a9a9-124">structure</span></span></td><td>

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
<tr><td><span data-ttu-id="1a9a9-125">ayrılmış birleşim</span><span class="sxs-lookup"><span data-stu-id="1a9a9-125">discriminated union</span></span></td><td>

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
<tr><td><span data-ttu-id="1a9a9-126">arabirim</span><span class="sxs-lookup"><span data-stu-id="1a9a9-126">interface</span></span></td><td>

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
<tr><td><span data-ttu-id="1a9a9-127">nesne ifadesi</span><span class="sxs-lookup"><span data-stu-id="1a9a9-127">object expression</span></span></td><td>

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
<tr><td><span data-ttu-id="1a9a9-128">arabirim uygulaması</span><span class="sxs-lookup"><span data-stu-id="1a9a9-128">interface implementation</span></span></td><td>

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
<tr><td><span data-ttu-id="1a9a9-129">tür uzantısı</span><span class="sxs-lookup"><span data-stu-id="1a9a9-129">type extension</span></span></td><td>

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
<tr><td><span data-ttu-id="1a9a9-130">modül</span><span class="sxs-lookup"><span data-stu-id="1a9a9-130">module</span></span></td><td>

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

## <a name="see-also"></a><span data-ttu-id="1a9a9-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a9a9-131">See also</span></span>

- [<span data-ttu-id="1a9a9-132">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="1a9a9-132">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="1a9a9-133">Derleyici Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="1a9a9-133">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="1a9a9-134">Kod Biçimlendirme Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="1a9a9-134">Code Formatting Guidelines</span></span>](code-formatting-guidelines.md)
