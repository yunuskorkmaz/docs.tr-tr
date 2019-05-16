---
title: bağlamsal anahtar sözcük - kaldırma C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: b5c604cbb0fef158750b0fa487374ab293795fc7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633717"
---
# <a name="remove-c-reference"></a>remove (C# Başvurusu)

`remove` Bağlamsal anahtar sözcüğü gelen istemci kodu aboneliği kaldırma çağrılan bir özel olay erişimci tanımlamak için kullanılır, [olay](event.md). Özel bir sağlarsanız `remove` erişimci gerekir da sağlamanız bir [ekleme](add.md) erişimcisi.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir özel olayla gösterir [ekleme](add.md) ve `remove` erişimcileri. Tam bir örnek için bkz [nasıl yapılır:  Arabirim olaylarını uygulama](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Genellikle kendi özel olay erişimcilerini sağlamanız gerekmez. Olay bildirdiğinizde, derleyici tarafından otomatik olarak oluşturulan erişimcileri, çoğu senaryo için yeterlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../programming-guide/events/index.md)
