---
title: Olaylarını işleme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 2af8fe5557e452db1ef3a72de35582b18117cc30
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553743"
---
# <a name="walkthrough-handling-events-visual-basic"></a>İzlenecek yol: Olaylarını işleme (Visual Basic)
Olaylar ile çalışmaya nasıl gösteren iki konuları saniyedir. İlk konu [izlenecek yol: Olayları bildirmek ve yükseltmeyi](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), bildirmek ve olaylarını gösterir. Bu bölümde, bu izlenecek yol sınıf ve form bunlar gerçekleştiğinde olayların nasıl işleneceğini göstermek için kullanılır.  
  
 `Widget` Geleneksel olay işleme deyimleri sınıfı örneğini kullanır. Visual Basic, olayları ile çalışmaya yönelik diğer teknikleri sağlar. Bu örneği kullanmak için değiştirebileceğiniz bir alıştırma olarak `AddHandler` ve `Handles` deyimleri.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Pencere öğesi sınıfının PercentDone olayı işlemek için  
  
1.  Aşağıdaki kodda yerleştirin `Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     `WithEvents` Anahtar sözcüğü belirtir değişkeni `mWidget` nesnenin olayları işlemek için kullanılır. Nesne türünün, nesnenin oluşturulacağı sınıfının adı sağlayarak belirtin.  
  
     Değişken `mWidget` bölümünde bildirilen `Form1` çünkü `WithEvents` sınıf düzeyi değişkenleri olması gerekir. Bu, yerleştirebilirsiniz, sınıf türünden bağımsız olarak geçerlidir.  
  
     Değişken `mblnCancel` iptal etmek için kullanılan `LongTask` yöntemi.  
  
## <a name="writing-code-to-handle-an-event"></a>Bir olayı işlemek için kod yazma  
 Bir değişken kullanarak bildirdiğiniz hemen sonra `WithEvents`, değişken adı sınıfın sol aşağı açılan listede görünür **Kod Düzenleyicisi**. Seçtiğinizde, `mWidget`, `Widget` sınıfın olayları, sağda açılan listede görünür. Bir olay seçerek görüntüler önek ile ilgili olay yordamı `mWidget` ve alt çizgi. İle ilişkili tüm olay yordamları bir `WithEvents` değişkeni, değişken adı bir önek olarak verilmiştir.  
  
#### <a name="to-handle-an-event"></a>Bir olayı işlemek için  
  
1.  Seçin `mWidget` sol aşağı açılan listeden **Kod Düzenleyicisi**.  
  
2.  Seçin `PercentDone` doğru aşağı açılan listeden olay. **Kod Düzenleyicisi** açılır `mWidget_PercentDone` olay yordamı.  
  
    > [!NOTE]
    >  **Kod Düzenleyicisi** kullanışlı, ancak gerekli değil, yeni olay işleyicileri ekleme. Bu kılavuzda, olay işleyicileri doğrudan kodunuza hemen kopyalayıp daha doğrudan.  
  
3.  Aşağıdaki kodu ekleyin `mWidget_PercentDone` olay işleyicisi:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     Her `PercentDone` olayı, olay yordamı, tamamlanma yüzdesini görüntüler bir `Label` denetimi. `DoEvents` Yöntemi çizilecek, etiket sağlar ve ayrıca kullanıcı tıklayın fırsatı sunar **iptal** düğmesi.  
  
4.  İçin aşağıdaki kodu ekleyin `Button2_Click` olay işleyicisi:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 Kullanıcı tıklarsa **iptal** düğmeye `LongTask` çalıştırıldığı `Button2_Click` olay yürütülür hemen sonra `DoEvents` deyimi gerçekleşmesi olay işleme sağlar. Sınıf düzeyi değişkenleri `mblnCancel` ayarlanır `True`ve `mWidget_PercentDone` olay ardından bunu test eder ve ayarlar `ByRef Cancel` bağımsız değişkeni `True`.  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Bir nesneye bir WithEvents değişkeni bağlanma  
 `Form1` artık işlemek üzere ayarlanmış bir `Widget` nesnenin olayları. Kalan tek şey bulmak için bir `Widget` yerde.  
  
 Bir değişken bildirdiğinizde `WithEvents` tasarım zamanında, kendisiyle ilişkilendirilmiş nesne yok. A `WithEvents` başka herhangi nesne bir değişken gibi bir değişkendir. Bir nesne oluşturun ve bunu bir başvuru atamak sahip olduğunuz `WithEvents` değişkeni.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Bir nesne oluşturun ve ona bir başvuru atamak için  
  
1.  Seçin **(Form1 olayları)** sol aşağı açılan listeden **Kod Düzenleyicisi**.  
  
2.  Seçin `Load` doğru aşağı açılan listeden olay. **Kod Düzenleyicisi** açılır `Form1_Load` olay yordamı.  
  
3.  İçin aşağıdaki kodu ekleyin `Form1_Load` oluşturmak için olay yordamı `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 Bu kod yürütüldüğünde, Visual Basic oluşturur bir `Widget` nesnesini ve ilişkili olay yordamları olaylarına bağlanır `mWidget`. Buradan işaret, zaman `Widget` başlatır, `PercentDone` olay `mWidget_PercentDone` olay yordamı yürütülür.  
  
