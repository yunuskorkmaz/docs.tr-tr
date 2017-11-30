---
title: "remove (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: remove_CSharpKeyword
helpviewer_keywords: remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 66647dee0c4cc728ae5e19457a4a5ef0e7f72248
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="remove-c-reference"></a>remove (C# Başvurusu)
`remove` Bağlamsal anahtar sözcüğü gelen istemci kodu işlemleri olduğunda çağrılan bir özel olay erişimcisi tanımlamak için kullanılır, [olay](../../../csharp/language-reference/keywords/event.md). Özel bir sağlarsanız `remove` erişimci de sağlamanız bir [ekleme](../../../csharp/language-reference/keywords/add.md) erişimcisi.  
  
## <a name="example"></a>Örnek  
 Özel bir olay aşağıdaki örnekte [ekleme](../../../csharp/language-reference/keywords/add.md) ve `remove` erişimciler. Tam örnek için bkz: [nasıl yapılır: arabirim olaylarını uygulama](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/remove_1.cs)]  
  
 Genellikle, kendi özel olay erişimcilerini sağlamanız gerekmez. Bir olay bildirirken derleyici tarafından otomatik olarak oluşturulan erişimciler çoğu senaryoları için yeterlidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olayları](../../../csharp/programming-guide/events/index.md)
