---
title: WriteOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: 163ec17f3ea96744290c54a73054ab132f842127
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647670"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Bir özellik yazılabileceğini ancak okunamayacağını olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="rules"></a>Kurallar  
 **Bildirim bağlamı.** Kullanabileceğiniz `WriteOnly` yalnızca Modül düzeyinde. Bildirim bağlamı başka bir deyişle bir `WriteOnly` özellik bir sınıf, yapı veya modül olmalıdır ve bir kaynak dosyası, ad alanı ya da yordamın olamaz.  
  
 Bir özellik olarak bildirebilirsiniz `WriteOnly`, ancak bir değişken değil.  
  
## <a name="when-to-use-writeonly"></a>WriteOnly kullanıldığı durumlar  
 Bazen bir değeri ayarlandı, ancak bunun ne olduğunu Bul değil yapabilmek için kullanan kodu istersiniz. Örneğin, sosyal kayıt numarası veya parola gibi hassas verilerin, ayarlamamış herhangi bir bileşeni erişime karşı korunması gerekir. Bu durumlarda, kullandığınız bir `WriteOnly` değeri ayarlamak için özellik.  
  
> [!IMPORTANT]
>  Ne zaman tanımlama ve kullanma bir `WriteOnly` özelliği, aşağıdaki ek koruyucu ölçüleri göz önünde bulundurun:  
  
- **Geçersiz kılma.** Özellik bir sınıf üyesi ise, varsayılan olarak izin [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)ve onu bildirmeyin `Overridable` veya `MustOverride`. Bu, türetilmiş bir sınıf bir geçersiz kılma yoluyla istenmeyen erişim bulunmasını önler.  
  
- **Erişim düzeyi.** Bir veya daha fazla değişkenlerinde özelliğin hassas verileri tutarsanız, bunları bildirdiğinizde [özel](../../../visual-basic/language-reference/modifiers/private.md) böylece başka bir kod onlara erişebilir.  
  
- **Şifreleme.** Tüm hassas verileri, şifreli biçimde yerine düz metin Store. Kötü amaçlı kod şekilde bellek alanı erişim kazanırsa, yapmak daha zor olan verilerin kullanın. Şifreleme de hassas verileri seri hale getirmek gerekli olması durumunda yararlıdır.  
  
- **Sıfırlanıyor.** Sınıf, yapı veya modül özellik tanımlama Sonlandırılmakta, hassas verileri varsayılan değerlerine veya diğer anlamsız değerlere sıfırlayın. Genel erişim için bellek alanı Boşaltıldığında bu ek koruma sağlar.  
  
- **Kalıcılık.** Bunu önlemek, örneğin diskte hassas verilerin kalıcı olarak tutmaz. Aynı zamanda, hassas verileri panoya yazma değil.  
  
 `WriteOnly` Bu bağlamda değiştirici kullanılabilir:  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
