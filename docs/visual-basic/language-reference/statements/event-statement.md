---
title: Event Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ba49d6582eb2ecac4846eaee570a4d92439a5d9
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
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
|`attrlist`|İsteğe bağlı. Bu olay için geçerli öznitelikler listesi. Birden çok öznitelik virgülle ayrılır. İçine almalısınız [öznitelik listesi](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraç ("`<`"ve"`>`").|  
|`accessmodifier`|İsteğe bağlı. Hangi kod olay erişip belirtir. Aşağıdakilerden biri olabilir:<br /><br /> -   [Ortak](../../../visual-basic/language-reference/modifiers/public.md)— bunu bildirir öğesi erişebilmeniz için herhangi bir kod erişim.<br />-   [Korumalı](../../../visual-basic/language-reference/modifiers/protected.md)— kod sınıfı veya türetilmiş bir sınıf içinde erişebildiğinizi yalnızca.<br />-   [Arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)— yalnızca aynı bütünleştirilmiş kodda, erişebilir.<br />-   [Özel](../../../visual-basic/language-reference/modifiers/private.md)— bunu bildirir öğesi yalnızca bir kodda erişebilirsiniz.<br /><br /> Belirleyebileceğiniz `Protected Friend` olay sınıfı, türetilmiş bir sınıf ya da aynı bütünleştirilmiş kodda erişimini etkinleştirmek için.|  
|`Shared`|İsteğe bağlı. Bu olay belirli bir sınıf veya yapı örneği ile ilişkili değil belirtir.|  
|`Shadows`|İsteğe bağlı. Bu olay redeclares ve bir aynı adlı programlama öğesi ya da bir taban sınıf içinde aşırı yüklenmiş öğelerin gizler gösterir. Bildirilen öğe herhangi bir tür başka herhangi bir tür ile gölge.<br /><br /> Gölgeli bir öğe, dışında gölgeleme öğesi erişilemez olduğu gelen shadows türetilmiş sınıf içinde kullanılamaz. Örneğin, varsa bir `Private` öğesi shadows erişim izni yok kod bir temel sınıf öğesi `Private` öğe temel sınıf öğesi yerine erişir.|  
|`eventname`|Gerekli. Olayın adı; Standart değişken adlandırma kuralları izler.|  
|`parameterlist`|İsteğe bağlı. Bu olay parametrelerinin temsil eden yerel değişkenler listesi. İçine almalısınız [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md) parantez içinde.|  
|`Implements`|İsteğe bağlı. Bu olay bir olay, bir arabirimi uygulayan gösterir.|  
|`implementslist`|Gerekli olursa `Implements` sağlanır. Listesi `Sub` uygulanan yordamlar. Birden çok yordam virgülle ayrılır:<br /><br /> *implementedprocedure* [, *implementedprocedure* ...]<br /><br /> Her `implementedprocedure` aşağıdaki söz dizimini ve bölümleri vardır:<br /><br /> `interface`.`definedname`<br /><br /> -   `interface`-Gerekli. Bu yordam, sınıf veya yapı içeren kullanıcının bir arabirim adı uygulama.<br />-   `Definedname`-Gerekli. Adı olarak yordamı tanımlanmış `interface`. Bu aynı olması gerekmez `name`, tanımlanmış yordamı uygulamak için bu yordamı kullanarak ad.|  
|`Custom`|Gerekli. Olayları bildirilen `Custom` özel tanımlamalısınız `AddHandler`, `RemoveHandler`, ve `RaiseEvent` erişimciler.|  
|`delegatename`|İsteğe bağlı. Olay işleyici imzası belirten bir temsilci adı.|  
|`AddHandler`|Gerekli. Bildiren bir `AddHandler` olay işleyicisi eklendiğinde yürütmek için ifadeleri belirtir, ya da açıkça kullanarak erişimcisi `AddHandler` deyimi kullanarak örtük veya `Handles` yan tümcesi.|  
|`End AddHandler`|Gerekli. Sonlandırır `AddHandler` bloğu.|  
|`value`|Gerekli. Parametre adı.|  
|`RemoveHandler`|Gerekli. Bildiren bir `RemoveHandler` olay işleyicisi kullanarak kaldırıldığında yürütmek için ifadeleri belirtir erişimcisi `RemoveHandler` deyimi.|  
|`End RemoveHandler`|Gerekli. Sonlandırır `RemoveHandler` bloğu.|  
|`RaiseEvent`|Gerekli. Bildiren bir `RaiseEvent` kullanarak olay oluşturulduğunda yürütmek için ifadeleri belirtir erişimcisi `RaiseEvent` deyimi. Genellikle, bu tarafından tutulan temsilciler listesini çağırır `AddHandler` ve `RemoveHandler` erişimciler.|  
|`End RaiseEvent`|Gerekli. Sonlandırır `RaiseEvent` bloğu.|  
|`delegatesignature`|Gerekli. Gereken parametrelerle eşleşen parametrelerin listesi `delegatename` temsilci. İçine almalısınız [parametre listesi](../../../visual-basic/language-reference/statements/parameter-list.md) parantez içinde.|  
|`statements`|İsteğe bağlı. Gövdeleri içeren deyimleri `AddHandler`, `RemoveHandler`, ve `RaiseEvent` yöntemleri.|  
|`End Event`|Gerekli. Sonlandırır `Event` bloğu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Olay bildirildikten sonra kullanın `RaiseEvent` deyimi olayı oluşturun. Tipik bir olay bildirilen ve aşağıdaki parçalanma gösterildiği gibi oluşturulur:  
  
 [!code-vb[VbVbalrEvents#13](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_1.vb)]  
  
> [!NOTE]
>  Yordamlar, aşağıdaki istisnalar dışında bağımsız gibi olay bağımsız bildirebilir: olaylar, bağımsız değişken adlı olamaz `ParamArray` bağımsız değişken veya `Optional` bağımsız değişkenler. Olaylar, dönüş değerleri yok.  
  
 Bir olayı işlemek için bunu kullanarak bir olay işleyicisi alt yordama ile ilişkilendirmeniz gerekir `Handles` veya `AddHandler` deyimi. Alt yordama ve olay imzalarını eşleşmesi gerekir. Paylaşılan olayını işlemek için kullanmanız gerekir `AddHandler` deyimi.  
  
 Kullanabileceğiniz `Event` yalnızca modülü düzeyinde. Yani *bildirimi bağlam* bir olay sınıfı, yapısı, modül veya arabirim olmalı ve kaynak dosyasını, ad alanı, yordam veya blok olamaz. Daha fazla bilgi için bkz: [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Çoğu durumda olaylarını bildirmek için bu konunun sözdizimi bölümünde ilk sözdizimini kullanabilirsiniz. Ancak, bazı senaryolar olay ayrıntılı davranışı hakkında daha fazla denetime sahip olmasını gerektirir. Son sözdizimi kullanan bu konu, söz dizimi bölümünde `Custom` anahtar sözcüğü, özel olaylar tanımlamanıza olanak sağlayarak bu denetim sağlar. Özel bir olay tam olarak kod ekler veya bir olay işleyicisi kaldırdığında veya olaydan neler veya ne zaman kodu olayını belirtin. Örnekler için bkz [nasıl yapılır: tasarruf bellek için olan özel olayları bildirme](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) ve [nasıl yapılır: bildirme özel olaylar kaçının engellemesine](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, 10 saniyeden 0 aşağı saymak için olayları kullanır. Kod olayla ilgili yöntemler, özellikler ve deyimleri çeşitli gösterir. Bu içerir `RaiseEvent` deyimi.  
  
 Olay kaynağı bir olay başlatır sınıf olduğunu ve olay işleme yöntemleri olay işleyicileri. Bir olay kaynağı ürettiği olaylar için birden çok işleyicileri olabilir. Olay sınıfı başlatır, bu olay nesnesinin bu örneği için olayları işlemek için katılmamayı her bir sınıf üzerinde tetiklenir.  
  
 Bu örnek ayrıca bir form kullanır (`Form1`) bir düğme ile (`Button1`) ve bir metin kutusu (`TextBox1`). Düğmeye tıkladığınızda, ilk metin kutusunu 0 saniye 10 geri sayım görüntüler. Tam zamanlı (10 saniye) geçtiğinde "Tamamlandı" ilk metin kutusunu görüntüler.  
  
 Kodunu `Form1` formun ilk ve terminal durumunu belirtir. Ayrıca, olayları ortaya çıktığında yürütülen kodu içerir.  
  
 Bu örneği kullanmak için yeni bir Windows Forms projesi açın. Adlı bir düğme ekleme `Button1` ve adlı bir metin kutusu `TextBox1` ana forma adlı `Form1`. Ardından formu sağ tıklatın ve **görünümü kodu** Kod Düzenleyicisi'ni açın.  
  
 Ekleme bir `WithEvents` değişken bildirimleri bölümüne `Form1` sınıfı:  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_2.vb)]  
  
 Aşağıdaki kodu için kod ekleme `Form1`. Aşağıdaki gibi bulunabilecek yinelenen yordamlarla Değiştir `Form_Load` veya `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/event-statement_3.vb)]  
  
 Önceki örneği çalıştırmak ve etiketli düğmesini için F5 tuşuna basın **Başlat**. Saniye sayısı ilk metin kutusunu başlatır. Tam zamanlı (10 saniye) geçtiğinde "Tamamlandı" ilk metin kutusunu görüntüler.  
  
> [!NOTE]
>  `My.Application.DoEvents` Yöntemi form yaptığı biçimde olayları işlemez. Olayları doğrudan işlemek form etkinleştirmek için kullanabileceğiniz çoklu iş parçacığı kullanımı. Daha fazla bilgi için bkz: [parçacıkları](../../programming-guide/concepts/threading/index.md).  
  
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
