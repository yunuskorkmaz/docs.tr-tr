---
title: Ayrıntılı Sözdizimi
description: F# programlama dilinde ayrıntılı ve hafif sözdizimi arasındaki farkı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 722807695c56beb0d681b95a78ed8cb8c1df3ddf
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463914"
---
# <a name="verbose-syntax"></a>Ayrıntılı Sözdizimi

F# dilinde birçok yapı için iki tür sözdizimi vardır: *ayrıntılı sözdizimi* ve *hafif sözdizimi.* Ayrıntılı sözdizimi yaygın olarak kullanılmaz, ancak girintiye karşı daha az duyarlı olma avantajına sahiptir. Hafif sözdizimi daha kısadır ve girintiyi, " `begin`, `end`, `in`ve benzeri ek anahtar kelimeler yerine, yapıların başlangıcını ve sonunu işaret etmek için kullanır. Varsayılan sözdizimi hafif sözdizimidir. Bu konu, hafif sözdizimi etkinleştirilmemişse F# yapıları için sözdizimini açıklar. Verbose sözdizimi her zaman etkindir, bu nedenle hafif sözdizimini etkinleştirseniz bile, bazı yapılar için verbose sözdizimini kullanmaya devam edebilirsiniz. Yönergeyi `#light "off"` kullanarak hafif sözdizimini devre dışı kullanabilirsiniz.

## <a name="table-of-constructs"></a>Yapılar Tablosu

Aşağıdaki tablo, f# dili için hafif ve ayrıntılı sözdizimini iki form arasında fark olan bağlamlarda gösterir. Bu tabloda, açı&lt;&gt;braketleri ( ) kullanıcı tarafından sağlanan sözdizimi öğelerini içine alıkonacaktır. Bu yapılar içinde kullanılan sözdizimi hakkında daha ayrıntılı bilgi için her dil yapısı için belgelere bakın.

<table>
<tr>
<th>Dil yapısı</th>
<th>Hafif sözdizimi</th>
<th>Verbose sözdizimi</th>
</tr>
<tr>
<td>
bileşik ifadeler
</td>
<td>

```xml
<expression1 />
<expression2 />
```

</td><td>

```fsharp
<expression1>; <expression2>
```

</td>
</tr>
<tr><td>

iç `let` içe bağlamalar

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
<tr><td>ayrımcı birlik</td><td>

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

- [F# Dil Referansı](index.md)
- [Derleyici Yönergeleri](compiler-directives.md)
- [Kod Biçimlendirme Yönergeleri](../style-guide/formatting.md)
