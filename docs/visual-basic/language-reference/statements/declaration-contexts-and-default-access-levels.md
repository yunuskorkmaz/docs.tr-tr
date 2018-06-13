---
title: Bildirim Bağlamları ve Varsayılan Erişim Düzeyleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: b30b1068fe662d5f0318a1712dc4690b79bd739d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605452"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Bildirim Bağlamları ve Varsayılan Erişim Düzeyleri (Visual Basic)
Bu konuda, hangi Visual Basic türleri içindeki diğer hangi tür bildirilebilir ve hangi kullanıcıların erişim düzeyleri için varsayılan belirtilmezse açıklanmaktadır.  
  
## <a name="declaration-context-levels"></a>Bildirim içerik düzeyi  
 *Bildirimi bağlam* bir programlama bölge kodu onu bildirilen öğesidir. Bu genellikle sonra adlı başka bir programlama öğesi olur *öğeyi içeren*.  
  
 Bildirim bağlamları düzeyleri şunlardır:  
  
-   *Namespace düzeyi* — bir kaynak dosya veya ad alanı içinde ancak sınıf, yapı, modül veya arabirimi içinde değil  
  
-   *Modül düzeyi* — bir sınıf, yapısı, modül veya arabirimi içinde ancak bir yordam veya bloğu içinde değil  
  
-   *Yordam düzeyi* — bir yordam veya bloğu içinde (gibi `If` veya `For`)  
  
 Aşağıdaki tabloda, bildirim bağlamları bağlı olarak çeşitli bildirilen programlama öğeleri varsayılan erişim düzeyleri gösterilmektedir.  
  
|Bildirilen öğe|Namespace düzeyi|Modül düzeyi|Yordam düzeyi|  
|----------------------|---------------------|------------------|---------------------|  
|Değişken ([Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md))|İzin verilmiyor|`Private` (`Public` içinde `Structure`, içinde izin verilmiyor `Interface`)|`Public`|  
|Sabit ([Const deyimi](../../../visual-basic/language-reference/statements/const-statement.md))|İzin verilmiyor|`Private` (`Public` içinde `Structure`, içinde izin verilmiyor `Interface`)|`Public`|  
|Numaralandırması ([Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
|Sınıf ([sınıf deyimi](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
|Yapısı ([yapısı deyimi](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
|Modül ([Module deyimi](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|İzin verilmiyor|İzin verilmiyor|  
|Arabirim ([arabirim deyimi](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
|Yordam ([işlev ifadesi](../../../visual-basic/language-reference/statements/function-statement.md), [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md))|İzin verilmiyor|`Public`|İzin verilmiyor|  
|Harici başvuru ([Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md))|İzin verilmiyor|`Public` (içinde izin verilmiyor `Interface`)|İzin verilmiyor|  
|İşleç ([Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md))|İzin verilmiyor|`Public` (içinde izin verilmiyor `Interface` veya `Module`)|İzin verilmiyor|  
|Özellik ([Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md))|İzin verilmiyor|`Public`|İzin verilmiyor|  
|Varsayılan özellik ([varsayılan](../../../visual-basic/language-reference/modifiers/default.md))|İzin verilmiyor|`Public` (içinde izin verilmiyor `Module`)|İzin verilmiyor|  
|Olay ([Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md))|İzin verilmiyor|`Public`|İzin verilmiyor|  
|Temsilci ([temsilci deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
  
 Daha fazla bilgi için bkz: [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)
