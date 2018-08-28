---
title: remove (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: 245ef0a16fd2cec2f36c86dd0ac3b8838a76b02e
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999777"
---
# <a name="remove-c-reference"></a>remove (C# Başvurusu)
`remove` Bağlamsal anahtar sözcüğü gelen istemci kodu aboneliği kaldırma çağrılan bir özel olay erişimci tanımlamak için kullanılır, [olay](../../../csharp/language-reference/keywords/event.md). Özel bir sağlarsanız `remove` erişimci gerekir da sağlamanız bir [ekleme](../../../csharp/language-reference/keywords/add.md) erişimcisi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir özel olayla gösterir [ekleme](../../../csharp/language-reference/keywords/add.md) ve `remove` erişimcileri. Tam bir örnek için bkz: [nasıl yapılır: arabirim olaylarını uygulama](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/remove_1.cs)]  
  
 Genellikle kendi özel olay erişimcilerini sağlamanız gerekmez. Olay bildirdiğinizde, derleyici tarafından otomatik olarak oluşturulan erişimcileri, çoğu senaryo için yeterlidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Olaylar](../../../csharp/programming-guide/events/index.md)
