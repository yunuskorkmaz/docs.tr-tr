---
description: "C 'de Add anahtar sözcüğünü kullanarak özel olay erişimcileri oluşturmayı öğrenin #"
title: Add-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 520267574320af7f85f2ee07e2778f8bebd01e4b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127015"
---
# <a name="add-c-reference"></a>add (C# Başvurusu)
`add`Bağlamsal anahtar sözcüğü, istemci kodu [olayınız](./event.md)için abone olduğunda çağrılan özel bir olay erişimcisini tanımlamak için kullanılır. Özel bir `add` erişimci sağlarsanız Ayrıca bir [kaldırma](./remove.md) erişimcisi sağlamanız gerekir.  
  
## <a name="example"></a>Örnek  
Aşağıdaki örnek, özel `add` ve [kaldırma](./remove.md) erişimcileri olan bir olay gösterir. Tam örnek için bkz. [arabirim olaylarını uygulama](../../programming-guide/events/how-to-implement-interface-events.md).
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Genellikle kendi özel olay erişimcilerini sağlamanız gerekmez. Bir olay bildirdiğinizde derleyici tarafından otomatik olarak oluşturulan erişimciler çoğu senaryo için yeterlidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ekinlikler](../../programming-guide/events/index.md)
