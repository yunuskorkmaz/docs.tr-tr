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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131591"
---
# <a name="how-to-raise-and-consume-events"></a>Nasıl yapılır: Olaylar Oluşturma ve Kullanma
Bu konudaki örnekler, olaylarla nasıl çalışılabildiğini gösterir. Bunlar, verileri <xref:System.EventHandler> olan ve <xref:System.EventHandler%601> olmayan olayları göstermek için temsilci, temsilci ve özel bir temsilci örnekleri içerir.  
  
 Örnekler, [Olaylar](../../../docs/standard/events/index.md) makalesinde açıklanan kavramları kullanır.  
  
## <a name="example"></a>Örnek  
 İlk örnek, veri olmayan bir olayın nasıl yükseltilip tüketilenin gösterilmektedir. Adı geçen bir `Counter` olay olan `ThresholdReached`bir sınıf içerir. Bu olay, sayaç değeri bir eşik değerine eşit olduğunda veya bir eşik değeri aştığında yükseltilir. Olay <xref:System.EventHandler> verisi sağlanamadığı için temsilci olayla ilişkilidir.  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnek, veri sağlayan bir olayın nasıl yükseltilip tüketilenin gösterilmektedir. Temsilci <xref:System.EventHandler%601> olayla ilişkilidir ve özel bir olay veri nesnesi örneği sağlanır.  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnek, bir olay için bir temsilcinin nasıl bildirilen gösterir. Temsilcinin adı `ThresholdReachedEventHandler`. Bu sadece bir illüstrasyon. Genellikle, bir olay için temsilci bildirmeniz gerekmez, çünkü temsilciyi <xref:System.EventHandler> veya <xref:System.EventHandler%601> temsilciyi kullanabilirsiniz. Sınıfınızı genel kullanılamayan eski kodlara kullanılabilir hale getirmek gibi nadir senaryolarda yalnızca bir temsilci bildirmelisiniz.  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../../docs/standard/events/index.md)
