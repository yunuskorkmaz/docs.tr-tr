---
title: "'<interfacename>. <membername>' taban sınıfı tarafından zaten uygulanmış '<baseclassname>'. Yeniden uygulanmasına <type> varsayıldı"
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 64bd7771820c2a4073350b7a5189d3a32c4775be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921335"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a>'\<InterfaceName >. \<membername >' taban sınıfının tarafından zaten uygulanmış\<baseclassname >'. Yeniden uygulanmasına \<türü > varsayıldı
Bir özellik, yordam veya türetilmiş bir sınıf içinde olay kullanan bir `Implements` temel sınıfta zaten uygulanmış bir arabirim üyesi belirleme yan tümcesi.  
  
 Türetilmiş bir sınıf, taban sınıfı tarafından uygulanan bir arabirim üyesi yeniden uygulayın. Bu temel sınıf uygulamasına geçersiz kılma ile aynı değildir. Daha fazla bilgi için [uygular](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz: [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42015  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Arabirim üyesini yeniden uygulayın yapmak istiyorsanız, herhangi bir eylemde bulunmanız gerekmez. Türetilmiş sınıfınızın kodda erişen reimplemented üye kullanılmadıkça `MyBase` temel sınıf uygulamasına erişmek için anahtar sözcüğü.  
  
- Arabirim üyesini yeniden uygulayın düşünmüyorsanız kaldırmak `Implements` özellik, yordam veya olay bildiriminin from yan tümcesi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arabirimler](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
