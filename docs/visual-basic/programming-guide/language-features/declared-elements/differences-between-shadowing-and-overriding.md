---
title: "Gölgeleme ve Geçersiz Kılma Arasındaki Farklar (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d67486d9c6af96d314abad7142ba86779d74f5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>Gölgeleme ve Geçersiz Kılma Arasındaki Farklar (Visual Basic)
Taban sınıfından devralan bir sınıf tanımladığınızda, bazen bir veya daha fazla türetilmiş sınıflarda temel sınıf öğe yeniden tanımlamak istiyor. Gölgeleme ve geçersiz kılma kullanılabilir hem de bu amaç için var.  
  
## <a name="comparison"></a>Karşılaştırma  
 Gölgeleme ve geçersiz kılma hem de türetilmiş bir sınıf bir taban sınıfından devralıyor ve her ikisi de bildirilen bir öğe başka bir yeniden tanımlamanız olduğunda kullanılır. Ancak ikisi arasındaki önemli farklılıklar vardır.  
  
 Aşağıdaki tabloda, geçersiz kılma ile gölgeleme karşılaştırır.  
  
||||  
|---|---|---|  
|Karşılaştırma noktası|Gölgeleme|Geçersiz kılma|  
|Amaç|Türetilen sınıfta zaten tanımlı bir üye tanıtır sonraki bir temel sınıf değişikliği korur|Çok biçimlilik farklı bir uygulama bir yordam veya aynı arama sırası özelliğiyle tanımlayarak başarır<sup>1</sup>|  
|Yeniden tanımlanan öğesi|Herhangi bir öğe türü bildirilen|Yalnızca bir yordam (`Function`, `Sub`, veya `Operator`) veya özellik|  
|Öğe yeniden tanımlama|Herhangi bir öğe türü bildirilen|Yalnızca bir yordam veya aynı arama sırası özelliğiyle<sup>1</sup>|  
|Erişim düzeyini öğesi yeniden tanımlama|Herhangi bir erişim düzeyi|Geçersiz kılınan öğe erişim düzeyini değiştiremezsiniz|  
|Okunabilirlik ve öğesi tanımlayarak, writability|Herhangi bir birleşimini|Okunabilirlik veya writability geçersiz kılınan özelliği değiştirilemez|  
|Yeniden tanımlama üzerinden denetleme|Taban sınıfı öğesi uygulayabilir veya gölgeleme engelle|Taban sınıfı öğesi belirtebilirsiniz `MustOverride`, `NotOverridable`, veya`Overridable`|  
|Anahtar kullanımı|`Shadows`türetilen sınıfta önerilir; `Shadows` hiçbiri kabul `Shadows` ya da `Overrides` belirtilen<sup>2</sup>|`Overridable`veya `MustOverride` taban sınıf içinde; gerekli `Overrides` türetilen sınıfta gerekli|  
|Türetilmiş sınıfından türetilen sınıflar tarafından öğesi tanımlayarak, devralma|Öğe gölgeleme devralınan sınıfları;'daha fazla türetilmiş hala gizli gölgeli öğesi<sup>3</sup>|Öğesi geçersiz kılma devralınan sınıfları;'daha fazla türetilmiş Geçersiz kılınan öğe hala geçersiz kılındı|  
  
 <sup>1</sup> *arama sırası* öğe türüne oluşur (`Function`, `Sub`, `Operator`, veya `Property`), ad, parametre listesi ve dönüş türü. Bir özellik ya da diğer yönden yordamla geçersiz kılamaz. Yordam bir tür geçersiz kılamaz (`Function`, `Sub`, veya `Operator`) başka bir tür ile.  
  
 <sup>2</sup> ya da belirtmezseniz, `Shadows` veya `Overrides`, kullanmak istediğiniz şemadaki hangi tür emin olmanıza yardımcı olması için bir uyarı iletisi derleyici verir. Uyarıyı yok sayarsanız gölgeleme mekanizması kullanılır.  
  
 <sup>3</sup> gölgeleme öğesi daha ileri bir türetilmiş sınıfta erişilemiyorsa gölgeleme devralınmaz. Örneğin, gölgeleme öğesi olarak bildirirseniz `Private`, özgün öğesi gölgeleme öğesi yerine türetilmiş sınıfından türetilen bir sınıfı devralır.  
  
## <a name="guidelines"></a>Kuralları  
 Normal olarak, aşağıdaki durumlarda geçersiz kılma kullanın:  
  
-   Çok biçimli türetilmiş sınıfları tanımlama.  
  
-   Aynı öğe türü ve arama sırası zorlamak derleyici sahip olmanın güvenlik istiyor.  
  
 Normal olarak, aşağıdaki durumlarda gölgeleme kullanın:  
  
-   Temel sınıfınız değiştirilebilir ve sizin aynı adı kullanarak bir öğe tanımlamak beklenir.  
  
-   Öğe türü değiştirme veya arama sırası erişebilmek isterler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bildirilmiş öğelere başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Visual Basic'de gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Nasıl yapılır: değişkeninizle aynı ada sahip bir değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [Nasıl yapılır: devralınmış değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [Nasıl yapılır: türetilmiş sınıf tarafından gizlenen bir değişkene erişme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Gölgeleri](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Geçersiz kılmaları](../../../../visual-basic/language-reference/modifiers/overrides.md)
