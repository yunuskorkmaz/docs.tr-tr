---
description: using yönergesi-C# başvurusu
title: using yönergesi-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: f22a67348b19b8c97513ca685b2b10b34b1fd6fd
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141952"
---
# <a name="using-directive-c-reference"></a>using yönergesi (C# Başvurusu)

`using`Yönergesinin üç kullanımı vardır:

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

`using`Anahtar sözcüğü Ayrıca, dosyalar ve yazı tipleri gibi nesnelerin doğru şekilde işlenmesini sağlamaya yardımcı olan *using deyimleri*oluşturmak için de kullanılır <xref:System.IDisposable> . Daha fazla bilgi için bkz. [using deyimleri](using-statement.md) .

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

`using`Yönerge şu şekilde görünebilir:

- Bir kaynak kodu dosyasının başlangıcında, herhangi bir ad alanı veya tür tanımlarından önce.
- Herhangi bir ad alanında, bu ad alanında bildirilmeyen herhangi bir ad alanı veya türden önce.

Aksi halde, derleyici hatası [CS1529](../../misc/cs1529.md) oluşturulur.

Bir `using` tanımlayıcıyı bir ad alanına veya türe göre bulmayı kolaylaştırmak için bir diğer ad yönergesi oluşturun. Herhangi bir `using` yönergede, daha `using` önce gelen yönergelerden bağımsız olarak tam nitelikli ad alanı veya tür kullanılmalıdır. `using`Bir yönergenin bildiriminde diğer ad kullanılamaz `using` . Örneğin, aşağıdakiler bir derleyici hatası oluşturur:

```csharp
using s = System.Text;
using s.RegularExpressions; // Generates a compiler error.
```

Ad `using` alanını belirtmek zorunda kalmadan bir ad alanındaki türleri kullanmak için bir yönerge oluşturun. Bir `using` yönerge, belirttiğiniz ad alanında iç içe yerleştirilmiş herhangi bir ad alanı için erişim sağlamaz.

Ad alanları iki kategoride gelir: Kullanıcı tanımlı ve sistem tanımlı. Kullanıcı tanımlı ad alanları kodunuzda tanımlı ad uzaylardır. Sistem tanımlı ad alanlarının listesi için bkz. [.NET API Browser](../../../../api/index.md).

## <a name="example-1"></a>Örnek 1

Aşağıdaki örnek, `using` bir ad alanı için bir diğer ad tanımlama ve kullanmayı gösterir:

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

Using takma ad yönergesinin sağ tarafta açık genel bir türü olamaz. Örneğin, için bir using diğer adı oluşturamazsınız `List<T>` , ancak bir için bir tane oluşturabilirsiniz `List<int>` .

## <a name="example-2"></a>Örnek 2

Aşağıdaki örnek bir `using` sınıfın bir yönergesinin ve diğer adının nasıl tanımlanacağını göstermektedir `using` :

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [yönergeleri kullanma](~/_csharplang/spec/namespaces.md#using-directives) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Ad alanlarını kullanma](../../programming-guide/namespaces/using-namespaces.md)
- [C# anahtar sözcükleri](index.md)
- [Ad Alanları](../../programming-guide/namespaces/index.md)
- [using Deyimi](using-statement.md)
