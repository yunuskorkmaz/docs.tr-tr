---
title: Olay Bildirme ve Oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 6f4c303604f9cf55b4ecd500636e0d2772b6234c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345095"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>İzlenecek yol: Olay Bildirme ve Oluşturma (Visual Basic)
Bu izlenecek yolda, `Widget`adlı bir sınıf için olayların nasıl bildirileceğini ve tetikleyeceğinizi gösterilmektedir. Adımları tamamladıktan sonra, bir uygulamada durum bilgilerini sağlamak için `Widget` nesnelerinden olayları nasıl kullanacağınızı gösteren [Izlenecek yol: olayları işleme](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)başlıklı yardımcı konuyu okumak isteyebilirsiniz.  
  
## <a name="the-widget-class"></a>Pencere öğesi sınıfı  
 `Widget` sınıfa sahip olduğunuz bir süre için varsayıyoruz. `Widget` sınıfınız, yürütülmesi uzun sürebilecek bir yönteme sahiptir ve uygulamanızın bir tür tamamlanma göstergesi koyabilmesini istersiniz.  
  
 Kuşkusuz, `Widget` nesnenin yüzde-Tamam iletişim kutusunu göstermesini sağlayabilirsiniz, ancak ardından `Widget` sınıfını kullandığınız her projede bu iletişim kutusuyla birlikte kalmış olursunuz. Nesne tasarımının iyi bir prensibi, nesnenin tüm amacı bir form veya iletişim kutusunu yönetmediği için, bir nesneyi kullanan uygulamanın kullanıcı arabirimini işlemesini sağlamaktır.  
  
 `Widget` amacı diğer görevleri gerçekleştirmelidir; bu nedenle, bir `PercentDone` olayı eklemek ve `Widget`yöntemlerini çağıran yordamın bu olayı işleme ve durum güncelleştirmelerini görüntülemesini sağlamak daha iyidir. `PercentDone` olay, görevi iptal etmek için bir mekanizma da sağlayabilir.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Bu konunun kod örneğini oluşturmak için  
  
1. Yeni bir Visual Basic Windows uygulaması projesi açın ve `Form1`adlı bir form oluşturun.  
  
2. `Form1`için iki düğme ve bir etiket ekleyin.  
  
3. Nesneleri aşağıdaki tabloda gösterildiği gibi adlandırın.  
  
    |Nesne|Özellik|Ayar|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Başlangıç görevi|  
    |`Button2`|`Text`|İptal|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4. **Proje menüsünde,** projeye `Widget.vb` adlı bir sınıf eklemek Için **Sınıf Ekle** ' yi seçin.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Pencere öğesi sınıfı için bir olay bildirmek için  
  
- `Widget` sınıfında bir olay bildirmek için `Event` anahtar sözcüğünü kullanın. Bir olayın `ByVal` ve `ByRef` bağımsız değişkenleri `Widget``PercentDone` olay gösterdiği gibi olabileceğini unutmayın:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 Çağıran nesne `PercentDone` bir olay aldığında, `Percent` bağımsız değişkeni tamamlanan görevin yüzdesini içerir. `Cancel` bağımsız değişkeni, olayı oluşturan yöntemi iptal etmek için `True` olarak ayarlanabilir.  
  
> [!NOTE]
> Aşağıdaki özel durumlarla birlikte, yordamların bağımsız değişkenlerini yaptığınız gibi olay bağımsız değişkenlerini bildirebilirsiniz: olaylarda `Optional` veya `ParamArray` bağımsız değişken olamaz ve olayların dönüş değerleri yoktur.  
  
 `PercentDone` olay `Widget` sınıfının `LongTask` yöntemi tarafından tetiklenir. `LongTask` iki bağımsız değişken alır: yöntemin iş yapmakta olduğu zaman uzunluğu ve `LongTask` duraklamadan önce `PercentDone` olayını tetikleyen en kısa zaman aralığı.  
  
#### <a name="to-raise-the-percentdone-event"></a>PercentDone olayını yükseltmek için  
  
1. Bu sınıf tarafından kullanılan `Timer` özelliğine erişimi basitleştirmek için, sınıf modülünüzün üst kısmına `Class Widget` deyimin üst kısmına bir `Imports` bildirimi ekleyin.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. `Widget` sınıfına aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 Uygulamanız `LongTask` yöntemini çağırdığında, `Widget` sınıfı her `MinimumInterval` saniyede `PercentDone` olayını oluşturur. Olay döndüğünde, `LongTask` `Cancel` bağımsız değişkeninin `True`olarak ayarlandığını denetler.  
  
 Burada birkaç bildirimler gereklidir. Kolaylık sağlaması için `LongTask` yordamı, görevin ne kadar süreceğine ilişkin olduğunu varsayar. Bu neredeyse hiçbir durum değildir. Görevleri bile eşit ölçekli parçalara bölmek zor olabilir ve genellikle kullanıcıların en önemli bir şeyi, bir şeyin meydana geldiğinin bir göstergesi olmadan önce geçen süreyi belirtir.  
  
 Bu örnekte başka bir kusuru açığa çıkabilir. `Timer` özelliği, gece yarısından beri geçen saniye sayısını döndürür; Bu nedenle, uygulama gece yarısından önce başlatıldıysa, takılmış olur. Bu süreyi ölçmeye yönelik daha dikkatli bir yaklaşım, `Now`gibi özellikleri kullanarak bunun dikkate alınması veya bunların tamamen olmaması gibi sınır koşullarını ele alır.  
  
 Artık `Widget` sınıfı olayları tetiklemediğini de bir sonraki izlenecek yol için geçebilirsiniz. [Izlenecek yol: olayları işleme](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) , bir olay işleyicisini `PercentDone` olay ile ilişkilendirmek için `WithEvents` nasıl kullanacağınızı gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [İzlenecek yol: Olayları İşleme](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)
