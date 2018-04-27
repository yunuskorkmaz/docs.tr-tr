---
title: Olay (Visual Basic) bildirme ve oluşturma
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 27db585084703607a7389f5a0aa3eba6f70dd793
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a>İzlenecek yol: Olay Bildirme ve Oluşturma (Visual Basic)
Bu kılavuz, bildirme ve olayları adlı bir sınıf için yükseltmek gösterilmiştir `Widget`. Adımları tamamladıktan sonra Yardımcısı konuyu okumak isteyebilirsiniz [izlenecek yol: olayları işleme](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), olayları kullanmayı gösterir `Widget` bir uygulamada durum bilgilerini sağlamak için nesneleri.  
  
## <a name="the-widget-class"></a>Pencere sınıfı  
 Sahip olduğunuz şu anda varsayın bir `Widget` sınıfı. `Widget` Tamamlama göstergesi çeşit yerleştirmek, uygulamanızın istediğiniz ve sınıfı yürütmek için uzun zaman alabilir bir yöntem vardır.  
  
 Elbette, yapabilir `Widget` nesne tamamlanma yüzdesi iletişim kutusunu göster, ancak daha sonra bu iletişim kutusu, kullandığınız her projede takılmış `Widget` sınıfı. Bir nesne tanıtıcısının kullanıcı arabirimi kullanan uygulama izin vermek için nesne tasarımı iyi ilkesi olan — bir form veya iletişim kutusu yönetmek için tüm nesne amacı olmadığı sürece.  
  
 Amacı `Widget` eklemek daha iyi şekilde diğer görevleri gerçekleştirmek için bir `PercentDone` olay ve let çağıran yordamı `Widget`kullanıcının yöntemlerini işlemek olay ve görüntü durumunu güncelleştirir. `PercentDone` Olay ayrıca görev iptal etmek için bir mekanizma sağlar.  
  
#### <a name="to-build-the-code-example-for-this-topic"></a>Bu konu için kod örneği oluşturmak için  
  
1.  Yeni bir Visual Basic Windows uygulama projesi açın ve adlı bir form oluşturun `Form1`.  
  
2.  İki düğme ve bir etiket eklemek `Form1`.  
  
3.  Aşağıdaki tabloda gösterildiği gibi nesneleri adlandırın.  
  
    |Nesne|Özellik|Ayar|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|Başlangıç görevi|  
    |`Button2`|`Text`|İptal|  
    |`Label`|`(Name)`, `Text`|lblPercentDone, 0|  
  
4.  Üzerinde **proje** menüsünde seçin **sınıfı Ekle** adlı bir sınıf eklemek için `Widget.vb` projeye.  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a>Pencere sınıfı için bir olay bildirmek için  
  
-   Kullanım `Event` olayda bildirmek için anahtar sözcüğü `Widget` sınıfı. Bir olay olabilir Not `ByVal` ve `ByRef` bağımsız değişken olarak `Widget`'s `PercentDone` olay gösterir:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_1.vb)]  
  
 Ne zaman çağıran nesne alır bir `PercentDone` olayı `Percent` bağımsız değişkeni tamamlandıktan görev yüzdesini içerir. `Cancel` Bağımsız değişkeni ayarlanabilir `True` olayı yöntemi iptal etmek için.  
  
> [!NOTE]
>  Yordamlar, aşağıdaki istisnalar dışında bağımsız gibi olay bağımsız bildirebilir: olayları olamaz `Optional` veya `ParamArray` bağımsız değişkenleri ve olaylar, dönüş değerleri gerekmez.  
  
 `PercentDone` Olayı tarafından `LongTask` yöntemi `Widget` sınıfı. `LongTask` iki bağımsız değişkeni alır: süre yöntemi çalışma ve önce en az zaman aralığını yaparak amaçları olan kişilerle tanışabilirsiniz `LongTask` yükseltmek için duraklatır `PercentDone` olay.  
  
#### <a name="to-raise-the-percentdone-event"></a>PercentDone olay yükseltmek için  
  
1.  Erişimi kolaylaştırmak için `Timer` Bu sınıf tarafından kullanılan özellik ekleme bir `Imports` sınıfı modülünüzün bildirimler bölümünün üst ifadesine yukarıda `Class Widget` deyimi.  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_2.vb)]  
  
2.  Aşağıdaki kodu ekleyin `Widget` sınıfı:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-declaring-and-raising-events_3.vb)]  
  
 Uygulamanızı çağırdığında `LongTask` yöntemi, `Widget` sınıfı başlatır `PercentDone` olay her `MinimumInterval` saniye. Olay geri döndüğünde, `LongTask` denetler `Cancel` bağımsız değişkeni ayarlandığı `True`.  
  
 Bazı bildirimler burada gereklidir. Basitleştirmek için `LongTask` yordam varsayar bildiğiniz önceden görevin ne kadar sürer. Bu neredeyse hiçbir zaman bir durumdur. Görevler bile boyutu parçalara bölmek zor olabilir ve genellikle de en önemli ne kullanıcılara yalnızca bir şey olmuyor göstergesidir elde önce geçen zamanı miktarıdır.  
  
 Bu örnekte başka bir kusur anlaþýlmaz. `Timer` Özelliği gece yarısından beri geçen saniye sayısını döndürür; bu nedenle, yalnızca gece yarısından önce başlattıysanız uygulama takılmış. Sürenin ölçülmesine daha dikkatli bir yaklaşım gibi bu sınır koşulları dikkate alın veya bunları tamamen özellikler gibi kullanmaktan kaçının `Now`.  
  
 Şimdi `Widget` sınıf olayları oluşturma, sonraki izlenecek taşıyabilirsiniz. [İzlenecek yol: Olaylarını işleme](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) nasıl kullanılacağı ortaya `WithEvents` olay işleyicisi ile ilişkilendirilecek `PercentDone` olay.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>  
 <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>  
 [İzlenecek yol: Olayları İşleme](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)  
 [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)
