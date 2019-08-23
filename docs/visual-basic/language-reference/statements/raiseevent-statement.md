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
ms.openlocfilehash: ee52b4adf893ea0926c4016fcb6a89d0010ee6ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957775"
---
# <a name="raiseevent-statement"></a>RaiseEvent Deyimi
Sınıf, form veya belge içinde modül düzeyinde belirtilen bir olayı tetikler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>Bölümler  
 `eventname`  
 Gerekli. Tetiklenecek etkinliğin adı.  
  
 `argumentlist`  
 İsteğe bağlı. Değişkenlerin, dizilerin veya ifadelerin virgülle ayrılmış listesi. `argumentlist` Bağımsız değişkenin parantez içine alınması gerekir. Bağımsız değişken yoksa, parantezler atlanmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 Gerekli `eventname` , modül içinde belirtilen bir olayın adıdır. Visual Basic değişken adlandırma kuralları ' nı izler.  
  
 Olayın oluşturulduğu modül içinde bildirilmemiş bir hata oluşur. Aşağıdaki kod parçası bir olay bildirimini ve olayın oluşturulduğu yordamı gösterir.  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 Modülde açıkça bildirilmeyen olayları yükseltmek içinkullanamazsınız.`RaiseEvent` Örneğin, tüm formlar öğesinden <xref:System.Windows.Forms.Control.Click> <xref:System.Windows.Forms.Form?displayProperty=nameWithType>bir olay devraldığı için, türetilmiş bir formda kullanılarak `RaiseEvent` gerçekleştirilemez. Form modülünde bir `Click` olay bildirirseniz, formun kendi <xref:System.Windows.Forms.Control.Click> olayını gölgeler. Yöntemini çağırarak formun <xref:System.Windows.Forms.Control.Click> olayını yine de çağırabilirsiniz. <xref:System.Windows.Forms.Control.OnClick%2A>  
  
 Varsayılan olarak, Visual Basic tanımlı bir olay, olay işleyicilerini bağlantıların kurulduğu sırada başlatır. Olayların `ByRef` parametreleri olabileceğinden, geç bağlanan bir işlem önceki bir olay işleyicisi tarafından değiştirilmiş parametreler alabilir. Olay işleyicileri çalıştırıldıktan sonra, olayı oluşturan alt yordama denetim döndürülür.  
  
> [!NOTE]
> Paylaşılmayan olaylar, bildirildiği sınıfın Oluşturucusu içinde çıkarılmamalıdır. Bu tür olaylar çalışma zamanı hatalarına neden olmasa da, ilişkili olay işleyicileri tarafından yakalanmayabilir. Bir oluşturucudan bir olay oluşturmanız gerekiyorsa paylaşılan bir olay oluşturmak için değiştiricisinikullanın.`Shared`  
  
> [!NOTE]
> Özel bir olay tanımlayarak olayların varsayılan davranışını değiştirebilirsiniz. Özel olaylar için, `RaiseEvent` ifade `RaiseEvent` olayın erişimcisini çağırır. Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, 10 ile 0 arasındaki saniye sayısını saymak için olayları kullanır. Kod, `RaiseEvent` deyimi dahil olmak üzere olayla ilgili yöntemlerin, özelliklerin ve deyimlerden birkaçını gösterir.  
  
 Olayı oluşturan sınıf olay kaynağıdır ve olayı işleyen yöntemler olay işleyicileridir. Bir olay kaynağı, oluşturduğu olaylar için birden çok işleyicilere sahip olabilir. Sınıf olayı harekete geçirirse, bu olay nesnenin bu örneğine yönelik olayları işlemek için seçilmiş olan her sınıfta oluşturulur.  
  
 Örnek ayrıca bir düğme (`Form1``Button1`) ve metin kutusu (`TextBox1`) içeren bir form () kullanır. Düğmeye tıkladığınızda, ilk metin kutusu 10 ila 0 saniye arasında bir geri sayım görüntüler. Tam süre (10 saniye) geçtiğinde, ilk metin kutusunda "bitti" görüntülenir.  
  
 Kodu, formun `Form1` ilk ve Terminal durumlarını belirtir. Ayrıca, olaylar oluşturulduğunda yürütülen kodu içerir.  
  
 Bu örneği kullanmak için yeni bir Windows uygulaması projesi açın, adlı bir düğme `Button1` ve adlı ana forma `Form1`adlı bir metin `TextBox1` kutusu ekleyin. Daha sonra forma sağ tıklayın ve kodu **görüntüle** ' ye tıklayarak kod düzenleyicisini açın.  
  
 `Form1` Sınıfının bildirimler `WithEvents` bölümüne bir değişken ekleyin.  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a>Örnek  
 Koduna aşağıdaki kodu ekleyin `Form1`. `Form_Load` Veya`Button_Click`gibi mevcut olabilecek yinelenen yordamları değiştirin.  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 Yukarıdaki örneği çalıştırmak için F5 tuşuna basın ve **Başlat**etiketli düğmeye tıklayın. İlk metin kutusu, saniyeyi saymaya başlar. Tam süre (10 saniye) geçtiğinde, ilk metin kutusunda "bitti" görüntülenir.  
  
> [!NOTE]
> `My.Application.DoEvents` Yöntemi, olayları yalnızca formla aynı şekilde işlemez. Formun olayları doğrudan işlemesine izin vermek için çoklu iş parçacığı kullanımı ' nı kullanabilirsiniz. Daha fazla bilgi için bkz. [yönetilen Iş parçacığı](../../../standard/threading/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [AddHandler Deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [RemoveHandler Deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [İşlendiğini](../../../visual-basic/language-reference/statements/handles-clause.md)
