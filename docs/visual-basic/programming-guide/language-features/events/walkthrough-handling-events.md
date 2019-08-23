---
title: Olayları işleme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 12267e0a70419298bc581421c4f3a220088d205f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956306"
---
# <a name="walkthrough-handling-events-visual-basic"></a>İzlenecek yol: Olayları işleme (Visual Basic)
Bu, etkinliklerle nasıl çalışabileceğini gösteren iki konunun ikinci konudır. İlk konu, [izlenecek yol: Olayları](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)bildirme ve oluşturma, olayların nasıl bildirilemeyeceğini ve tetiklemeyeceğini gösterir. Bu bölüm, bu kılavuzda yer alan formu ve sınıfı kullanır.  
  
 `Widget` Sınıf örneği geleneksel olay işleme deyimlerini kullanır. Visual Basic olaylarla çalışmaya yönelik başka teknikler de sağlar. Bir alıştırma olarak, `AddHandler` ve `Handles` deyimlerini kullanmak için bu örneği değiştirebilirsiniz.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Pencere öğesi sınıfının PercentDone olayını işlemek için  
  
1. Aşağıdaki kodu içine `Form1`yerleştirin:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     Anahtar sözcüğü, değişkenin `mWidget` bir nesnenin olaylarını işlemek için kullanıldığını belirtir. `WithEvents` Nesnenin türünü, nesnenin oluşturulacağı sınıfın adını sağlayarak belirtirsiniz.  
  
     Değişkenler sınıf `mWidget` düzeyi olması gerektiğinden `Form1` `WithEvents` değişken içinde olarak belirtilir. Bu, yerleştirdiğiniz sınıf türünden bağımsız olarak geçerlidir.  
  
     Değişkeni `mblnCancel` , `LongTask` yöntemi iptal etmek için kullanılır.  
  
## <a name="writing-code-to-handle-an-event"></a>Bir olayı Işlemek için kod yazma  
 Kullanarak `WithEvents`bir değişken bildirdikten hemen sonra, sınıfın **kod düzenleyicisinin**sol açılır listesinde değişken adı belirir. `mWidget` Seçtiğinizde`Widget` , sınıfın olayları sağ açılan listede görüntülenir. Bir olay seçilmesi, ilgili olay yordamını önek `mWidget` ve alt çizgi ile görüntüler. Bir `WithEvents` değişkenle ilişkili tüm olay yordamlarına önek olarak değişken adı verilir.  
  
#### <a name="to-handle-an-event"></a>Bir olayı işlemek için  
  
1. `mWidget` **Kod düzenleyicisinde**sol aşağı açılan listeden seçim yapın.  
  
2. Sağ açılan listeden olayı seçin. `PercentDone` **Kod Düzenleyicisi** `mWidget_PercentDone` olay yordamını açar.  
  
    > [!NOTE]
    > **Kod Düzenleyicisi** , yeni olay işleyicileri eklemek için yararlıdır, ancak gerekli değildir. Bu kılavuzda, yalnızca olay işleyicilerini doğrudan kodunuza kopyalamak daha doğrudan bir örnek olur.  
  
3. Aşağıdaki kodu `mWidget_PercentDone` olay işleyicisine ekleyin:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     Olay gerçekleştiğinde olay yordamı bir `Label` denetimdeki tamamlanma yüzdesini gösterir. `PercentDone` Yöntemi etiketin yeniden çizileceğü sağlar ve kullanıcıya iptal düğmesine tıklama fırsatı verir. `DoEvents`  
  
4. `Button2_Click` Olay işleyicisi için aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 Kullanıcı çalışırken **iptal** `LongTask` düğmesine tıkladığında, `Button2_Click` etkinlik olay işlemenin oluşmasına izin verdiği anda `DoEvents` olay yürütülür. Sınıf `mblnCancel` düzeyi değişkeni `True`olarak `True`ayarlanır ve `mWidget_PercentDone` olay bundan sonra test eder ve `ByRef Cancel` bağımsız değişkenini olarak ayarlar.  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Bir WithEvents değişkenini bir nesneye bağlama  
 `Form1`Artık bir `Widget` nesnenin olaylarını işleyecek şekilde ayarlanır. Her şey bir `Widget` yerde bulunmaya devam etmektedir.  
  
 Tasarım zamanında bir değişken `WithEvents` bildirdiğinizde, onunla ilişkili bir nesne yoktur. `WithEvents` Değişken, tıpkı diğer nesne değişkenleri gibi. Bir nesnesi oluşturmanız ve `WithEvents` değişkenine bir başvuru atamanız gerekir.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Bir nesne oluşturmak ve buna bir başvuru atamak için  
  
1. **Kod düzenleyicisinde**sol aşağı açılan listeden **(Form1 olayları)** öğesini seçin.  
  
2. Sağ açılan listeden olayı seçin. `Load` **Kod Düzenleyicisi** `Form1_Load` olay yordamını açar.  
  
