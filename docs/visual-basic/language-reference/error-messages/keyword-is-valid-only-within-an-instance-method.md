---
description: "Hakkında daha fazla bilgi edinin: BC30043: ' <keyword> ' yalnızca bir örnek yöntemi içinde geçerlidir"
title: "'<keyword>' yalnızca bir örnek yöntemi içinde geçerlidir"
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 0bca2df44e096da016c9cb0c2031a8ef6faeb2b0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795982"
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
