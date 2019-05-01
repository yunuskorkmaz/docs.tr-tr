---
title: "'<structurename>' yapısı en az bir örnek üye değişkeni veya 'Custom' olarak işaretlenmemiş en az bir örnek olay bildirimi içermelidir"
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 598aef3943a53ee6eb97064819c9128de1839f52
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055114"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a>Yapı '\<structurename >' en az bir örnek üye değişkeni veya 'Custom' olarak işaretlenmemiş en az bir örnek olay bildirimi içermelidir
Bir yapı tanımı, herhangi bir paylaşılmayan değişkenler veya paylaşılmayan, özel olmayan olaylar içermez.  
  
 Her yapı bir değişken ya da her belirli bir örneğine (yerine paylaşılmayan) tüm örneklerini topluca uygulandığı bir olay olmalıdır ([paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md)). Paylaşılmayan sabitler, özellikler ve yordamlar bu gereksinimi karşılamıyor. Ayrıca, herhangi bir paylaşılmayan değişkenler ve yalnızca bir paylaşılmayan olay varsa, bu olay olamaz bir `Custom` olay.  
  
 **Hata Kimliği:** BC30941  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- En az bir değişken veya değil olay tanımlama `Shared`. Yalnızca bir olay tanımlarsanız, özel olmayan yanı sıra paylaşılmayan olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nasıl yapılır: Yapıyı Bildirme](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
