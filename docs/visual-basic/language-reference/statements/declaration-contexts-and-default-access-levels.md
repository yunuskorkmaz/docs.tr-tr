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
ms.openlocfilehash: 0d899342383bdf9d262fc9a1ab5e00bbe43066e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638193"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>Bildirim Bağlamları ve Varsayılan Erişim Düzeyleri (Visual Basic)
Bu konuda, hangi Visual Basic türleri, hangi bir tür içinde bildirilebilir ve hangi kullanıcıların erişim düzeylerini varsayılan belirtilmezse açıklanmaktadır.  
  
## <a name="declaration-context-levels"></a>Bildirim bağlam düzeyleri  
 *Bildirim içeriğinin* programlama öğesinin, bildirilen kod bölgedir. Ardından adlı başka bir programlama öğesi, genellikle budur *öğeyi içeren*.  
  
 Bildirim bağlamları düzeyleri şunlardır:  
  
- *Namespace düzeyi* — bir kaynak dosya veya ad alanı içinde ancak bir sınıf, yapı, modül veya arabirimi içinde değil  
  
- *Modül düzeyi* — bir sınıf, yapı, modül veya arabirimi içinde ancak bir yordam veya blok içinde değil  
  
- *Yordam düzeyi* — bir yordam veya blok içinde (gibi `If` veya `For`)  
  
 Aşağıdaki tabloda, bildirim bağlamları bağlı olarak çeşitli bildirilmiş programlama öğesine varsayılan erişim düzeyleri gösterilmektedir.  
  
|Bildirilen öğe|Namespace düzeyi|Modül düzeyi|Yordam düzeyi|  
|----------------------|---------------------|------------------|---------------------|  
|Değişken ([Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md))|İzin verilmiyor|`Private` (`Public` içinde `Structure`, içinde izin verilmiyor `Interface`)|`Public`|  
|Sabit ([Const deyimi](../../../visual-basic/language-reference/statements/const-statement.md))|İzin verilmiyor|`Private` (`Public` içinde `Structure`, içinde izin verilmiyor `Interface`)|`Public`|  
|Sabit listesi ([Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
|Sınıf ([sınıf bildirimi](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
|Yapı ([yapısı deyimi](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
|Modül ([Module deyimi](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|İzin verilmiyor|İzin verilmiyor|  
|Arabirim ([Interface deyimi](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
|Yordam ([işlev bildirimi](../../../visual-basic/language-reference/statements/function-statement.md), [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md))|İzin verilmiyor|`Public`|İzin verilmiyor|  
|Dış başvuru ([Declare Deyimi'nin](../../../visual-basic/language-reference/statements/declare-statement.md))|İzin verilmiyor|`Public` (içinde izin verilmiyor `Interface`)|İzin verilmiyor|  
|İşleç ([Operator deyimi](../../../visual-basic/language-reference/statements/operator-statement.md))|İzin verilmiyor|`Public` (içinde izin verilmiyor `Interface` veya `Module`)|İzin verilmiyor|  
|Özellik ([Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md))|İzin verilmiyor|`Public`|İzin verilmiyor|  
|Varsayılan özellik ([varsayılan](../../../visual-basic/language-reference/modifiers/default.md))|İzin verilmiyor|`Public` (içinde izin verilmiyor `Module`)|İzin verilmiyor|  
|Olay ([Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md))|İzin verilmiyor|`Public`|İzin verilmiyor|  
|Temsilci ([temsilci bildirimi](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|İzin verilmiyor|  
  
 Daha fazla bilgi için [erişim düzeyini Visual Basic'te](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
