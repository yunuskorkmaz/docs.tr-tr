---
title: Const Deyimi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 720a465f1459b663a1fca2a48856f51762328459
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="const-statement-visual-basic"></a>Const Deyimi (Visual Basic)
Bildirir ve bir veya daha fazla sabitleri tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ]   
Const constantlist  
```  
  
## <a name="parts"></a>Bölümler  
 `attributelist`  
 İsteğe bağlı. İçin tüm sabit uygulamak özniteliklerin listesi, bu deyim içinde bildirildi. Bkz: [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraç ("`<`"ve"`>`").  
  
 `accessmodifier`  
 İsteğe bağlı. Hangi kod bu sabitleri erişebileceğini belirtmek için bunu kullanın. Olabilir [ortak](../../../visual-basic/language-reference/modifiers/public.md), [korumalı](../../../visual-basic/language-reference/modifiers/protected.md), [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md), `Protected Friend`, veya [özel](../../../visual-basic/language-reference/modifiers/private.md).  
  
 `Shadows`  
 İsteğe bağlı. Redeclare ve bir programlama öğesi bir taban sınıf içinde gizlemek için bunu kullanın. Bkz: [gölgeleri](../../../visual-basic/language-reference/modifiers/shadows.md).  
  
 `constantlist`  
 Gerekli. Bu deyim içinde bildirilen sabitleri listesi.  
  
 `constant``[ ,``constant``... ]`  
  
 Her `constant` aşağıdaki söz dizimini ve bölümleri vardır:  
  
 `constantname` `[ As` `datatype` `] =` `initializer`  
  
|Bölümü|Açıklama|  
|----------|-----------------|  
|`constantname`|Gerekli. Sabit adı. Bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`datatype`|Gerekli olursa `Option Strict` olan `On`. Sabit veri türü.|  
|`initializer`|Gerekli. Derleme zamanında değerlendirilir ve sabite atanan ifade.|  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulamanızda hiçbir zaman değiştiren bir değer varsa, adlandırılmış bir sabit tanımlamak ve bir hazır değer yerine kullanın. Bir değerden daha kolay addır. Yalnızca bir kez sabiti tanımlayabilir ve birçok yerde kodunuzda kullanabilirsiniz. Sonraki bir sürümde değeri yeniden tanımlamanız gerekiyorsa, `Const` deyimi bir değişiklik yapmanız gereken tek yerdir.  
  
 Kullanabileceğiniz `Const` yalnızca düzeyinde modül veya yordam. Yani *bildirimi bağlam* bir değişken sınıfı, yapısı, modül, yordam veya blok olmalı ve bir kaynak dosyasını, ad alanı veya arabirim olamaz. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Yerel Sabitleri (içinde bir yordam) varsayılan genel erişim ve bunlar üzerinde hiçbir erişim değiştiricileri kullanamazsınız. Özel erişim için üye Sabitleri (dışında herhangi bir yordam) varsayılan sınıf ve modül ve yapısı üye sabitleri varsayılan genel erişim için. Erişim değiştiricileri ile erişim düzeylerine göre ayarlayabilirsiniz.  
  
## <a name="rules"></a>Kurallar  
  
-   **Bildirim bağlamı.** Bir sabit bildirilmiş herhangi bir yordam dışında modülü düzeyinde bir *üye sabiti*; sınıf, yapı, üyesi olan veya modülü bildiren onu.  
  
     Yordam düzeyinde bildirilen bir sabit değer bir *yerel sabit*; yordamı ya da onu tanımlandığı blok yereldir.  
  
-   **Öznitelikler.** Öznitelikleri yalnızca üye sabitleri için değil, yerel sabitleri uygulayabilirsiniz. Bir öznitelik derlemenin meta verilerini, bilgileri yerel sabitleri gibi geçici depolama için anlamlı olmayan katkıda bulunur.  
  
-   **Değiştirici.** Varsayılan olarak, tüm sabittir `Shared`, `Static`, ve `ReadOnly`. Bu anahtar sözcükler herhangi bir sabit bildirirken kullanamazsınız.  
  
     Yordam düzeyinde kullanamazsınız `Shadows` veya herhangi bir erişim değiştiricileri yerel sabitleri bildirin.  
  
-   **Birden çok sabitleri.** Aynı bildirimi deyiminde birkaç sabitleri bildirebilir belirtme `constantname` her biri için bölüm. Birden çok sabitleri virgülle ayrılır.  
  
## <a name="data-type-rules"></a>Veri türü kuralları  
  
-   **Veri türleri.** `Const` İfadesi bir değişken veri türü bildirebilirsiniz. Herhangi bir veri türü veya numaralandırma adını belirtebilirsiniz.  
  
-   **Varsayılan türü.** Belirtmezseniz, `datatype`, sabit veri türünü alır `initializer`. Her ikisini de belirtirseniz, `datatype` ve `initializer`, veri türü `initializer` dönüştürülebilir olmalıdır `datatype`. Ne `datatype` ya da `initializer` varsa, veri türü için varsayılan `Object`.  
  
-   **Farklı türler.** Ayrı bir kullanarak farklı veri türleri için farklı sabitleri belirtebilirsiniz `As` yan tümcesi bildirdiğiniz her değişken için. Ancak, ortak bir kullanarak aynı türde olması için birkaç sabitleri bildiremezsiniz `As` yan tümcesi.  
  
-   **Başlatma.** Her sabit değeri başlatmalıdır `constantlist`. Kullandığınız `initializer` sabite atanacak bir ifade sağlamak için. İfade değişmez değerleri, önceden tanımlanmış diğer sabitleri ve önceden tanımlanmış numaralandırma üyeleri herhangi bir bileşimi olabilir. Bu öğeler birleştirmek için aritmetik ve mantıksal işleçleri kullanabilirsiniz.  
  
     Değişkenleri veya işlevleri kullanamazsınız `initializer`. Ancak, dönüşüm anahtar sözcükleri gibi kullanabilir `CByte` ve `CShort`. Aynı zamanda `AscW` bir sabit ile çağırırsanız `String` veya `Char` derleme zamanında değerlendirilebilir beri bağımsız değişkeni.  
  
## <a name="behavior"></a>Davranış  
  
-   **Kapsamı.** Yerel sabitleri kendi yordamı veya bloğu içinde yalnızca erişilebilir. Üye sabitleri herhangi bir yere kendi sınıf, yapı veya modülü içinde erişilebilir.  
  
-   **Niteliğe.** Kod bir sınıf dışında yapısı veya modülü bu sınıf, yapı veya modül adını üye sabit 's adıyla nitelemeniz gerekir. Dış bir yordam veya blok Bu yordam veya bloğu içinde herhangi bir yerel sabit başvuramaz kodu.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `Const` sabitleri değişmez değerler yerine kullanılacak bildirmek için deyimi.  
  
 [!code-vb[VbVbalrStatements#13](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_1.vb)]  
  
## <a name="example"></a>Örnek  
 Veri türüne sahip bir sabit tanımlarsanız `Object`, Visual Basic derleyici, bu tür verir `initializer`, yerine `Object`. Aşağıdaki örnekte, sabit `naturalLogBase` çalışma zamanı türüne sahip `Decimal`.  
  
 [!code-vb[VbVbalrStatements#87](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/const-statement_2.vb)]  
  
 Önceki örnekte kullanan <xref:System.Type.ToString%2A> yöntemi <xref:System.Type> tarafından döndürülen nesne [GetType işleci](../../../visual-basic/language-reference/operators/gettype-operator.md), çünkü <xref:System.Type> dönüştürülemiyor `String` kullanarak `CStr`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [Enum deyimi](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [#Const yönergesi](../../../visual-basic/language-reference/directives/const-directive.md)  
 [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ReDim deyimi](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Örtük ve açık dönüştürmeler](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Sabitler ve numaralandırmalar](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 [Sabitler ve numaralandırmalar](../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [Tür dönüşüm işlevleri](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
