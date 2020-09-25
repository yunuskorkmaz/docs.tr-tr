---
title: Özel olay erişimcileri uygulama-C# Programlama Kılavuzu
description: Özel olay erişimcilerinin nasıl uygulanacağını öğrenin. Bir kod örneğine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 41c9bd255bf66cd914982b6044c4acaef66b8fcf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167567"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Özel olay erişimcilerini uygulama (C# Programlama Kılavuzu)

Bir olay, yalnızca içinde bildirildiği sınıftan çağrılabilir olan özel bir çok noktaya yayın temsilcisi türüdür. İstemci kodu olay harekete geçirildiğinde çağrılması gereken bir yönteme başvuru sağlayarak olaya abone olur. Bu yöntemler, olay erişimcileri, ve ' nin adlandırılmasının dışında, özellik erişimcilerine benzeyen, temsilcinin çağrı listesine eklenir `add` `remove` . Çoğu durumda, özel olay erişimcileri sağlamanız gerekmez. Kodunuzda hiçbir özel olay erişimcisi sağlanmadığında, derleyici bunları otomatik olarak ekler. Ancak, bazı durumlarda özel davranış sağlamanız gerekebilir. Bu tür bir durum, [arabirim olaylarının nasıl uygulanacağı](./how-to-implement-interface-events.md)konusunda gösterilmektedir.
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, özel ekleme ve kaldırma olay erişimcilerinin nasıl uygulanacağını gösterir. Erişimcilerinin içinde herhangi bir kodu değiştirebilseniz de, yeni bir olay işleyici yöntemi eklemeden veya kaldırmadan önce olayı kilitlemenizi öneririz.  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](./index.md)
- [olay](../../language-reference/keywords/event.md)
