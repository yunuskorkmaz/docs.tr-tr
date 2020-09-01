---
description: Bağlamsal anahtar sözcüğü kaldır-C# başvurusu
title: Bağlamsal anahtar sözcüğü kaldır-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: a5514e72a04daa1232dbdf9a37813f09de791590
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136960"
---
# <a name="remove-c-reference"></a>remove (C# Başvurusu)

`remove`Bağlam anahtar sözcüğü, istemci kodu [olayınızdan](event.md)aboneliği kaldırılırken çağrılan özel bir olay erişimcisini tanımlamak için kullanılır. Özel bir `remove` erişimci sağlarsanız, bir [Add](add.md) erişimcisi sağlamanız gerekir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, özel [Add](add.md) ve erişimcileri ile bir olay gösterir `remove` . Tam örnek için bkz. [arabirim olaylarını uygulama](../../programming-guide/events/how-to-implement-interface-events.md).

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

Genellikle kendi özel olay erişimcilerini sağlamanız gerekmez. Bir olay bildirdiğinizde derleyici tarafından otomatik olarak oluşturulan erişimciler çoğu senaryo için yeterlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Ekinlikler](../../programming-guide/events/index.md)
