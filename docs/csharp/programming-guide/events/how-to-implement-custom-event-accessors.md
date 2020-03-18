---
title: Özel etkinlik erişime erişimleri nasıl uygulanır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 34e816799f472e8945962e334b9a90b2582e0393
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705359"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Özel olay erişime erişimleri nasıl uygulanır (C# Programlama Kılavuzu)
Olay, yalnızca beyan edildiği sınıfın içinden çağrılabilen özel bir çok noktaya yayın temsilcisi türüdür. İstemci kodu, olay başlatıldığında çağrılması gereken bir yönteme başvuru sağlayarak olaya abone olur. Bu yöntemler, olay erişime girenlerin adlandırılması `add` ve `remove`. Çoğu durumda, özel olay erişime sahip olmak zorunda değildir. Kodunuzda özel olay erişimcisi sağlandığında, derleyici bunları otomatik olarak ekler. Ancak, bazı durumlarda özel davranış sağlamanız gerekebilir. Böyle bir durumda arayüz [olayları nasıl uygulanacağı](./how-to-implement-interface-events.md)konusunda gösterilir.
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özel ekleme ve olay erişime erişime erişiminnasıl kaldırılacağını gösterir. Erişimcilerin içindeki herhangi bir kodu değiştirebiliyor olsanız da, yeni bir olay işleyicisi yöntemi eklemeden veya kaldırmadan önce olayı kilitlemenizi öneririz.  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](./index.md)
- [Olay](../../language-reference/keywords/event.md)
