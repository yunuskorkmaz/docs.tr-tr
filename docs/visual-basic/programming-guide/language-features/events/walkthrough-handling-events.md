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
ms.openlocfilehash: cb42f2e41e366cf8765cb9395d1a5641434bab40
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345078"
---
# <a name="walkthrough-handling-events-visual-basic"></a>İzlenecek yol: Olayları İşleme (Visual Basic)
Bu, etkinliklerle nasıl çalışabileceğini gösteren iki konunun ikinci konudır. [Izlenecek yol: Izlenecek yol: olayları bildirme ve](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)oluşturma, olayların nasıl bildirilemeyeceğini ve tetikleyeceğinizi gösterir. Bu bölüm, bu kılavuzda yer alan formu ve sınıfı kullanır.  
  
 `Widget` sınıfı örneği geleneksel olay işleme deyimlerini kullanır. Visual Basic olaylarla çalışmaya yönelik başka teknikler de sağlar. Bir alıştırma olarak, `AddHandler` ve `Handles` deyimlerini kullanmak için bu örneği değiştirebilirsiniz.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Pencere öğesi sınıfının PercentDone olayını işlemek için  
  
1. Aşağıdaki kodu `Form1`yerleştirin:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     `WithEvents` anahtar sözcüğü, `mWidget` değişkeninin bir nesnenin olaylarını işlemek için kullanıldığını belirtir. Nesnenin türünü, nesnenin oluşturulacağı sınıfın adını sağlayarak belirtirsiniz.  
  
     `WithEvents` değişkenlerinin sınıf düzeyi olması gerektiğinden `mWidget` değişkeni `Form1` olarak bildirilmiştir. Bu, yerleştirdiğiniz sınıf türünden bağımsız olarak geçerlidir.  
  
     `mblnCancel` değişkeni `LongTask` metodunu iptal etmek için kullanılır.  
  
## <a name="writing-code-to-handle-an-event"></a>Bir olayı Işlemek için kod yazma  
 `WithEvents`kullanarak bir değişken bildirdikten hemen sonra, sınıfın **kod düzenleyicisinin**sol açılır listesinde değişken adı belirir. `mWidget`' yi seçtiğinizde, `Widget` sınıfının olayları sağ açılan listede görüntülenir. Bir olay seçildiğinde ilgili olay yordamı, önek `mWidget` ve alt çizgiyle birlikte görüntülenir. Bir `WithEvents` değişkeniyle ilişkili tüm olay yordamlarına önek olarak değişken adı verilir.  
  
#### <a name="to-handle-an-event"></a>Bir olayı işlemek için  
  
1. **Kod düzenleyicisinde**sol aşağı açılan listeden `mWidget` ' yi seçin.  
  
2. Sağ açılan listeden `PercentDone` olayı ' nı seçin. **Kod düzenleyicisi** `mWidget_PercentDone` olay yordamını açar.  
  
    > [!NOTE]
    > **Kod Düzenleyicisi** , yeni olay işleyicileri eklemek için yararlıdır, ancak gerekli değildir. Bu kılavuzda, yalnızca olay işleyicilerini doğrudan kodunuza kopyalamak daha doğrudan bir örnek olur.  
  
3. `mWidget_PercentDone` olay işleyicisine aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     `PercentDone` olayı her oluşturulduğunda, olay yordamı bir `Label` denetimindeki tamamlanma yüzdesini gösterir. `DoEvents` yöntemi etiketin yeniden çizileceğinin yanı sıra kullanıcıya **iptal** düğmesine tıklama fırsatı verir.  
  
4. `Button2_Click` olay işleyicisi için aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 `LongTask` çalışırken Kullanıcı **iptal** düğmesine tıkladığında, `DoEvents` deyimin olay işlemenin oluşmasına izin verdiği anda `Button2_Click` olay yürütülür. Sınıf düzeyi değişken `mblnCancel` `True`olarak ayarlanır ve `mWidget_PercentDone` olayı bunu sınar ve `ByRef Cancel` bağımsız değişkenini `True`olarak ayarlar.  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Bir WithEvents değişkenini bir nesneye bağlama  
 `Form1` artık `Widget` nesnenin olaylarını işleyecek şekilde ayarlanmıştır. Her şey bir yerde `Widget` bulmaktadır.  
  
 Tasarım zamanında `WithEvents` bir değişken bildirdiğinizde, onunla ilişkili bir nesne yoktur. `WithEvents` değişken diğer herhangi bir nesne değişkeni gibidir. Bir nesne oluşturmanız ve `WithEvents` değişkeniyle buna bir başvuru atamanız gerekir.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Bir nesne oluşturmak ve buna bir başvuru atamak için  
  
1. **Kod düzenleyicisinde**sol aşağı açılan listeden **(Form1 olayları)** öğesini seçin.  
  
