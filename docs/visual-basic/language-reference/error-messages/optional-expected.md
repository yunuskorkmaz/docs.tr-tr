---
description: "Hakkında daha fazla bilgi edinin: BC30202: ' Optional ' bekleniyor"
title: "'Optional' bekleniyor"
ms.date: 07/20/2015
f1_keywords:
- bc30202
- vbc30202
helpviewer_keywords:
- BC30202
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
ms.openlocfilehash: 543dbf6226d4d298d46764ee506b55e770c91604
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795553"
---
# <a name="bc30202-optional-expected"></a>BC30202: ' Optional ' bekleniyor

Yordam bildiriminde isteğe bağlı bir bağımsız değişken, ardından gerekli bir bağımsız değişken tarafından izlenir. İsteğe bağlı bağımsız değişkenden sonraki her bağımsız değişken de isteğe bağlı olmalıdır.

 **Hata kimliği:** BC30202

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Bağımsız değişkenin gerekli olması amaçlanıyorsa, bağımsız değişken listesindeki ilk isteğe bağlı bağımsız değişkenden önce onu taşıyın.

- Bağımsız değişkenin isteğe bağlı olması amaçlanıyorsa, `Optional` anahtar sözcüğünü kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [İsteğe Bağlı Parametreler](../../programming-guide/language-features/procedures/optional-parameters.md)
