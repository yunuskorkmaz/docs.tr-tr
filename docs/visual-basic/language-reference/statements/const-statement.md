---
title: Const Deyimi (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 089c2dca99373f379e1eff319cf8c41242e5f135
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638322"
---
# <a name="const-statement-visual-basic"></a>Const Deyimi (Visual Basic)
Bildirir ve bir veya daha fazla sabitlerini tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## <a name="parts"></a>Bölümler  
 `attributelist`  
 İsteğe bağlı. İçin tüm sabit uygulanan öznitelikler listesinde bu deyiminde bildirilen. Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraçlar içinde ("`<`"ve"`>`").  
  
 `accessmodifier`  
 İsteğe bağlı. Hangi kod bu sabiti erişebileceğini belirtmek için bunu kullanın. Olabilir [genel](../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [özel](../../../visual-basic/language-reference/modifiers/private.md), veya [Korunan özel](../../language-reference/modifiers/private-protected.md).
  
 `Shadows`  
 İsteğe bağlı. Bu, yeniden bildirmek ve temel sınıfta bir programlama öğesi gizlemek için kullanın. Bkz: [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `constantlist`  
 Gerekli. Bu deyiminde bildirilen sabit listesi.  
  
 `constant` `[ ,` `constant` `... ]`  
  
 Her `constant` aşağıdaki söz dizimini ve bölümleri vardır:  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|Bölümü|Açıklama|  
|----------|-----------------|  
|`constantname`|Gerekli. Sabit adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`datatype`|Gerekli if `Option Strict` olduğu `On`. Sabit veri türü.|  
|`initializer`|Gerekli. Derleme zamanında değerlendirilir ve sabiti için atanan ifade.|  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulamanızda asla değişmez bir değer varsa, adlandırılmış bir konstantu ve değişmez değer yerine kullanın. Bir ad, bir değer kolaydır. Yalnızca bir kez konstantu ve birçok yerde kodunuzda kullanabilirsiniz. Sonraki bir sürümde değeri yeniden tanımlanacak ihtiyacınız varsa `Const` deyimi bir değişiklik yapmanız gereken tek yerdir.  
  
 Kullanabileceğiniz `Const` yalnızca düzeyinde modülü veya yordam. Başka bir deyişle *bildirim içeriğinin* bir değişken sınıf, yapı, modülü, yordam veya blok olmalıdır ve bir kaynak dosyası, ad alanı veya arabirimi olamaz. Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Yerel Sabitleri (bir yordam) içindeki varsayılan genel erişim ve bunlar üzerinde herhangi bir erişim değiştiricileri kullanamazsınız. Özel erişim sınıfı ve modül üye Sabitleri (dışında herhangi bir yordam) varsayılan ve yapı üyesi sabitleri varsayılan genel erişim için. Erişim değiştiricileri ile kullanıcıların erişim düzeylerini ayarlayabilirsiniz.  
  
## <a name="rules"></a>Kurallar  
  
- **Bildirim bağlamı.** Bir sabit bildirilen her türlü yordam dışında Modül düzeyinde bir *üyeye sabitine*; yapısı, sınıfın bir üyesidir veya modül bildiren.  
  
     Yordam düzeyinde bildirilen bir sabit değeri bir *yerel sabit*; yordam veya onu bildiren blok için yereldir.  
  
- **Öznitelikleri.** Öznitelikleri yalnızca üye sabitleri için değil, yerel sabit uygulayabilirsiniz. Bir özniteliği derleme meta bilgileri yerel sabitler gibi geçici depolama için anlamlı değil katkıda bulunur.  
  
- **Değiştiriciler.** Varsayılan olarak, tüm sabittir `Shared`, `Static`, ve `ReadOnly`. Bu anahtar sözcüklerden biri bir sabiti bildirirken kullanamazsınız.  
  
     Yordam düzeyinde kullanamazsınız `Shadows` veya herhangi bir erişim değiştiricilerine yerel sabitleri bildirmek için.  
  
- **Birden fazla sabit.** Aynı bildirim deyiminde birkaç sabitleri bildirebilirsiniz belirtme `constantname` her biri için bölüm. Birden fazla sabit virgülle ayrılır.  
  
## <a name="data-type-rules"></a>Veri türü kuralları  
  
- **Veri türleri.** `Const` İfadesi bir değişken veri türünü bildirebilirsiniz. Herhangi bir veri türü veya bir numaralandırma adını belirtebilirsiniz.  
  
- **Varsayılan türü.** Siz belirtmezseniz `datatype`, veri türü sabit alır `initializer`. Her ikisini de belirtirseniz `datatype` ve `initializer`, veri türü `initializer` dönüştürülebilmelidir `datatype`. Kullanılmazsa `datatype` ya da `initializer` varsa, veri türü için varsayılan değerleri `Object`.  
  
- **Farklı türler.** Farklı veri türleri farklı sabitleri için ayrı bir kullanarak belirtebileceğiniz `As` bildirdiğiniz her bir değişken yan tümcesi. Ancak, ortak bir'ı kullanarak aynı türde olacak şekilde birkaç sabitleri bildiremezsiniz `As` yan tümcesi.  
  
- **Başlatma.** Her sabiti değerini başlatmalıdır `constantlist`. Kullandığınız `initializer` sabiti için atanmış bir ifade sağlamanız için. İfade değişmez değerleri, önceden tanımlanmış diğer sabitleri ve önceden tanımlanmış numaralandırma üyeleri herhangi bir birleşimi olabilir. Bu öğeleri birleştirin, aritmetik ve mantıksal işleçlerini kullanabilirsiniz.  
  
     Değişkenler veya işlevlerinde kullanılamaz `initializer`. Bununla birlikte, dönüşüm anahtar sözcükleri gibi kullanabileceğiniz `CByte` ve `CShort`. Ayrıca `AscW` bir sabit ile çağırırsanız `String` veya `Char` bağımsız değişkeni, derleme zamanında değerlendirilebilen olduğundan.  
  
## <a name="behavior"></a>Davranış  
  
- **Kapsam.** Yerel sabitleri, yordam veya blok içinde yalnızca erişilebilir. Üye sabitleri herhangi bir yerde kendi sınıf, yapı veya modül içinde erişilebilir.  
  
- **Nitelik.** Kod bir sınıf dışında yapısını veya modülünü üye sabitin adı bu sınıf, yapı veya modül adıyla nitelemeniz gerekir. Bir yordam veya blok Bu yordam veya blok içinde herhangi bir yerel sabit başvurulamaz dışındaki kod.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Const` sabitler değişmez değerler yerine kullanılmak için deyimi.  
  
 [!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]  
  
## <a name="example"></a>Örnek  
 Veri türüne sahip bir sabit tanımlarsanız `Object`, isteğe bağlı olarak Visual Basic Derleyicisi türünü verir `initializer`, yerine `Object`. Aşağıdaki örnekte, sabit `naturalLogBase` çalışma zamanı türü `Decimal`.  
  
 [!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]  
  
 Önceki örnekte <xref:System.Type.ToString%2A> metodunda <xref:System.Type> tarafından döndürülen nesne [GetType işleci](../../../visual-basic/language-reference/operators/gettype-operator.md), çünkü <xref:System.Type> dönüştürülemez `String` kullanarak `CStr`.  
  
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