2. Sağ açılan listeden `Load` olayı ' nı seçin. **Kod düzenleyicisi** `Form1_Load` olay yordamını açar.  
  
3. `Widget`oluşturmak için `Form1_Load` olay yordamı için aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 Bu kod yürütüldüğünde, Visual Basic bir `Widget` nesnesi oluşturur ve olaylarını `mWidget`ilişkili olay yordamlarına bağlar. Bu noktadan itibaren, `Widget` `PercentDone` olayını her yükseldiğinde `mWidget_PercentDone` olay yordamı yürütülür.  
  
#### <a name="to-call-the-longtask-method"></a>LongTask yöntemini çağırmak için  
  
- `Button1_Click` olay işleyicisine aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 `LongTask` yöntemi çağrılmadan önce, tamamlanma yüzdesini gösteren etiketin başlatılması ve yöntemin iptal edilmesi için sınıf düzeyi `Boolean` bayrağının `False`olarak ayarlanması gerekir.  
  
 `LongTask`, 12,2 saniyelik bir görev süresiyle çağrılır. `PercentDone` olay, saniyenin her biri üçte bir kez tetiklenir. Olay her oluşturulduğunda `mWidget_PercentDone` olay yordamı yürütülür.  
  
 `LongTask` tamamlandığında, `LongTask` normal şekilde sonlandırıldığı veya `mblnCancel` `True`olarak ayarlandığı için `mblnCancel` test edilmiştir. Tamamlanma yüzdesi yalnızca önceki durumda güncelleştirilir.  
  
#### <a name="to-run-the-program"></a>Programı çalıştırmak için  
  
1. Projeyi çalışma moduna almak için F5 tuşuna basın.  
  
2. **Görevi Başlat** düğmesine tıklayın. `PercentDone` olayı her oluşturulduğunda etiket, tamamlanan görevin yüzdesine göre güncelleştirilir.  
  
3. Görevi durdurmak için **iptal** düğmesine tıklayın. **İptal** düğmesinin görünümü tıkladığınızda hemen değişmediğine dikkat edin. `My.Application.DoEvents` deyimin olay işlemeye izin verdiğinden `Click` olayı gerçekleşmeyecek.  
  
    > [!NOTE]
    > `My.Application.DoEvents` yöntemi, olayları yalnızca formla aynı şekilde işlemez. Örneğin, bu kılavuzda, **iptal** düğmesine iki kez tıklamanız gerekir. Formun olayları doğrudan işlemesine izin vermek için çoklu iş parçacığı kullanımı ' nı kullanabilirsiniz. Daha fazla bilgi için bkz. [yönetilen Iş parçacığı](../../../../standard/threading/index.md).
  
 Programı F11 ile çalıştırmaya ve bir kerede bir satırda bir satır adım adım ilerlebileceğinizi fark edebilirsiniz. Yürütmenin `LongTask`nasıl girdiğini açıkça görebilir ve `PercentDone` olayı her oluşturulduğunda `Form1` kısa bir süre sonra yeniden girebilirsiniz.  
  
 Yürütme `Form1`koduna geri alındığı sürece ne olur? `LongTask` yöntemi yeniden çağrıldı mı? En kötü, olay her başlatıldığında `LongTask` çağrılırsa bir yığın taşması meydana gelebilir.  
  
 Yeni `Widget` `mWidget`için bir başvuru atayarak, değişken `mWidget` farklı bir `Widget` nesnesinin olaylarını işlemesini sağlayabilirsiniz. Aslında, düğmesine her tıkladığınızda kodu `Button1_Click` yapabilirsiniz.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Farklı bir pencere öğesinin olaylarını işlemek için  
  
- Aşağıdaki kod satırını, `mWidget.LongTask(12.2, 0.33)`okuyan satırdan hemen önce `Button1_Click` yordama ekleyin:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 Yukarıdaki kod, düğme tıklandığında yeni bir `Widget` oluşturur. `LongTask` yöntemi tamamlandıktan hemen sonra, `Widget` başvurusu serbest bırakılır ve `Widget` yok edilir.  
  
 Bir `WithEvents` değişken aynı anda yalnızca bir nesne başvurusu içerebilir, bu nedenle `mWidget`farklı bir `Widget` nesnesi atarsanız, önceki `Widget` nesnesinin olayları artık işlenmeyecek. `mWidget` eski `Widget`bir başvuru içeren tek nesne değişkense, nesne yok edilir. Birkaç `Widget` nesnesinden olayları işlemek istiyorsanız, her bir nesneden olayları ayrı olarak işlemek için `AddHandler` ifadesini kullanın.  
  
> [!NOTE]
> İhtiyaç duyduğunuz sayıda `WithEvents` değişken bildirebilirsiniz, ancak `WithEvents` değişkenlerin dizileri desteklenmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: Olay Bildirme ve Oluşturma](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)
