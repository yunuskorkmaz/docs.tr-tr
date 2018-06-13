---
title: add (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: c1fa8c130475a67ac175205fe3491a32654ea475
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216036"
---
# <a name="add-c-reference"></a>add (C# Başvurusu)
`add` Bağlamsal anahtar sözcüğü için istemci kodu abone olduğunda çağrılan bir özel olay erişimcisi tanımlamak için kullanılır, [olay](../../../csharp/language-reference/keywords/event.md). Özel bir sağlarsanız `add` erişimci de sağlamanız bir [kaldırmak](../../../csharp/language-reference/keywords/remove.md) erişimcisi.  
  
## <a name="example"></a>Örnek  
 Özel sahip bir olay aşağıdaki örnekte `add` ve [kaldırmak](../../../csharp/language-reference/keywords/remove.md) erişimciler. Tam örnek için bkz: [nasıl yapılır: arabirim olaylarını uygulama](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/add_1.cs)]  
  
 Genellikle, kendi özel olay erişimcilerini sağlamanız gerekmez. Bir olay bildirirken derleyici tarafından otomatik olarak oluşturulan erişimciler çoğu senaryoları için yeterlidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olaylar](../../../csharp/programming-guide/events/index.md)
