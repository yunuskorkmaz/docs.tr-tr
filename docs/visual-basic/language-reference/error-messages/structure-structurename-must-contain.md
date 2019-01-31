---
title: "'<structurename>' yapısı en az bir örnek üye değişkeni veya 'Custom' olarak işaretlenmemiş en az bir örnek olay bildirimi içermelidir"
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: a8a85f4f089de9be6f2ecadac05256b30d3014b0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267462"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a>Yapı '\<structurename >' en az bir örnek üye değişkeni veya 'Custom' olarak işaretlenmemiş en az bir örnek olay bildirimi içermelidir
Bir yapı tanımı, herhangi bir paylaşılmayan değişkenler veya paylaşılmayan, özel olmayan olaylar içermez.  
  
 Her yapı bir değişken ya da her belirli bir örneğine (yerine paylaşılmayan) tüm örneklerini topluca uygulandığı bir olay olmalıdır ([paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md)). Paylaşılmayan sabitler, özellikler ve yordamlar bu gereksinimi karşılamıyor. Ayrıca, herhangi bir paylaşılmayan değişkenler ve yalnızca bir paylaşılmayan olay varsa, bu olay olamaz bir `Custom` olay.  
  
 **Hata Kimliği:** BC30941  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   En az bir değişken veya değil olay tanımlama `Shared`. Yalnızca bir olay tanımlarsanız, özel olmayan yanı sıra paylaşılmayan olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yapılar](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Nasıl yapılır: Yapıyı Bildirme](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
