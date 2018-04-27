---
title: İşleme olaylar (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c1743e5f5d9dcdf83ab646407cd1fcdc77ff71cd
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-handling-events-visual-basic"></a>İzlenecek yol: Olayları İşleme (Visual Basic)
Bu olayları ile çalışmak nasıl gösteren iki konuları saniyedir. İlk konu [izlenecek yol: bildiren ve yükseltmeyi olayları](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), bildirme ve olaylarının arttığı gösterilmektedir. Bu bölümde, bunlar gerçekleştiğinde olayları işlemek nasıl göstermek için bu gözden geçirme sınıfından ve form kullanır.  
  
 `Widget` Sınıf örneği, geleneksel olay işleme deyimleri kullanır. Visual Basic olaylar ile çalışmak için başka teknikler sağlar. Bir alıştırma kullanmak için bu örnek değiştirebilirsiniz `AddHandler` ve `Handles` deyimleri.  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>Pencere sınıfı PercentDone olayını işlemek için  
  
1.  Aşağıdaki kodda yerleştirin `Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     `WithEvents` Anahtar sözcüğü belirtir değişkeni `mWidget` nesnenin olayları işlemek için kullanılır. Nesne Oluşturulacak sınıfın adını sağlayarak nesne türünü belirtin.  
  
     Değişkeni `mWidget` içinde bildirilen `Form1` çünkü `WithEvents` değişkenleri sınıf düzeyinde olması gerekir. Bu, bunların içine yerleştirin sınıf türü ne olursa olsun geçerlidir.  
  
     Değişkeni `mblnCancel` iptal etmek için kullanılan `LongTask` yöntemi.  
  
## <a name="writing-code-to-handle-an-event"></a>Bir olay işlemek için kod yazma  
 Bir değişken kullanarak bildirme hemen `WithEvents`, değişken adı sınıfının sol aşağı açılan listede görüntülenir **Kod düzenleyicisinde**. Seçtiğinizde, `mWidget`, `Widget` sınıfının olayları sağda açılan listede görünür. Bir olay seçerek görüntüler önek ile ilgili olay yordamını `mWidget` ve alt çizgi. İle ilişkili tüm olay yordamları bir `WithEvents` değişkeni, değişken adı öneki olarak verilmiştir.  
  
#### <a name="to-handle-an-event"></a>Bir olay işleme  
  
1.  Seçin `mWidget` sol aşağı açılan listeden **Kod düzenleyicisinde**.  
  
2.  Seçin `PercentDone` sağda açılan listeden olay. **Kod düzenleyicisinde** açılır `mWidget_PercentDone` olay yordamı.  
  
    > [!NOTE]
    >  **Kod düzenleyicisinde** yararlıdır, ancak gerekli değil, yeni olay işleyicileri ekleme. Bu kılavuzda, doğrudan erişimli olay işleyicileri yalnızca doğrudan kodunuza kopyalayın.  
  
3.  Aşağıdaki kodu ekleyin `mWidget_PercentDone` olay işleyicisi:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     Her `PercentDone` olayı, olay yordamı içinde tamamlanma görüntüler bir `Label` denetim. `DoEvents` Yöntemi çizilecek, etiket sağlar ve ayrıca kullanıcı tıklatın fırsatı sunar **iptal** düğmesi.  
  
4.  İçin aşağıdaki kodu ekleyip `Button2_Click` olay işleyicisi:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 Kullanıcı tıklarsa **iptal** düğmesini basılı `LongTask` çalıştığından, `Button2_Click` olay yürütüldüğünde hemen `DoEvents` deyimi olay işleme oluşmasına izin verir. Sınıf düzeyi değişkeni `mblnCancel` ayarlanır `True`ve `mWidget_PercentDone` olay sonra onu sınar ve ayarlar `ByRef Cancel` bağımsız değişkeni `True`.  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>Bir nesneye bir WithEvents değişkeni bağlanma  
 `Form1` Şimdi işlemek üzere ayarlanmış bir `Widget` nesnenin olaylar. Kalan tek şey bulmak için bir `Widget` yere.  
  
 Bir değişken bildirme zaman `WithEvents` tasarım zamanında hiçbir nesne ile ilişkilidir. A `WithEvents` yalnızca herhangi bir başka nesne değişken gibi bir değişkendir. Bir nesne oluşturmak ve onunla başvuru atamak kullandığınız `WithEvents` değişkeni.  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>Bir nesne oluşturmak ve ona başvuru atamak için  
  
1.  Seçin **(Form1 olayları)** sol aşağı açılan listeden **Kod düzenleyicisinde**.  
  
2.  Seçin `Load` sağda açılan listeden olay. **Kod düzenleyicisinde** açılır `Form1_Load` olay yordamı.  
  
3.  İçin aşağıdaki kodu ekleyip `Form1_Load` oluşturmak için olay yordamı `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 Bu kod yürütüldüğünde, Visual Basic oluşturur bir `Widget` nesne ve ilişkili olay yordamları olaylarına bağlanır `mWidget`. Noktasındaki, her `Widget` başlatır kendi `PercentDone` olay `mWidget_PercentDone` olay yordamı gerçekleştirilir.  
  
#### <a name="to-call-the-longtask-method"></a>LongTask yöntemini çağırmak için  
  
-   Aşağıdaki kodu ekleyin `Button1_Click` olay işleyicisi:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 Önce `LongTask` yöntemi çağrıldığında, tamamlanma görüntüler başlatılmalıdır etiketi ve sınıf düzeyi `Boolean` yöntemi iptal etme ayarlanmalıdır için bayrak `False`.  
  
 `LongTask` görev süresi 12.2 saniye olarak adlandırılır. `PercentDone` Olayı kez her üçte birinden bir saniye. Olayı, her zaman `mWidget_PercentDone` olay yordamı gerçekleştirilir.  
  
 Zaman `LongTask` yapılır, `mblnCancel` olup olmadığını test `LongTask` normal şekilde sona erdi veya çünkü durdurduysanız `mblnCancel` ayarlandı `True`. Tamamlanma yüzdesi yalnızca eski durumda güncelleştirilir.  
  
#### <a name="to-run-the-program"></a>Programı çalıştırmak için  
  
1.  Proje çalışma moduna için F5 tuşuna basın.  
  
2.  Tıklatın **görevi Başlat** düğmesi. Her zaman `PercentDone` olayı, etiket tamamlandıktan görev yüzdesi güncelleştirilir.  
  
3.  Tıklatın **iptal** görevi Durdur düğmesini. Dikkat görünümünü **iptal** düğmesini tıklatın zaman hemen değiştirmez. `Click` Olamaz olay meydana kadar `My.Application.DoEvents` deyimi olay işleme izin verir.  
  
    > [!NOTE]
    >  `My.Application.DoEvents` Yöntemi form yaptığı gibi tam olarak aynı şekilde olayları işlemez. Örneğin, bu kılavuzda, tıklatmalısınız **iptal** iki kez düğmesine tıklayın. Formun olayları doğrudan işlemek izin vermek için kullanabileceğiniz çoklu iş parçacığı kullanımı. Daha fazla bilgi için bkz: [parçacıkları](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).  
  
 İle F11 programını çalıştırın ve kodda bir defada bir satır adım için eğitici bulabilirsiniz. Yürütme nasıl girer açıkça görebilirsiniz `LongTask`ve ardından kısaca yeniden girer `Form1` her zaman `PercentDone` olayı oluşturulur.  
  
 Ne olacağını yürütme geri kodunda ederken IF `Form1`, `LongTask` yönteminden yeniden? En kötü senaryoda, bir yığın taşması oluşabilir `LongTask` olayın tetiklendiği her zaman çağrılır.  
  
 Değişkeni neden `mWidget` için farklı bir olayları işlemek için `Widget` yeni başvuru atayarak nesne `Widget` için `mWidget`. Aslında, kodda yapabileceğiniz `Button1_Click` düğmesini her zaman bu yapın.  
  
#### <a name="to-handle-events-for-a-different-widget"></a>Farklı bir pencere öğesi için olayları işlemek için  
  
-   Aşağıdaki kod satırını ekleyin `Button1_Click` yazan satırı hemen önceki yordamı, `mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 Yukarıdaki kod yeni bir oluşturur `Widget` düğmesine tıklandığında her zaman. Hemen `LongTask` yöntemi tamamlayan, başvuru `Widget` yayımlandığı ve `Widget` yok.  
  
 A `WithEvents` değişkeni, bir kerede yalnızca bir nesne başvurusu içerebilir bunu farklı bir atarsanız `Widget` nesnesini `mWidget`, önceki `Widget` nesnenin olayları artık işleneceğini. Varsa `mWidget` olan eski bir başvuru içeren yalnızca nesne değişkeni `Widget`, nesne yok. Birkaç olayları işlemek istiyorsanız `Widget` nesneleri, kullanın `AddHandler` her nesneden olayları ayrı ayrı işlemek için deyimi.  
  
> [!NOTE]
>  Sayıda bildirebilir `WithEvents` değişkenleri, olarak gerekir, dizi `WithEvents` değişkenleri desteklenmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Olay Bildirme ve Oluşturma](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)  
 [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)
