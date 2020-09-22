---
title: CLS uyumlu olmayan <membername> öğesine CLS uyumlu arabirimde izin verilmez.
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: d8394fb995bb7b009b4ee40dccc41e3435ae7309
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873696"
---
# <a name="non-cls-compliant-membername-is-not-allowed-in-a-cls-compliant-interface"></a>CLS uyumlu olmayan \<membername> öğesine CLS uyumlu arabirimde izin verilmez.

Arabirimdeki bir özellik, yordam veya olay, `<CLSCompliant(True)>` arabirimin kendisi olarak işaretlendiğinde `<CLSCompliant(False)>` veya işaretlenmediğinde olarak işaretlenir.  
  
 Bir arabirimin, [Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS) ile uyumlu olması için tüm üyelerinin uyumlu olması gerekir.  
  
 <xref:System.CLSCompliantAttribute>' I bir programlama öğesine uyguladığınızda, ya `isCompliant` da `True` `False` Uyumluluk veya uyumsuzluk olduğunu göstermek için özniteliğin parametresini veya olarak ayarlayın. Bu parametre için varsayılan yoktur ve bir değer belirtmeniz gerekir.  
  
 <xref:System.CLSCompliantAttribute>Öğesini bir öğesine uygulamazsanız, uyumsuz olduğu kabul edilir.  
  
 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata kimliği:** BC40033  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- CLS uyumluluğuna ihtiyacınız varsa ve arabirim kaynak kodu üzerinde denetiminiz varsa, arabirimi `<CLSCompliant(True)>` tüm üyeleri uyumlu olduğu gibi işaretleyin.  
  
- CLS uyumluluğu varsa ve arabirim kaynak kodu üzerinde denetiminiz yoksa veya uyumlu hale getirmek için uygun değilse, bu üyeyi farklı bir arabirim içinde tanımlayın.  
  
- Bu üyenin geçerli arabiriminde kalmasını gerektiriyorsa, öğesini <xref:System.CLSCompliantAttribute> tanımından kaldırın veya olarak işaretleyin `<CLSCompliant(False)>` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Interface Deyimi](../statements/interface-statement.md)
