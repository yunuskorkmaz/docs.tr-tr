---
title: statik değiştirici C# başvurusu
ms.date: 01/22/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: e7671e9db488a7b50f4ed736864d6fa8d95eef1a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744666"
---
# <a name="static-c-reference"></a>static (C# Başvurusu)

Belirli bir nesne yerine türüne ait olan statik bir üye bildirmek için `static` değiştiricisini kullanın. `static` değiştiricisi `static` sınıfları bildirmek için kullanılabilir. Sınıflarda, arabirimlerde ve yapılarda `static` değiştiricisini alanlara, yöntemlere, özelliklere, işleçlere, olaylara ve oluşturuculara ekleyebilirsiniz. `static` değiştiricisi Dizin oluşturucular veya sonlandırıcılar ile kullanılamaz. Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example"></a>Örnek

Aşağıdaki sınıf `static` olarak bildirilmiştir ve yalnızca `static` yöntemleri içerir:

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Sabit veya tür bildirimi örtük olarak bir `static` üyesidir. Bir `static` üyesine bir örnek üzerinden başvurulamaz. Bunun yerine tür adı ile başvurulur. Örneğin, aşağıdaki sınıfı göz önünde bulundurun:

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

`static` üye `x`başvurmak için, üyenin aynı kapsamdan erişilebilir olmadığı durumlar `MyBaseC.MyStruct.x`tam adı kullanın:

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Bir sınıf örneği, sınıfının tüm örnek alanlarının ayrı bir kopyasını içerdiğinde, her bir `static` alanın yalnızca bir kopyası vardır.

`static` yöntemlere veya özellik erişimcilerine başvurmak için [`this`](this.md) kullanılması mümkün değildir.

`static` anahtar sözcüğü bir sınıfa uygulanırsa, sınıfın tüm üyeleri `static`olmalıdır.

Sınıflar, arabirimler ve `static` sınıfları `static` oluşturuculara sahip olabilir. `static` Oluşturucusu, programın başladığı ve sınıfın örneği oluşturulan bir noktada çağrılır.

> [!NOTE]
> `static` anahtar sözcüğü, öğesinden daha sınırlı kullanımları vardır C++. Anahtar sözcükle karşılaştırmak için bkz. [Depolama sınıfları (C++).](/cpp/cpp/storage-classes-cpp#static) C++

`static` üyelerini göstermek için, bir şirket çalışanını temsil eden bir sınıf düşünün. Sınıfın çalışanları saymak için bir yöntem ve çalışanların sayısını depolamak için bir alan içerdiğini varsayın. Hem yöntemi hem de alanı bir çalışan örneğine ait değildir. Bunun yerine, çalışanlar sınıfına bir bütün olarak aittir. Sınıfın `static` üyesi olarak bildirilmelidir.

## <a name="example"></a>Örnek

Bu örnek, yeni bir çalışanın adını ve KIMLIĞINI okur, bir çalışan sayacını bir artırır ve yeni çalışana ait bilgileri ve yeni çalışanların sayısını görüntüler. Bu program, klavyeden geçerli çalışan sayısını okur.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a>Örnek

Bu örnek, henüz bildirilmemiş başka bir `static` alanını kullanarak bir `static` alanı başlatabilmeniz gerektiğini gösterir. `static` alana açıkça bir değer atamaz kadar sonuçlar tanımsız olur.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Değiştiriciler](index.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
