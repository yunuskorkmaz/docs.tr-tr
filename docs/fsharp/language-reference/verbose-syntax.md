---
title: Ayrıntılı Sözdizimi
description: 'F # programlama dilinde verbose ve hafif sözdizimi arasındaki farkı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 4e1725b58c8cb67c074ba12fd4ca25ce0c000a1e
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97595183"
---
# <a name="verbose-syntax"></a>Ayrıntılı Sözdizimi

F # dilinde birçok yapı için kullanılabilen iki sözdizimi biçimi vardır: *ayrıntılı sözdizimi* ve *hafif sözdizimi*. Ayrıntılı sözdizimi yaygın olarak kullanılmaz, ancak girintide daha az hassas olmasının avantajına sahiptir. Hafif sözdizimi daha kısadır ve,,, ve gibi ek anahtar sözcükler yerine yapıların başını ve sonunu bildirmek için girinti kullanır `begin` `end` `in` . Varsayılan sözdizimi, hafif sözdizimidir. Bu konu, hafif sözdizimi etkin olmadığında F # yapıları için sözdizimi açıklar. Ayrıntılı sözdizimi her zaman etkindir, bu nedenle basit söz dizimini etkinleştirseniz bile bazı yapılar için ayrıntılı söz dizimi kullanmaya devam edebilirsiniz. Yönergesini kullanarak hafif sözdizimini devre dışı bırakabilirsiniz `#light "off"` .

## <a name="table-of-constructs"></a>Yapılar tablosu

Aşağıdaki tabloda, iki form arasında fark olduğu bağlamlarda F # dil yapıları için hafif ve ayrıntılı sözdizimi gösterilmektedir. Bu tabloda, açılı ayraç ( &lt; &gt; ) Kullanıcı tarafından sağlanan sözdizimi öğelerini kapsar. Bu yapılar içinde kullanılan sözdizimi hakkında daha ayrıntılı bilgi için her dil yapısına yönelik belgelere bakın.

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

```fsharp
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

iç içe `let` bağlamalar

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
<tr><td>kaydet
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

- [F # dil başvurusu](index.md)
- [Derleyici Yönergeleri](compiler-directives.md)
- [Kod Biçimlendirme Yönergeleri](../style-guide/formatting.md)
