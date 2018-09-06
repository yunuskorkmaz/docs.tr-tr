---
title: 'Nasıl yapılır: Kodda Fare ve Klavye Olaylarının Benzetimini Yapma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboards [Windows Forms], event simulation
- user input [Windows Forms], simulating
- SendKeys [Windows Forms], using
- mouse clicks [Windows Forms], simulating
- mouse [Windows Forms], event simulation
ms.assetid: 6abcb67e-3766-4af2-9590-bf5dabd17e41
ms.openlocfilehash: 56c7d534d5428ff116c6de1aeffd9a31bd7a5063
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43798119"
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a>Nasıl yapılır: Kodda Fare ve Klavye Olaylarının Benzetimini Yapma
Windows Forms programlama yoluyla fare ve klavye girdisi benzetimi için çeşitli seçenekler sunar. Bu konu, bu seçeneklerine genel bakış sağlar.  
  
## <a name="simulating-mouse-input"></a>Fare girişi benzetimi  
 Fare olayları benzetimini yapmak için en iyi yolu `On` *EventName* benzetimini yapmak istediğiniz fare olayını yöntemi. Olay yöntemleri korunur ve denetim veya form dışında erişilemez olduğundan bu seçenek yalnızca özel denetimler ve formları içinde genellikle mümkündür. Örneğin, aşağıdaki adımlar, kod sağ fare düğmesine tıklayarak benzetimini yapma göstermektedir.  
  
#### <a name="to-programmatically-click-the-right-mouse-button"></a>Program aracılığıyla sağ fare düğmesini tıklatın  
  
1.  Oluşturma bir <xref:System.Windows.Forms.MouseEventArgs> olan <xref:System.Windows.Forms.MouseEventArgs.Button%2A> özelliği <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> değeri.  
  
2.  Çağrı <xref:System.Windows.Forms.Control.OnMouseClick%2A> bu yöntemle <xref:System.Windows.Forms.MouseEventArgs> bağımsız değişken olarak.  
  
 Özel denetimler hakkında daha fazla bilgi için bkz. [tasarım zamanında Windows Forms denetimleri geliştirme](../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).  
  
 Fare girişi benzetimini yapmanın başka yolları da vardır. Örneğin, program aracılığıyla genellikle fare girdisi ayarlanan bir durumu temsil eden denetim özelliğini ayarlayabilirsiniz (gibi <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği <xref:System.Windows.Forms.CheckBox> denetimi), veya olaya bağlı temsilcinin doğrudan çağırabilir, benzetimini yapmak istediğiniz.  
  
## <a name="simulating-keyboard-input"></a>Klavye girişini benzetimi  
 Yukarıda Windows Forms ayrıca sağlar fare girişi için açıklanan stratejileri kullanarak klavye giriş benzetimini yapabilirsiniz ancak <xref:System.Windows.Forms.SendKeys> etkin uygulamaya tuş vuruşları göndermek için sınıf.  
  
