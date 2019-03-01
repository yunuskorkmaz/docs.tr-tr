---
title: (Visual Basic) olay bildirme ve oluşturma
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 04f3cab43f7f7f7fc73e0b209b1bacee136513b5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975400"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>İzlenecek yol: (Visual Basic) olay bildirme ve oluşturma
Bu izlenecek yolda bildirme ve adlı bir sınıf için bir olay yapmayı gösteren `Widget`. Adımları tamamladıktan sonra Yardımcısı konuyu okumak isteyebilirsiniz [izlenecek yol: Olayları işleme](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), olaylarından kullanmak nasıl `Widget` uygulamada durum bilgilerini sağlamak için nesneleri.  
  
## <a name="the-widget-class"></a>Pencere sınıfı  
 Sahip olduğunuz süre varsayar bir `Widget` sınıfı. `Widget` Sınıfında bir yöntem çalıştırmak uzun sürebilir ve uygulamanızın tamamlama göstergesi tür yerleştirebilir istiyorsanız.  
  
 Elbette yapabileceğiniz `Widget` nesne bir tamamlanma yüzdesi iletişim kutusu gösterir, ancak daha sonra bu iletişim kutusu, kullandığınız her projede takılmış `Widget` sınıfı. Bir nesne tanıtıcısına kullanıcı arabirimini kullanan uygulamaya bildirmek için iyi bir nesne tasarım ilkesini olan — bir form veya iletişim kutusu yönetmek için tek amaç nesnenin olmadığı sürece.  
  
 Amacı `Widget` eklemek daha iyi, bu nedenle diğer görevleri gerçekleştirmek için bir `PercentDone` olay ve let çağıran yordam `Widget`kullanıcının, yöntemleri işleyen olayı ve görüntü durumunu güncelleştirir. `PercentDone` Olay ayrıca görev iptal etmek için bir mekanizma sağlar.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Bu konu için kod örneği oluşturmak için  
  
1.  Yeni bir Visual Basic Windows uygulaması projesi açın ve adlı bir form oluşturun `Form1`.  
  
2.  İki düğme ve bir etiketin ekleme `Form1`.  
  
3.  Aşağıdaki tabloda gösterildiği gibi nesneleri ad.  
  
    |Nesne|Özellik|Ayar|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Başlangıç görevi|  
    |`Button2`|`Text`|İptal|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4.  Üzerinde **proje** menüsünde seçin **sınıfı Ekle** adlı bir sınıf eklemek için `Widget.vb` projeye.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Pencere sınıfı için bir olay bildirmek için  
  
-   Kullanım `Event` bir olayı bildirmek için anahtar sözcüğü `Widget` sınıfı. Bir olay olabilir Not `ByVal` ve `ByRef` bağımsız olarak `Widget`'s `PercentDone` olay gösterir:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 Çağrı nesnesi aldığında bir `PercentDone` olay `Percent` tamamlanmış görev yüzdesi bağımsız değişken içeriyor. `Cancel` Bağımsız değişkeni ayarlanabilir `True` olayı başlatan yöntem iptal etmek için.  
  
> [!NOTE]
>  Yordamlar, aşağıdaki istisnalarla birlikte bağımsız olarak olay bağımsız değişkenleri bildirebilirsiniz: Olaylar olamaz `Optional` veya `ParamArray` bağımsız değişkenleri ve olaylar, dönüş değerleri yok.  
  
 `PercentDone` Olayı tarafından oluşturulur `LongTask` yöntemi `Widget` sınıfı. `LongTask` iki bağımsız değişkeni alır: sürenin uzunluğunu yöntemi önce en az zaman aralığını yanı sıra iş çıkarıyor amaçları olan kişilerle tanışabilirsiniz `LongTask` yükseltmek için duraklamaları `PercentDone` olay.  
  
#### <a name="to-raise-the-percentdone-event"></a>PercentDone olayı yükseltmek için  
  
1.  Erişimini basitleştirmek için `Timer` Bu sınıf tarafından kullanılan özellik Ekle bir `Imports` sınıfı modülünüzde bildirimler bölümünü üstüne deyimi yukarıda `Class Widget` deyimi.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2.  Aşağıdaki kodu ekleyin `Widget` sınıfı:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 Uygulamanızı çağırdığında `LongTask` yöntemi `Widget` sınıfı harekete geçirirse `PercentDone` olay her `MinimumInterval` saniye. Olay döndürüldüğünde `LongTask` denetler `Cancel` bağımsız değişken ayarlanmıştır `True`.  
  
 Bazı bildirimler burada gereklidir. Kolaylık olması için `LongTask` yordam varsayar bildiğiniz önceden görevin ne kadar sürer. Neredeyse hiç durum budur. Görevleri bile boyutu öbeklere bölünmesi zor olabilir ve kullanıcılara en sık şeylere yalnızca bir şeyler oluyor göstergesidir aldıkları önce geçen süre miktarıdır.  
  
 Bu örnekte başka bir kusur anlaþýlmaz. `Timer` Özelliği gece yarısından beri geçen saniye sayısını döndürür; bu nedenle, yalnızca gece yarısından önce başlattıysanız uygulama takılı. Sürenin ölçülmesine daha dikkatli bir yaklaşım gibi bu sınır koşulları dikkate alın veya gibi özellikleri kullanarak bunları sorunlarını tamamen önlemek `Now`.  
  
 Şimdi `Widget` sınıf olayları oluşturma, sonraki adım adım kılavuz taşıyabilirsiniz. [İzlenecek yol: Olayları işleme](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) nasıl kullanılacağını gösteren `WithEvents` bir olay işleyicisi ile ilişkilendirilecek `PercentDone` olay.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [İzlenecek yol: Olayları işleme](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)
