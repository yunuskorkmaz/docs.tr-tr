---
title: "'<interfacename>.<membername>', '<baseclassname>' temel sınıfı tarafından zaten uygulandı. <type> öğesinin yeniden uygulandığı varsayılıyor"
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 4056c61bf6556f54276817c1c105ba7a17b6fd5a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873937"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a>'\<interfacename>.\<membername>', '\<baseclassname>' temel sınıfı tarafından zaten uygulandı. \<type> öğesinin yeniden uygulandığı varsayılıyor

Türetilmiş sınıftaki bir özellik, yordam veya olay, `Implements` temel sınıfta zaten uygulanmış olan bir arabirim üyesini belirten bir yan tümce kullanır.  
  
 Türetilmiş bir sınıf, temel sınıfı tarafından uygulanan bir arabirim üyesini yeniden uygulayabilir. Bu, temel sınıf uygulamasını geçersiz kılma ile aynı değildir. Daha fazla bilgi için bkz. [Implements](../statements/implements-clause.md).  
  
 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata kimliği:** BC42015  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Arabirim üyesini yeniden uygulamak istiyorsanız, herhangi bir işlem yapmanız gerekmez. Türetilmiş sınıfınıza ait kod, `MyBase` temel sınıf uygulamasına erişmek için anahtar sözcüğünü kullanmadığınız müddetçe yeniden uygulanan üyeye erişir.  
  
- Arabirim üyesini yeniden uygulamayı düşünmüyorsanız, `Implements` özelliğinden, yordamdan veya olay bildiriminden yan tümceyi kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Arabirimler](../../programming-guide/language-features/interfaces/index.md)
