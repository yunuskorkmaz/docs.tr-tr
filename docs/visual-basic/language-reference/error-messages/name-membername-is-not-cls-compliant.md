---
title: <membername> adı CLS uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- bc40031
- vbc40031
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
ms.openlocfilehash: 45c9332237dffc7311daeedaf36035d9e9958415
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397187"
---
# <a name="name-membername-is-not-cls-compliant"></a>\<membername> adı CLS uyumlu değil
Bir derleme olarak işaretlenir, `<CLSCompliant(True)>` ancak alt çizgi () ile başlayan bir ada sahip bir üye ortaya koyar `_` .  
  
 Bir programlama öğesi bir veya daha fazla alt çizgi içerebilir, ancak [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olmak için bir alt çizgiyle başlamamalıdır. Bkz. [tanımlanmış öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).  
  
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
