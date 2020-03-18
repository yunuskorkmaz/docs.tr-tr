---
title: Arayüz Özellikleri - C# Programlama Kılavuzu
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 5798b80526f34e923e2eaab43847b98f6c64e14b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626626"
---
# <a name="interface-properties-c-programming-guide"></a>Arabirim Özellikleri (C# Programlama Kılavuzu)

Özellikler bir [arabirimde](../../language-reference/keywords/interface.md)bildirilebilir. Aşağıdaki örnek, arabirim özelliği neresini bildiren bir özellik bildirir:

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

Arabirim özellikleri genellikle bir gövdeye sahip değildir. Erişime girenler, özelliğin okuma-yazma, salt okuma veya yalnızca yazma olup olmadığını gösterir. Sınıflar ve structs aksine, bir vücut olmadan erişimini bildiren [otomatik uygulanan bir özellik](auto-implemented-properties.md)bildirmez. C# 8.0 ile başlayarak, bir arabirim özellikleri de dahil olmak üzere üyeler için varsayılan bir uygulama tanımlayabilir. Arabirimler örnek veri alanlarını tanımlamayabileceğinden, arabirimdeki bir özellik için varsayılan bir uygulama tanımlamak nadirdir.

## <a name="example"></a>Örnek

Bu örnekte, `IEmployee` arabirimde okuma-yazma `Name`özelliği ve salt okunur `Counter`özelliği vardır. Sınıf `Employee` `IEmployee` arabirimi uygular ve bu iki özelliği kullanır. Program yeni bir çalışanın adını ve geçerli çalışan sayısını okur ve çalışan adını ve hesaplanan çalışan numarasını görüntüler.

Üyenin beyan edildiği arabirime başvuran özelliğin tam nitelikli adını kullanabilirsiniz. Örnek:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

Önceki [örnek, Açık Arabirim Uygulamasını](../interfaces/explicit-interface-implementation.md)gösterir. Örneğin, `Employee` sınıf iki arabirim `ICitizen` uyguluyorsa `IEmployee` ve her iki `Name` arabirim de özelliğe sahipse, açık arabirim üyesi uygulaması gerekir. Diğer bir şey, aşağıdaki özellik bildirimidir:

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

aşağıdaki bildirimde bulunurken, `Name` özelliği arabirimde uygular: `IEmployee`

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

`Name` özelliği arabirimde `ICitizen` uygular.

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
