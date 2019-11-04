---
title: Ayrıntılı Sözdizimi
description: F# Programlama dilindeki verbose ve hafif sözdizimi arasındaki farkı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 575585b201acc1366980cfc5cf523c4117259084
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421172"
---
# <a name="verbose-syntax"></a>Ayrıntılı Sözdizimi

F# Dilde birçok yapı için kullanılabilen iki sözdizimi biçimi vardır: *ayrıntılı sözdizimi* ve *hafif sözdizimi*. Ayrıntılı sözdizimi yaygın olarak kullanılmaz, ancak girintide daha az hassas olmasının avantajına sahiptir. Hafif sözdizimi daha kısadır ve `begin`, `end`, `in`vb. gibi ek anahtar sözcükler yerine yapıların başını ve sonunu bildirmek için girinti kullanır. Varsayılan sözdizimi, hafif sözdizimidir. Bu konu, hafif sözdizimi etkin F# olmadığında yapıların sözdizimini açıklar. Ayrıntılı sözdizimi her zaman etkindir, bu nedenle basit söz dizimini etkinleştirseniz bile bazı yapılar için ayrıntılı söz dizimi kullanmaya devam edebilirsiniz. `#light "off"` yönergesini kullanarak hafif sözdizimini devre dışı bırakabilirsiniz.

## <a name="table-of-constructs"></a>Yapılar tablosu

Aşağıdaki tabloda, iki form arasında fark olduğu bağlamlarda F# dil yapıları için hafif ve ayrıntılı sözdizimi gösterilmektedir. Bu tabloda, açılı ayraçlar (&lt;&gt;) Kullanıcı tarafından sağlanan söz dizimi öğelerini kapsar. Bu yapılar içinde kullanılan sözdizimi hakkında daha ayrıntılı bilgi için her dil yapısına yönelik belgelere bakın.

<table>
<tr>
<th>Dil yapısı</th>
<th>Hafif sözdizimi</th>
<th>Ayrıntılı sözdizimi</th>
</tr>
<tr>
<td>
bileşik ifadeler
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

iç içe `let` bağlamaları

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
kod bloğu
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
<tr><td>Kayıtlar
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
<tr><td>sınıf
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
<tr><td>yapı</td><td>

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
<tr><td>ayırt edici bileşim</td><td>

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
<tr><td>arabirim</td><td>

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
<tr><td>nesne ifadesi</td><td>

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
<tr><td>arabirim uygulaması</td><td>

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
<tr><td>tür uzantısı</td><td>

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
<tr><td>modül</td><td>

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

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
- [Derleyici Yönergeleri](compiler-directives.md)
- [Kod Biçimlendirme Yönergeleri](../style-guide/formatting.md)
