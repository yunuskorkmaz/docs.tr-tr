---
title: "'<keyword>' yalnızca bir örnek yöntemi içinde geçerlidir"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: ad39ade294b362b20f2dfb93455445bf41d056cd
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163330"
---
# <a name="bc30043-keyword-is-valid-only-within-an-instance-method"></a>BC30043: ' \<keyword> ' yalnızca bir örnek yöntemi içinde geçerlidir

`Me`, `MyClass` Ve `MyBase` anahtar sözcükleri belirli sınıf örneklerine başvurur. Onları paylaşılan bir veya yordam içinde kullanamazsınız `Function` `Sub` .

*Hata kimliği:** BC30043

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Yordamından anahtar sözcüğünü kaldırın veya `Shared` yordam bildiriminden anahtar sözcüğü kaldırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Nesne Değişkeni Ataması](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase ve MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Devralma Temelleri](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
