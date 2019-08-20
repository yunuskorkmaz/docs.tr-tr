---
title: Arabirim özellikleri- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: cdd425970442e284d6fd6488bbb13394c12e939a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596443"
---
# <a name="interface-properties-c-programming-guide"></a>Arabirim Özellikleri (C# Programlama Kılavuzu)
Özellikler, bir [arabirimde](../../language-reference/keywords/interface.md)bildirilemez. Aşağıda bir arabirim özelliği erişimcisi örneği verilmiştir:  
  
 [!code-csharp[csProgGuideProperties#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#14)]  
  
 Bir arabirim özelliğinin erişimcisinin gövdesi yok. Bu nedenle, erişimcilerinin amacı, özelliğin okuma-yazma, salt okunurdur veya salt yazılır olduğunu belirtsağlamaktır.  
  
## <a name="example"></a>Örnek  
 Bu örnekte, arabirimin `IEmployee` okuma-yazma `Name`özelliği, ve `Counter`salt okunurdur özelliği vardır. Sınıfı `Employee` arabirimini`IEmployee` uygular ve bu iki özelliği kullanır. Program yeni bir çalışanın adını ve geçerli çalışan sayısını okur ve çalışan adını ve hesaplanan çalışan numarasını görüntüler.  
  
 Özelliğin, üyenin bildirildiği arabirime başvuruda bulunduğu tam nitelikli adını kullanabilirsiniz. Örneğin:  
  
 [!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]  
  
 Buna [Açık arabirim uygulama](../interfaces/explicit-interface-implementation.md)adı verilir. `Employee` Örneğin, sınıfı `Name` iki `ICitizen` arabirim uygusa ve her iki arabirimde özelliği varsa, açık arabirim üye uygulaması gerekli olacaktır. `IEmployee` Diğer bir deyişle, aşağıdaki özellik bildirimi:  
  
 [!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]  
  
 Aşağıdaki bildirim sırasında, `IEmployee` özelliğiarayüzdeuygular:`Name`  
  
 [!code-csharp[csProgGuideProperties#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#17)]  
  
 `Name` arabirimindeki özelliği`ICitizen` arabirimini uygular.  
  
 [!code-csharp[csProgGuideProperties#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#15)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a>Örnek Çıktı  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özellikler](./properties.md)
- [Özellikleri Kullanma](./using-properties.md)
- [Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma](../indexers/comparison-between-properties-and-indexers.md)
- [Dizin Oluşturucular](../indexers/index.md)
- [Arabirimler](../interfaces/index.md)
