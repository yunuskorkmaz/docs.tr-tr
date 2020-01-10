---
title: Bağlamsal anahtar sözcük C# başvurusunu kaldır
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: 8ea3ea1910e28c03b2a894c64415cb2ccff942d0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713150"
---
# <a name="remove-c-reference"></a>remove (C# Başvurusu)

`remove` bağlamsal anahtar sözcüğü, istemci kodu [olayınızdan](event.md)aboneliği kaldırılırken çağrılan özel bir olay erişimcisini tanımlamak için kullanılır. Özel bir `remove` erişimcisi sağlarsanız, bir [Add](add.md) erişimcisi de sağlamanız gerekir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, özel [Add](add.md) ve `remove` erişimcileri ile bir olay gösterir. Tam örnek için bkz. [arabirim olaylarını uygulama](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Genellikle kendi özel olay erişimcilerini sağlamanız gerekmez. Bir olay bildirdiğinizde derleyici tarafından otomatik olarak oluşturulan erişimciler çoğu senaryo için yeterlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../programming-guide/events/index.md)
