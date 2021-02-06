---
description: "Hakkında daha fazla bilgi edinin: BC30941: Structure ' <structurename> ' en az bir örnek üye değişkeni veya en az bir örnek olay bildirimi içermelidir ' Custom"
title: "'<structurename>' yapısı en az bir örnek üye değişkeni veya 'Custom' olarak işaretlenmemiş en az bir örnek olay bildirimi içermelidir"
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 08596997decd9d739ac95ad3e4191cb126b3efb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641453"
---
# <a name="bc30941-structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a>BC30941: ' ' yapısı en \<structurename> az bir örnek üye değişkeni veya ' Custom ' olarak işaretlenmemiş en az bir örnek olay bildirimi içermelidir

Bir yapı tanımı, paylaşılmayan olmayan değişkenler veya paylaşılmayan özel olmayan olaylar içermez.

 Her yapının, tek tek ([paylaşılan](../modifiers/shared.md)) tüm örnekler yerine her belirli örnek (paylaşılmayan) için geçerli olan bir değişkene veya olaya sahip olması gerekir. Paylaşılmayan sabitler, Özellikler ve yordamlar bu gereksinimi karşılamıyor. Ayrıca, paylaşılmayan değişkenler ve yalnızca paylaşılan olmayan bir olay yoksa, bu olay bir `Custom` olay olamaz.

 **Hata kimliği:** BC30941

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- En az bir değişken veya olmayan olay tanımlayın `Shared` . Yalnızca bir olay tanımlarsanız, özel olmayan ve paylaşılmayan olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılar](../../programming-guide/language-features/data-types/structures.md)
- [Nasıl yapılır: Yapıyı Bildirme](../../programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Structure Yapısı](../statements/structure-statement.md)