3. Oluşturmak için `Form1_Load` olay yordamı için aşağıdaki kodu ekleyin: `Widget`  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 Bu kod yürütüldüğünde, Visual Basic bir `Widget` nesnesi oluşturur ve olaylarını ile `mWidget`ilişkili olay yordamlarına bağlar. Bu noktadan itibaren, olayı her ne `Widget` zaman `PercentDone` oluşturur `mWidget_PercentDone` olay yordamı yürütülür.  
  
#### <a name="to-call-the-longtask-method"></a>LongTask yöntemini çağırmak için  
  
- Aşağıdaki kodu `Button1_Click` olay işleyicisine ekleyin:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 Yöntemi çağrılmadan önce, tamamlanma yüzdesini gösteren etiketin başlatılması ve yöntemin iptal edilmesi için sınıf düzeyi `Boolean` bayrağının olarak `False`ayarlanması gerekir. `LongTask`  
  
 `LongTask`, 12,2 saniyelik bir görev süresiyle çağrılır. Olay `PercentDone` , saniyenin her biri üçte bir kez tetiklenir. Olay her oluşturulduğunda `mWidget_PercentDone` olay yordamı yürütülür.  
  
 `mblnCancel` İşinizbittiğinde`mblnCancel` , normal olarak mısonlandırıldığı`LongTask` , yoksa durdurulmuş mi olduğunu görmek için test edilmiştir. `True` `LongTask` Tamamlanma yüzdesi yalnızca önceki durumda güncelleştirilir.  
  
#### <a name="to-run-the-program"></a>Programı çalıştırmak için  
  
1. Projeyi çalışma moduna almak için F5 tuşuna basın.  
  
2. **Görevi Başlat** düğmesine tıklayın. `PercentDone` Olay her oluşturulduğunda etiket, tamamlanan görevin yüzdesine göre güncelleştirilir.  
  
3. Görevi durdurmak için **iptal** düğmesine tıklayın. **İptal** düğmesinin görünümü tıkladığınızda hemen değişmediğine dikkat edin. Etkinlik olay işlemeye izin verdiğinden olay gerçekleşmeyecek `My.Application.DoEvents`. `Click`  
  
    > [!NOTE]
    > `My.Application.DoEvents` Yöntemi, olayları yalnızca formla aynı şekilde işlemez. Örneğin, bu kılavuzda, **iptal** düğmesine iki kez tıklamanız gerekir. Formun olayları doğrudan işlemesine izin vermek için çoklu iş parçacığı kullanımı ' nı kullanabilirsiniz. Daha fazla bilgi için bkz. [yönetilen Iş parçacığı](../../../../standard/threading/index.md).
  
 Programı F11 ile çalıştırmaya ve bir kerede bir satırda bir satır adım adım ilerlebileceğinizi fark edebilirsiniz. Yürütmenin nasıl girdiğini `LongTask`açıkça görebilir ve `PercentDone` olay `Form1` her oluşturulduğunda kısa bir süre sonra yeniden girebilirsiniz.  
  
 Yürütme kodunda `Form1` `LongTask` geri yüklenirken ne olur?, yöntem yeniden çağırılır mi? En kötü, olay her oluştuğunda çağrılırsa bir yığın `LongTask` taşması meydana gelebilir.  
  
 `mWidget` `Widget` Yeni öğesinebir`mWidget`başvuru atayarak, değişkenin farklı bir nesne için olayları işlemesine neden olabilirsiniz. `Widget` Aslında, düğmeye her tıkladığınızda kodu `Button1_Click` bunu yapabilirsiniz.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Farklı bir pencere öğesinin olaylarını işlemek için  
  
- Aşağıdaki kod satırını, şu şekilde `Button1_Click` `mWidget.LongTask(12.2, 0.33)`görüntülenen satırdan hemen önce ekleyin:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 Yukarıdaki kod, düğme tıklandığında yeni `Widget` bir oluşturur. `LongTask` Yöntemi tamamlandıktan hemen sonra, başvurusu `Widget` serbest bırakılır ve `Widget` yok edilir.  
  
 Bir değişken tek seferde yalnızca bir nesne başvurusu içerebilir, bu nedenle ' `mWidget`ye farklı `Widget` bir nesne atarsanız, önceki `Widget` nesnenin olayları artık işlenmeyecek. `WithEvents` Eğer `mWidget` eski`Widget`bir başvuruyu içeren tek nesne değişkense, nesne yok edilir. Çeşitli `Widget` nesnelerden olayları işlemek istiyorsanız, her bir nesneden olayları ayrı olarak `AddHandler` işlemek için ifadesini kullanın.  
  
> [!NOTE]
> İhtiyaç duyduğunuz kadar çok `WithEvents` değişken bildirebilirsiniz, ancak `WithEvents` değişkenlerin dizileri desteklenmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Olayları bildirme ve oluşturma](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)
