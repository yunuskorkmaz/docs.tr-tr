---
title: Bildirim Bağlamları ve Varsayılan Erişim Düzeyleri
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: 1ba25d830b1e7529bdf09c1195cc1fe7f9b2243b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354098"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Bildirim Bağlamları ve Varsayılan Erişim Düzeyleri (Visual Basic)
Bu konuda, hangi Visual Basic türlerinin diğer türler içinde bildirilebilecek ve belirtilmemişse erişim düzeylerinin varsayılan olarak ne olduğu açıklanmaktadır.  
  
## <a name="declaration-context-levels"></a>Bildirim bağlamı düzeyleri  
 Bir programlama öğesinin *Bildirim bağlamı* , bildirildiği kodun bölgesidir. Bu, genellikle *kapsayan öğe*olarak adlandırılan diğer bir programlama öğesidir.  
  
 Bildirim bağlamlarının düzeyleri şunlardır:  
  
- *Ad alanı düzeyi* — bir kaynak dosya veya ad alanı içinde, ancak bir sınıf, yapı, modül veya arabirim içinde değil  
  
- *Modül düzeyi* — bir sınıf, yapı, modül veya arabirim içinde, ancak yordam veya blok içinde değil  
  
- *Yordam düzeyi* — yordam veya blok içinde (`If` veya `For`gibi)  
  
 Aşağıdaki tabloda, bildirim bağlamlarına bağlı olarak, çeşitli tanımlanmış programlama öğeleri için varsayılan erişim düzeyleri gösterilmektedir.  
  
|Bildirilmeyen öğe|Ad alanı düzeyi|Modül düzeyi|Yordam düzeyi|  
|----------------------|---------------------|------------------|---------------------|  
|Variable ([Dim deyimleri](../../../visual-basic/language-reference/statements/dim-statement.md))|İzin verilmiyor|`Private` (`Structure``Public` `Interface`izin verilmiyor)|`Public`|  
|Sabit ([const ekstresi](../../../visual-basic/language-reference/statements/const-statement.md))|İzin verilmiyor|`Private` (`Structure``Public` `Interface`izin verilmiyor)|`Public`|  
|Sabit Listesi ([enum ekstresi](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
|Class ([sınıf ekstresi](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
|Structure ([Yapı ekstresi](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
|Module ([module ekstresi](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|İzin verilmiyor|İzin verilmiyor|  
|Arabirim ([arabirim ekstresi](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
|PROCEDURE ([Işlev ekstresi](../../../visual-basic/language-reference/statements/function-statement.md), [alt ifade](../../../visual-basic/language-reference/statements/sub-statement.md))|İzin verilmiyor|`Public`|İzin verilmiyor|  
|Dış başvuru ([Declare bildirimi](../../../visual-basic/language-reference/statements/declare-statement.md))|İzin verilmiyor|`Public` (`Interface`izin verilmiyor)|İzin verilmiyor|  
|İşleç ([Işleç ekstresi](../../../visual-basic/language-reference/statements/operator-statement.md))|İzin verilmiyor|`Public` (`Interface` veya `Module`'de izin verilmiyor)|İzin verilmiyor|  
|Property ([özellik ekstresi](../../../visual-basic/language-reference/statements/property-statement.md))|İzin verilmiyor|`Public`|İzin verilmiyor|  
|Varsayılan Özellik ([varsayılan](../../../visual-basic/language-reference/modifiers/default.md))|İzin verilmiyor|`Public` (`Module`izin verilmiyor)|İzin verilmiyor|  
|Event ([olay ekstresi](../../../visual-basic/language-reference/statements/event-statement.md))|İzin verilmiyor|`Public`|İzin verilmiyor|  
|Temsilci ([temsilci ekstresi](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
  
 Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
