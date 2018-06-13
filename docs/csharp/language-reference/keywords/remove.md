---
title: remove (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: 16a169ce1a0ef5dbc29739b2d808acb19737669e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269125"
---
# <a name="remove-c-reference"></a>remove (C# Başvurusu)
`remove` Bağlamsal anahtar sözcüğü gelen istemci kodu işlemleri olduğunda çağrılan bir özel olay erişimcisi tanımlamak için kullanılır, [olay](../../../csharp/language-reference/keywords/event.md). Özel bir sağlarsanız `remove` erişimci de sağlamanız bir [ekleme](../../../csharp/language-reference/keywords/add.md) erişimcisi.  
  
## <a name="example"></a>Örnek  
 Özel bir olay aşağıdaki örnekte [ekleme](../../../csharp/language-reference/keywords/add.md) ve `remove` erişimciler. Tam örnek için bkz: [nasıl yapılır: arabirim olaylarını uygulama](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/remove_1.cs)]  
  
 Genellikle, kendi özel olay erişimcilerini sağlamanız gerekmez. Bir olay bildirirken derleyici tarafından otomatik olarak oluşturulan erişimciler çoğu senaryoları için yeterlidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olaylar](../../../csharp/programming-guide/events/index.md)
