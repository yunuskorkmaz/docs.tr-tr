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
ms.openlocfilehash: a136a517c7ce865b4e1d349270696e2704d61592
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404673"
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
  
|Bölüm|Description|  
|---|---|  
|`attrlist`|İsteğe bağlı. Bu olay için uygulanan özniteliklerin listesi. Birden çok öznitelik virgülle ayrılır. [Öznitelik listesini](attribute-list.md) açılı ayraçlar (" `<` " ve " `>` ") içine almalısınız.|  
|`accessmodifier`|İsteğe bağlı. Olaya hangi kodun erişebileceğini belirtir. Aşağıdakilerden biri olabilir:<br /><br /> -   [Public](../modifiers/public.md)— onu bildiren öğeye erişebilen herhangi bir kod, buna erişebilir.<br />-   [Korumalı](../modifiers/protected.md)— yalnızca kendi sınıfı veya türetilmiş bir sınıf içindeki kodlar buna erişebilir.<br />-   [Friend](../modifiers/friend.md)— yalnızca aynı derlemede bulunan kod erişebilir.<br />-   [Özel](../modifiers/private.md)— yalnızca bu öğeyi bildiren kod, ona erişebilir.<br /> -   Yalnızca olayın sınıfında, türetilmiş bir sınıfta veya aynı derlemede bulunan yalnızca [arkadaş](../modifiers/protected-friend.md)kod, buna erişebilir. <br />- Yalnızca olayın sınıfında veya aynı derlemede bulunan türetilmiş bir sınıfta bulunan [özel korumalı](../modifiers/private-protected.md)kod, buna erişebilir.|  
|`Shared`|İsteğe bağlı. Bu olayın bir sınıfın veya yapının belirli bir örneğiyle ilişkilendirilmediği belirtir.|  
|`Shadows`|İsteğe bağlı. Bu olayın, bir temel sınıfta aynı adlı programlama öğesi veya aşırı yüklenmiş öğeler kümesini yeniden bildirdiğini ve gizlediğini belirtir. Herhangi bir tür tanımlanmış öğeyi başka bir tür ile gölgelendirebilmeniz gerekir.<br /><br /> Gölgelendirilmiş bir öğe, gölgeleme öğesinin erişilemez olması dışında, kendisini gölgelendirilebilen türetilmiş sınıfın içinden kullanılamaz. Örneğin, bir öğe bir `Private` temel sınıf öğesini gölerse, öğesine erişim izni olmayan kod, `Private` bunun yerine temel sınıf öğesine erişir.|  
|`eventname`|Gereklidir. Olayın adı; Standart değişken adlandırma kurallarını izler.|  
|`parameterlist`|İsteğe bağlı. Bu olayın parametrelerini temsil eden yerel değişkenlerin listesi. [Parametre listesini](parameter-list.md) parantez içine almalısınız.|  
|`Implements`|İsteğe bağlı. Bu olayın bir arabirimin olayını uyguladığını gösterir.|  
|`implementslist`|Sağlanırsa gereklidir `Implements` . `Sub`Uygulanan yordamların listesi. Birden çok yordam virgüllerle ayrılır:<br /><br /> *ımplementedprocedure* [, *ımplementedprocedure* ...]<br /><br /> Her birinin `implementedprocedure` aşağıdaki söz dizimi ve parçaları vardır:<br /><br /> `interface`.`definedname`<br /><br /> -   `interface`İstenir. Bu yordamın kendisini içeren sınıf veya yapının uyguladığı arabirimin adı.<br />-   `Definedname`İstenir. Yordamın tanımlandığı ad `interface` . Bu `name` , tanımlanan yordamı uygulamak için bu yordamın kullandığı ad ile aynı olmak zorunda değildir.|  
|`Custom`|Gereklidir. Olarak belirtilen olaylar `Custom` özel `AddHandler` , `RemoveHandler` ve `RaiseEvent` erişimcileri tanımlamalıdır.|  
|`delegatename`|İsteğe bağlı. Olay işleyicisi imzasını belirten bir temsilcinin adı.|  
|`AddHandler`|Gereklidir. `AddHandler`Bir olay işleyicisi eklendiğinde, açıkça `AddHandler` deyimi kullanarak veya yan tümcesini kullanarak örtülü olarak yürütülecek deyimleri belirten bir erişimci bildirir `Handles` .|  
|`End AddHandler`|Gereklidir. Bloğu sonlandırır `AddHandler` .|  
|`value`|Gereklidir. Parametre adı.|  
|`RemoveHandler`|Gereklidir. `RemoveHandler`Bir olay işleyicisi deyimi kullanılarak kaldırıldığında yürütülecek deyimleri belirten bir erişimci bildirir `RemoveHandler` .|  
|`End RemoveHandler`|Gereklidir. Bloğu sonlandırır `RemoveHandler` .|  
|`RaiseEvent`|Gereklidir. `RaiseEvent`Olay deyimi kullanılarak oluşturulduğunda yürütülecek deyimleri belirten bir erişimci bildirir `RaiseEvent` . Genellikle, ve erişimcileri tarafından tutulan temsilcilerin listesini çağırır `AddHandler` `RemoveHandler` .|  
|`End RaiseEvent`|Gereklidir. Bloğu sonlandırır `RaiseEvent` .|  
|`delegatesignature`|Gereklidir. Temsilcinin gerektirdiği parametrelerle eşleşen parametrelerin listesi `delegatename` . [Parametre listesini](parameter-list.md) parantez içine almalısınız.|  
|`statements`|İsteğe bağlı. `AddHandler`, Ve yöntemlerinin gövdelerini içeren deyimler `RemoveHandler` `RaiseEvent` .|  
|`End Event`|Gereklidir. Bloğu sonlandırır `Event` .|  
  
