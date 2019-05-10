---
title: "'<name>' içinde uygun imzaya sahip erişilebilir bir 'Main' yöntemi bulunamadı"
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 559c905d1e2e2de4500771a93d6116f9630011ba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591994"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>İçinde uygun imzaya sahip hiçbir erişilebilir 'Main' yöntemi bulunamadı '\<adı >'
Komut satırı uygulamaları olmalıdır bir `Sub Main` tanımlı. `Main` olarak bildirilmelidir `Public Shared` bir sınıf veya olarak tanımlanmışsa `Public` bir modülde tanımlı değilse.  
  
 **Hata Kimliği:** BC30737  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Tanımlayan bir `Public Sub Main` projeniz için yordamı. Olarak bildirin `Shared` bir sınıf içinde tanımlamak ve yalnızca.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic programının yapısı](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [Yordamlar](../../../visual-basic/programming-guide/language-features/procedures/index.md)
