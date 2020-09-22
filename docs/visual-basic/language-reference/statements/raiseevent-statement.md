---
title: RaiseEvent Deyimi
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
ms.openlocfilehash: 13d86aad8b68391f7effe2f6637adc68d8a3b59a
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872011"
---
# <a name="raiseevent-statement"></a>RaiseEvent Deyimi

Sınıf, form veya belge içinde modül düzeyinde belirtilen bir olayı tetikler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>Bölümler  

 `eventname`  
 Gereklidir. Tetiklenecek etkinliğin adı.  
  
 `argumentlist`  
 İsteğe bağlı. Değişkenlerin, dizilerin veya ifadelerin virgülle ayrılmış listesi. `argumentlist`Bağımsız değişkenin parantez içine alınması gerekir. Bağımsız değişken yoksa, parantezler atlanmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  

 Gerekli, `eventname` modül içinde belirtilen bir olayın adıdır. Visual Basic değişken adlandırma kuralları ' nı izler.  
  
 Olayın oluşturulduğu modül içinde bildirilmemiş bir hata oluşur. Aşağıdaki kod parçası bir olay bildirimini ve olayın oluşturulduğu yordamı gösterir.  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 `RaiseEvent`Modülde açıkça bildirilmeyen olayları yükseltmek için kullanamazsınız. Örneğin, tüm formlar <xref:System.Windows.Forms.Control.Click> öğesinden bir olay devraldığı için <xref:System.Windows.Forms.Form?displayProperty=nameWithType> , `RaiseEvent` türetilmiş bir formda kullanılarak gerçekleştirilemez. `Click`Form modülünde bir olay bildirirseniz, formun kendi <xref:System.Windows.Forms.Control.Click> olayını gölgeler. Yöntemini çağırarak formun olayını yine de çağırabilirsiniz <xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.Control.OnClick%2A> .  
  
 Varsayılan olarak, Visual Basic tanımlı bir olay, olay işleyicilerini bağlantıların kurulduğu sırada başlatır. Olayların `ByRef` parametreleri olabileceğinden, geç bağlanan bir işlem önceki bir olay işleyicisi tarafından değiştirilmiş parametreler alabilir. Olay işleyicileri çalıştırıldıktan sonra, olayı oluşturan alt yordama denetim döndürülür.  
  
> [!NOTE]
> Paylaşılmayan olaylar, bildirildiği sınıfın Oluşturucusu içinde çıkarılmamalıdır. Bu tür olaylar çalışma zamanı hatalarına neden olmasa da, ilişkili olay işleyicileri tarafından yakalanmayabilir. `Shared`Bir oluşturucudan bir olay oluşturmanız gerekiyorsa paylaşılan bir olay oluşturmak için değiştiricisini kullanın.  
  
> [!NOTE]
> Özel bir olay tanımlayarak olayların varsayılan davranışını değiştirebilirsiniz. Özel olaylar için, `RaiseEvent` ifade olayın `RaiseEvent` erişimcisini çağırır. Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](event-statement.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, 10 ile 0 arasındaki saniye sayısını saymak için olayları kullanır. Kod, deyimi dahil olmak üzere olayla ilgili yöntemlerin, özelliklerin ve deyimlerden birkaçını gösterir `RaiseEvent` .  
  
 Olayı oluşturan sınıf olay kaynağıdır ve olayı işleyen yöntemler olay işleyicileridir. Bir olay kaynağı, oluşturduğu olaylar için birden çok işleyicilere sahip olabilir. Sınıf olayı harekete geçirirse, bu olay nesnenin bu örneğine yönelik olayları işlemek için seçilmiş olan her sınıfta oluşturulur.  
  
 Örnek ayrıca bir `Form1` düğme ( `Button1` ) ve metin kutusu () içeren bir form () kullanır `TextBox1` . Düğmeye tıkladığınızda, ilk metin kutusu 10 ila 0 saniye arasında bir geri sayım görüntüler. Tam süre (10 saniye) geçtiğinde, ilk metin kutusunda "bitti" görüntülenir.  
  
 Kodu, `Form1` formun ilk ve Terminal durumlarını belirtir. Ayrıca, olaylar oluşturulduğunda yürütülen kodu içerir.  
  
 Bu örneği kullanmak için yeni bir Windows uygulaması projesi açın, adlı bir düğme ve adlı `Button1` ana forma adlı bir metin kutusu ekleyin `TextBox1` `Form1` . Daha sonra forma sağ tıklayın ve kodu **görüntüle** ' ye tıklayarak kod düzenleyicisini açın.  
  
 `WithEvents`Sınıfının bildirimler bölümüne bir değişken ekleyin `Form1` .  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a>Örnek  

 Koduna aşağıdaki kodu ekleyin `Form1` . Veya gibi mevcut olabilecek yinelenen yordamları değiştirin `Form_Load` `Button_Click` .  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Yukarıdaki örneği çalıştırmak için F5 tuşuna basın ve **Başlat**etiketli düğmeye tıklayın. İlk metin kutusu, saniyeyi saymaya başlar. Tam süre (10 saniye) geçtiğinde, ilk metin kutusunda "bitti" görüntülenir.  
  
> [!NOTE]
> `My.Application.DoEvents`Yöntemi, olayları yalnızca formla aynı şekilde işlemez. Formun olayları doğrudan işlemesine izin vermek için çoklu iş parçacığı kullanımı ' nı kullanabilirsiniz. Daha fazla bilgi için bkz. [yönetilen Iş parçacığı](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ekinlikler](../../programming-guide/language-features/events/index.md)
- [Event Deyimi](event-statement.md)
- [AddHandler Deyimi](addhandler-statement.md)
- [RemoveHandler Deyimi](removehandler-statement.md)
- [Handles](handles-clause.md)
