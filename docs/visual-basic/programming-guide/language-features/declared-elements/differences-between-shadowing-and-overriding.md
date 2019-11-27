---
title: Gölgeleme ve Geçersiz Kılma Arasındaki Farklar
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: 8d1ebdcd0a23dff69a7acca22268c03e30ec06d9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345410"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>Gölgeleme ve Geçersiz Kılma Arasındaki Farklar (Visual Basic)
Temel sınıftan devralan bir sınıf tanımladığınızda, bazen türetilmiş sınıftaki bir veya daha fazla temel sınıf öğelerinden birini yeniden tanımlamak isteyebilirsiniz. Gölgeleme ve geçersiz kılma, bu amaçla kullanılabilir.  
  
## <a name="comparison"></a>Karşılaştırma  
 Hem türetilmiş bir sınıf temel sınıftan devralındığında hem de hem de bir tane ile tanımlanmış öğeyi yeniden tanımlayarak, gölgeleme ve geçersiz kılma kullanılır. Ancak ikisi arasında önemli farklılıklar vardır.  
  
 Aşağıdaki tabloda gölgeleme, geçersiz kılma ile karşılaştırılır.  
  
||||  
|---|---|---|  
|Karşılaştırma noktası|Gölge Kullanım|Si|  
|Amaç|Türetilmiş sınıfta zaten tanımladığınız bir üyeyi tanıtan, sonraki bir temel sınıf değişikliğine karşı koruma sağlar|Aynı arama sırası<sup>1</sup> ile bir yordamın veya özelliğin farklı bir uygulamasını tanımlayarak çok biçimliliği elde edin|  
|Öğe yeniden tanımlandı|Herhangi bir beyan edilen öğe türü|Yalnızca bir yordam (`Function`, `Sub`veya `Operator`) veya özellik|  
|Öğe yeniden tanımlama|Herhangi bir beyan edilen öğe türü|Yalnızca özdeş çağrı sırası<sup>1</sup> olan yordam veya özellik|  
|Öğe yeniden tanımlama için erişim düzeyi|Herhangi bir erişim düzeyi|Geçersiz kılınan öğenin erişim düzeyi değiştirilemez|  
|Öğe yeniden tanımlama için okunabilirlik ve yazılabilirlik|Herhangi bir bileşim|Geçersiz kılınan özelliğin okunabilirlik veya yazılabilirlik özelliği değiştirilemez|  
|Yeniden tanımlama üzerinde denetim|Temel sınıf öğesi, gölgelendirmeyi zorlayamıyor veya yasaklaamaz|Temel sınıf öğesi `MustOverride`, `NotOverridable`veya `Overridable` belirtebilir|  
|Anahtar sözcük kullanımı|türetilmiş sınıfta önerilen `Shadows`; Ne `Shadows` ne de `Shadows` `Overrides` belirtilen<sup>2</sup>|temel sınıfta `Overridable` veya `MustOverride` gerekli; türetilmiş sınıfta gerekli `Overrides`|  
|Türetilmiş sınıfınızdan türetilen sınıfların öğe yeniden tanımlanması devralma|Daha fazla türetilmiş sınıflar tarafından devralınan gölgeleme öğesi; gölgeli öğe hala gizli<sup>3</sup>|Daha fazla türetilmiş sınıflar tarafından devralınan öğe geçersiz kılınıyor; geçersiz kılınan öğe hala geçersiz kılındı|  
  
 <sup>1</sup> *çağrı dizisi* , öğe türünden (`Function`, `Sub`, `Operator`veya `Property`), ad, parametre listesi ve dönüş türünden oluşur. Bir yordamı bir özellik veya başka bir yöntemle geçersiz kılamazsınız. Bir tür yordamı (`Function`, `Sub`veya `Operator`) başka bir tür ile geçersiz kılamazsınız.  
  
 <sup>2</sup> `Shadows` veya `Overrides`belirtmezseniz, derleyici hangi tür yeniden tanımlama türünü kullanmak istediğinize emin olmanıza yardımcı olması için bir uyarı mesajı yayınlar. Uyarıyı yoksayabilirsiniz, gölgeleme mekanizması kullanılır.  
  
 <sup>3</sup> gölgeleme öğesine daha fazla türetilmiş bir sınıfta erişilemiyorsa, gölgeleme devralınmaz. Örneğin, gölgeleme öğesini `Private`olarak bildirirseniz, türetilen sınıftan türetilen bir sınıf, gölgeleme öğesi yerine özgün öğeyi devralır.  
  
## <a name="guidelines"></a>Kuralları  
 Normal olarak, aşağıdaki durumlarda geçersiz kılma kullanırsınız:  
  
- Çok biçimli türetilmiş sınıflar tanımlamanız gerekir.  
  
- Derleyiciye sahip olmanın güvenliğini, aynı öğe türünü ve çağırma sırasını zorunlu kılmak istiyorsunuz.  
  
 Genellikle, aşağıdaki durumlarda gölgeleme kullanırsınız:  
  
- Temel sınıfınızın değiştirilmiş olabileceğini ve sizinkiyle aynı adı kullanarak bir öğe tanımlanacağını tahmin edersiniz.  
  
- Öğe türünü veya çağrı sırasını değiştirme özgürlüğünü istiyorsunuz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic gölgeleme](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Nasıl yapılır: Devralınmış Değişkeni Gizleme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
