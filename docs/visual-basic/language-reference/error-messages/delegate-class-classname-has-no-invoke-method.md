---
description: "Hakkında daha fazla bilgi edinin: BC30220: ' <classname> ' temsilci sınıfının Invoke yöntemi yok, bu nedenle bu türdeki bir ifade bir yöntem çağrısının hedefi olamaz"
title: "'<classname>' temsilci sınıfında Invoke yöntemi yok, bu nedenle bu türdeki bir ifade bir yöntem çağrısının hedefi olamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: c0d3f6e352a98e194b2c2ddca04bfa7254ec37a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796632"
---
# <a name="bc30220-delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>BC30220: ' ' temsilci sınıfında \<classname> Invoke yöntemi yok, bu nedenle bu türdeki bir ifade bir yöntem çağrısının hedefi olamaz

Temsilci `Invoke` sınıfında uygulanmadığı için bir temsilci aracılığıyla yapılan çağrı başarısız oldu `Invoke` .

 **Hata kimliği:** BC30220

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Temsilci sınıfının bir örneğinin bir `Dim` ifadesiyle oluşturulduğundan ve bu işleç ile temsilci örneğine bir yordamın atandığından emin olun `AddressOf` .

2. Temsilci sınıfını uygulayan kodu bulun ve yordamı gerçekleştirdiğinden emin olun `Invoke` .

## <a name="see-also"></a>Ayrıca bkz.

- [Temsilciler](../../programming-guide/language-features/delegates/index.md)
- [Delegate Deyimi](../statements/delegate-statement.md)
- [AddressOf İşleci](../operators/addressof-operator.md)
- [Dim Deyimi](../statements/dim-statement.md)
