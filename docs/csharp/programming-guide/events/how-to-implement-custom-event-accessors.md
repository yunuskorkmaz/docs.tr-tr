---
title: Özel olay erişimcileri uygulama- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 34e816799f472e8945962e334b9a90b2582e0393
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705359"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Özel olay erişimcileri uygulama (C# Programlama Kılavuzu)
Bir olay, yalnızca içinde bildirildiği sınıftan çağrılabilir olan özel bir çok noktaya yayın temsilcisi türüdür. İstemci kodu olay harekete geçirildiğinde çağrılması gereken bir yönteme başvuru sağlayarak olaya abone olur. Bu yöntemler, olay erişimcilerinin `add` ve `remove`adlandırılmasının dışında, özellik erişimcileri aracılığıyla temsilcinin çağrı listesine eklenir. Çoğu durumda, özel olay erişimcileri sağlamanız gerekmez. Kodunuzda hiçbir özel olay erişimcisi sağlanmadığında, derleyici bunları otomatik olarak ekler. Ancak, bazı durumlarda özel davranış sağlamanız gerekebilir. Bu tür bir durum, [arabirim olaylarının nasıl uygulanacağı](./how-to-implement-interface-events.md)konusunda gösterilmektedir.
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özel ekleme ve kaldırma olay erişimcilerinin nasıl uygulanacağını gösterir. Erişimcilerinin içinde herhangi bir kodu değiştirebilseniz de, yeni bir olay işleyici yöntemi eklemeden veya kaldırmadan önce olayı kilitlemenizi öneririz.  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](./index.md)
- [event](../../language-reference/keywords/event.md)