> [!CAUTION]
>  Uygulamanızın kullanımını klavye çeşitli Uluslararası kullanıma yöneliktir, <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> tahmin edilmeyen sonuçlara neden ve kaçınılmalıdır.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.SendKeys> Sınıfı, Windows Vista üzerinde çalıştırılan uygulamalardaki kullanımını etkinleştirmek .NET Framework 3.0 için güncelleştirilmiştir. Windows Vista'nın (kullanıcı hesabı denetimi veya UAC olarak bilinir) Artırılmış güvenlik, beklendiği gibi önceki uygulama çalışmasını engeller.  
>   
>  <xref:System.Windows.Forms.SendKeys> Sınıfı, bazı geliştiriciler, geçici olarak çözmek için çalıştırılmış zamanlama sorunları, maruz kalabilir. Güncelleştirilmiş uygulama zamanlama sorunları için saldırılara açıktır, ancak biraz daha hızlıdır ve geçici çözümler değişiklikler gerektirebilir. <xref:System.Windows.Forms.SendKeys> Sınıfı önceki uygulaması kullanmayı dener ve bu başarısız olursa yeni uygulamayı kullanır. Sonuç olarak, <xref:System.Windows.Forms.SendKeys> sınıfı davranır farklı farklı işletim sistemlerinde. Ayrıca, <xref:System.Windows.Forms.SendKeys> sınıfını kullanan yeni bir uygulama <xref:System.Windows.Forms.SendKeys.SendWait%2A> yöntemi başka bir işleme gönderildiğinde işlenecek iletiler için değil bekleyecek.  
>   
>  Uygulamanızı işletim sisteminden bağımsız olarak tutarlı davranışına dayanıyorsa zorlayabilirsiniz <xref:System.Windows.Forms.SendKeys> app.config dosyanıza aşağıdaki uygulama ayarı ekleyerek yeni uygulamayı kullanmak için sınıf.  
>   
>  `<appSettings>`  
>   
>  `<add key="SendKeys" value="SendInput"/>`  
>   
>  `</appSettings>`  
>   
>  Zorlamak için <xref:System.Windows.Forms.SendKeys> önceki uygulamasını kullanın, değer sınıfı `"JournalHook"` yerine.  
  
#### <a name="to-send-a-keystroke-to-the-same-application"></a>Aynı uygulamanın bir tuş vuruşu göndermek için  
  
1.  Çağrı <xref:System.Windows.Forms.SendKeys.Send%2A> veya <xref:System.Windows.Forms.SendKeys.SendWait%2A> yöntemi <xref:System.Windows.Forms.SendKeys> sınıfı. Belirtilen tuş vuruşları uygulamanın etkin denetim alınır. Aşağıdaki kod örneğinde <xref:System.Windows.Forms.SendKeys.Send%2A> form yüzeyi kullanıcı çift tıkladığında ENTER tuşuna basarak benzetimi yapmak için. Bu örnekte bir <xref:System.Windows.Forms.Form> tek bir <xref:System.Windows.Forms.Button> bir sekme dizini 0 olan denetim.  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]  
  
#### <a name="to-send-a-keystroke-to-a-different-application"></a>Farklı bir uygulamaya tuş vuruşu göndermek için  
  
1.  Tuş vuruşları almak ve sonra çağrı uygulama penceresini etkinleştir <xref:System.Windows.Forms.SendKeys.Send%2A> veya <xref:System.Windows.Forms.SendKeys.SendWait%2A> yöntemi. Başka bir uygulamayı etkinleştirmek için Yönetilen yöntem olduğundan, diğer uygulamaları odak zorlamak için yerel Windows yöntemlerini kullanmanız gerekir. Aşağıdaki kod örneği kullanan platform çağırma çağrılacak `FindWindow` ve `SetForegroundWindow` hesaplayıcı uygulama penceresi ve ardından aramaları etkinleştirmek için yöntemleri <xref:System.Windows.Forms.SendKeys.SendWait%2A> hesaplayıcısı uygulaması için bir dizi hesaplamalar verecek.  
  
    > [!NOTE]
    >  Doğru parametreleri `FindWindow` hesaplayıcısı uygulaması bulur çağrı Windows sürümünüz göre değişir.  Aşağıdaki kod üzerinde hesaplayıcısı uygulaması bulur [!INCLUDE[win7](../../../includes/win7-md.md)]. Üzerinde [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], "SciCalc" için ilk parametre değiştirin. Visual Studio'ya dahil edildi Spy ++ araç, doğru parametreleri belirlemek için kullanabilirsiniz.  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, önceki kod örnekleri için tam uygulamasıdır.  
  
 [!code-cpp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  Ayrıca bkz: [nasıl yapılır: derleme ve çalıştırma bir tam Windows Formları kod örneği kullanarak Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'ta Kullanıcı Girdisi](../../../docs/framework/winforms/user-input-in-windows-forms.md)
