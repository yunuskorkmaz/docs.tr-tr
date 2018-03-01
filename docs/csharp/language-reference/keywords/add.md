---
title: "add (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cab77ad5a990cf85075455e347a4b1c02645af37
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="add-c-reference"></a>add (C# Başvurusu)
`add` Bağlamsal anahtar sözcüğü için istemci kodu abone olduğunda çağrılan bir özel olay erişimcisi tanımlamak için kullanılır, [olay](../../../csharp/language-reference/keywords/event.md). Özel bir sağlarsanız `add` erişimci de sağlamanız bir [kaldırmak](../../../csharp/language-reference/keywords/remove.md) erişimcisi.  
  
## <a name="example"></a>Örnek  
 Özel sahip bir olay aşağıdaki örnekte `add` ve [kaldırmak](../../../csharp/language-reference/keywords/remove.md) erişimciler. Tam örnek için bkz: [nasıl yapılır: arabirim olaylarını uygulama](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/add_1.cs)]  
  
 Genellikle, kendi özel olay erişimcilerini sağlamanız gerekmez. Bir olay bildirirken derleyici tarafından otomatik olarak oluşturulan erişimciler çoğu senaryoları için yeterlidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olayları](../../../csharp/programming-guide/events/index.md)
