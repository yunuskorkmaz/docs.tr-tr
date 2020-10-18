---
title: "'Optional' bekleniyor"
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 9c717cef2052722563e04595ef7a808ea103a75d
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159826"
---
# <a name="bc30202-optional-expected"></a>BC30202: ' Optional ' bekleniyor

Yordam bildiriminde isteğe bağlı bir bağımsız değişken, ardından gerekli bir bağımsız değişken tarafından izlenir. İsteğe bağlı bağımsız değişkenden sonraki her bağımsız değişken de isteğe bağlı olmalıdır.

 **Hata kimliği:** BC30202

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Bağımsız değişkenin gerekli olması amaçlanıyorsa, bağımsız değişken listesindeki ilk isteğe bağlı bağımsız değişkenden önce onu taşıyın.

- Bağımsız değişkenin isteğe bağlı olması amaçlanıyorsa, `Optional` anahtar sözcüğünü kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [İsteğe Bağlı Parametreler](../../programming-guide/language-features/procedures/optional-parameters.md)
