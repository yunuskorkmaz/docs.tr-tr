---
title: statik değiştirici - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: b288e57d9241e294a0fa18edafe72eec675327a7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633184"
---
# <a name="static-c-reference"></a>static (C# Başvurusu)

Kullanım `static` belirli bir nesne yerine türün kendisine ait olduğu statik bir üye bildirmek için değiştiricisi. `static` Değiştiricisi sınıflar, alanları, yöntemleri, özellikleri, işleçler, olaylar ve oluşturucular ile kullanılabilir, ancak dizin oluşturucular, bir sonlandırıcı ya da sınıfları dışındaki türler ile kullanılamaz. Daha fazla bilgi için [statik sınıflar ve statik sınıf üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

## <a name="example"></a>Örnek

Aşağıdaki sınıf olarak bildirilir `static` ve yalnızca içeren `static` yöntemleri:

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

Bir sabit değer veya tür bildirimi örtük olarak statik bir üyedir.

Statik bir üyeye bir örnek başvurulamaz. Bunun yerine, bu tür adı ile başvurulur. Örneğin, aşağıdaki sınıf göz önünde bulundurun:

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

Statik bir üyeye başvuruda bulunmak için `x`, tam adı kullanmanız `MyBaseC.MyStruct.x`, üye aynı kapsamdan erişilebilir değilse:

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

Bir sınıf örneği ayrı bir sınıfın tüm örnek alanları kopyasını içerirken, her bir statik alanı yalnızca bir kopyası yoktur.

Kullanmak mümkün değil [bu](this.md) statik yöntemler veya özellik erişimcileri başvurmak için.

Varsa `static` anahtar sözcüğü, bir sınıfa uygulandığında, sınıfın tüm üyeleri statik olmalıdır.

Sınıflar ve statik sınıfların statik oluşturucuları olabilir. Statik oluşturucular arasında belirli bir noktada program başlar ve sınıfın örneği çağrılır.

> [!NOTE]
> `static` Anahtar sözcüğü C++'ta kullanımı daha fazla sınırlı sahiptir. C++ anahtar sözcüğüyle karşılaştırmak için bkz [depolama sınıfları (C++)](/cpp/cpp/storage-classes-cpp#static).

Statik üyeleri göstermek için bir şirket çalışanı temsil eden bir sınıf göz önünde bulundurun. Sınıf sayısı çalışan ve bir alan çalışanların sayısını depolamak için bir yöntem içerdiğini varsayın. Yöntemi hem de alan hiçbir örneği çalışana ait değil. Bunun yerine şirket sınıfa ait. Bu nedenle, statik sınıf üyeleri olarak bildirilmelidir.

## <a name="example"></a>Örnek

Bu örnekte yeni bir çalışanın Kimliğini ve adını okur, çalışan sayacı bir artar ve yeni çalışan ve yeni kaç kişi bilgilerini görüntüler. Kolaylık olması için bu programı klavyeden çalışanların geçerli sayısını okur. Gerçek bir uygulamada, bu bilgileri bir dosyadan okunmalıdır.

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a>Örnek

Bu örnek, henüz bildirilen başka bir statik alan kullanarak statik alanı başlatabilirsiniz, ancak açıkça statik alanı için bir değer atamak kadar sonuçlar tanımsız olacağını gösterir.

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Değiştiriciler](modifiers.md)
- [Statik Sınıflar ve Statik Sınıf Üyeleri](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
