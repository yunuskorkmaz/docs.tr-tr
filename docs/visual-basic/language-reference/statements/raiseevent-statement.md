---
title: RaiseEvent Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2575598577820bd7a72fae2d9b8ba52978f5952d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="raiseevent-statement"></a>RaiseEvent Deyimi
Tetikleyiciler bir olay sınıfı, form veya belge içinde modülü düzeyinde bildirildi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>Bölümler  
 `eventname`  
 Gerekli. Tetiklemek için olayın adı.  
  
 `argumentlist`  
 İsteğe bağlı. Virgülle ayrılmış listesi değişkenleri, dizileri veya ifade. `argumentlist` Bağımsız değişkeni tarafından parantez içine gerekir. Bağımsız değişkenler varsa, parantez atlanmış gerekir.  
  
## <a name="remarks"></a>Açıklamalar  
 Gerekli `eventname` bir olayın adı modülü içinde bildirilir. Visual Basic değişken adlandırma kuralları izler.  
  
 Olay ortaya çıkar modül içinde bildirilen değil, bir hata oluşur. Aşağıdaki kod parçası, bir olay bildirimi ve olay yükseltildiği bir yordam gösterilmektedir.  
  
 [!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]  
  
 Kullanamazsınız `RaiseEvent` modülünde açıkça bildirilmemiş olayları yükseltmek için. Örneğin, tüm form devralma bir <xref:System.Windows.Forms.Control.Click> olayından <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, kullanarak yükseltilemez `RaiseEvent` türetilmiş bir biçimde. Bildirirseniz bir `Click` olay isteğe bağlı olarak form modülünde formun kendi shadows <xref:System.Windows.Forms.Control.Click> olay. Formun hala çağırabileceği <xref:System.Windows.Forms.Control.Click> çağırarak olay <xref:System.Windows.Forms.Control.OnClick%2A> yöntemi.  
  
 Varsayılan olarak, kendi olay işleyicileri bağlantıları kurulduğundan emin sırayla Visual Basic'te tanımlı bir olay başlatır. Olayları olabileceğinden `ByRef` parametreleri geç bağlanan bir işlem önceki olay işleyici tarafından değiştirilmiş parametreleri alabilirsiniz. Olay işleyicileri yürüttükten sonra denetim olayı alt yordama döndürülür.  
  
> [!NOTE]
>  Olayları paylaşılmayan bildirilen sınıf oluşturucu içinde oluşmalıdır değil. Bu gibi olaylar çalışma zamanı hataları neden olmaz ancak ilişkili olay işleyicileri tarafından yakalanan başarısız olabilir. Kullanım `Shared` bir olayı bir oluşturucusundan gerekiyorsa, paylaşılan bir olay oluşturmak için değiştiricisi.  
  
> [!NOTE]
>  Özel bir olay tanımlayarak olayları varsayılan davranışını değiştirebilirsiniz. Özel olaylar için `RaiseEvent` deyimi çağırır olayın `RaiseEvent` erişimcisi. Özel olaylar hakkında daha fazla bilgi için bkz: [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, 10 saniyeden 0 aşağı saymak için olayları kullanır. Kod olayla ilgili yöntemler, özellikler ve ifadeleri de dahil olmak üzere, çeşitli gösterir `RaiseEvent` deyimi.  
  
 Olay kaynağı bir olay başlatır sınıf olduğunu ve olay işleme yöntemleri olay işleyicileri. Bir olay kaynağı ürettiği olaylar için birden çok işleyicileri olabilir. Olay sınıfı başlatır, bu olay nesnesinin bu örneği için olayları işlemek için katılmamayı her bir sınıf üzerinde tetiklenir.  
  
 Bu örnek ayrıca bir form kullanır (`Form1`) bir düğme ile (`Button1`) ve bir metin kutusu (`TextBox1`). Düğmeye tıkladığınızda, ilk metin kutusunu 0 saniye 10 geri sayım görüntüler. Tam zamanlı (10 saniye) geçtiğinde "Tamamlandı" ilk metin kutusunu görüntüler.  
  
 Kodunu `Form1` formun ilk ve terminal durumunu belirtir. Ayrıca, olayları ortaya çıktığında yürütülen kodu içerir.  
  
 Bu örneği kullanmak için yeni bir Windows uygulama projesi açın, adlı bir düğme ekleme `Button1` ve adlı bir metin kutusu `TextBox1` ana forma adlı `Form1`. Ardından formu sağ tıklatın ve **görünümü kodu** Kod Düzenleyicisi'ni açın.  
  
 Ekleme bir `WithEvents` değişken bildirimleri bölümüne `Form1` sınıfı.  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kodu için kod ekleme `Form1`. Aşağıdaki gibi bulunabilecek yinelenen yordamlarla Değiştir `Form_Load`, veya `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]  
  
 Önceki örnekte çalıştırın ve etiketli düğmesini tıklatın için F5 tuşuna basın **Başlat**. Saniye sayısı ilk metin kutusunu başlatır. Tam zamanlı (10 saniye) geçtiğinde "Tamamlandı" ilk metin kutusunu görüntüler.  
  
> [!NOTE]
>  `My.Application.DoEvents` Yöntemi form yaptığı gibi tam olarak aynı şekilde olayları işlemez. Formun olayları doğrudan işlemek izin vermek için kullanabileceğiniz çoklu iş parçacığı kullanımı. Daha fazla bilgi için bkz: [parçacıkları](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olayları](../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
 [AddHandler deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [RemoveHandler deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [İşleme](../../../visual-basic/language-reference/statements/handles-clause.md)
