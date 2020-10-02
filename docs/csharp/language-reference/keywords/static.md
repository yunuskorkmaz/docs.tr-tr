---
description: statik değiştirici-C# başvurusu
title: statik değiştirici-C# başvurusu
ms.date: 09/25/2020
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: 239163fc2f91ccbfe8b1c111a358db87d36a8308
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654645"
---
# <a name="static-c-reference"></a>static (C# Başvurusu)

Bu sayfa `static` değiştirici anahtar sözcüğünü içerir. `static`Anahtar sözcüğü ayrıca yönergesinin bir parçasıdır [`using static`](using-static.md) .

Belirli bir `static` nesne yerine türüne ait olan statik bir üye bildirmek için değiştiricisini kullanın. `static`Değiştirici, sınıfları bildirmek için kullanılabilir `static` . Sınıflar, arabirimler ve yapılar ' da `static` alanları, yöntemleri, özellikleri, işleçleri, olayları ve oluşturuculara değiştiricisini ekleyebilirsiniz. `static`Değiştirici, Dizin oluşturucular veya sonlandırıcılar ile kullanılamaz. Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

C# 8,0 ' den başlayarak, `static` değiştirici bir [Yerel işleve](../../programming-guide/classes-and-structs/local-functions.md)eklenebilir. Statik bir yerel işlev yerel değişkenler veya örnek durumu yakalayamaz.

C# 9,0 ' den başlayarak `static` bir [lambda ifadesine](../operators/lambda-expressions.md) veya [anonim yönteme](../operators/delegate-operator.md)değiştirici ekleyebilirsiniz. Statik lambda veya anonim yöntem yerel değişkenleri veya örnek durumunu yakalayabilir.

## <a name="example---static-class"></a>Örnek-statik sınıf

Aşağıdaki sınıf olarak bildirilmiştir `static` ve yalnızca `static` yöntemleri içerir:

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Sabit veya tür bildirimi örtük olarak bir `static` üyedir. Bir `static` üyeye bir örnek üzerinden başvurulamaz. Bunun yerine tür adı ile başvurulur. Örneğin, aşağıdaki sınıfı göz önünde bulundurun:

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Üyeye başvurmak için, `static` `x` `MyBaseC.MyStruct.x` üyenin aynı kapsamdan erişilebilir olmadığı durumlar dışında tam adı kullanın:

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Bir sınıf örneği, sınıfının tüm örnek alanlarının ayrı bir kopyasını içerdiğinde, her alanın yalnızca bir kopyası vardır `static` .

[`this`](this.md) `static` Yöntemlere veya özellik erişimcilerine başvurmak için kullanılması mümkün değildir.

`static`Anahtar sözcüğü bir sınıfa uygulanırsa, sınıfın tüm üyeleri olmalıdır `static` .

Sınıflar, arabirimler ve `static` sınıflar oluşturuculara sahip olabilir `static` . Bir `static` Oluşturucu, programın başladığı ve sınıfın örneği oluşturulan bir noktada çağrılır.

> [!NOTE]
> `static`Anahtar sözcüğünün C++ ' dan daha fazla sınırlı kullanımı vardır. C++ anahtar sözcüğüyle karşılaştırmak için bkz. [Depolama sınıfları (c++)](/cpp/cpp/storage-classes-cpp#static).

Üyeleri göstermek için `static` , bir şirket çalışanını temsil eden bir sınıf düşünün. Sınıfın çalışanları saymak için bir yöntem ve çalışanların sayısını depolamak için bir alan içerdiğini varsayın. Hem yöntemi hem de alanı bir çalışan örneğine ait değildir. Bunun yerine, çalışanlar sınıfına bir bütün olarak aittir. `static`Sınıfın üyeleri olarak bildirilmelidir.

## <a name="example---static-field-and-method"></a>Örnek-statik alan ve Yöntem

Bu örnek, yeni bir çalışanın adını ve KIMLIĞINI okur, bir çalışan sayacını bir artırır ve yeni çalışana ait bilgileri ve yeni çalışanların sayısını görüntüler. Bu program, klavyeden geçerli çalışan sayısını okur.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example---static-initialization"></a>Örnek-statik başlatma

Bu örnek, `static` henüz bildirilmemiş olan başka bir alanı kullanarak bir alanı başlatabilmeniz gerektiğini gösterir `static` . Alana açıkça bir değer atanana kadar sonuçlar tanımsız olur `static` .

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Değiştiriciler](index.md)
- [static yönergesini kullanma](using-static.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
