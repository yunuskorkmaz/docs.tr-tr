---
title: CLS uyumlu olmayan &lt;membername&gt; CLS uyumlu arabirimde izin verilmez
ms.date: 07/20/2015
f1_keywords:
- bc40033
- vbc40033
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
ms.openlocfilehash: c837065d2d448fc2523cfbd18efac962445f8bf0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627704"
---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a>CLS uyumlu olmayan &lt;membername&gt; CLS uyumlu arabirimde izin verilmez
Bir özellik, yordam veya bir arabirim olay olarak işaretlenmiş `<CLSCompliant(True)>` olarak arabirimi işaretlendiğinde `<CLSCompliant(False)>` veya hiçbir işaret konulmadıysa.  
  
 Bir arabirim ile uyumlu olması için [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), tüm üyeleri olmalıdır uyumlu.  
  
 Uyguladığınızda <xref:System.CLSCompliantAttribute> bir programlama öğesine özniteliğin ayarladığınız `isCompliant` ya da parametre `True` veya `False` uyumluluk veya uyumsuzluk belirtmek için. Bu parametre için varsayılan yok ve bir değer sağlamanız gerekir.  
  
 Geçerli <xref:System.CLSCompliantAttribute> bir öğe için uyumsuz olarak değerlendirilir.  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC40033  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   CLS uyumluluğu gerektir ve denetime arabirimi kaynak kodu varsa arabirimi olarak işaretlemek `<CLSCompliant(True)>` tüm üyeleri uyumlu ise.  
  
-   CLS uyumluluğu gerektir ve arabirimi kaynak kod üzerinde denetim sahibi olmadığınız veya uyumlu olması uymuyorsa, farklı bir arabirim içinde bu üye tanımlayın.  
  
-   Bu üye, geçerli arabirimi içinde kalmasını gerektiriyorsa, kaldırma <xref:System.CLSCompliantAttribute> kendi tanımından veya olarak işaretlemek `<CLSCompliant(False)>`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Interface Deyimi](../../../visual-basic/language-reference/statements/interface-statement.md)

