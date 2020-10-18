---
title: "'<methodname>' içinde aynı imzaya sahip birden fazla tanım var"
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: 663b22421d1a0e401cfb3c135c99bd097163a78b
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160372"
---
# <a name="bc30269-methodname-has-multiple-definitions-with-identical-signatures"></a>BC30269: ' \<methodname> ', aynı imzalara sahip birden fazla tanıma sahip

Bir `Function` veya `Sub` yordam bildirimi, önceki bir bildirim olarak aynı yordam adı ve bağımsız değişken listesini kullanır. Olası bir neden, özgün yordamı aşırı yükleme girişimdir. Aşırı yüklenmiş yordamların farklı bağımsız değişken listeleri olmalıdır.

 **Hata kimliği:** BC30269

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Yordam adını veya bağımsız değişken listesini değiştirin veya yinelenen bildirimi kaldırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Yordamları Aşırı Yüklemeye İlişkin Düşünceler](../../programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
