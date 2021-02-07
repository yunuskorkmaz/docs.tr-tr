---
description: 'Hakkında daha fazla bilgi edinin: bildirim bağlamları ve varsayılan erişim düzeyleri (Visual Basic)'
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
ms.openlocfilehash: c550db39862fbe9f69e5651b6e9fc7fdfcc88513
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700344"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Bildirim Bağlamları ve Varsayılan Erişim Düzeyleri (Visual Basic)

Bu konuda, hangi Visual Basic türlerinin diğer türler içinde bildirilebilecek ve belirtilmemişse erişim düzeylerinin varsayılan olarak ne olduğu açıklanmaktadır.  
  
## <a name="declaration-context-levels"></a>Bildirim bağlamı düzeyleri  

 Bir programlama öğesinin *Bildirim bağlamı* , bildirildiği kodun bölgesidir. Bu, genellikle *kapsayan öğe* olarak adlandırılan diğer bir programlama öğesidir.  
  
 Bildirim bağlamlarının düzeyleri şunlardır:  
  
- *Ad alanı düzeyi* — bir kaynak dosya veya ad alanı içinde, ancak bir sınıf, yapı, modül veya arabirim içinde değil  
  
- *Modül düzeyi* — bir sınıf, yapı, modül veya arabirim içinde, ancak yordam veya blok içinde değil  
  
- *Yordam düzeyi* — yordam veya blok içinde ( `If` veya gibi `For` )  
  
 Aşağıdaki tabloda, bildirim bağlamlarına bağlı olarak, çeşitli tanımlanmış programlama öğeleri için varsayılan erişim düzeyleri gösterilmektedir.  
  
|Bildirilmeyen öğe|Ad alanı düzeyi|Modül düzeyi|Yordam düzeyi|  
|----------------------|---------------------|------------------|---------------------|  
|Variable ([Dim deyimleri](dim-statement.md))|İzin verilmiyor|`Private` ( `Public` içinde `Structure` , içinde izin verilmiyor `Interface` )|`Public`|  
|Sabit ([const ekstresi](const-statement.md))|İzin verilmiyor|`Private` ( `Public` içinde `Structure` , içinde izin verilmiyor `Interface` )|`Public`|  
|Sabit Listesi ([enum ekstresi](enum-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
|Class ([sınıf ekstresi](class-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
|Structure ([Yapı ekstresi](structure-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
|Module ([module ekstresi](module-statement.md))|`Friend`|İzin verilmiyor|İzin verilmiyor|  
|Arabirim ([arabirim ekstresi](interface-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
|PROCEDURE ([Işlev ekstresi](function-statement.md), [alt ifade](sub-statement.md))|İzin verilmiyor|`Public`|İzin verilmiyor|  
|Dış başvuru ([Declare bildirimi](declare-statement.md))|İzin verilmiyor|`Public` (içinde izin verilmiyor `Interface` )|İzin verilmiyor|  
|İşleç ([Işleç ekstresi](operator-statement.md))|İzin verilmiyor|`Public` (veya içinde izin `Interface` verilmiyor `Module` )|İzin verilmiyor|  
|Property ([özellik ekstresi](property-statement.md))|İzin verilmiyor|`Public`|İzin verilmiyor|  
|Varsayılan Özellik ([varsayılan](../modifiers/default.md))|İzin verilmiyor|`Public` (içinde izin verilmiyor `Module` )|İzin verilmiyor|  
|Event ([olay ekstresi](event-statement.md))|İzin verilmiyor|`Public`|İzin verilmiyor|  
|Temsilci ([temsilci ekstresi](delegate-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
  
 Daha fazla bilgi için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arkadaş](../modifiers/friend.md)
- [Özel](../modifiers/private.md)
- [Genel](../modifiers/public.md)