#### <a name="to-call-the-longtask-method"></a>LongTask yöntemini çağırmak için  
  
-   Aşağıdaki kodu ekleyin `Button1_Click` olay işleyicisi:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 Önce `LongTask` yöntemi çağrıldığında, tamamlanma görüntüler başlatılmalıdır etiket ve sınıf düzeyi `Boolean` yöntemi iptal ayarlanmalıdır için bayrak `False`.  
  
 `LongTask` görev süresi 12.2 saniye ile adlandırılır. `PercentDone` Olayı kez her üçte birinin bir saniye. Olayı oluşturulur, her zaman `mWidget_PercentDone` olay yordamı yürütülür.  
  
 Zaman `LongTask` yapıldığında `mblnCancel` olmadığını görmek için test `LongTask` normalde, sona erdi veya nedeniyle durursa `mblnCancel` ayarlandı `True`. Tamamlanma yüzdesi, yalnızca önceki durumda güncelleştirilir.  
  
#### <a name="to-run-the-program"></a>Programı çalıştırmak için  
  
1.  Proje çalışma moduna için F5 tuşuna basın.  
  
2.  Tıklayın **görevi Başlat** düğmesi. Her zaman `PercentDone` olayı, etiketi tamamlandığında görev yüzdesi ile güncelleştirilir.  
  
3.  Tıklayın **iptal** görevi Durdur düğmesini. Dikkat görünümünü **iptal** tıkladığınız zaman hemen düğmesi değiştirmez. `Click` Olamaz, olay ortaya kadar `My.Application.DoEvents` deyimi olay işleme sağlar.  
  
    > [!NOTE]
    >  `My.Application.DoEvents` Yöntemi form gibi tam olarak aynı şekilde olayları işlemez. Örneğin, bu kılavuzda, tıklatmalısınız **iptal** düğmesini iki kez. Olayları doğrudan işlemeye izin vermek için kullanabileceğiniz çoklu iş parçacığı kullanımı. Daha fazla bilgi için [yönetilen iş parçacığı](../../../../standard/threading/index.md).
  
 F11 ile programı çalıştırın ve kodda bir satır aynı anda adım öğretici bulabilirsiniz. NET bir şekilde nasıl yürütme aşamasına girer gördüğünüz `LongTask`ve sonra kısa bir süreliğine yeniden girer `Form1` her zaman `PercentDone` olayı oluşturulur.  
  
 Ne olacağını yürütme kod içinde geri ederken ise `Form1`, `LongTask` yöntemi yeniden çağırılırsa? En kötü senaryoda, bir yığın taşması oluşabilir `LongTask` her olayın tetiklendiği zaman adı veriliyordu.  
  
 Değişken neden olabilir `mWidget` için farklı bir olayları işlemek için `Widget` yeni başvuru atayarak nesne `Widget` için `mWidget`. Aslında, kodda yapabileceğiniz `Button1_Click` düğmesine her seferinde bunu.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Farklı bir pencere öğesi için olayları işlemek için  
  
-   Aşağıdaki kod satırını ekleyin `Button1_Click` yazan satırı hemen önceki yordamı `mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 Yukarıdaki kod yeni bir oluşturur `Widget` düğmesine tıklandığında her zaman. Hemen sonra `LongTask` yöntemi tamamlandığında, başvuru `Widget` yayımlandığı ve `Widget` yok.  
  
 A `WithEvents` değişkeni, bir kerede yalnızca bir nesne başvurusu içerebilir bunu farklı bir atarsanız `Widget` nesnesini `mWidget`, önceki `Widget` nesnenin olayları artık işleneceğini. Varsa `mWidget` içeren eski bir başvuru yalnızca nesne değişkeni `Widget`, nesne yok. Birkaç olayları işlemek isterseniz `Widget` nesneleri kullanan `AddHandler` her bir nesneden olayları ayrı ayrı işlemek için deyimi.  
  
> [!NOTE]
>  Çok bildirebilirsiniz `WithEvents` yazarken değişkenleri gerekir, dizileri `WithEvents` değişkenleri desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [İzlenecek yol: Olay bildirme ve oluşturma](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)
