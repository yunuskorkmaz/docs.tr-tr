---
description: "Şu konuda daha fazla bilgi edinin: BC30737: ' içinde uygun imzaya sahip erişilebilir bir ' Main ' yöntemi bulunamadı<name>"
title: "'<name>' içinde uygun imzaya sahip erişilebilir bir 'Main' yöntemi bulunamadı"
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 1865d6baea824c435d276aa9c160bcd282abf4ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795657"
---
# <a name="bc30737-no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>BC30737: ' ' içinde uygun imzaya sahip erişilebilir bir ' Main ' yöntemi bulunamadı \<name>

Komut satırı uygulamalarının tanımlanmış olması gerekir `Sub Main` . `Main``Public Shared`bir sınıfta tanımlanmalı veya `Public` bir modülde tanımlanmış gibi bildirilmelidir.

 **Hata kimliği:** BC30737

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- `Public Sub Main`Projeniz için bir yordam tanımlayın. Bunu `Shared` yalnızca bir sınıf içinde tanımlarsanız, ve olarak bildirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir Visual Basic Programının Yapısı](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [Yordamlar](../../programming-guide/language-features/procedures/index.md)
