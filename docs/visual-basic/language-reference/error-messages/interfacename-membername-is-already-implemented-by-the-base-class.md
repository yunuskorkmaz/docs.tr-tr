---
title: '&#39;&lt;InterfaceName&gt;.&lt; membername&gt; &#39; taban sınıfı tarafından zaten uygulanmış &#39; &lt;baseclassname&gt;&#39;. Yeniden uygulanmasına &lt;türü&gt; varsayıldı'
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 22a3bd4e8c09c0d070e7fa5e75571a7215c3a274
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507206"
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a>&#39;&lt;InterfaceName&gt;.&lt; membername&gt; &#39; taban sınıfı tarafından zaten uygulanmış &#39; &lt;baseclassname&gt;&#39;. Yeniden uygulanmasına &lt;türü&gt; varsayıldı
Bir özellik, yordam veya türetilmiş bir sınıf içinde olay kullanan bir `Implements` temel sınıfta zaten uygulanmış bir arabirim üyesi belirleme yan tümcesi.  
  
 Türetilmiş bir sınıf, taban sınıfı tarafından uygulanan bir arabirim üyesi yeniden uygulayın. Bu temel sınıf uygulamasına geçersiz kılma ile aynı değildir. Daha fazla bilgi için [uygular](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42015  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Arabirim üyesini yeniden uygulayın yapmak istiyorsanız, herhangi bir eylemde bulunmanız gerekmez. Türetilmiş sınıfınızın kodda erişen reimplemented üye kullanılmadıkça `MyBase` temel sınıf uygulamasına erişmek için anahtar sözcüğü.  
  
-   Arabirim üyesini yeniden uygulayın düşünmüyorsanız kaldırmak `Implements` özellik, yordam veya olay bildiriminin from yan tümcesi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
