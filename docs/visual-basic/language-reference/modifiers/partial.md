---
title: Kısmi
ms.date: 07/20/2015
f1_keywords:
- vb.Partial
- partial
helpviewer_keywords:
- structures [Visual Basic], partial
- classes [Visual Basic]
- partial, types [Visual Basic]
- partial, structures
- partial, classes [Visual Basic]
- classes [Visual Basic], partial
- Partial keyword [Visual Basic]
- type promotion
ms.assetid: 7adaef80-f435-46e1-970a-269fff63b448
ms.openlocfilehash: 2482facadd0e0528ed1b71df6edb4a447947a902
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867772"
---
# <a name="partial-visual-basic"></a>Kısmi (Visual Basic)

Tür bildiriminin türün kısmi bir tanımı olduğunu gösterir.  
  
 Anahtar sözcüğünü kullanarak, bir türün tanımını birkaç bildirim arasında bölebilirsiniz `Partial` . İstediğiniz kadar çok sayıda kısmi bildirim, istediğiniz kadar farklı kaynak dosyasında kullanabilirsiniz. Ancak, tüm bildirimlerin aynı derlemede ve aynı ad alanında olması gerekir.  
  
> [!NOTE]
> Visual Basic, genellikle kısmi sınıflarda uygulanan *Kısmi yöntemleri*destekler. Daha fazla bilgi için bkz. [kısmi Yöntemler](../../programming-guide/language-features/procedures/partial-methods.md) ve [Sub deyimleri](../statements/sub-statement.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
[ <attrlist> ] [ accessmodifier ] [ Shadows ] [ MustInherit | NotInheritable ] _  
Partial { Class | Structure | Interface | Module } name [ (Of typelist) ]  
    [ Inherits classname ]  
    [ Implements interfacenames ]  
    [ variabledeclarations ]  
    [ proceduredeclarations ]  
{ End Class | End Structure }  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`attrlist`|İsteğe bağlı. Bu tür için uygulanan özniteliklerin listesi. [Öznitelik listesini](../statements/attribute-list.md) açılı ayraç () içine almalısınız `< >` .|  
|`accessmodifier`|İsteğe bağlı. Hangi kodun bu türe erişebileceğini belirtir. [Visual Basic erişim düzeylerine](../../programming-guide/language-features/declared-elements/access-levels.md)bakın.|  
|`Shadows`|İsteğe bağlı. Bkz. [gölgeler](shadows.md).|  
|`MustInherit`|İsteğe bağlı. Bkz. [MustInherit](mustinherit.md).|  
|`NotInheritable`|İsteğe bağlı. [NotInheritable](notinheritable.md)öğesine bakın.|  
|`name`|Gereklidir. Bu türün adı. Aynı türdeki tüm diğer kısmi bildirimlerde tanımlanan adla eşleşmelidir.|  
|`Of`|İsteğe bağlı. Bunun genel bir tür olduğunu belirtir. Bkz. [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md).|  
|`typelist`|[Kullanıyorsanız gereklidir.](../statements/of-clause.md) Bkz. [tür listesi](../statements/type-list.md).|  
|`Inherits`|İsteğe bağlı. Bkz. [Inherits açıklaması](../statements/inherits-statement.md).|  
|`classname`|Kullanıyorsanız gereklidir `Inherits` . Bu sınıfın türetildiği sınıfın veya arabirimin adı.|  
|`Implements`|İsteğe bağlı. Bkz. [Implements açıklaması](../statements/implements-statement.md).|  
|`interfacenames`|Kullanıyorsanız gereklidir `Implements` . Bu türün uyguladığı arabirimlerin adları.|  
|`variabledeclarations`|İsteğe bağlı. Türün ek değişkenlerini ve olaylarını bildiren deyimler.|  
|`proceduredeclarations`|İsteğe bağlı. Tür için ek yordamlar bildiren ve tanımlayan deyimler.|  
|`End Class` veya `End Structure`|Bu kısmı `Class` veya `Structure` tanımı sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  

 Visual Basic, oluşturulan kodu ayrı kaynak dosyalardaki Kullanıcı tarafından yazılan koddan ayırmak için kısmi sınıf tanımları kullanır. Örneğin, **Windows Form Tasarımcısı** gibi denetimler için kısmi sınıfları tanımlar <xref:System.Windows.Forms.Form> . Bu denetimlerde oluşturulan kodu değiştirmemelisiniz.  
  
 Değiştirici kullanımı ve devralmayla ilgili olanlar gibi sınıf, yapı, arabirim ve modül oluşturma kuralları kısmi bir tür oluştururken geçerlidir.  
  
## <a name="best-practices"></a>En İyi Uygulamalar  
  
- Normal koşullarda, tek bir türün geliştirilmesini iki veya daha fazla bildirim arasında bölmemelisiniz. Bu nedenle, çoğu durumda `Partial` anahtar sözcüğe gerek kalmaz.  
  
- Okunabilirlik için, bir türün her kısmi bildirimi `Partial` anahtar sözcüğünü içermelidir. Derleyici en çok bir kısmi bildirimin anahtar sözcüğünü atmasını sağlar; iki veya daha fazla atlarsanız, derleyici bir hata bildirir.  
  
## <a name="behavior"></a>Davranış  
  
- **Bildirimlerin birleşimi.** Derleyici, türü tüm kısmi bildirimlerinin birleşimi olarak değerlendirir. Her kısmi tanımdaki her değiştirici tüm tür için geçerlidir ve her kısmi tanımdan her üye tüm tür için kullanılabilir.  
  
- **Modüllerde kısmi türler Için tür yükseltmeye Izin verilmiyor.** Kısmi Tanım bir modülün içindeyse, bu türden yükseltme otomatik olarak doldurulur. Böyle bir durumda, kısmi tanımlar kümesi beklenmedik sonuçlara ve hatta derleyici hatalarına neden olabilir. Daha fazla bilgi için bkz. [yükseltme türü](../../programming-guide/language-features/declared-elements/type-promotion.md).  
  
     Derleyici, kısmi tanımları yalnızca kendi tam yolları özdeş olduğunda birleştirir.  
  
 `Partial`Anahtar sözcüğü şu bağlamlarda kullanılabilir:  
  
 [Class Deyimi](../statements/class-statement.md)  
  
 [Structure Yapısı](../statements/structure-statement.md)  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, sınıfının tanımını `sampleClass` , her biri farklı bir yordam tanımlayan iki bildirime ayırır `Sub` .  
  
 [!code-vb[VbVbalrKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#3)]  
  
 Yukarıdaki örnekteki iki kısmi tanım aynı kaynak dosyasında veya iki farklı kaynak dosyada olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Class Deyimi](../statements/class-statement.md)
- [Structure Yapısı](../statements/structure-statement.md)
- [Tür Yükseltme](../../programming-guide/language-features/declared-elements/type-promotion.md)
- [Shadows](shadows.md)
- [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md)
- [Kısmi Yöntemler](../../programming-guide/language-features/procedures/partial-methods.md)
