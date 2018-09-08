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
ms.openlocfilehash: aa933e0fc589d0dbfec741e9db7fb11222cfdf38
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193230"
---
# <a name="how-to-raise-and-consume-events"></a>Nasıl yapılır: Olaylar Oluşturma ve Kullanma
Bu konudaki örnekler, olaylarla nasıl gösterir. Örneklerini içerirler <xref:System.EventHandler> temsilcisi, <xref:System.EventHandler%601> temsilci ve olayları verilerle ve Verisiz göstermek için özel bir temsilci.  
  
 Örnekler açıklanan kavramları kullanmaktadır [olayları](../../../docs/standard/events/index.md) makalesi.  
  
## <a name="example"></a>Örnek  
 İlk örnek veri içermeyen bir olay yükseltilip tüketileceğini gösterilmektedir. Adlı bir sınıf içeren `Counter` adlı bir olaya sahip `ThresholdReached`. Sayaç değeri bir eşik değeri değerine eşit veya bu olay tetiklenir. <xref:System.EventHandler> Olay verisi sağlanmadığından temsilcisi olayla ilişkili.  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnek veri sağlayan bir olay yükseltilip tüketileceğini gösterilmektedir. <xref:System.EventHandler%601> Temsilcisi olayla ilişkili ve özel olay veri nesnesinin bir örneği sağlanmıştır.  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>Örnek  
 Sonraki örnek, bir olay için bir temsilcinin nasıl belirtileceğini gösterir. Temsilci adlandırılmış `ThresholdReachedEventHandler`. Bu sadece bir örnektir. Ya da kullanabileceğinizden genellikle, bir olayın bir temsilci bildirmeniz erişiminiz yok <xref:System.EventHandler> veya <xref:System.EventHandler%601> temsilci. Yalnızca kendi sınıfınızı genel türler kullanamayan eski kod için kullanılabilir hale getirme gibi nadir senaryolarda bir temsilci bildirmeniz gerekir.  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../../docs/standard/events/index.md)
