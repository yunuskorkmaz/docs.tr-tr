---
title: Event Deyimi
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
ms.openlocfilehash: dd42e3364d96a8a9b3800b3d1f5e94b2fa25bad4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351221"
---
# <a name="event-statement"></a>Event Deyimi
Kullanıcı tanımlı bir olay bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
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
  
|Bölümüyle|Açıklama|  
|---|---|  
|`attrlist`|İsteğe bağlı. Bu olay için uygulanan özniteliklerin listesi. Birden çok öznitelik virgülle ayrılır. [Öznitelik listesini](../../../visual-basic/language-reference/statements/attribute-list.md) açılı ayraç içine almalısınız ("`<`" ve "`>`").|  
|`accessmodifier`|İsteğe bağlı. Olaya hangi kodun erişebileceğini belirtir. Aşağıdakilerden biri olabilir:<br /><br /> -   [Public](../../../visual-basic/language-reference/modifiers/public.md)— onu bildiren öğeye erişebilen tüm kodlar buna erişebilir.<br />-   [korumalı](../../../visual-basic/language-reference/modifiers/protected.md)— yalnızca kendi sınıfı veya türetilmiş bir sınıf içindeki kodlar buna erişebilir.<br />-   [arkadaş](../../../visual-basic/language-reference/modifiers/friend.md)— yalnızca aynı derlemedeki kod erişebilir.<br />-   [Private](../../../visual-basic/language-reference/modifiers/private.md)— yalnızca bu öğeyi bildiren kod, ona erişebilir.<br /> olay sınıfında, türetilmiş bir sınıfta veya aynı bütünleştirilmiş kodda yalnızca [korunan arkadaş](../../language-reference/modifiers/protected-friend.md)kodu -   . <br />olay sınıfında veya aynı derlemede bulunan türetilmiş bir sınıfta [özel olarak korunan](../../language-reference/modifiers/private-protected.md)kod - buna erişebilir.|  
|`Shared`|İsteğe bağlı. Bu olayın bir sınıfın veya yapının belirli bir örneğiyle ilişkilendirilmediği belirtir.|  
|`Shadows`|İsteğe bağlı. Bu olayın, bir temel sınıfta aynı adlı programlama öğesi veya aşırı yüklenmiş öğeler kümesini yeniden bildirdiğini ve gizlediğini belirtir. Herhangi bir tür tanımlanmış öğeyi başka bir tür ile gölgelendirebilmeniz gerekir.<br /><br /> Gölgelendirilmiş bir öğe, gölgeleme öğesinin erişilemez olması dışında, kendisini gölgelendirilebilen türetilmiş sınıfın içinden kullanılamaz. Örneğin, bir `Private` öğesi bir temel sınıf öğesini göltikten sonra, `Private` öğesine erişim izni olmayan kod, bunun yerine temel sınıf öğesine erişir.|  
|`eventname`|Gerekli. Olayın adı; Standart değişken adlandırma kurallarını izler.|  
|`parameterlist`|İsteğe bağlı. Bu olayın parametrelerini temsil eden yerel değişkenlerin listesi. [Parametre listesini](../../../visual-basic/language-reference/statements/parameter-list.md) parantez içine almalısınız.|  
|`Implements`|İsteğe bağlı. Bu olayın bir arabirimin olayını uyguladığını gösterir.|  
|`implementslist`|`Implements` sağlanırsa gereklidir. Uygulanan `Sub` yordamlarının listesi. Birden çok yordam virgüllerle ayrılır:<br /><br /> *ımplementedprocedure* [, *ımplementedprocedure* ...]<br /><br /> Her `implementedprocedure` aşağıdaki söz dizimi ve bölümlere sahiptir:<br /><br /> `interface`.`definedname`<br /><br /> -   `interface`-gerekli. Bu yordamın kendisini içeren sınıf veya yapının uyguladığı arabirimin adı.<br />-   `Definedname`-gerekli. Yordamın `interface`tanımladığı ad. Bu, tanımlanan yordamı uygulamak için bu yordamın kullandığı ad `name`ile aynı olmak zorunda değildir.|  
|`Custom`|Gerekli. `Custom` olarak belirtilen olaylar, özel `AddHandler`, `RemoveHandler`ve `RaiseEvent` erişimcileri tanımlamalıdır.|  
|`delegatename`|İsteğe bağlı. Olay işleyicisi imzasını belirten bir temsilcinin adı.|  
|`AddHandler`|Gerekli. Bir olay işleyicisi eklendiğinde yürütülecek deyimleri belirten bir `AddHandler` erişimcisi bildirir, açıkça `AddHandler` deyimini veya `Handles` yan tümcesini kullanarak örtülü olarak.|  
|`End AddHandler`|Gerekli. `AddHandler` bloğunu sonlandırır.|  
|`value`|Gerekli. Parametre adı.|  
|`RemoveHandler`|Gerekli. Bir olay işleyicisi `RemoveHandler` deyimi kullanılarak kaldırıldığında yürütülecek deyimleri belirten bir `RemoveHandler` erişimcisi bildirir.|  
|`End RemoveHandler`|Gerekli. `RemoveHandler` bloğunu sonlandırır.|  
|`RaiseEvent`|Gerekli. Olay `RaiseEvent` deyimi kullanılarak oluşturulduğunda yürütülecek deyimleri belirten bir `RaiseEvent` erişimcisi bildirir. Genellikle, bu, `AddHandler` ve `RemoveHandler` erişimcileri tarafından tutulan temsilcilerin listesini çağırır.|  
|`End RaiseEvent`|Gerekli. `RaiseEvent` bloğunu sonlandırır.|  
|`delegatesignature`|Gerekli. `delegatename` temsilcisinin gerektirdiği parametrelerle eşleşen parametrelerin listesi. [Parametre listesini](../../../visual-basic/language-reference/statements/parameter-list.md) parantez içine almalısınız.|  
|`statements`|İsteğe bağlı. `AddHandler`, `RemoveHandler`ve `RaiseEvent` yöntemlerinin gövdelerini içeren deyimler.|  
|`End Event`|Gerekli. `Event` bloğunu sonlandırır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Olay bildirildiğinde, olayı yükseltmek için `RaiseEvent` ifadesini kullanın. Tipik bir olay, aşağıdaki parçalar gösterildiği gibi bildirilebilecek ve ortaya çıkabilir:  
  
 [!code-vb[VbVbalrEvents#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#13)]  
  
> [!NOTE]
> Aşağıdaki özel durumlarla birlikte, yordam bağımsız değişkenleri yaptığınız gibi olay bağımsız değişkenlerini bildirebilirsiniz: olaylarda adlandırılmış bağımsız değişkenler, `ParamArray` bağımsız değişkenler veya `Optional` bağımsız değişken olamaz. Olayların dönüş değeri yok.  
  
 Bir olayı işlemek için `Handles` ya da `AddHandler` ifadesini kullanarak bir olay işleyicisi alt yordamı ile ilişkilendirmeniz gerekir. Altyordam ve olayın imzaları eşleşmelidir. Paylaşılan bir olayı işlemek için `AddHandler` ifadesini kullanmanız gerekir.  
  
 Yalnızca modül düzeyinde `Event` kullanabilirsiniz. Bu, bir olayın *bildirim bağlamının* bir sınıf, yapı, modül veya arabirim olması ve kaynak dosya, ad alanı, yordam veya blok olması gerektiği anlamına gelir. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Çoğu durumda, olayları bildirmek için bu konunun söz dizimi bölümünde ilk sözdizimini kullanabilirsiniz. Ancak, bazı senaryolar etkinliğin ayrıntılı davranışı üzerinde daha fazla denetime sahip olmanızı gerektirir. `Custom` anahtar sözcüğünü kullanan bu konunun sözdizimi bölümündeki son sözdizimi, özel olayları tanımlamanızı sağlayarak bu denetimi sağlar. Özel bir olayda, kod bir olay işleyicisini olaya eklendiğinde veya olaya kaldırdığında ya da kod olayı harekete geçirirse tam olarak ne olduğunu belirtirsiniz. Örnekler için bkz. [nasıl yapılır: belleği korumak Için özel olaylar bildirme](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) ve [nasıl yapılır: engellemeyi önlemek Için özel olaylar bildirme](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, 10 ile 0 arasındaki saniye sayısını saymak için olayları kullanır. Kod, olayla ilgili yöntemlerin, özelliklerin ve deyimlerden birkaçını gösterir. Buna `RaiseEvent` deyimleri de dahildir.  
  
 Olayı oluşturan sınıf olay kaynağıdır ve olayı işleyen yöntemler olay işleyicileridir. Bir olay kaynağı, oluşturduğu olaylar için birden çok işleyicilere sahip olabilir. Sınıf olayı harekete geçirirse, bu olay nesnenin bu örneğine yönelik olayları işlemek için seçilmiş olan her sınıfta oluşturulur.  
  
 Örnek ayrıca bir düğme (`Button1`) ve metin kutusu (`TextBox1`) içeren bir form (`Form1`) kullanır. Düğmeye tıkladığınızda, ilk metin kutusu 10 ila 0 saniye arasında bir geri sayım görüntüler. Tam süre (10 saniye) geçtiğinde, ilk metin kutusunda "bitti" görüntülenir.  
  
 `Form1` kodu, formun başlangıç ve Terminal durumlarını belirtir. Ayrıca, olaylar oluşturulduğunda yürütülen kodu içerir.  
  
 Bu örneği kullanmak için yeni bir Windows Forms projesi açın. Ardından `Button1` adlı bir düğme ve `TextBox1` adlı ana forma `Form1`adlı bir metin kutusu ekleyin. Daha sonra forma sağ tıklayın ve kodu **görüntüle** ' ye tıklayarak kod düzenleyicisini açın.  
  
 `Form1` sınıfının bildirimler bölümüne bir `WithEvents` değişkeni ekleyin:  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
 `Form1`koda aşağıdaki kodu ekleyin. `Form_Load` veya `Button_Click`gibi, mevcut olabilecek yinelenen yordamları değiştirin.  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Önceki örneği çalıştırmak için F5 tuşuna basın ve **Başlat**etiketli düğmeye tıklayın. İlk metin kutusu, saniyeyi saymaya başlar. Tam süre (10 saniye) geçtiğinde, ilk metin kutusunda "bitti" görüntülenir.  
  
> [!NOTE]
> `My.Application.DoEvents` yöntemi, olayları formla aynı şekilde işlemez. Formun olayları doğrudan işlemesini sağlamak için çoklu iş parçacığı kullanımı ' nı kullanabilirsiniz. Daha fazla bilgi için bkz. [yönetilen Iş parçacığı](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [RaiseEvent Deyimi](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [Implements Deyimi](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
- [AddHandler Deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [RemoveHandler Deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [İşlendiğini](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
- [Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme](../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
