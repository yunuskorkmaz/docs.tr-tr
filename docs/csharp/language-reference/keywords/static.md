---
title: statik değiştirici C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: cbd0f6b4ef7976ccc2da2a735ccbba2bf23177e4
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422327"
---
# <a name="static-c-reference"></a>static (C# Başvurusu)

Belirli bir nesne yerine türüne ait olan statik bir üye bildirmek için `static` değiştiricisini kullanın. `static` değiştiricisi sınıflar, alanlar, Yöntemler, özellikler, işleçler, olaylar ve oluşturucularla birlikte kullanılabilir, ancak sınıf dışındaki Dizin oluşturucular, sonlandırıcılar veya türler ile kullanılamaz. Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example"></a>Örnek

Aşağıdaki sınıf `static` olarak bildirilmiştir ve yalnızca `static` yöntemleri içerir:

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Sabit veya tür bildirimi örtük olarak statik bir üyedir.

Statik üyeye bir örnek üzerinden başvurulamaz. Bunun yerine tür adı ile başvurulur. Örneğin, aşağıdaki sınıfı göz önünde bulundurun:

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Statik üye `x`başvurmak için, üyenin aynı kapsamdan erişilebilir olmadığı müddetçe, `MyBaseC.MyStruct.x`tam adı kullanın:

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Bir sınıf örneği, sınıfının tüm örnek alanlarının ayrı bir kopyasını içerdiğinde, her statik alanın yalnızca bir kopyası vardır.

Statik yöntemlere veya özellik erişimcilerine başvurmak için [bunu](this.md) kullanmak mümkün değildir.

`static` anahtar sözcüğü bir sınıfa uygulanırsa, sınıfın tüm üyeleri statik olmalıdır.

Sınıflar ve statik sınıfların statik oluşturucuları olabilir. Statik oluşturucular, programın başladığı ve sınıfın örneği oluşturulan bir noktada çağrılır.

> [!NOTE]
> `static` anahtar sözcüğü, öğesinden daha sınırlı kullanımları vardır C++. Anahtar sözcükle karşılaştırmak için bkz. [Depolama sınıfları (C++).](/cpp/cpp/storage-classes-cpp#static) C++

Statik üyeleri göstermek için, bir şirket çalışanını temsil eden bir sınıf düşünün. Sınıfın çalışanları saymak için bir yöntem ve çalışanların sayısını depolamak için bir alan içerdiğini varsayın. Hem yöntem hem de alan herhangi bir örnek çalışana ait değildir. Bunun yerine, şirket sınıfına ait olurlar. Bu nedenle, sınıfın statik üyeleri olarak bildirilmelidir.

## <a name="example"></a>Örnek

Bu örnek, yeni bir çalışanın adını ve KIMLIĞINI okur, bir çalışan sayacını bir artırır ve yeni çalışana ait bilgileri ve yeni çalışanların sayısını görüntüler. Kolaylık olması için, bu program klavyeden geçerli çalışan sayısını okur. Gerçek bir uygulamada, bu bilgiler bir dosyadan okunmalıdır.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a>Örnek

Bu örnek, henüz bildirilmemiş başka bir statik alanı kullanarak bir statik alanı başlatabilmenize karşın, statik alana açıkça bir değer atayana kadar sonuçlar tanımsız olacaktır.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Değiştiriciler](index.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