## <a name="remarks"></a>Açıklamalar  
 Olay bildirildiğinde `RaiseEvent` olayı yükseltmek için ifadesini kullanın. Tipik bir olay, aşağıdaki parçalar gösterildiği gibi bildirilebilecek ve ortaya çıkabilir:  
  
 [!code-vb[VbVbalrEvents#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#13)]  
  
> [!NOTE]
> Aşağıdaki özel durumlarla birlikte, yordam bağımsız değişkenleri yaptığınız gibi olay bağımsız değişkenlerini bildirebilirsiniz: olaylarda adlandırılmış bağımsız değişkenler, `ParamArray` bağımsız değişkenler veya bağımsız değişkenler bulunamaz `Optional` . Olayların dönüş değeri yok.  
  
 Bir olayı işlemek için, ya da ifadesini kullanarak bir olay işleyicisi alt yordamı ile ilişkilendirmeniz gerekir `Handles` `AddHandler` . Altyordam ve olayın imzaları eşleşmelidir. Paylaşılan bir olayı işlemek için, ifadesini kullanmanız gerekir `AddHandler` .  
  
 `Event`Yalnızca modül düzeyinde kullanabilirsiniz. Bu, bir olayın *bildirim bağlamının* bir sınıf, yapı, modül veya arabirim olması ve kaynak dosya, ad alanı, yordam veya blok olması gerektiği anlamına gelir. Daha fazla bilgi için bkz. [bildirim bağlamları ve varsayılan erişim düzeyleri](declaration-contexts-and-default-access-levels.md).  
  
 Çoğu durumda, olayları bildirmek için bu konunun söz dizimi bölümünde ilk sözdizimini kullanabilirsiniz. Ancak, bazı senaryolar etkinliğin ayrıntılı davranışı üzerinde daha fazla denetime sahip olmanızı gerektirir. Anahtar sözcüğünü kullanan bu konunun sözdizimi bölümündeki son sözdizimi `Custom` , özel olayları tanımlamanızı sağlayarak bu denetimi sağlar. Özel bir olayda, kod bir olay işleyicisini olaya eklendiğinde veya olaya kaldırdığında ya da kod olayı harekete geçirirse tam olarak ne olduğunu belirtirsiniz. Örnekler için bkz. [nasıl yapılır: belleği korumak Için özel olaylar bildirme](../../programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md) ve [nasıl yapılır: engellemeyi önlemek Için özel olaylar bildirme](../../programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, 10 ile 0 arasındaki saniye sayısını saymak için olayları kullanır. Kod, olayla ilgili yöntemlerin, özelliklerin ve deyimlerden birkaçını gösterir. Bu, `RaiseEvent` ifadesini içerir.  
  
 Olayı oluşturan sınıf olay kaynağıdır ve olayı işleyen yöntemler olay işleyicileridir. Bir olay kaynağı, oluşturduğu olaylar için birden çok işleyicilere sahip olabilir. Sınıf olayı harekete geçirirse, bu olay nesnenin bu örneğine yönelik olayları işlemek için seçilmiş olan her sınıfta oluşturulur.  
  
 Örnek ayrıca bir `Form1` düğme ( `Button1` ) ve metin kutusu () içeren bir form () kullanır `TextBox1` . Düğmeye tıkladığınızda, ilk metin kutusu 10 ila 0 saniye arasında bir geri sayım görüntüler. Tam süre (10 saniye) geçtiğinde, ilk metin kutusunda "bitti" görüntülenir.  
  
 Kodu, `Form1` formun ilk ve Terminal durumlarını belirtir. Ayrıca, olaylar oluşturulduğunda yürütülen kodu içerir.  
  
 Bu örneği kullanmak için yeni bir Windows Forms projesi açın. Ardından adlı bir düğme `Button1` ve adlı ana forma adlı bir metin kutusu ekleyin `TextBox1` `Form1` . Daha sonra forma sağ tıklayın ve kodu **görüntüle** ' ye tıklayarak kod düzenleyicisini açın.  
  
 `WithEvents`Sınıfının bildirimler bölümüne bir değişken ekleyin `Form1` :  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
 Koduna aşağıdaki kodu ekleyin `Form1` . Ya da gibi, var olabilecek yinelenen yordamları değiştirin `Form_Load` `Button_Click` .  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Önceki örneği çalıştırmak için F5 tuşuna basın ve **Başlat**etiketli düğmeye tıklayın. İlk metin kutusu, saniyeyi saymaya başlar. Tam süre (10 saniye) geçtiğinde, ilk metin kutusunda "bitti" görüntülenir.  
  
> [!NOTE]
> `My.Application.DoEvents`Yöntemi, olayları formla aynı şekilde işlemez. Formun olayları doğrudan işlemesini sağlamak için çoklu iş parçacığı kullanımı ' nı kullanabilirsiniz. Daha fazla bilgi için bkz. [yönetilen Iş parçacığı](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [RaiseEvent Deyimi](raiseevent-statement.md)
- [Implements Deyimi](implements-statement.md)
- [Olaylar](../../programming-guide/language-features/events/index.md)
- [AddHandler Deyimi](addhandler-statement.md)
- [RemoveHandler Deyimi](removehandler-statement.md)
- [Handles](handles-clause.md)
- [Delegate Deyimi](delegate-statement.md)
- [Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme](../../programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
- [Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme](../../programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
- [Shared](../modifiers/shared.md)
- [Shadows](../modifiers/shadows.md)
