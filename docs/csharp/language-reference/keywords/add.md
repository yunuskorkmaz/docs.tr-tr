---
title: C# başvuru Ekle
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 323064dcbe7596b5f1d2f0f6aa566b07cee45789
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713805"
---
# <a name="add-c-reference"></a>add (C# Başvurusu)
`add` bağlamsal anahtar sözcüğü, istemci kodu [olayınız](./event.md)için abone olduğunda çağrılan özel bir olay erişimcisini tanımlamak için kullanılır. Özel bir `add` erişimcisi sağlarsanız Ayrıca bir [kaldırma](./remove.md) erişimcisi sağlamanız gerekir.  
  
## <a name="example"></a>Örnek  
Aşağıdaki örnek, özel `add` olan bir olayı gösterir ve erişimcileri [kaldırır](./remove.md) . Tam örnek için bkz. [arabirim olaylarını uygulama](../../programming-guide/events/how-to-implement-interface-events.md).
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Genellikle kendi özel olay erişimcilerini sağlamanız gerekmez. Bir olay bildirdiğinizde derleyici tarafından otomatik olarak oluşturulan erişimciler çoğu senaryo için yeterlidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../programming-guide/events/index.md)
