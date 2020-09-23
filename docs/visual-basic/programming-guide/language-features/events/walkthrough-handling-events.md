---
title: Olayları İşleme
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 4489f75e50a783a9b1acfb9c30568fdec6614488
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057916"
---
# <a name="walkthrough-handling-events-visual-basic"></a>İzlenecek yol: Olayları İşleme (Visual Basic)

Bu, etkinliklerle nasıl çalışabileceğini gösteren iki konunun ikinci konudır. [Izlenecek yol: Izlenecek yol: olayları bildirme ve](walkthrough-declaring-and-raising-events.md)oluşturma, olayların nasıl bildirilemeyeceğini ve tetikleyeceğinizi gösterir. Bu bölüm, bu kılavuzda yer alan formu ve sınıfı kullanır.  
  
 `Widget`Sınıf örneği geleneksel olay işleme deyimlerini kullanır. Visual Basic olaylarla çalışmaya yönelik başka teknikler de sağlar. Bir alıştırma olarak, ve deyimlerini kullanmak için bu örneği değiştirebilirsiniz `AddHandler` `Handles` .  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Pencere öğesi sınıfının PercentDone olayını işlemek için  
  
1. Aşağıdaki kodu içine yerleştirin `Form1` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     `WithEvents`Anahtar sözcüğü, değişkenin `mWidget` bir nesnenin olaylarını işlemek için kullanıldığını belirtir. Nesnenin türünü, nesnenin oluşturulacağı sınıfın adını sağlayarak belirtirsiniz.  
  
     `mWidget` `Form1` Değişkenler sınıf düzeyi olması gerektiğinden değişken içinde olarak belirtilir `WithEvents` . Bu, yerleştirdiğiniz sınıf türünden bağımsız olarak geçerlidir.  
  
     Değişkeni, `mblnCancel` yöntemi iptal etmek için kullanılır `LongTask` .  
  
## <a name="writing-code-to-handle-an-event"></a>Bir olayı Işlemek için kod yazma  

 Kullanarak bir değişken bildirdikten hemen sonra `WithEvents` , sınıfın **kod düzenleyicisinin**sol açılır listesinde değişken adı belirir. Seçtiğinizde `mWidget` , `Widget` sınıfın olayları sağ açılan listede görüntülenir. Bir olay seçilmesi, ilgili olay yordamını önek `mWidget` ve alt çizgi ile görüntüler. Bir değişkenle ilişkili tüm olay yordamlarına `WithEvents` önek olarak değişken adı verilir.  
  
#### <a name="to-handle-an-event"></a>Bir olayı işlemek için  
  
1. `mWidget` **Kod düzenleyicisinde**sol aşağı açılan listeden seçim yapın.  
  
2. `PercentDone`Sağ açılan listeden olayı seçin. **Kod Düzenleyicisi** `mWidget_PercentDone` olay yordamını açar.  
  
    > [!NOTE]
    > **Kod Düzenleyicisi** , yeni olay işleyicileri eklemek için yararlıdır, ancak gerekli değildir. Bu kılavuzda, yalnızca olay işleyicilerini doğrudan kodunuza kopyalamak daha doğrudan bir örnek olur.  
  
3. Aşağıdaki kodu `mWidget_PercentDone` olay işleyicisine ekleyin:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     Olay gerçekleştiğinde `PercentDone` olay yordamı bir denetimdeki tamamlanma yüzdesini gösterir `Label` . `DoEvents`Yöntemi etiketin yeniden çizileceğü sağlar ve kullanıcıya **iptal** düğmesine tıklama fırsatı verir.  
  
4. Olay işleyicisi için aşağıdaki kodu ekleyin `Button2_Click` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 Kullanıcı çalışırken **iptal** düğmesine tıkladığında `LongTask` , etkinlik `Button2_Click` `DoEvents` olay işlemenin oluşmasına izin verdiği anda olay yürütülür. Sınıf düzeyi değişkeni `mblnCancel` olarak ayarlanır `True` ve `mWidget_PercentDone` olay bundan sonra test eder ve `ByRef Cancel` bağımsız değişkenini olarak ayarlar `True` .  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Bir WithEvents değişkenini bir nesneye bağlama  

 `Form1` Artık bir nesnenin olaylarını işleyecek şekilde ayarlanır `Widget` . Her şey bir yerde bulunmaya devam etmektedir `Widget` .  
  
 Tasarım zamanında bir değişken bildirdiğinizde `WithEvents` , onunla ilişkili bir nesne yoktur. `WithEvents`Değişken, tıpkı diğer nesne değişkenleri gibi. Bir nesnesi oluşturmanız ve değişkenine bir başvuru atamanız gerekir `WithEvents` .  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Bir nesne oluşturmak ve buna bir başvuru atamak için  
  
1. **Kod düzenleyicisinde**sol aşağı açılan listeden **(Form1 olayları)** öğesini seçin.  
  
2. `Load`Sağ açılan listeden olayı seçin. **Kod Düzenleyicisi** `Form1_Load` olay yordamını açar.  
  
