---
title: "'<structurename>' yapısı en az bir örnek üye değişkeni veya 'Custom' olarak işaretlenmemiş en az bir örnek olay bildirimi içermelidir"
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: a350940cf052aa8fbee4a1e3c61cbeaa4e37408a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870590"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a>'\<structurename>' yapısı en az bir örnek üye değişkeni veya 'Custom' olarak işaretlenmemiş en az bir örnek olay bildirimi içermelidir

Bir yapı tanımı, paylaşılmayan olmayan değişkenler veya paylaşılmayan özel olmayan olaylar içermez.  
  
 Her yapının, tek tek ([paylaşılan](../modifiers/shared.md)) tüm örnekler yerine her belirli örnek (paylaşılmayan) için geçerli olan bir değişkene veya olaya sahip olması gerekir. Paylaşılmayan sabitler, Özellikler ve yordamlar bu gereksinimi karşılamıyor. Ayrıca, paylaşılmayan değişkenler ve yalnızca paylaşılan olmayan bir olay yoksa, bu olay bir `Custom` olay olamaz.  
  
 **Hata kimliği:** BC30941  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- En az bir değişken veya olmayan olay tanımlayın `Shared` . Yalnızca bir olay tanımlarsanız, özel olmayan ve paylaşılmayan olması gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yapılar](../../programming-guide/language-features/data-types/structures.md)
- [Nasıl yapılır: Yapıyı Bildirme](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Structure Yapısı](../statements/structure-statement.md)
