---
title: Const Deyimi (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 522ac71767707ae90a3f1d11d45ef8b29471ae6c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005115"
---
# <a name="const-statement-visual-basic"></a>Const Deyimi (Visual Basic)
Bir veya daha fazla sabiti bildirir ve tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## <a name="parts"></a>Bölümler  
 `attributelist`  
 İsteğe bağlı. Bu bildirimde belirtilen tüm sabitlere uygulanan özniteliklerin listesi. Bkz. [öznitelik listesine](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraçlar ("`<`" ve "`>`").  
  
 `accessmodifier`  
 İsteğe bağlı. Bu sabitlere hangi kodun erişebileceğini belirtmek için bunu kullanın. [Ortak](../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md), [korumalı arkadaş](../modifiers/protected-friend.md), [özel](../../../visual-basic/language-reference/modifiers/private.md)veya [özel korumalı](../../language-reference/modifiers/private-protected.md)olabilir.
  
 `Shadows`  
 İsteğe bağlı. Bir temel sınıftaki programlama öğesini yeniden bildirmek ve gizlemek için bunu kullanın. Bkz. [gölgeler](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `constantlist`  
 Gerekli. Bu bildirimde bildirildiği sabitlerin listesi.  
  
 `constant` `[ ,` `constant` `... ]`  
  
 Her `constant` aşağıdaki söz dizimi ve bölümlere sahiptir:  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|Bölümüyle|Açıklama|  
|----------|-----------------|  
|`constantname`|Gerekli. Sabitin adı. Bkz. [tanımlanmış öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`datatype`|@No__t-0 `On` ise gereklidir. Sabitin veri türü.|  
|`initializer`|Gerekli. Derleme zamanında değerlendirilen ve sabitine atanan ifade.|  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulamanızda hiçbir değişiklik olmayan bir değer varsa, adlandırılmış bir sabit tanımlayabilir ve bunu bir sabit değer yerine kullanabilirsiniz. Bir ad, bir değerden daha kolay anımsanacak. Sabiti yalnızca bir kez tanımlayabilir ve kodunuzda birçok yerde kullanabilirsiniz. Daha sonraki bir sürümde değeri yeniden tanımlamanız gerekiyorsa `Const` ifadesinde değişiklik yapmanız gereken tek yer vardır.  
  
 @No__t-0 ' i yalnızca modül veya yordam düzeyinde kullanabilirsiniz. Diğer bir deyişle, bir değişken için *Bildirim bağlamı* bir sınıf, yapı, modül, yordam veya blok olmalıdır ve kaynak dosya, ad alanı veya arabirim olamaz. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Yerel sabitler (bir yordam içinde) varsayılan olarak genel erişime ve bunlara hiçbir erişim değiştiricilerini kullanamazsınız. Sınıf ve modül üyesi sabitleri (herhangi bir yordam dışında), özel erişim için varsayılan olarak, üye sabitlerinin varsayılan olarak ortak erişimine sahiptir. Erişim değiştiricilerini kullanarak erişim düzeylerini ayarlayabilirsiniz.  
  
## <a name="rules"></a>Kurallar  
  
- **Bildirim bağlamı.** Modül düzeyinde belirtilen bir sabit, herhangi bir yordamın dışında, bir *üye sabiti*; Onu bildiren sınıf, yapı veya modülün bir üyesidir.  
  
     Yordam düzeyinde belirtilen bir sabit, yerel bir *sabittir*; Bu, onu bildiren yordamın veya bloğun yereldir.  
  
- **Özelliklerine.** Öznitelikleri yerel sabitlere değil yalnızca üye sabitlerine uygulayabilirsiniz. Bir öznitelik, bilgileri derlemenin meta verilerine katkıda bulunur ve bu, yerel sabitler gibi geçici depolama için anlamlı değildir.  
  
- **İlerine.** Varsayılan olarak, tüm sabitler `Shared`, `Static` ve `ReadOnly` ' dir. Bir sabit bildirirken bu anahtar sözcüklerden hiçbirini kullanamazsınız.  
  
     Yordam düzeyinde, yerel sabitleri bildirmek için `Shadows` veya herhangi bir erişim değiştiricilerini kullanamazsınız.  
  
- **Birden çok sabit.** Aynı bildirim ifadesinde, her biri için `constantname` bölümünü belirterek birçok sabit bildirebilirsiniz. Birden çok sabit virgülle ayrılır.  
  
## <a name="data-type-rules"></a>Veri türü kuralları  
  
- **Veri türleri.** @No__t-0 bildirimi, bir değişkenin veri türünü bildirebilirler. Herhangi bir veri türü veya bir numaralandırma adı belirtebilirsiniz.  
  
- **Varsayılan tür.** @No__t-0 ' ı belirtmezseniz, sabit `initializer` ' in veri türünü alır. @No__t-0 ve `initializer` ' i belirtirseniz, `initializer` ' nin veri türü `datatype` ' e dönüştürülebilir olmalıdır. Ne `datatype` ne de `initializer` yoksa, veri türü varsayılan olarak `Object` ' dir.  
  
- **Farklı türler.** Bildirdiğiniz her değişken için ayrı bir `As` yan tümcesi kullanarak farklı sabitler için farklı veri türleri belirtebilirsiniz. Ancak, ortak bir `As` yan tümcesini kullanarak aynı türde olan birkaç sabiti bildiremezsiniz.  
  
- **Başlatılmasında.** @No__t-0 ' da her bir sabit değeri başlatmalısınız. @No__t-0 kullanarak sabitine atanacak bir ifade sağlayabilirsiniz. İfade, herhangi bir sabit değer, önceden tanımlanmış diğer sabitler ve önceden tanımlanmış sabit listesi üyeleri olabilir. Bu tür öğeleri birleştirmek için aritmetik ve mantıksal işleçler kullanabilirsiniz.  
  
     @No__t-0 ' da değişkenleri veya işlevleri kullanamazsınız. Ancak, `CByte` ve `CShort` gibi dönüştürme anahtar sözcüklerini kullanabilirsiniz. @No__t-0 ' ı bir sabit `String` veya `Char` bağımsız değişkeniyle çağırırsanız, bu, derleme zamanında değerlendirilebileceğinizden de kullanabilirsiniz.  
  
## <a name="behavior"></a>Davranış  
  
- **Kapsam.** Yerel sabitler yalnızca kendi yordamının veya bloğunun içinden erişilebilir. Üye sabitlerine, sınıfları, yapısı veya modülü içinde herhangi bir yerden erişilebilir.  
  
- **Yeter.** Bir sınıf, yapı veya modülün dışındaki kodun, bir üye sabitinin adını bu sınıf, yapı veya modülün adı ile nitelemeniz gerekir. Bir yordamın veya bloğun dışındaki kod, bu yordam veya blok içindeki herhangi bir yerel sabitlere başvuramaz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, sabit değerlerin yerine kullanılacak sabitleri bildirmek için `Const` ifadesini kullanır.  
  
 [!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]  
  
## <a name="example"></a>Örnek  
 @No__t-0 veri türüyle bir sabit tanımlarsanız Visual Basic derleyici, `Object` yerine `initializer` türü verir. Aşağıdaki örnekte, `naturalLogBase` ' ın sabit `Decimal` çalışma zamanı türü vardır.  
  
 [!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]  
  
 Yukarıdaki örnekte, <xref:System.Type> `CStr` kullanılarak `String` ' e dönüştürülemediği için, [GetType işleci](../../../visual-basic/language-reference/operators/gettype-operator.md)tarafından döndürülen <xref:System.Type> nesnesi üzerinde <xref:System.Type.ToString%2A> yöntemini kullanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [Enum Deyimi](../../../visual-basic/language-reference/statements/enum-statement.md)
- [#Const Yönergesi](../../../visual-basic/language-reference/directives/const-directive.md)
- [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)
- [ReDim Deyimi](../../../visual-basic/language-reference/statements/redim-statement.md)
- [Örtük ve Açık Dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Sabitler ve Sabit Listeleri](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [Sabitler ve Sabit Listeleri](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [Tür Dönüştürme İşlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
