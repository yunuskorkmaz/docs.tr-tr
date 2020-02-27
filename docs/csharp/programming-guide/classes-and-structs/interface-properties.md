---
title: Arabirim özellikleri- C# Programlama Kılavuzu
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 5798b80526f34e923e2eaab43847b98f6c64e14b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626626"
---
# <a name="interface-properties-c-programming-guide"></a>Arabirim Özellikleri (C# Programlama Kılavuzu)

Özellikler, bir [arabirimde](../../language-reference/keywords/interface.md)bildirilemez. Aşağıdaki örnek bir arabirim özelliği erişimcisi bildirir:

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

Arabirim özelliklerinin genellikle gövdesi yoktur. Erişimciler, özelliğin okuma-yazma, salt okunurdur veya salt yazılır olduğunu gösterir. Sınıfların ve yapıların aksine, bir gövde olmadan erişimcileri bildirmek [Otomatik uygulanan bir özellik](auto-implemented-properties.md)bildirmez. 8,0 ile C# başlayarak, bir arabirim, özellikler dahil olmak üzere Üyeler için varsayılan bir uygulama tanımlayabilir. Arabirimler örnek veri alanlarını tanımlayamadığından, bir arabirimdeki özellik için varsayılan bir uygulamanın tanımlanması nadir bir durumdur.

## <a name="example"></a>Örnek

Bu örnekte, `IEmployee` arabirim, bir okuma-yazma özelliğine, `Name`ve salt okunurdur bir özelliğe sahiptir `Counter`. Sınıf `Employee` `IEmployee` arabirimini uygular ve bu iki özelliği kullanır. Program yeni bir çalışanın adını ve geçerli çalışan sayısını okur ve çalışan adını ve hesaplanan çalışan numarasını görüntüler.

Özelliğin, üyenin bildirildiği arabirime başvuruda bulunduğu tam nitelikli adını kullanabilirsiniz. Örnek:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

Yukarıdaki örnekte [Açık arabirim uygulamaları](../interfaces/explicit-interface-implementation.md)gösterilmektedir. Örneğin, sınıfı `Employee` iki arabirimi `ICitizen` ve `IEmployee` ve her iki arabirimde de `Name` özelliği varsa, açık arabirim üye uygulaması gerekli olacaktır. Diğer bir deyişle, aşağıdaki özellik bildirimi:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

, aşağıdaki bildirim sırasında `IEmployee` arabirimindeki `Name` özelliğini uygular:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

`ICitizen` arabirimindeki `Name` özelliğini uygular.

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a>Örnek çıktı

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özellikler](./properties.md)
- [Özellikleri Kullanma](./using-properties.md)
- [Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma](../indexers/comparison-between-properties-and-indexers.md)
- [Dizin Oluşturucular](../indexers/index.md)
- [Arabirimler](../interfaces/index.md)
