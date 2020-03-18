---
title: yönergeyi kullanarak - C# Referans
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 4f7ddad8c3dc12391ef6bf345a73ebb384400b38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093155"
---
# <a name="using-directive-c-reference"></a>yönergeyi kullanma (C# Reference)

`using` Yönergeüç kullanıma sahiptir:

- Bu ad alanında bir tür kullanımını hak kazanmak zorunda kalmamak için bir ad alanında türlerin kullanımına izin vermek için:

    ```csharp
    using System.Text;
    ```

- Erişimi tür adıyla nitelemek zorunda kalmadan statik üyelere ve iç içe geçmiş türtürlerine erişmenize izin vermek için.

    ```csharp
    using static System.Math;
    ```

    Daha fazla bilgi için statik [yönergeleri kullanarak](using-static.md)bakın.

- Ad alanı veya tür için takma ad oluşturmak için. Buna kullanma *diğer adı yönergesi*denir.

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

Anahtar kelime, dosya ve yazı tipleri gibi <xref:System.IDisposable> nesnelerin doğru şekilde işlenmesini sağlamaya yardımcı olan ifadeleri kullanarak oluşturmak için de kullanılır. *using statements* `using` Daha fazla bilgi için [Bildirim'i kullanma](using-statement.md) bilgisine bakın.

## <a name="using-static-type"></a>Statik türü kullanma

Erişimi tür adıyla nitelemek zorunda kalmadan bir türün statik üyelerine erişebilirsiniz:

```csharp
using static System.Console;
using static System.Math;
class Program
{
    static void Main()
    {
        WriteLine(Sqrt(3*3 + 4*4));
    }
}
```

## <a name="remarks"></a>Açıklamalar

Bir `using` yönergenin kapsamı, görüntülendiği dosyayla sınırlıdır.

Yönerge `using` şu şekilde görünebilir:

- Kaynak kodu dosyasının başında, herhangi bir ad alanı veya tür tanımlarından önce.
- Herhangi bir ad alanında, ancak bu ad alanında bildirilen herhangi bir ad alanı veya türleri önce.

Aksi takdirde, derleyici hatası [CS1529](../../misc/cs1529.md) oluşturulur.

Bir `using` tanımlayıcıyı bir ad alanı veya türe hak kazanmak için bir takma ad yönergesi oluşturun. Herhangi `using` bir yönergede, tam nitelikli ad alanı veya `using` türü, ondan önce gelen yönergelerden bağımsız olarak kullanılmalıdır. Bir yönerge bildiriminde başka `using` bir ad kullanılamaz. `using` Örneğin, aşağıdaki derleyici hatası oluşturur:

```csharp
using s = System.Text;
using s.RegularExpressions; // Generates a compiler error.
```

Ad `using` alanını belirtmek zorunda kalmadan, türleri ad alanında kullanmak için bir yönerge oluşturun. Yönerge, `using` belirttiğiniz ad alanında iç içe olan ad alanlarına erişmenizi sağlamaz.

Ad alanları iki kategoride gelir: kullanıcı tanımlı ve sistem tanımlı. Kullanıcı tanımlı ad alanları, kodunuzda tanımlanan ad alanlarıdır. Sistem tanımlı ad alanlarının listesi [için](../../../../api/index.md)bkz.

## <a name="example-1"></a>Örnek 1

Aşağıdaki örnek, ad alanı için `using` takma adınasıl tanımlanırken kullanılacağını gösterir:

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

Bir diğer ad yönergesi sağ tarafta açık bir genel türü olamaz. Örneğin, bir `List<T>`, bir için bir ' için bir `List<int>`', bir ' için bir ' için bir ' sözcük oluşturamazsınız.

## <a name="example-2"></a>Örnek 2

Aşağıdaki örnek, bir sınıf `using` için `using` bir yönerge ve diğer adnasıl tanımlanabildiğini gösterir:

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için Bkz. [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [yönergeleri kullanma.](~/_csharplang/spec/namespaces.md#using-directives) Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Ad Alanlarını Kullanma](../../programming-guide/namespaces/using-namespaces.md)
- [C# Anahtar Kelimeler](index.md)
- [Ad Alanları](../../programming-guide/namespaces/index.md)
- [Ekstresi'ni kullanma](using-statement.md)
