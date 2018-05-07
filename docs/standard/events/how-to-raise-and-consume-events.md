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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: efeed61c5748a0a6ac731cdcfce1a110982b2941
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-raise-and-consume-events"></a>Nasıl yapılır: Olaylar Oluşturma ve Kullanma
Bu konudaki örnekler olayları ile çalışmak nasıl gösterir. Örnek olarak verilebilir <xref:System.EventHandler> temsilci, <xref:System.EventHandler%601> temsilci ve olayları ile ve veri olmadan göstermek için özel bir temsilci.  
  
 Açıklanan kavramları örneklerde [olayları](../../../docs/standard/events/index.md) makalesi.  
  
## <a name="example"></a>Örnek  
 İlk örnek, yükseltmek ve veri sahip olmayan bir olay kullanma gösterilmektedir. Adlı bir sınıf içeriyor `Counter` adlı bir olay olan `ThresholdReached`. Bir sayaç değeri değerine eşit veya eşik değeri bu olay tetiklenir. <xref:System.EventHandler> Temsilci olduğundan olayla ilişkili olay verisi sağlanır.  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnekte, yükseltmek ve veri sağlayan bir olay kullanma gösterilmektedir. <xref:System.EventHandler%601> Temsilcisidir olayla ilişkili ve özel bir olay veri nesnesi örneği sağlanır.  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnek, bir olay için bir temsilci bildirme gösterilmektedir. Temsilci adlı `ThresholdReachedEventHandler`. Bu yalnızca bir çizimidir. Ya da kullanabileceğinizden genellikle, bir olay için bir temsilci bildirmek elinizde <xref:System.EventHandler> veya <xref:System.EventHandler%601> temsilci. Yalnızca sınıfınız genel türler kullanamazsınız eski kod için kullanılabilir hale getirme gibi nadir senaryolarda bir temsilci bildirmeniz gerekir.  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olaylar](../../../docs/standard/events/index.md)
