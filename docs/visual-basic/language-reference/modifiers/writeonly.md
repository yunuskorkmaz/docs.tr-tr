---
title: WriteOnly
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
ms.openlocfilehash: 847617ea6534089857a759fbea3bb16a3a5a36a1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344198"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Bir özelliğin yazılabileceğini ancak okunlamayacağını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="rules"></a>Kurallar  
 **Bildirim bağlamı.** Yalnızca modül düzeyinde `WriteOnly` kullanabilirsiniz. Bu, bir `WriteOnly` özelliği için bildirim bağlamının bir sınıf, yapı veya modül olması ve kaynak dosya, ad alanı veya yordam olması anlamına gelir.  
  
 Bir özelliği `WriteOnly`, ancak bir değişken olarak bildirebilirsiniz.  
  
## <a name="when-to-use-writeonly"></a>WriteOnly ne zaman kullanılır?  
 Bazen, tüketen kodun bir değer ayarlayabilmesini, ancak ne olduğunu bulamayacağını isteyebilirsiniz. Örneğin, sosyal kayıt numarası veya parola gibi hassas verilerin, onu ayarlanmamış herhangi bir bileşene erişiminin korunması gerekir. Bu gibi durumlarda, değeri ayarlamak için bir `WriteOnly` özelliği kullanabilirsiniz.  
  
> [!IMPORTANT]
> `WriteOnly` özelliğini tanımlayıp kullandığınızda, aşağıdaki ek koruyucu ölçüleri göz önünde bulundurun:  
  
- **Si.** Özelliği bir sınıfın üyesiyse, [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)' ın varsayılan yapmasına izin verin ve `Overridable` veya `MustOverride`bildirmeyin. Bu, türetilmiş bir sınıfın bir geçersiz kılma aracılığıyla istenmeyen erişim yapmasını engeller.  
  
- **Erişim düzeyi.** Özelliğin hassas verilerini bir veya daha fazla değişkenlerde tutarsanız, başka hiçbir kodun erişemez olması için bunları [özel](../../../visual-basic/language-reference/modifiers/private.md) olarak bildirin.  
  
- **Şifreleme.** Tüm hassas verileri düz metin yerine şifreli biçimde depolayın. Kötü amaçlı kod, bu bellek alanına bir şekilde erişim kazanıyorsa, verilerin kullanılması daha zordur. Şifreleme, hassas verileri serileştirmek için gerekliyse da yararlıdır.  
  
- **Sıfırlanması.** Özelliği tanımlayan sınıf, yapı veya modül sonlandırıldığı zaman, hassas verileri varsayılan değerlere veya daha anlamlı değerlere sıfırlayın. Bu, bellek alanı genel erişim için serbest bırakıldığında daha fazla koruma sağlar.  
  
- **Kalıcılığı.** Herhangi bir hassas verileri (örneğin, disk üzerinde) kalıcı olarak kullanmayın. Ayrıca, panoya gizli veriler eklemeyin.  
  
 `WriteOnly` değiştiricisi Bu bağlamda kullanılabilir:  
  
 [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
