---
title: "Yapı &#39; &lt;structurename&gt;&#39; en az bir örnek üye değişkeni veya işaretlenmemiş en az bir örnek olay bildirimi &#39; içermelidir Özel &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b28dd59271bdaca52072710ea797fae6e9168eab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a>Yapı &#39; &lt;structurename&gt;&#39; en az bir örnek üye değişkeni veya işaretlenmemiş en az bir örnek olay bildirimi &#39; içermelidir Özel &#39;
Yapı tanımı, herhangi bir paylaşılmayan değişkenleri veya paylaşılmayan de olayları içermez.  
  
 Her yapısı, değişken veya her belirli bir örneğine (yerine paylaşılmayan) tüm örneklerini topluca uygulandığı olaya sahip olması gerekir ([paylaşılan](../../../visual-basic/language-reference/modifiers/shared.md)). Paylaşılmayan sabitleri, özellikleri ve yordamlar bu gereksinimi karşılamıyor. Ayrıca, paylaşılmayan değişken yok ve yalnızca bir paylaşılmayan olay varsa, bu olay olamaz bir `Custom` olay.  
  
 **Hata Kimliği:** BC30941  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   En az bir değişken veya değil olay tanımlama `Shared`. Yalnızca bir olay tanımlarsanız de yanı sıra paylaşılmayan olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yapıları](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Nasıl yapılır: bir yapıyı bildirme](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
