---
title: Event deyimi (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Event
- vb.Custom
helpviewer_keywords:
- Event statement [Visual Basic]
- declaring events [Visual Basic], syntax
- Public keyword [Visual Basic], Event statements
- Custom keyword [Visual Basic]
- declarations [Visual Basic], events
- event keyword [Visual Basic]
- WithEvents keyword [Visual Basic], Event statements
- events [Visual Basic], declaring
- ByVal keyword [Visual Basic], Event statements
- events [Visual Basic], custom
- ByRef keyword [Visual Basic], Event statements
- declaring user-defined events
ms.assetid: 306ff8ed-74dd-4b6a-bd2f-e91b17474042
ms.openlocfilehash: 5ae25cbca73f7c8e767cad0ac332d77c306724a1
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43739103"
---
# <a name="event-statement"></a>Event Deyimi
Kullanıcı tanımlı bir olay bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Event eventname[(parameterlist)] _  
[ Implements implementslist ]  
' -or-  
[ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Event eventname As delegatename _  
[ Implements implementslist ]  
' -or-  
 [ <attrlist> ] [ accessmodifier ] _  
[ Shared ] [ Shadows ] Custom Event eventname As delegatename _  
[ Implements implementslist ]  
   [ <attrlist> ] AddHandler(ByVal value As delegatename)  
      [ statements ]  
   End AddHandler  
   [ <attrlist> ] RemoveHandler(ByVal value As delegatename)  
      [ statements ]  
   End RemoveHandler  
   [ <attrlist> ] RaiseEvent(delegatesignature)  
      [ statements ]  
   End RaiseEvent  
End Event  
```  
  
## <a name="parts"></a>Bölümler  
  
|Bölümü|Açıklama|  
|---|---|  
|`attrlist`|İsteğe bağlı. Bu olaya uygulanan öznitelikler listesi. Birden çok öznitelik virgülle ayrılır. İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraçlar içinde ("`<`"ve"`>`").|  
|`accessmodifier`|İsteğe bağlı. Hangi kod olay erişip belirtir. Aşağıdakilerden biri olabilir:<br /><br /> -   [Genel](../../../visual-basic/language-reference/modifiers/public.md)— bildirir, öğe erişimi olan herhangi bir kod da erişebilirsiniz.<br />-   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)— yalnızca kendi sınıfı veya türetilmiş bir sınıf içinde kod da erişebilir.<br />-   [Arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)— yalnızca aynı bütünleştirilmiş kodda, erişebilir.<br />-   [Özel](../../../visual-basic/language-reference/modifiers/private.md)— yalnızca onu bildiren öğesindeki kodu erişebilirsiniz.<br /> -   [Korumalı Friend](../../language-reference/modifiers/protected-friend.md)-yalnızca olay sınıfı, türetilmiş bir sınıf ya da aynı bütünleştirilmiş kod da erişebilir. <br />- [Özel korumalı](../../language-reference/modifiers/private-protected.md)-yalnızca olay sınıfı veya türetilmiş sınıf içinde aynı bütünleştirilmiş kodda, erişebilir.|  
|`Shared`|İsteğe bağlı. Bu olay bir sınıf veya yapı belirli örneği ile ilişkili olduğunu belirtir.|  
|`Shadows`|İsteğe bağlı. Bu olay redeclares ve bir programlama aynı adlı bir öğeyi veya taban sınıfında aşırı yüklenmiş bir öğe kümesini gizler gösterir. Bildirilen öğe herhangi bir türden başka bir tür ile gölge.<br /><br /> Gölgeli öğe, dışında gölgeleme öğesi erişilemez olduğu gelen gölgeleri türetilmiş sınıf içinde kullanılamaz. Örneğin, bir `Private` öğesi bir temel sınıf öğesi, erişim iznine sahip olmayan kod gölgeliyor `Private` öğe temel sınıf öğe yerine erişir.|  
|`eventname`|Gerekli. Olayın adı; Standart değişken adlandırma kurallarını izler.|  
|`parameterlist`|İsteğe bağlı. Bu olay parametrelerinin temsil eden yerel değişkenlerin listesi. İçine almalısınız [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md) parantez içinde.|  
|`Implements`|İsteğe bağlı. Bu olay bir olay arabirim uyguladığını belirtir.|  
|`implementslist`|Gerekli if `Implements` sağlanır. Listesi `Sub` uygulanmakta olan yordamlar. Birden çok yordam virgülle ayrılır:<br /><br /> *implementedprocedure* [, *implementedprocedure* ...]<br /><br /> Her `implementedprocedure` aşağıdaki söz dizimini ve bölümleri vardır:<br /><br /> `interface`.`definedname`<br /><br /> -   `interface` -Gerekli. Bu yordam, sınıf veya yapı içeren uygulamanın bir arabirimin adını uygular.<br />-   `Definedname` -Gerekli. Ad tarafından yordamı tanımlanan `interface`. Bu aynı olmak zorunda değil `name`, tanımlı bir yordamdan uygulamak için bu yordamı kullanarak ad.|  
|`Custom`|Gerekli. Olaylar olarak bildirilen `Custom` özel tanımlamalıdır `AddHandler`, `RemoveHandler`, ve `RaiseEvent` erişimcileri.|  
|`delegatename`|İsteğe bağlı. Olay işleyici signatura bir temsilci adı.|  
|`AddHandler`|Gerekli. Bildiren bir `AddHandler` bir olay işleyicisi eklendiğinde çalıştırılacak deyimleri belirtir, kullanarak ya da açıkça erişimci `AddHandler` deyimi kullanarak örtük olarak veya `Handles` yan tümcesi.|  
|`End AddHandler`|Gerekli. Sonlandırır `AddHandler` blok.|  
|`value`|Gerekli. Parametre adı.|  
|`RemoveHandler`|Gerekli. Bildiren bir `RemoveHandler` kullanarak bir olay işleyicisi kaldırıldığında çalıştırılacak deyimleri belirtir erişimci `RemoveHandler` deyimi.|  
|`End RemoveHandler`|Gerekli. Sonlandırır `RemoveHandler` blok.|  
|`RaiseEvent`|Gerekli. Bildiren bir `RaiseEvent` kullanarak olay ortaya çıktığında çalıştırılacak deyimleri belirtir erişimci `RaiseEvent` deyimi. Genellikle, bu temsilcileri tarafından tutulan bir listesini başlatır `AddHandler` ve `RemoveHandler` erişimcileri.|  
|`End RaiseEvent`|Gerekli. Sonlandırır `RaiseEvent` blok.|  
|`delegatesignature`|Gerekli. Gereken parametrelerle eşleşen parametrelerinin listesi `delegatename` temsilci. İçine almalısınız [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md) parantez içinde.|  
|`statements`|İsteğe bağlı. Gövdeleri içeren ifadeler `AddHandler`, `RemoveHandler`, ve `RaiseEvent` yöntemleri.|  
|`End Event`|Gerekli. Sonlandırır `Event` blok.|  
  
## <a name="remarks"></a>Açıklamalar  
 Olay bildirildikten sonra kullanın `RaiseEvent` deyimini olayı oluşturun. Tipik bir olay bildirildi ve aşağıdaki parçası gösterildiği gibi oluşturulur:  
  
 [!code-vb[VbVbalrEvents#13](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_1.vb)]  
  
> [!NOTE]
>  Yordamlar, aşağıdaki istisnalarla birlikte bağımsız olarak olay bağımsız değişkenleri bildirebilirsiniz: olay bağımsız değişkenleri, adlandırılmış olamaz `ParamArray` bağımsız değişken veya `Optional` bağımsız değişkenler. Olaylar, dönüş değeri yoktur.  
  
 Bir olayı işlemek için onu kullanarak bir olay işleyicisi alt ile ilişkilendirmelisiniz `Handles` veya `AddHandler` deyimi. Alt yordam ve olay imzalarını eşleşmesi gerekir. Paylaşılan bir olayı işlemek için kullanmalısınız `AddHandler` deyimi.  
  
 Kullanabileceğiniz `Event` yalnızca Modül düzeyinde. Başka bir deyişle *bildirim içeriğinin* bir olay, bir sınıf, yapı, modül veya arabirimi olması gerekir ve bir kaynak dosyası, ad alanı, yordam veya blok olamayacağı için. Daha fazla bilgi için [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Çoğu durumda, olayları bildirmek için bu konunun söz dizimi bölümünde ilk sözdizimini kullanabilirsiniz. Ancak, bazı senaryolar, olayın ayrıntılı davranışı hakkında daha fazla denetime sahip olmasını gerektirir. Son söz dizimini kullanan bu konu, sözdizimi bölümündeki `Custom` anahtar sözcüğü, özel olaylar tanımlamanıza olanak sağlayarak bu denetim sağlar. Özel bir olay tam olarak bir olay işleyicisi için kod ekler veya kaldırdığında veya olaydan neler veya ne zaman kod olayını belirtin. Örnekler için bkz [nasıl yapılır: tasarrufu bellek için olan özel olayları bildirme](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) ve [nasıl yapılır: bildirmek özel olayları önlemek engellemesine](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, 0, 10 saniye basılı saymak için olayları kullanır. Kod birkaç ilgili olay yöntemleri, özellikleri ve ifadeleri gösterir. Bu içerir `RaiseEvent` deyimi.  
  
 Bir olay başlatır sınıf olay kaynağı olan ve olay işleme yöntemleri olay işleyicileridir. Olay kaynağı, oluşturduğu olaylar için birden çok işleyiciler olabilir. Olay sınıfı başlatır, nesnenin Bu örneği için olayları işlemek için katılmamayı her sınıfta bu olay tetiklenir.  
  
 Örnek ayrıca bir form kullanır (`Form1`) bir düğme olan (`Button1`) ve bir metin kutusu (`TextBox1`). Düğmeye tıkladığınızda, 10'dan geri sayım 0 saniyeye ilk metin kutusunu görüntüler. Tam zamanlı (10 saniye) geçtikten sonra "Bitti" ilk metin kutusunu görüntüler.  
  
 Kodu `Form1` formun ilk ve terminal durumunu belirtir. Ayrıca, olaylar oluştuğunda yürütülen kodu içerir.  
  
 Bu örneği kullanmak için yeni bir Windows Forms projesi açın. Ardından adlı bir düğme ekleyin `Button1` ve adlı bir metin kutusu `TextBox1` ana forma adlı `Form1`. Ardından formun sağ tıklatıp **kodu görüntüle** Kod Düzenleyicisi'ni açın.  
  
 Ekleme bir `WithEvents` değişken bildirimleri bölümüne `Form1` sınıfı:  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_2.vb)]  
  
 Aşağıdaki kodu için kod ekleyin `Form1`. Oluşabilecek, gibi yinelenen yordamlarla değiştirin `Form_Load` veya `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_3.vb)]  
  
 Önceki örneği çalıştırmak ve etiketli düğmeye tıklayın için F5 tuşuna basın **Başlat**. İlk metin kutusuna saniye sayısı başlar. Tam zamanlı (10 saniye) geçtikten sonra "Bitti" ilk metin kutusunu görüntüler.  
  
> [!NOTE]
>  `My.Application.DoEvents` Yöntemi olayları form mu aynı şekilde işlemez. Doğrudan olaylarını işlemek form etkinleştirmek için kullanabileceğiniz çoklu iş parçacığı kullanımı. Daha fazla bilgi için [parçacıkları](../../programming-guide/concepts/threading/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [RaiseEvent Deyimi](../../../visual-basic/language-reference/statements/raiseevent-statement.md)  
 [Implements Deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)  
 [AddHandler Deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [RemoveHandler Deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [İşleme](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)  
 [Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
