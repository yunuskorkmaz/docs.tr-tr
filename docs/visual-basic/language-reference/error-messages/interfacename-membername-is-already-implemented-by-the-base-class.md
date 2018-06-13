---
title: '&#39;&lt;InterfaceName&gt;.&lt; membername&gt; &#39; temel sınıfı tarafından zaten uygulanmış &#39; &lt;baseclassname&gt;&#39;. Yeniden uyarlamasını &lt;türü&gt; varsayılır'
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 9054c293ede9db4637f23579407f2f76db29f2ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588976"
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a>&#39;&lt;InterfaceName&gt;.&lt; membername&gt; &#39; temel sınıfı tarafından zaten uygulanmış &#39; &lt;baseclassname&gt;&#39;. Yeniden uyarlamasını &lt;türü&gt; varsayılır
Bir özellik, yordam veya türetilmiş bir sınıf olayda kullanan bir `Implements` yan tümcesi taban sınıf içinde zaten uygulanmış bir arabirim üyesini belirtme.  
  
 Türetilmiş bir sınıf kendi temel sınıfı tarafından uygulanan bir arabirim üyesini yeniden uygulamalı. Bu taban sınıfı uygulama geçersiz kılma olarak aynı değildir. Daha fazla bilgi için bkz: [uygulayan](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42015  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Arabirim üyesini yeniden uygulamalı yapmak istiyorsanız, herhangi bir eylemde bulunmanız gerekmez. Kullanmadığınız sürece, türetilmiş bir sınıf kodda erişen reimplemented üye `MyBase` taban sınıfı uygulama erişmek için anahtar sözcüğü.  
  
-   Arabirim üyesini yeniden uygulamalı düşünmüyorsanız kaldırmak `Implements` özelliği, yordam veya olay bildiriminin from yan tümcesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
