---
title: 'Nasıl yapılır: Olay Özelliklerini Kullanarak Birden Çok Olayı İşleme'
description: Olay özelliklerini kullanarak çok sayıda olayı nasıl işleyeceğinizi öğrenin. Temsilci koleksiyonları, olay anahtarlarını & olay özelliklerini tanımlayın. Add & Remove erişimcisi yöntemlerini uygulayın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- event properties [.NET]
- multiple events [.NET]
- event handling [.NET], with multiple events
- events [.NET], multiple
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
ms.openlocfilehash: 2f2cd2d17df6d4bbbdaec09be27f8e74367d2bcb
ms.sourcegitcommit: 652f62fc8f3ab6a264681b6eb5211ac7539bd115
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105964786"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a>Nasıl yapılır: Olay Özelliklerini Kullanarak Birden Çok Olayı İşleme

Olay özelliklerini kullanmak için olayları oluşturan sınıftaki olay özelliklerini tanımlayın ve ardından olayları işleyen sınıflardaki olay özellikleri için temsilcileri ayarlayın. Bir sınıfta birden çok olay özelliği uygulamak için sınıfı, her olay için tanımlanan temsilciyi dahili olarak depolayıp sürdürmelidir. Her alan-benzeri olay için, karşılık gelen bir yedekleme alanı başvuru türü oluşturulur. Bu, olayların sayısı arttıkça gereksiz ayırmaya yol açabilir. Alternatif olarak, <xref:System.ComponentModel.EventHandlerList> olayları anahtara göre depolayan ortak bir yaklaşım vardır.
  
 Her bir olay için temsilcileri depolamak amacıyla <xref:System.ComponentModel.EventHandlerList> sınıfını kullanabilirsiniz ya da kendi koleksiyonunuzu uygulayabilirsiniz. Koleksiyon sınıfı olay anahtarına bağlı olarak ayarlama, erişme ve olay işleyici temsilcisini almak için yöntemler sağlamak zorundadır. Örneğin, bir <xref:System.Collections.Hashtable> sınıfı kullanabilir veya <xref:System.Collections.DictionaryBase> sınıfından özel bir sınıf türetebilirsiniz. Temsilci koleksiyonuna ait uygulama detaylarının sınıfınızın dışında sunulmasına gerek yoktur.  
  
 Sınıf içindeki her bir olay özelliği, bir ekleme erişimci yöntemi ve bir kaldırma erişimci yöntemi tanımlar. Bir olay özelliğine ait ekleme erişimcisi girdi temsilci örneğini temsilci koleksiyonuna ekler. Bir olay özelliğine ait kaldırma erişimcisi girdi temsilci örneğini temsilci koleksiyondan kaldırır. Olay özellik erişimcileri, örnekleri temsilci koleksiyona eklemek veya kaldırmak için olay özelliği için önceden tanımlanmış anahtarı kullanır.  
  
### <a name="to-handle-multiple-events-using-event-properties"></a>Olay özelliklerini kullanarak birden çok olayı işlemek için  
  
1. Olayları oluşturan sınıf içinde bir temsilci koleksiyon tanımlayın.  
  
2. Her bir olay için bir anahtar tanımlayın.  
  
3. Olayları oluşturan sınıftaki olay özelliklerini tanımlayın.  
  
4. Olay özelliklerine ait ekleme ve kaldırma erişimci yöntemlerini uygulamak için temsilci koleksiyonu kullanın.  
  
5. Olayları işleyen sınıflardaki olay işleyici temsilcilerini eklemek ve kaldırmak için ortak olay özelliklerini kullanın.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki C# örneği her bir olay temsilcisini depolamak için bir `MouseDown` kullanarak `MouseUp` ve <xref:System.ComponentModel.EventHandlerList> olay özelliklerini uygular. Olay özellik yapılarının anahtar kelimeleri kalın yazı tipindedir.  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>
- [Ekinlikler](index.md)
- <xref:System.Web.UI.Control.Events%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme](../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
