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
ms.openlocfilehash: 4f34f7f4ada3f8d61c9d855eab1b8b073a3d5ed8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599209"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Bir özellik yazılmış ancak okunamıyor belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="rules"></a>Kurallar  
 **Bildirim bağlamı.** Kullanabileceğiniz `WriteOnly` yalnızca modülü düzeyinde. Bu bildirimi bağlamının anlamına gelir bir `WriteOnly` özelliği bir sınıf, yapı veya modülü olmalıdır ve bir kaynak dosyasını, ad alanı veya yordamı olamaz.  
  
 Bir özellik olarak bildirebilir `WriteOnly`, ancak bir değişken değil.  
  
## <a name="when-to-use-writeonly"></a>WriteOnly kullanma zamanı  
 Bazen bir değere ayarlayın ancak nedir Bul değil Süren kod istersiniz. Örneğin, bir sosyal kayıt numarası veya bir parola gibi hassas verileri, ayarlamamış herhangi bir bileşenin erişime karşı korunması gerekir. Bu durumlarda, kullanabileceğiniz bir `WriteOnly` özellik değeri ayarlanamıyor.  
  
> [!IMPORTANT]
>  Ne zaman tanımlama ve kullanma bir `WriteOnly` özelliği, aşağıdaki ek koruyucu ölçüleri göz önünde bulundurun:  
  
-   **Geçersiz kılma.** Özellik bir sınıf üyesi ise, varsayılan olarak izin [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)ve bunu bildirme `Overridable` veya `MustOverride`. Bu, türetilmiş bir sınıf bir geçersiz kılma istenmeyen erişimin yapmasını engeller.  
  
-   **Erişim düzeyi.** Bir veya daha fazla değişkenlerde özelliğin hassas verileri tutarsanız, bunları bildirme [özel](../../../visual-basic/language-reference/modifiers/private.md) başka bir kod bunlara erişebilmesi için.  
  
-   **Şifreleme.** Şifrelenmiş biçimde yerine düz metin tüm hassas verileri depolar. Kötü amaçlı kod şekilde bellek alanı erişim sağlarsa, yapmak daha zor olduğundan verileri kullanın. Şifreleme de hassas verileri seri hale getirmek gerekliyse, yararlıdır.  
  
-   **Sıfırlanıyor.** Sınıf, yapı veya özellik tanımlama modülü sonlandırılıyor, hassas verileri varsayılan değerleri veya diğer anlamsız değerlere sıfırlanır. Genel erişim için bellek alanı Boşaltıldığında bu ek koruma sağlar.  
  
-   **Kalıcılık.** Bunu önlemek, örneğin diskteki herhangi bir duyarlı veri devam etmez. Ayrıca, herhangi bir duyarlı veri panoya yazma.  
  
 `WriteOnly` Bu bağlamda değiştirici kullanılabilir:  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
