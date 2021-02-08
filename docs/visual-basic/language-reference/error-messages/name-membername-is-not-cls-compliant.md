---
description: 'Şu konuda daha fazla bilgi edinin: BC40031: ad <membername> CLS uyumlu değil'
title: <membername> adı CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 7abc4aee8bb468b523e5bdd2ac13947d19c926bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795761"
---
# <a name="bc40031-name-membername-is-not-cls-compliant"></a>BC40031: ad \<membername> CLS uyumlu değil

Bir derleme olarak işaretlenir, `<CLSCompliant(True)>` ancak alt çizgi () ile başlayan bir ada sahip bir üye ortaya koyar `_` .

 Bir programlama öğesi bir veya daha fazla alt çizgi içerebilir, ancak [Dil bağımsızlığı ve Language-Independent bileşenleri](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olmak için bir alt çizgiyle başlamamalıdır. Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).

 <xref:System.CLSCompliantAttribute>' I bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu göstermek için özniteliğin parametresini veya olarak ayarlayın. Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.

 <xref:System.CLSCompliantAttribute>Öğesini bir öğesine uygulamazsanız, uyumsuz olduğu kabul edilir.

 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **Hata kimliği:** BC40031

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Kaynak kodu üzerinde denetiminiz varsa, üye adını alt çizgiyle başlamayan şekilde değiştirin.

- Üye adının değişmeden kalmasını gerektiriyorsa, öğesini <xref:System.CLSCompliantAttribute> tanımından kaldırın veya olarak işaretleyin `<CLSCompliant(False)>` . Derlemeyi hala olarak işaretleyebilirsiniz `<CLSCompliant(True)>` .

## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilen Öğe Adları](../../programming-guide/language-features/declared-elements/declared-element-names.md)
- [Visual Basic Adlandırma Kuralları](../../programming-guide/program-structure/naming-conventions.md)
