---
title: Yapı &#39; &lt;structurename&gt; &#39; en az bir örnek üye değişkeni ya da en az bir örnek olay bildirimi işaretlenmemiş içermelidir &#39;özel&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 85a4babc808e274a99f2c9faf08a02abf8aa4e93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a>Yapı &#39; &lt;structurename&gt; &#39; en az bir örnek üye değişkeni ya da en az bir örnek olay bildirimi işaretlenmemiş içermelidir &#39;özel&#39;
Yapı tanımı, herhangi bir paylaşılmayan değişkenleri veya paylaşılmayan de olayları içermez.  
  
 Her yapısı, değişken veya her belirli bir örneğine (yerine paylaşılmayan) tüm örneklerini topluca uygulandığı olaya sahip olması gerekir ([paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md)). Paylaşılmayan sabitleri, özellikleri ve yordamlar bu gereksinimi karşılamıyor. Ayrıca, paylaşılmayan değişken yok ve yalnızca bir paylaşılmayan olay varsa, bu olay olamaz bir `Custom` olay.  
  
 **Hata Kimliği:** BC30941  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   En az bir değişken veya değil olay tanımlama `Shared`. Yalnızca bir olay tanımlarsanız de yanı sıra paylaşılmayan olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Nasıl yapılır: Bir Yapıyı Bildirme](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
