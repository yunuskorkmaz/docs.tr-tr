---
title: 'Nasıl yapılır: Özel olay erişimcileri uygulama- C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 4eaf8b4c3038d07d5b0fc021e21c7f1a2de85d74
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590534"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Nasıl yapılır: Özel olay erişimcileri uygulama (C# Programlama Kılavuzu)
Bir olay, yalnızca içinde bildirildiği sınıftan çağrılabilir olan özel bir çok noktaya yayın temsilcisi türüdür. İstemci kodu olay harekete geçirildiğinde çağrılması gereken bir yönteme başvuru sağlayarak olaya abone olur. Bu yöntemler, olay erişimcileri, ve `add` `remove`' nin adlandırılmasının dışında, özellik erişimcilerine benzeyen, temsilcinin çağrı listesine eklenir. Çoğu durumda, özel olay erişimcileri sağlamanız gerekmez. Kodunuzda hiçbir özel olay erişimcisi sağlanmadığında, derleyici bunları otomatik olarak ekler. Ancak, bazı durumlarda özel davranış sağlamanız gerekebilir. Böyle bir durum söz konusu [şekilde gösterilmiştir:  Arabirim olaylarını](./how-to-implement-interface-events.md)uygulayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özel ekleme ve kaldırma olay erişimcilerinin nasıl uygulanacağını gösterir. Erişimcilerinin içinde herhangi bir kodu değiştirebilseniz de, yeni bir olay işleyici yöntemi eklemeden veya kaldırmadan önce olayı kilitlemenizi öneririz.  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](./index.md)
- [event](../../language-reference/keywords/event.md)
