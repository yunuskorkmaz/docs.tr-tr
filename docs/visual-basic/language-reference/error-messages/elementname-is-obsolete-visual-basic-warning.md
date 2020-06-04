---
title: "'<elementname>' eski (Visual Basic Uyarısı)"
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: 7914bc859966e17f3da41c9a13a01573b31baf91
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409679"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a>'\<elementname>' eski (Visual Basic Uyarısı)
Bir ifade, özniteliğiyle işaretlenmiş bir programlama öğesine <xref:System.ObsoleteAttribute> ve bir uyarı olarak kabul edilecek yönergeye erişmeyi dener.  
  
 Herhangi bir programlama öğesini, bu uygulamaya uygulama tarafından artık kullanımda olmayacak şekilde işaretleyebilirsiniz <xref:System.ObsoleteAttribute> . Bunu yaparsanız özniteliğin <xref:System.ObsoleteAttribute.IsError%2A> özelliğini ya da olarak ayarlayabilirsiniz `True` `False` . Öğesini olarak ayarlarsanız `True` , derleyici bir hata olarak öğeyi kullanma denemesine davranır. Bunu olarak ayarlarsanız `False` veya varsayılan olarak izin verirseniz `False` , öğesini kullanma girişimi varsa derleyici bir uyarı verir.  
  
 Varsayılan olarak, bu ileti bir uyarıdır, çünkü <xref:System.ObsoleteAttribute.IsError%2A> öğesinin özelliği <xref:System.ObsoleteAttribute> olur `False` . Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata kimliği:** BC40008  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Kaynak kodu başvurusunun öğe adının doğru yazıldığından emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özniteliklere genel bakış](../../programming-guide/concepts/attributes/index.md)
