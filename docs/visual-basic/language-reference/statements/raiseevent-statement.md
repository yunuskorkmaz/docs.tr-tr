---
title: RaiseEvent deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: ffe08dc8aeef9498d2e9f4c973c5ccbc31fec0b9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973307"
---
# <a name="raiseevent-statement"></a>RaiseEvent Deyimi
Tetikleyiciler bir olay, bir sınıf, form ya da belge içinde Modül düzeyinde bildirilmiş.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>Bölümler  
 `eventname`  
 Gerekli. Tetiklemek için olayın adı.  
  
 `argumentlist`  
 İsteğe bağlı. Değişkenleri, diziler veya ifadelerin virgülle ayrılmış listesi. `argumentlist` Bağımsız değişkeni parantezle alınmalıdır. Hiçbir bağımsız değişken varsa, parantezler atlanmış olabilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Gerekli `eventname` içinde modül olarak bildirilen bir olayın adı. Bu, Visual Basic değişken adlandırma kurallarını izler.  
  
 Olayı ortaya çıkar modülü içinde bildirilmedi, bir hata meydana gelir. Aşağıdaki kod parçası, bir olay bildirimi ve olay harekete geçirilen bir yordam gösterir.  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 Kullanamazsınız `RaiseEvent` modülünde açıkça bildirilmeyen olayları yükseltmek için. Örneğin, tüm form devralma bir <xref:System.Windows.Forms.Control.Click> olaydan <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, kullanarak yükseltilemez `RaiseEvent` türetilmiş bir biçimde. Bildirirseniz bir `Click` olay isteğe bağlı olarak form modülünde formun kendi gölgeleri <xref:System.Windows.Forms.Control.Click> olay. Formun yine de çağırabilirsiniz <xref:System.Windows.Forms.Control.Click> çağırarak olay <xref:System.Windows.Forms.Control.OnClick%2A> yöntemi.  
  
 Varsayılan olarak, kendi olay işleyicileri bağlantı kurulur sırada Visual Basic içinde tanımlanan bir olay başlatır. Olayları olabileceğinden `ByRef` parametreleri, geç bağlanan bir işlem daha önceki bir olay işleyicisi tarafından değiştirilmiş parametreleri alabilirsiniz. Olay işleyicileri yürüttükten sonra olayı tetikleyen alt yordama döndürülür.  
  
> [!NOTE]
>  Olayları paylaşılmayan içinde bildirildikleri sınıf oluşturucusu içinde harekete Geçirilmemesi gereken. Bu tür olayların çalışma zamanı hatalarına neden olmaz ancak ilişkili olay işleyicileri tarafından yakalanması kesin başarısız olabilir. Kullanım `Shared` değiştiricisi bir oluşturucu bir olaydan bulunmanız, paylaşılan bir olay oluşturmak için.  
  
> [!NOTE]
>  Özel olay tanımlayarak olayları'nın varsayılan davranışını değiştirebilirsiniz. Özel olaylar için `RaiseEvent` deyimi çağırır olayın `RaiseEvent` erişimcisi. Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, 0, 10 saniye basılı saymak için olayları kullanır. İlgili olay yöntemleri, özellikleri ve ifadeleri dahil olmak üzere, birkaç kod göstermektedir `RaiseEvent` deyimi.  
  
 Bir olay başlatır sınıf olay kaynağı olan ve olay işleme yöntemleri olay işleyicileridir. Olay kaynağı, oluşturduğu olaylar için birden çok işleyiciler olabilir. Olay sınıfı başlatır, nesnenin Bu örneği için olayları işlemek için katılmamayı her sınıfta bu olay tetiklenir.  
  
 Örnek ayrıca bir form kullanır (`Form1`) bir düğme olan (`Button1`) ve bir metin kutusu (`TextBox1`). Düğmeye tıkladığınızda, 10'dan geri sayım 0 saniyeye ilk metin kutusunu görüntüler. Tam zamanlı (10 saniye) geçtikten sonra "Bitti" ilk metin kutusunu görüntüler.  
  
 Kodu `Form1` formun ilk ve terminal durumunu belirtir. Ayrıca, olaylar oluştuğunda yürütülen kodu içerir.  
  
 Bu örneği kullanmak için yeni bir Windows uygulaması projesi açın, adlı bir düğme ekleyin `Button1` ve adlı bir metin kutusu `TextBox1` ana forma adlı `Form1`. Ardından formun sağ tıklatıp **kodu görüntüle** Kod Düzenleyicisi'ni açın.  
  
 Ekleme bir `WithEvents` değişken bildirimleri bölümüne `Form1` sınıfı.  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kodu için kod ekleyin `Form1`. Oluşabilecek, gibi yinelenen yordamlarla değiştirin `Form_Load`, veya `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Önceki örneği çalıştırmak ve etiketli düğmeye tıklayın için F5 tuşuna basın **Başlat**. İlk metin kutusuna saniye sayısı başlar. Tam zamanlı (10 saniye) geçtikten sonra "Bitti" ilk metin kutusunu görüntüler.  
  
> [!NOTE]
>  `My.Application.DoEvents` Yöntemi form gibi tam olarak aynı şekilde olayları işlemez. Olayları doğrudan işlemeye izin vermek için kullanabileceğiniz çoklu iş parçacığı kullanımı. Daha fazla bilgi için [yönetilen iş parçacığı](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [AddHandler Deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [RemoveHandler Deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [İşleme](../../../visual-basic/language-reference/statements/handles-clause.md)
