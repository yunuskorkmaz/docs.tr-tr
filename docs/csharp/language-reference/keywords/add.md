---
title: C# başvuru Ekle
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 1cf82e3d048e465d533e87dc639a13071b41544a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606046"
---
# <a name="add-c-reference"></a>add (C# Başvurusu)
Bağlamsal `add` anahtar sözcüğü, istemci kodu olayınız için abone olduğunda çağrılan özel bir olay erişimcisini tanımlamak için kullanılır [](./event.md). Özel `add` bir erişimci sağlarsanız Ayrıca bir [kaldırma](./remove.md) erişimcisi sağlamanız gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özel `add` ve [kaldırma](./remove.md) erişimcileri olan bir olay gösterir. Tam örnek için bkz [. nasıl yapılır:  Arabirim olaylarını](../../programming-guide/events/how-to-implement-interface-events.md)uygulayın.  
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Genellikle kendi özel olay erişimcilerini sağlamanız gerekmez. Bir olay bildirdiğinizde derleyici tarafından otomatik olarak oluşturulan erişimciler çoğu senaryo için yeterlidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../programming-guide/events/index.md)
