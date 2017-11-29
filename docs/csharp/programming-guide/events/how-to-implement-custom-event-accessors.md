---
title: "Nasıl yapılır: Özel Olay Erişimcilerini Uygulama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3ff5fedeeaa427bb62991f9b406c167647dc376d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Nasıl yapılır: Özel Olay Erişimcilerini Uygulama (C# Programlama Kılavuzu)
Bir olay bir özel olarak bildirilen için yalnızca gelen sınıfı içinde çağrılabilir çok noktaya yayın temsilci türüdür. İstemci kodu, olay başlatıldığında, çağrılması gereken bir yöntem başvuru sağlayarak olaya abone olur. Bu yöntemler olay erişimcileri adlı dışında bu özellik erişimcisi benzer olay erişimcileri aracılığıyla temsilcinin çağırma listesine eklenir `add` ve `remove`. Çoğu durumda, özel olay erişimcilerini sağlamanız gerekmez. Derleyici hiçbir özel olay erişimcilerini kodunuzda sağlandığında, bunları otomatik olarak eklenir. Ancak, bazı durumlarda özel davranışı sağlamak olabilir. Böyle bir durumda konusunda gösterilen [nasıl yapılır: arabirim olaylarını uygulama](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özel uygulamak gösterilmiştir ekleme ve kaldırma olay erişimcisi. Erişimciler içinde herhangi bir kod yerine kullanabilirsiniz, ancak ekleyin veya yeni bir olay işleyicisi yöntemi kaldırmadan önce olay kilitlemek öneririz.  
  
```  
event EventHandler IDrawingObject.OnDraw  
        {  
            add  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent += value;  
                }  
            }  
            remove  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent -= value;  
                }  
            }  
        }  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olayları](../../../csharp/programming-guide/events/index.md)  
 [Olay](../../../csharp/language-reference/keywords/event.md)
