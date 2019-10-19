---
title: RaiseEvent ekstresi (Visual Basic)
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
ms.openlocfilehash: efc7da34a297fd01411302b717cfda83aa9f87d2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582103"
---
# <a name="raiseevent-statement"></a>RaiseEvent Deyimi
Sınıf, form veya belge içinde modül düzeyinde belirtilen bir olayı tetikler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>Bölümler  
 `eventname`  
 Gerekli. Tetiklenecek etkinliğin adı.  
  
 `argumentlist`  
 İsteğe bağlı. Değişkenlerin, dizilerin veya ifadelerin virgülle ayrılmış listesi. @No__t_0 bağımsız değişkeni parantez içine alınmalıdır. Bağımsız değişken yoksa, parantezler atlanmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 Gerekli `eventname`, modül içinde belirtilen bir olayın adıdır. Visual Basic değişken adlandırma kuralları ' nı izler.  
  
 Olayın oluşturulduğu modül içinde bildirilmemiş bir hata oluşur. Aşağıdaki kod parçası bir olay bildirimini ve olayın oluşturulduğu yordamı gösterir.  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 Modülde açıkça bildirilmeyen olayları yükseltmek için `RaiseEvent` kullanamazsınız. Örneğin, tüm formlar <xref:System.Windows.Forms.Form?displayProperty=nameWithType> <xref:System.Windows.Forms.Control.Click> bir olayı miras alarak, türetilmiş bir formda `RaiseEvent` kullanılarak gerçekleştirilemez. Form modülünde bir `Click` olayı bildirirseniz, formun kendi <xref:System.Windows.Forms.Control.Click> olayını gölgeler. Yine de, <xref:System.Windows.Forms.Control.OnClick%2A> yöntemini çağırarak formun <xref:System.Windows.Forms.Control.Click> olayını çağırabilirsiniz.  
  
 Varsayılan olarak, Visual Basic tanımlı bir olay, olay işleyicilerini bağlantıların kurulduğu sırada başlatır. Olaylar `ByRef` parametrelere sahip olabileceğinden, geç bağlanan bir işlem önceki bir olay işleyicisi tarafından değiştirilmiş parametreler alabilir. Olay işleyicileri çalıştırıldıktan sonra, olayı oluşturan alt yordama denetim döndürülür.  
  
> [!NOTE]
> Paylaşılmayan olaylar, bildirildiği sınıfın Oluşturucusu içinde çıkarılmamalıdır. Bu tür olaylar çalışma zamanı hatalarına neden olmasa da, ilişkili olay işleyicileri tarafından yakalanmayabilir. Bir oluşturucudan bir olay oluşturmanız gerekiyorsa, paylaşılan bir olay oluşturmak için `Shared` değiştiricisini kullanın.  
  
> [!NOTE]
> Özel bir olay tanımlayarak olayların varsayılan davranışını değiştirebilirsiniz. Özel olaylar için `RaiseEvent` ifade, olayın `RaiseEvent` erişimcisini çağırır. Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, 10 ile 0 arasındaki saniye sayısını saymak için olayları kullanır. Kod, `RaiseEvent` deyimi de dahil olmak üzere olayla ilgili yöntemlerin, özelliklerin ve deyimlerden birkaçını gösterir.  
  
 Olayı oluşturan sınıf olay kaynağıdır ve olayı işleyen yöntemler olay işleyicileridir. Bir olay kaynağı, oluşturduğu olaylar için birden çok işleyicilere sahip olabilir. Sınıf olayı harekete geçirirse, bu olay nesnenin bu örneğine yönelik olayları işlemek için seçilmiş olan her sınıfta oluşturulur.  
  
 Örnek ayrıca bir düğme (`Button1`) ve metin kutusu (`TextBox1`) içeren bir form (`Form1`) kullanır. Düğmeye tıkladığınızda, ilk metin kutusu 10 ila 0 saniye arasında bir geri sayım görüntüler. Tam süre (10 saniye) geçtiğinde, ilk metin kutusunda "bitti" görüntülenir.  
  
 @No__t_0 kodu, formun başlangıç ve Terminal durumlarını belirtir. Ayrıca, olaylar oluşturulduğunda yürütülen kodu içerir.  
  
 Bu örneği kullanmak için, yeni bir Windows uygulaması projesi açın, `Button1` adlı bir düğme ve `TextBox1` adlı ana forma `Form1` adlı bir metin kutusu ekleyin. Daha sonra forma sağ tıklayın ve kodu **görüntüle** ' ye tıklayarak kod düzenleyicisini açın.  
  
 @No__t_1 sınıfının bildirimler bölümüne `WithEvents` değişken ekleyin.  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a>Örnek  
 @No__t_0 koda aşağıdaki kodu ekleyin. @No__t_0 veya `Button_Click` gibi, mevcut olabilecek yinelenen yordamları değiştirin.  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Yukarıdaki örneği çalıştırmak için F5 tuşuna basın ve **Başlat**etiketli düğmeye tıklayın. İlk metin kutusu, saniyeyi saymaya başlar. Tam süre (10 saniye) geçtiğinde, ilk metin kutusunda "bitti" görüntülenir.  
  
> [!NOTE]
> @No__t_0 yöntemi, olayları yalnızca formla aynı şekilde işlemez. Formun olayları doğrudan işlemesine izin vermek için çoklu iş parçacığı kullanımı ' nı kullanabilirsiniz. Daha fazla bilgi için bkz. [yönetilen Iş parçacığı](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [AddHandler Deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [RemoveHandler Deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [İşlendiğini](../../../visual-basic/language-reference/statements/handles-clause.md)