3. `Form1_Load`Oluşturmak için olay yordamı için aşağıdaki kodu ekleyin `Widget` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 Bu kod yürütüldüğünde, Visual Basic bir nesnesi oluşturur `Widget` ve olaylarını ile ilişkili olay yordamlarına bağlar `mWidget` . Bu noktadan itibaren, olayı her ne zaman `Widget` oluşturur `PercentDone` `mWidget_PercentDone` olay yordamı yürütülür.  
  
#### <a name="to-call-the-longtask-method"></a>LongTask yöntemini çağırmak için  
  
- Aşağıdaki kodu `Button1_Click` olay işleyicisine ekleyin:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 `LongTask`Yöntemi çağrılmadan önce, tamamlanma yüzdesini gösteren etiketin başlatılması ve `Boolean` yöntemin iptal edilmesi için sınıf düzeyi bayrağının olarak ayarlanması gerekir `False` .  
  
 `LongTask` , 12,2 saniyelik bir görev süresiyle çağrılır. `PercentDone`Olay, saniyenin her biri üçte bir kez tetiklenir. Olay her oluşturulduğunda `mWidget_PercentDone` olay yordamı yürütülür.  
  
 İşiniz `LongTask` bittiğinde, `mblnCancel` `LongTask` normal olarak mı sonlandırıldığı, yoksa durdurulmuş mi olduğunu görmek için test edilmiştir `mblnCancel` `True` . Tamamlanma yüzdesi yalnızca önceki durumda güncelleştirilir.  
  
#### <a name="to-run-the-program"></a>Programı çalıştırmak için  
  
1. Projeyi çalışma moduna almak için F5 tuşuna basın.  
  
2. **Görevi Başlat** düğmesine tıklayın. `PercentDone`Olay her oluşturulduğunda etiket, tamamlanan görevin yüzdesine göre güncelleştirilir.  
  
3. Görevi durdurmak için **iptal** düğmesine tıklayın. **İptal** düğmesinin görünümü tıkladığınızda hemen değişmediğine dikkat edin. `Click`Etkinlik `My.Application.DoEvents` Olay işlemeye izin verdiğinden olay gerçekleşmeyecek.  
  
    > [!NOTE]
    > `My.Application.DoEvents`Yöntemi, olayları yalnızca formla aynı şekilde işlemez. Örneğin, bu kılavuzda, **iptal** düğmesine iki kez tıklamanız gerekir. Formun olayları doğrudan işlemesine izin vermek için çoklu iş parçacığı kullanımı ' nı kullanabilirsiniz. Daha fazla bilgi için bkz. [yönetilen Iş parçacığı](../../../../standard/threading/index.md).
  
 Programı F11 ile çalıştırmaya ve bir kerede bir satırda bir satır adım adım ilerlebileceğinizi fark edebilirsiniz. Yürütmenin nasıl girdiğini açıkça görebilir `LongTask` ve `Form1` olay her oluşturulduğunda kısa bir süre sonra yeniden girebilirsiniz `PercentDone` .  
  
 Yürütme kodunda geri yüklenirken ne olur `Form1` `LongTask` ?, yöntem yeniden çağırılır mi? En kötü, `LongTask` olay her oluştuğunda çağrılırsa bir yığın taşması meydana gelebilir.  
  
 `mWidget` `Widget` Yeni öğesine bir başvuru atayarak, değişkenin farklı bir nesne için olayları işlemesine neden olabilirsiniz `Widget` `mWidget` . Aslında, `Button1_Click` düğmeye her tıkladığınızda kodu bunu yapabilirsiniz.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Farklı bir pencere öğesinin olaylarını işlemek için  
  
- Aşağıdaki kod satırını, şu şekilde `Button1_Click` görüntülenen satırdan hemen önce ekleyin `mWidget.LongTask(12.2, 0.33)` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 Yukarıdaki kod, düğme tıklandığında yeni bir oluşturur `Widget` . Yöntemi tamamlandıktan hemen sonra, `LongTask` başvurusu serbest bırakılır ve yok edilir `Widget` `Widget` .  
  
 Bir `WithEvents` değişken tek seferde yalnızca bir nesne başvurusu içerebilir, bu nedenle ' ye farklı bir nesne atarsanız `Widget` `mWidget` , önceki `Widget` nesnenin olayları artık işlenmeyecek. Eğer `mWidget` eski bir başvuruyu içeren tek nesne değişkense `Widget` , nesne yok edilir. Çeşitli nesnelerden olayları işlemek istiyorsanız `Widget` , `AddHandler` her bir nesneden olayları ayrı olarak işlemek için ifadesini kullanın.  
  
> [!NOTE]
> `WithEvents`İhtiyaç duyduğunuz kadar çok değişken bildirebilirsiniz, ancak `WithEvents` değişkenlerin dizileri desteklenmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Olay Bildirme ve Oluşturma](walkthrough-declaring-and-raising-events.md)
- [Ekinlikler](index.md)
