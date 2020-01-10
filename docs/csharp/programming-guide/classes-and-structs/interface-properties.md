---
title: Arabirim özellikleri- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: ff892a35f4be6600c00bc0c72c2f789ef6eb4408
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705541"
---
# <a name="interface-properties-c-programming-guide"></a>Arabirim Özellikleri (C# Programlama Kılavuzu)

Özellikler, bir [arabirimde](../../language-reference/keywords/interface.md)bildirilemez. Aşağıda bir arabirim özelliği erişimcisi örneği verilmiştir:

[!code-csharp[csProgGuideProperties#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#14)]

Bir arabirim özelliğinin erişimcisinin gövdesi yok. Bu nedenle, erişimcilerinin amacı, özelliğin okuma-yazma, salt okunurdur veya salt yazılır olduğunu belirtsağlamaktır.

## <a name="example"></a>Örnek

Bu örnekte, `IEmployee` arabirim, bir okuma-yazma özelliğine, `Name`ve salt okunurdur bir özelliğe sahiptir `Counter`. Sınıf `Employee` `IEmployee` arabirimini uygular ve bu iki özelliği kullanır. Program yeni bir çalışanın adını ve geçerli çalışan sayısını okur ve çalışan adını ve hesaplanan çalışan numarasını görüntüler.

Özelliğin, üyenin bildirildiği arabirime başvuruda bulunduğu tam nitelikli adını kullanabilirsiniz. Örneğin:

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

Buna [Açık arabirim uygulama](../interfaces/explicit-interface-implementation.md)adı verilir. Örneğin, sınıfı `Employee` iki arabirimi `ICitizen` ve `IEmployee` ve her iki arabirimde de `Name` özelliği varsa, açık arabirim üye uygulaması gerekli olacaktır. Diğer bir deyişle, aşağıdaki özellik bildirimi:

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

, aşağıdaki bildirim sırasında `IEmployee` arabirimindeki `Name` özelliğini uygular:

[!code-csharp[csProgGuideProperties#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#17)]

`ICitizen` arabirimindeki `Name` özelliğini uygular.

[!code-csharp[csProgGuideProperties#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#15)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a>Örnek çıkış

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Veri Erişimi](./properties.md)
- [Özellikleri Kullanma](./using-properties.md)
- [Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma](../indexers/comparison-between-properties-and-indexers.md)
- [Dizin Oluşturucular](../indexers/index.md)
- [Arabirimler](../interfaces/index.md)
