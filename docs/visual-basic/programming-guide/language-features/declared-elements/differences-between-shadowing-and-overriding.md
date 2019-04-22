---
title: Gölgeleme ve Geçersiz Kılma Arasındaki Farklar (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: b935184f0e4d0378bfea69811aa4e6c068a9776f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827932"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>Gölgeleme ve Geçersiz Kılma Arasındaki Farklar (Visual Basic)
Bir temel sınıftan devralınan bir sınıf tanımladığınızda, bazen bir veya daha fazla türetilmiş sınıf içinde temel sınıf öğe yeniden tanımlamak istersiniz. Gölgeleme ve geçersiz kılma ikisi de bu amaç için olan.  
  
## <a name="comparison"></a>Karşılaştırma  
 Gölgeleme ve geçersiz kılma her ikisi de bir temel sınıftan türetilmiş bir sınıf devralır ve her ikisini de diğerine ile bildirilen bir öğe yeniden kullanılır. Ancak, ikisi arasındaki önemli farklar vardır.  
  
 Aşağıdaki tabloda, geçersiz kılma ile gölgeleme karşılaştırır.  
  
||||  
|---|---|---|  
|Karşılaştırma noktası|Gölge Kullanım|Geçersiz kılma|  
|Amaç|Türetilen bir sınıfta zaten tanımlanmış bir üye tanıtan sonraki bir temel sınıf değişikliği karşı korur|Bir yordam veya özellik ile aynı çağrı sırası farklı uygulamalarını tanımlayarak çok biçimlilik başarır<sup>1</sup>|  
|Yeniden tanımlanan öğe|Herhangi bir öğe türü bildirilen|Yalnızca bir yordam (`Function`, `Sub`, veya `Operator`) veya özellik|  
|Öğe yeniden tanımlama|Herhangi bir öğe türü bildirilen|Yalnızca bir yordam veya özellik ile aynı çağrı sırası<sup>1</sup>|  
|Erişim düzeyini öğesi yeniden tanımlama|Herhangi bir erişim düzeyi|Geçersiz kılınan öğe erişim düzeyi değiştirilemez|  
|Okunabilirlik ve yazılabilirlik öğesini tanımlayarak|Herhangi bir birleşimi|Okunabilirlik veya geçersiz kılınan özelliğin yazılabilirlik değiştiremezsiniz|  
|Yeniden tanımlama üzerinden denetleme|Temel sınıf öğesi uygulayabilir veya gölgeleme engelle|Temel sınıf öğesi belirtebilirsiniz `MustOverride`, `NotOverridable`, veya `Overridable`|  
|Anahtar sözcüğü kullanım|`Shadows` türetilen sınıfta önerilir; `Shadows` ne kabul `Shadows` ya da `Overrides` belirtilen<sup>2</sup>|`Overridable` veya `MustOverride` temel sınıfta; gerekli `Overrides` türetilen sınıfta gerekli|  
|Öğesi, türetilmiş bir sınıftan türetilen sınıflar tarafından tanımlayarak, devralma|Öğe gölgeleme tarafından devralınan sınıflar;'daha fazla türetilmiş Gölgeli öğe gizlenmiş<sup>3</sup>|Öğe geçersiz kılma tarafından devralınan sınıflar;'daha fazla türetilmiş Geçersiz kılınan öğe hala geçersiz kılındı|  
  
 <sup>1</sup> *arama sırası* öğe türü oluşur (`Function`, `Sub`, `Operator`, veya `Property`), adı, parametre listesi ve dönüş türü. Bir özellik veya tersine içeren bir yordamı geçersiz kılamaz. Yordamın bir türü geçersiz kılınamaz (`Function`, `Sub`, veya `Operator`) ile başka bir tür.  
  
 <sup>2</sup> ya da belirtmezseniz `Shadows` veya `Overrides`, derleyici kullanmak istediğiniz hangi tür yeniden tanımlama emin olmanıza yardımcı olacak bir uyarı iletisi verir. Uyarıyı yoksay, gölgelendirme mekanizması kullanılır.  
  
 <sup>3</sup> gölgeleme öğe başka bir türetilmiş sınıfta erişilemez durumdaysa gölgeleme devralınmaz. Örneğin, gölgelendirme öğesi olarak bildirirseniz `Private`, özgün öğe gölgeleme öğe yerine, türetilen bir sınıftan türetilen sınıf devralır.  
  
## <a name="guidelines"></a>Kuralları  
 Normalde, aşağıdaki durumlarda geçersiz kılma kullanın:  
  
-   Çok biçimli türetilmiş sınıflar tanımlarsınız.  
  
-   Aynı öğe türü ve çağrı sırası zorunlu derleyici yaşama güvenliği kullanmanız gerekir.  
  
 Normalde, aşağıdaki durumlarda gölgeleme kullanın:  
  
-   Temel sınıfınız değiştirilebilir ve sizinki aynı adı kullanarak bir öğe tanımlama beklenir.  
  
-   Öğe türü değiştirme veya arama sırası isterler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic'de gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Nasıl yapılır: Değişkeninizle aynı ada sahip bir değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Nasıl yapılır: Devralınmış değişkeni gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Nasıl yapılır: Türetilmiş sınıf tarafından gizlenen bir değişkene erişme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
