---
title: ekle - C# Referans
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 323064dcbe7596b5f1d2f0f6aa566b07cee45789
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713805"
---
# <a name="add-c-reference"></a>add (C# Başvurusu)
`add` Bağlamsal anahtar kelime, istemci kodu [etkinliğinize](./event.md)abone olduğunda çağrılan özel bir olay erişimini tanımlamak için kullanılır. Özel `add` bir erişimci sağlıyorsanız, bir [kaldırıcı](./remove.md) da sağlamanız gerekir.  
  
## <a name="example"></a>Örnek  
Aşağıdaki örnekte, özel `add` ve erişimi [kaldıran](./remove.md) bir olay gösterilmektedir. Tam örnek için [arabirim olaylarının nasıl uygulanacağını](../../programming-guide/events/how-to-implement-interface-events.md)görün.
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Genellikle kendi özel olay erişime sahip olanları sağlamanız gerekmez. Bir olayı bildirdiğinizde derleyici tarafından otomatik olarak oluşturulan erişime sahip erişimler çoğu senaryo için yeterlidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../programming-guide/events/index.md)
