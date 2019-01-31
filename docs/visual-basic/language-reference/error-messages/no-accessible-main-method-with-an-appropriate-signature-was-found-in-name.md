---
title: "'<name>' içinde uygun imzaya sahip erişilebilir bir 'Main' yöntemi bulunamadı"
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: b3aa66416f0cad6a6fb29a20aa0bca5e3486a18e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275437"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>İçinde uygun imzaya sahip hiçbir erişilebilir 'Main' yöntemi bulunamadı '\<adı >'
Komut satırı uygulamaları olmalıdır bir `Sub Main` tanımlı. `Main` olarak bildirilmelidir `Public Shared` bir sınıf veya olarak tanımlanmışsa `Public` bir modülde tanımlı değilse.  
  
 **Hata Kimliği:** BC30737  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Tanımlayan bir `Public Sub Main` projeniz için yordamı. Olarak bildirin `Shared` bir sınıf içinde tanımlamak ve yalnızca.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic programının yapısı](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
