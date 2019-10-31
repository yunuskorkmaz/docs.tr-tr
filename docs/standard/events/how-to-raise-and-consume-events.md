---
title: 'Nasıl yapılır: Olaylar Oluşturma ve Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
ms.openlocfilehash: 256b5ae9ac2145e339136985872dfa5423aca730
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131591"
---
# <a name="how-to-raise-and-consume-events"></a>Nasıl yapılır: Olaylar Oluşturma ve Kullanma
Bu konudaki örneklerde, olaylarla nasıl çalışılacağı gösterilmektedir. Bunlar, verileri içeren ve olmayan olayları göstermek için <xref:System.EventHandler> temsilci, <xref:System.EventHandler%601> temsilcisi ve özel bir temsilci örnekleri içerir.  
  
 Örnekler, [Olaylar](../../../docs/standard/events/index.md) makalesinde açıklanan kavramları kullanır.  
  
## <a name="example"></a>Örnek  
 İlk örnek, verileri olmayan bir olayın nasıl oluşturulduğunu ve kullanıldığını gösterir. `ThresholdReached`adlı bir olaya sahip `Counter` adlı bir sınıf içerir. Bu olay, bir sayaç değeri bir eşik değerini eşitse veya aştığında tetiklenir. Olay verileri sağlanmadığından <xref:System.EventHandler> temsilcisi olayla ilişkilendirilir.  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnekte, veri sağlayan bir olayın nasıl oluşturulduğu ve kullanılacağı gösterilmektedir. <xref:System.EventHandler%601> temsilci olayla ilişkilendirilir ve bir özel olay veri nesnesi örneği sağlanır.  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnekte bir olay için nasıl temsilci bildirireceğiniz gösterilmektedir. Temsilci `ThresholdReachedEventHandler`olarak adlandırılır. Bu yalnızca bir çizim. Genellikle, bir olay için temsilci bildirmeniz gerekmez, çünkü <xref:System.EventHandler> ya da <xref:System.EventHandler%601> temsilcisini kullanabilirsiniz. Bir temsilciyi yalnızca nadir senaryolar halinde bildirmeniz gerekir. Örneğin, sınıfınızın genel türler kullanamaz eski kod için kullanılabilir hale getirilmesi.  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../../docs/standard/events/index.md)
