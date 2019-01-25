---
title: Ekle - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: d0eb05b5f7cb2e9ad51fe8787299a51f77ea276e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736909"
---
# <a name="add-c-reference"></a>add (C# Başvurusu)
`add` Bağlamsal anahtar sözcük için istemci kodu abone olduğunda çağrılan bir özel olay erişimci tanımlamak için kullanılır, [olay](../../../csharp/language-reference/keywords/event.md). Özel bir sağlarsanız `add` erişimci gerekir da sağlamanız bir [Kaldır](../../../csharp/language-reference/keywords/remove.md) erişimcisi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, özel bir olayını gösterir `add` ve [Kaldır](../../../csharp/language-reference/keywords/remove.md) erişimcileri. Tam bir örnek için bkz [nasıl yapılır:  Arabirim olaylarını uygulama](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Genellikle kendi özel olay erişimcilerini sağlamanız gerekmez. Olay bildirdiğinizde, derleyici tarafından otomatik olarak oluşturulan erişimcileri, çoğu senaryo için yeterlidir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Olaylar](../../../csharp/programming-guide/events/index.md)
