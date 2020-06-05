---
title: Gölgeleme ve Geçersiz Kılma Arasındaki Farklar
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: a6ea83fadf18ef3be778e6de31c0eb4e65e74824
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392876"
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
|Öğe yeniden tanımlandı|Herhangi bir beyan edilen öğe türü|Yalnızca bir yordam ( `Function` , `Sub` , veya `Operator` ) veya özellik|  
|Öğe yeniden tanımlama|Herhangi bir beyan edilen öğe türü|Yalnızca özdeş çağrı sırası<sup>1</sup> olan yordam veya özellik|  
|Öğe yeniden tanımlama için erişim düzeyi|Herhangi bir erişim düzeyi|Geçersiz kılınan öğenin erişim düzeyi değiştirilemez|  
|Öğe yeniden tanımlama için okunabilirlik ve yazılabilirlik|Herhangi bir bileşim|Geçersiz kılınan özelliğin okunabilirlik veya yazılabilirlik özelliği değiştirilemez|  
|Yeniden tanımlama üzerinde denetim|Temel sınıf öğesi, gölgelendirmeyi zorlayamıyor veya yasaklaamaz|Temel sınıf öğesi,, `MustOverride` `NotOverridable` veya belirtebilir`Overridable`|  
|Anahtar sözcük kullanımı|`Shadows`türetilmiş sınıfta önerilir; `Shadows`ne yoksa `Shadows` ne de `Overrides` belirtilmemişse<sup>2</sup> varsayılır|`Overridable`veya `MustOverride` temel sınıfta gerekli; `Overrides` türetilmiş sınıfta gereklidir|  
|Türetilmiş sınıfınızdan türetilen sınıfların öğe yeniden tanımlanması devralma|Daha fazla türetilmiş sınıflar tarafından devralınan gölgeleme öğesi; gölgeli öğe hala gizli<sup>3</sup>|Daha fazla türetilmiş sınıflar tarafından devralınan öğe geçersiz kılınıyor; geçersiz kılınan öğe hala geçersiz kılındı|  
  
 <sup>1</sup> *çağıran sıra* , öğe türü ( `Function` , `Sub` , `Operator` , veya `Property` ), ad, parametre listesi ve dönüş türünden oluşur. Bir yordamı bir özellik veya başka bir yöntemle geçersiz kılamazsınız. Bir tür yordamı ( `Function` , `Sub` , veya `Operator` ) başka bir tür ile geçersiz kılamazsınız.  
  
 <sup>2</sup> ya da belirtmezseniz `Shadows` `Overrides` , derleyici ne tür bir yeniden tanımlama kullanmak istediğinize emin olmanıza yardımcı olması için bir uyarı iletisi yayınlar. Uyarıyı yoksayabilirsiniz, gölgeleme mekanizması kullanılır.  
  
 <sup>3</sup> gölgeleme öğesine daha fazla türetilmiş bir sınıfta erişilemiyorsa, gölgeleme devralınmaz. Örneğin, gölgeleme öğesini olarak bildirirseniz `Private` , türetilmiş sınıfınızdan türeyen bir sınıf, gölgeleme öğesi yerine özgün öğeyi devralır.  
  
## <a name="guidelines"></a>Yönergeler  
 Normal olarak, aşağıdaki durumlarda geçersiz kılma kullanırsınız:  
  
- Çok biçimli türetilmiş sınıflar tanımlamanız gerekir.  
  
- Derleyiciye sahip olmanın güvenliğini, aynı öğe türünü ve çağırma sırasını zorunlu kılmak istiyorsunuz.  
  
 Genellikle, aşağıdaki durumlarda gölgeleme kullanırsınız:  
  
- Temel sınıfınızın değiştirilmiş olabileceğini ve sizinkiyle aynı adı kullanarak bir öğe tanımlanacağını tahmin edersiniz.  
  
- Öğe türünü veya çağrı sırasını değiştirme özgürlüğünü istiyorsunuz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bildirilmiş Öğelere Başvurular](references-to-declared-elements.md)
- [Visual Basic'de Gölgeleme](shadowing.md)
- [Nasıl yapılır: Değişkeninizle Aynı Adı Taşıyan Bir Değişkeni Gizleme](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Nasıl yapılır: Devralınmış Değişkeni Gizleme](how-to-hide-an-inherited-variable.md)
- [Nasıl yapılır: Türetilmiş Sınıf Tarafından Gizlenen Bir Değişkene Erişme](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
- [Geçersiz Kılmalar](../../../language-reference/modifiers/overrides.md)
