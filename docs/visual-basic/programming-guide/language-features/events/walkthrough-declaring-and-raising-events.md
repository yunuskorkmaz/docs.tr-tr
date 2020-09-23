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
ms.openlocfilehash: 07ef611b50cfa13f77fa168d58dd3b43e97eeec6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057994"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>İzlenecek yol: Olay Bildirme ve Oluşturma (Visual Basic)

Bu izlenecek yol, adlı bir sınıf için olayların nasıl bildirileceğini ve oluşturulduğunu gösterir `Widget` . Adımları tamamladıktan sonra, bir uygulamada durum bilgilerini sağlamak için nesnelerden olayları nasıl kullanacağınızı gösteren [Izlenecek yol: olayları işleme](walkthrough-handling-events.md)başlıklı yardımcı konuyu okumak isteyebilirsiniz `Widget` .  
  
## <a name="the-widget-class"></a>Pencere öğesi sınıfı  

 Bir sınıfa sahip olduğunuz andaki varsayılır `Widget` . `Widget`Sınıfınız, yürütülmesi uzun sürebilecek bir yönteme sahiptir ve uygulamanızın bir tür tamamlanma göstergesi koyabilmesini istiyorsunuz.  
  
 Kuşkusuz, `Widget` nesneyi yüzde-tam-Tamam iletişim kutusu olarak gösterebilirsiniz, ancak bu iletişim kutusuyla sınıfı kullandığınız her projede bu iletişim kutusuyla birlikte kalmış olursunuz `Widget` . Nesne tasarımının iyi bir prensibi, nesnenin tüm amacı bir form veya iletişim kutusunu yönetmediği için, bir nesneyi kullanan uygulamanın kullanıcı arabirimini işlemesini sağlamaktır.  
  
 Amacı `Widget` diğer görevleri gerçekleştirmelidir, bu nedenle bir `PercentDone` olay eklemek ve yöntemlerini çağıran yordamın `Widget` Bu olayı işleme ve durum güncelleştirmelerini görüntülemesini sağlamak daha iyidir. `PercentDone`Olay, görevi iptal etmek için bir mekanizma da sağlayabilir.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Bu konunun kod örneğini oluşturmak için  
  
1. Yeni bir Visual Basic Windows uygulaması projesi açın ve adlı bir form oluşturun `Form1` .  
  
2. İçin iki düğme ve bir etiket ekleyin `Form1` .  
  
3. Nesneleri aşağıdaki tabloda gösterildiği gibi adlandırın.  
  
    |Nesne|Özellik|Ayar|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Başlangıç görevi|  
    |`Button2`|`Text`|İptal|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4. **Proje menüsünde,** projeye adlı bir sınıf eklemek Için **Sınıf Ekle** ' yi seçin `Widget.vb` .  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Pencere öğesi sınıfı için bir olay bildirmek için  
  
- `Event`Sınıfında bir olay bildirmek için anahtar sözcüğünü kullanın `Widget` . Olayın `ByVal` `ByRef` , olay gösterdiği gibi, ve bağımsız değişkenlerine sahip olabileceğini unutmayın `Widget` `PercentDone` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 Çağıran nesne bir `PercentDone` olay aldığında, `Percent` bağımsız değişken tamamlanmış görevin yüzdesini içerir. `Cancel`Bağımsız değişkeni, `True` olayı oluşturan yöntemi iptal etmek için olarak ayarlanabilir.  
  
> [!NOTE]
> Aşağıdaki özel durumlarla birlikte, yordam bağımsız değişkenlerini yaptığınız gibi olay bağımsız değişkenlerini bildirebilirsiniz: olaylar `Optional` veya `ParamArray` bağımsız değişkenlere sahip olamaz ve olayların dönüş değerleri yoktur.  
  
 `PercentDone`Olay, sınıfının yöntemi tarafından tetiklenir `LongTask` `Widget` . `LongTask` iki bağımsız değişken alır: yöntemin iş yapmakta olduğu sürenin uzunluğu ve `LongTask` olayı yükseltmek için duraklamadan önce en kısa zaman aralığı `PercentDone` .  
  
#### <a name="to-raise-the-percentdone-event"></a>PercentDone olayını yükseltmek için  
  
1. `Timer`Bu sınıf tarafından kullanılan özelliğe erişimi basitleştirmek için, `Imports` sınıfının üst kısmındaki bildirim bölümünün üst kısmına bir ifade ekleyin `Class Widget` .  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. Sınıfına aşağıdaki kodu ekleyin `Widget` :  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 Uygulamanız `LongTask` yöntemini çağırdığında, `Widget` sınıfı `PercentDone` olayı her `MinimumInterval` saniye yükseltir. Olay döndüğünde, `LongTask` `Cancel` bağımsız değişkenin olarak ayarlanmış olup olmadığını denetler `True` .  
  
 Burada birkaç bildirimler gereklidir. Kolaylık olması için, `LongTask` yordamda görevin ne kadar süreceğine ilişkin daha fazla bilgi sahibi olduğunuz varsayılır. Bu neredeyse hiçbir durum değildir. Görevleri bile eşit ölçekli parçalara bölmek zor olabilir ve genellikle kullanıcıların en önemli bir şeyi, bir şeyin meydana geldiğinin bir göstergesi olmadan önce geçen süreyi belirtir.  
  
 Bu örnekte başka bir kusuru açığa çıkabilir. `Timer`Özelliği, gece yarısından beri geçen saniye sayısını döndürür; bu nedenle, uygulama gece yarısından önce başlatılmışsa, uygulama takılmış olur. Bu süreyi ölçmeye yönelik daha dikkatli bir yaklaşım, gibi özellikleri kullanarak, bunun dikkate alınması veya bunların tamamen olmaması gibi sınır koşullarını ele alır `Now` .  
  
 Artık `Widget` sınıfın olayları tetiklemediğini, sonraki izlenecek yolu izleyebilirsiniz. [Izlenecek yol: olayları işleme](walkthrough-handling-events.md) `WithEvents` , olay işleyicisini olayla ilişkilendirmek için nasıl kullanılacağını gösterir `PercentDone` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [İzlenecek yol: Olayları İşleme](walkthrough-handling-events.md)
- [Ekinlikler](index.md)
