---
title: bağlamsal anahtar sözcüğü kaldırma - C# Reference
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: 8ea3ea1910e28c03b2a894c64415cb2ccff942d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713150"
---
# <a name="remove-c-reference"></a>remove (C# Başvurusu)

`remove` Bağlamsal anahtar kelime, istemci kodu [etkinliğinizden](event.md)aboneliğini kaldırdığında çağrılan özel bir olay erişimini tanımlamak için kullanılır. Özel `remove` bir erişimci sağlıyorsanız, bir [ekleme](add.md) erişimcisi de sağlamanız gerekir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, özel [ekleme](add.md) `remove` ve erişime sahip bir olay gösterilmektedir. Tam örnek için [arabirim olaylarının nasıl uygulanacağını](../../programming-guide/events/how-to-implement-interface-events.md)görün.

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Genellikle kendi özel olay erişime sahip olanları sağlamanız gerekmez. Bir olayı bildirdiğinizde derleyici tarafından otomatik olarak oluşturulan erişime sahip erişimler çoğu senaryo için yeterlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../programming-guide/events/index.md)
