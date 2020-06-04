---
title: Özel
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 524f03e77e075bef08a1b41b563985de41baacb6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404816"
---
# <a name="private-visual-basic"></a>Özel (Visual Basic)
Bir ya da daha fazla bildirilmemiş programlama öğesine, içerilen türlerin dahil olduğu gibi yalnızca kendi bildirim bağlamlarından erişilebilir olduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir programlama öğesi özel işlevselliği gösteriyorsa veya gizli veriler içeriyorsa, genellikle erişimi mümkün olduğunca kesin bir şekilde sınırlandırmak istersiniz. Yalnızca ona erişmek için onu tanımlayan modüle, sınıfa veya yapıya izin vererek en yüksek kısıtlamayı elde edersiniz. Bu şekilde bir öğeye erişimi sınırlandırmak için, ile bildirimini yapabilirsiniz `Private` .  

> [!NOTE]
> Ayrıca, bir üyeyi bu sınıftan ve kapsayan derlemede bulunan türetilmiş sınıflardan erişilebilir hale getiren [özel korumalı](private-protected.md) erişim değiştiricisini de kullanabilirsiniz.

## <a name="rules"></a>Kurallar  

- **Bildirim bağlamı.** `Private`Yalnızca modül düzeyinde kullanabilirsiniz. Bu, bir öğe için bildirim bağlamının `Private` bir modül, sınıf veya yapı olması ve kaynak dosya, ad alanı, arabirim veya yordam olması anlamına gelir.  
  
## <a name="behavior"></a>Davranış  
  
- **Erişim düzeyi.** Bir bildirim bağlamı içindeki tüm kod `Private` öğelerine erişebilir. Bu, iç içe geçmiş bir sınıf veya bir Numaralandırmadaki atama ifadesi gibi içerilen bir tür içindeki kodu içerir. Bildirim bağlamı dışında hiçbir kod `Private` öğelerine erişemez.  
  
- **Erişim değiştiricileri.** Erişim düzeyi belirten anahtar sözcüklere *erişim değiştiricileri*denir. Erişim değiştiricilerinden oluşan bir karşılaştırma için bkz. [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Private`Değiştirici şu bağlamlarda kullanılabilir:  
  
 [Class Deyimi](../statements/class-statement.md)  
  
 [Const Deyimi](../statements/const-statement.md)  
  
 [Declare Deyimi](../statements/declare-statement.md)  
  
 [Delegate Deyimi](../statements/delegate-statement.md)  
  
 [Dim Deyimi](../statements/dim-statement.md)  
  
 [Enum Deyimi](../statements/enum-statement.md)  
  
 [Event Deyimi](../statements/event-statement.md)  
  
 [Function Deyimi](../statements/function-statement.md)  
  
 [Interface Deyimi](../statements/interface-statement.md)  
  
 [Property Deyimi](../statements/property-statement.md)  
  
 [Structure Yapısı](../statements/structure-statement.md)  
  
 [Sub Deyimi](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Geneldir](public.md)
- [Korunamadı](protected.md)
- [Dost](friend.md)
- [Özel korumalı](./private-protected.md)
- [Protected Friend](./protected-friend.md)
- [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Yordamlar](../../programming-guide/language-features/procedures/index.md)
- [Yapılar](../../programming-guide/language-features/data-types/structures.md)
- [Nesneler ve sınıflar](../../programming-guide/language-features/objects-and-classes/index.md)
