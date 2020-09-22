---
title: "'<name>' içinde uygun imzaya sahip erişilebilir bir 'Main' yöntemi bulunamadı"
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6958e778701066760aa74e3b4d566800b7527b76
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871483"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>'\<name>' içinde uygun imzaya sahip erişilebilir bir 'Main' yöntemi bulunamadı

Komut satırı uygulamalarının tanımlanmış olması gerekir `Sub Main` . `Main``Public Shared`bir sınıfta tanımlanmalı veya `Public` bir modülde tanımlanmış gibi bildirilmelidir.  
  
 **Hata kimliği:** BC30737  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- `Public Sub Main`Projeniz için bir yordam tanımlayın. Bunu `Shared` yalnızca bir sınıf içinde tanımlarsanız, ve olarak bildirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir Visual Basic Programının Yapısı](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [Yordamlar](../../programming-guide/language-features/procedures/index.md)
