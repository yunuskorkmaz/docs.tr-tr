---
title: Olayları bildirme ve oluşturma (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 20e2b0efbf40597049c515134f408927f18d5603
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956332"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>İzlenecek yol: Olayları bildirme ve oluşturma (Visual Basic)
Bu izlenecek yol, adlı `Widget`bir sınıf için olayların nasıl bildirileceğini ve oluşturulduğunu gösterir. Adımları tamamladıktan sonra yardımcı konusunu okumak isteyebilirsiniz, [izlenecek yol: Bir uygulamada](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)durum bilgilerini sağlamak için `Widget` nesnelerden olayları nasıl kullanacağınızı gösteren olayları işleme.  
  
## <a name="the-widget-class"></a>Pencere öğesi sınıfı  
 Bir `Widget` sınıfa sahip olduğunuz andaki varsayılır. `Widget` Sınıfınız, yürütülmesi uzun sürebilecek bir yönteme sahiptir ve uygulamanızın bir tür tamamlanma göstergesi koyabilmesini istiyorsunuz.  
  
 Kuşkusuz `Widget` , nesneyi yüzde-tam-Tamam iletişim kutusu olarak gösterebilirsiniz, ancak bu iletişim kutusuyla `Widget` sınıfı kullandığınız her projede bu iletişim kutusuyla birlikte kalmış olursunuz. Nesne tasarımının iyi bir prensibi, nesnenin tüm amacı bir form veya iletişim kutusunu yönetmediği için, bir nesneyi kullanan uygulamanın kullanıcı arabirimini işlemesini sağlamaktır.  
  
 Amacı `Widget` diğer görevleri gerçekleştirmelidir, bu nedenle bir `PercentDone` olay eklemek ve yöntemlerini çağıran `Widget`yordamın bu olayı işleme ve durum güncelleştirmelerini görüntülemesini sağlamak daha iyidir. `PercentDone` Olay, görevi iptal etmek için bir mekanizma da sağlayabilir.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Bu konunun kod örneğini oluşturmak için  
  
1. Yeni bir Visual Basic Windows uygulaması projesi açın ve adlı `Form1`bir form oluşturun.  
  
2. İçin `Form1`iki düğme ve bir etiket ekleyin.  
  
3. Nesneleri aşağıdaki tabloda gösterildiği gibi adlandırın.  
  
    |Nesne|Özellik|Ayar|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Başlangıç görevi|  
    |`Button2`|`Text`|İptal|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4. Proje menüsünde , projeye adlı `Widget.vb` bir sınıf eklemek için **Sınıf Ekle** ' yi seçin.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Pencere öğesi sınıfı için bir olay bildirmek için  
  
- `Widget` Sınıfında bir olay bildirmek için anahtarsözcüğünükullanın.`Event` Olayın, `ByVal` olaygösterdiğigibi`PercentDone` `ByRef` `Widget`, ve bağımsız değişkenlerine sahip olabileceğini unutmayın:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 Çağıran nesne bir `PercentDone` olay aldığında `Percent` , bağımsız değişken tamamlanmış görevin yüzdesini içerir. Bağımsız değişkeni, olayı oluşturan yöntemi `True` iptal etmek için olarak ayarlanabilir. `Cancel`  
  
> [!NOTE]
> Aşağıdaki özel durumlarla birlikte, yordam bağımsız değişkenlerini yaptığınız gibi olay bağımsız değişkenlerini bildirebilirsiniz: Olaylar veya `Optional` `ParamArray` bağımsız değişkenlere sahip olamaz ve olayların dönüş değerleri yoktur.  
  
 Olay, `Widget` sınıfının `LongTask` yöntemi tarafından tetiklenir. `PercentDone` `LongTask`iki bağımsız değişken alır: yöntemin iş yapmakta olduğu sürenin uzunluğu ve `LongTask` `PercentDone` olayı yükseltmek için duraklamadan önce en kısa zaman aralığı.  
  
#### <a name="to-raise-the-percentdone-event"></a>PercentDone olayını yükseltmek için  
  
1. Bu sınıf tarafından kullanılan `Timer` özelliğe erişimi basitleştirmek için, `Class Widget` sınıfının üst kısmındaki bildirim `Imports` bölümünün üst kısmına bir ifade ekleyin.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. `Widget` Sınıfına aşağıdaki kodu ekleyin:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 Uygulamanız `LongTask` yöntemini çağırdığında `Widget` , sınıfı `PercentDone` olayı her `MinimumInterval` saniye yükseltir. Olay döndüğünde, `LongTask` `Cancel` bağımsız değişkenin olarak `True`ayarlanmış olup olmadığını denetler.  
  
 Burada birkaç bildirimler gereklidir. Kolaylık olması için, `LongTask` yordamda görevin ne kadar süreceğine ilişkin daha fazla bilgi sahibi olduğunuz varsayılır. Bu neredeyse hiçbir durum değildir. Görevleri bile eşit ölçekli parçalara bölmek zor olabilir ve genellikle kullanıcıların en önemli bir şeyi, bir şeyin meydana geldiğinin bir göstergesi olmadan önce geçen süreyi belirtir.  
  
 Bu örnekte başka bir kusuru açığa çıkabilir. `Timer` Özelliği, gece yarısından beri geçen saniye sayısını döndürür; bu nedenle, uygulama gece yarısından önce başlatılmışsa, uygulama takılmış olur. Bu süreyi ölçmeye yönelik daha dikkatli bir yaklaşım, gibi özellikleri `Now`kullanarak, bunun dikkate alınması veya bunların tamamen olmaması gibi sınır koşullarını ele alır.  
  
 Artık `Widget` sınıfın olayları tetiklemediğini, sonraki izlenecek yolu izleyebilirsiniz. [İzlenecek yol: Olayları](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) işleme `WithEvents` ,`PercentDone` olay işleyicisini olayla ilişkilendirmek için nasıl kullanılacağını gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [İzlenecek yol: Olayları işleme](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)
