---
description: 'Daha fazla bilgi edinin: WriteOnly (Visual Basic)'
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
ms.openlocfilehash: 514a1de3c8c2cfbde6a9cffc5c235d92454dd966
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674746"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)

Bir özelliğin yazılabileceğini ancak okunlamayacağını belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="rules"></a>Kurallar  

 **Bildirim bağlamı.** `WriteOnly`Yalnızca modül düzeyinde kullanabilirsiniz. Yani, bir özelliğin bildirim bağlamı `WriteOnly` bir sınıf, yapı veya modül olmalıdır ve kaynak dosya, ad alanı veya yordam olamaz.  
  
 Bir özelliği `WriteOnly` bir değişken değil, olarak bildirebilirsiniz.  
  
## <a name="when-to-use-writeonly"></a>WriteOnly ne zaman kullanılır?  

 Bazen, tüketen kodun bir değer ayarlayabilmesini, ancak ne olduğunu bulamayacağını isteyebilirsiniz. Örneğin, sosyal kayıt numarası veya parola gibi hassas verilerin, onu ayarlanmamış herhangi bir bileşene erişiminin korunması gerekir. Bu durumlarda, `WriteOnly` değeri ayarlamak için bir özelliği kullanabilirsiniz.  
  
> [!IMPORTANT]
> Bir özelliği tanımlayıp kullandığınızda `WriteOnly` , aşağıdaki ek koruyucu ölçüleri göz önünde bulundurun:  
  
- **Si.** Özelliği bir sınıfın üyesiyse, [NotOverridable](notoverridable.md)' ın varsayılan yapmasına izin verin ve bunu veya bildirmeyin `Overridable` `MustOverride` . Bu, türetilmiş bir sınıfın bir geçersiz kılma aracılığıyla istenmeyen erişim yapmasını engeller.  
  
- **Erişim düzeyi.** Özelliğin hassas verilerini bir veya daha fazla değişkenlerde tutarsanız, başka hiçbir kodun erişemez olması için bunları [özel](private.md) olarak bildirin.  
  
- **Şifreleme.** Tüm hassas verileri düz metin yerine şifreli biçimde depolayın. Kötü amaçlı kod, bu bellek alanına bir şekilde erişim kazanıyorsa, verilerin kullanılması daha zordur. Şifreleme, hassas verileri serileştirmek için gerekliyse da yararlıdır.  
  
- **Sıfırlanması.** Özelliği tanımlayan sınıf, yapı veya modül sonlandırıldığı zaman, hassas verileri varsayılan değerlere veya daha anlamlı değerlere sıfırlayın. Bu, bellek alanı genel erişim için serbest bırakıldığında daha fazla koruma sağlar.  
  
- **Kalıcılığı.** Herhangi bir hassas verileri (örneğin, disk üzerinde) kalıcı olarak kullanmayın. Ayrıca, panoya gizli veriler eklemeyin.  
  
 `WriteOnly`Değiştirici Bu bağlamda kullanılabilir:  
  
 [Property Deyimi](../statements/property-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özelliğinin](readonly.md)
- [Özel](private.md)
- [Anahtar sözcükler](../keywords/index.md)
