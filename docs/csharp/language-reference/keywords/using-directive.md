---
title: using yönergesi- C# başvuru
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: d6e3667861c2b1ac9a84ca7b4e2cabb5784d793d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970051"
---
# <a name="using-directive-c-reference"></a>using yönergesi (C# başvuru)

`using` Yönergesinin üç kullanımı vardır:

- Bir ad alanında türlerin kullanılmasına izin vermek için, bu ad alanında bir tür kullanımını nitelendirmeniz gerekmez:

    ```csharp
    using System.Text;
    ```

- Tür adıyla erişimi nitelemek zorunda kalmadan statik üyelere ve bir tür iç içe türlerine erişmenize izin vermek için.

    ```csharp
    using static System.Math;
    ```

    Daha fazla bilgi için bkz. [using static yönergesi](using-static.md).

- Bir ad alanı veya tür için bir diğer ad oluşturmak için. Bu, *Using alias yönergesi*olarak adlandırılır.

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

Anahtar sözcüğü Ayrıca, dosyalar ve yazı tipleri gibi <xref:System.IDisposable> nesnelerin doğru şekilde işlenmesini sağlamaya yardımcı olan *using deyimleri*oluşturmak için de kullanılır. `using` Daha fazla bilgi için bkz. [using deyimleri](using-statement.md) .

## <a name="using-static-type"></a>Statik tür kullanma

Tür adıyla erişimi nitelemek zorunda kalmadan, bir türün statik üyelerine erişebilirsiniz:

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

Bir `using` yönergenin kapsamı göründüğü dosyayla sınırlıdır.

`using` Yönerge şu şekilde görünebilir:

- Bir kaynak kodu dosyasının başlangıcında, herhangi bir ad alanı veya tür tanımlarından önce.
- Herhangi bir ad alanında, bu ad alanında bildirilmeyen herhangi bir ad alanı veya türden önce.

Aksi halde, derleyici hatası [CS1529](../../misc/cs1529.md) oluşturulur.

Bir tanımlayıcıyı `using` bir ad alanına veya türe göre bulmayı kolaylaştırmak için bir diğer ad yönergesi oluşturun. Herhangi bir `using` yönergede, daha önce gelen `using` yönergelerden bağımsız olarak tam nitelikli ad alanı veya tür kullanılmalıdır. `using` Bir`using` yönergenin bildiriminde diğer ad kullanılamaz. Örneğin, aşağıdakiler bir derleyici hatası oluşturur:

```csharp
using s = System.Text;
using s.RegularExpressions;
```

Ad alanını `using` belirtmek zorunda kalmadan bir ad alanındaki türleri kullanmak için bir yönerge oluşturun. Bir `using` yönerge, belirttiğiniz ad alanında iç içe yerleştirilmiş herhangi bir ad alanı için erişim sağlamaz.

Ad alanları iki kategoride gelir: Kullanıcı tanımlı ve sistem tanımlı. Kullanıcı tanımlı ad alanları kodunuzda tanımlı ad uzaylardır. Sistem tanımlı ad alanlarının listesi için bkz. [.NET API Browser](../../../../api/index.md).

## <a name="example-1"></a>Örnek 1

Aşağıdaki örnek, bir ad alanı için bir `using` diğer ad tanımlama ve kullanmayı gösterir:

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

Using takma ad yönergesinin sağ tarafta açık genel bir türü olamaz. Örneğin, için `List<T>`bir using diğer adı oluşturamazsınız, ancak bir `List<int>`için bir tane oluşturabilirsiniz.

## <a name="example-2"></a>Örnek 2

Aşağıdaki örnek bir sınıfın bir `using` yönergesinin `using` ve diğer adının nasıl tanımlanacağını göstermektedir:

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için bkz. [ C# dil belirtiminde](../language-specification/index.md) [yönergeleri kullanma](~/_csharplang/spec/namespaces.md#using-directives) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Ad Alanlarını Kullanma](../../programming-guide/namespaces/using-namespaces.md)
- [C# Anahtar Sözcükleri](index.md)
- [Ad Alanları](../../programming-guide/namespaces/index.md)
- [using Deyimi](using-statement.md)
