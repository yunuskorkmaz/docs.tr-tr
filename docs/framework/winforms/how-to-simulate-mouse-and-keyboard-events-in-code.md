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
ms.openlocfilehash: cdb37fe549ebfbcdb5a0c5b6008a1922fdbf471b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a>Nasıl yapılır: Kodda Fare ve Klavye Olaylarının Benzetimini Yapma
Windows Forms program aracılığıyla fare ve klavye girdisi benzetimi için çeşitli seçenekler sağlar. Bu konu, bu seçenekleri genel bir bakış sağlar.  
  
## <a name="simulating-mouse-input"></a>Fare girişi benzetimini yapma  
 Fare olayları benzetimini yapmak için en iyi yolu çağırmaktır `On` *EventName* benzetimini yapmak istediğiniz fare olayını yöntemi. Olaylarını yöntemleri korunur ve denetim veya formun dışında erişilemez olduğundan bu seçenek yalnızca özel denetimler ve formları içinde genellikle mümkündür. Örneğin, aşağıdaki adımları kodda sağ fare düğmesini tıklatarak benzetimini yapma gösterir.  
  
#### <a name="to-programmatically-click-the-right-mouse-button"></a>Program aracılığıyla farenin sağ düğmesiyle tıklatın  
  
1.  Oluşturma bir <xref:System.Windows.Forms.MouseEventArgs> , <xref:System.Windows.Forms.MouseEventArgs.Button%2A> özelliği ayarlanmış <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> değeri.  
  
2.  Çağrı <xref:System.Windows.Forms.Control.OnMouseClick%2A> bu yöntemle <xref:System.Windows.Forms.MouseEventArgs> bağımsız değişkeni olarak.  
  
 Özel denetimler hakkında daha fazla bilgi için bkz: [tasarım zamanında Windows Forms denetimleri geliştirme](../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md).  
  
 Fare girişi benzetimini yapmak için başka yolları vardır. Örneğin, program aracılığıyla genellikle fare girdisi ayarlanır durumunu temsil eden bir denetim özelliğini ayarlayabilirsiniz (gibi <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği <xref:System.Windows.Forms.CheckBox> denetimi), ya da olaya bağlı temsilci doğrudan çağırabilir miyim, benzetimini yapmak istediğiniz.  
  
## <a name="simulating-keyboard-input"></a>Klavye girişi benzetimini yapma  
 Yukarıda Windows Forms de sağlar fare girdisi için açıklanan stratejileri kullanarak klavye girişi benzetimini yapabilirsiniz ancak <xref:System.Windows.Forms.SendKeys> etkin uygulamaya tuş vuruşları göndermek için sınıf.  
  
> [!CAUTION]
>  Uygulamanızı klavyeler, kullanımını çeşitli uluslararası kullanmaya yönelik varsa <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> beklenmeyen sonuçlar ve kaçınılmalıdır.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.SendKeys> Sınıfı, Windows Vista üzerinde çalışan uygulamaları kullanımını etkinleştirmek .NET Framework 3.0 için güncelleştirilmiştir. Windows Vista'nın (kullanıcı hesabı denetimi veya UAC da bilinir) Artırılmış güvenlik, beklendiği gibi çalışmasını önceki uygulaması engeller.  
>   
>  <xref:System.Windows.Forms.SendKeys> Sınıfı, bazı geliştiriciler çözmek zorunda zamanlama sorunları için açıktır. Güncelleştirilmiş uygulama zamanlama sorunları için hala açıktır, ancak biraz daha hızlıdır ve geçici çözümler değişiklikler gerektirebilir. <xref:System.Windows.Forms.SendKeys> Sınıfı önceki uygulaması kullanmayı dener ve başarısız olursa, yeni uygulama kullanır. Sonuç olarak, <xref:System.Windows.Forms.SendKeys> sınıfı davranır farklı farklı işletim sistemleri üzerinde. Ayrıca, <xref:System.Windows.Forms.SendKeys> sınıfını kullanan yeni uygulama <xref:System.Windows.Forms.SendKeys.SendWait%2A> yöntemi için başka bir işleme gönderildiğinde işlenecek iletilerinin değil bekleyecek.  
>   
>  Uygulamanız işletim sistemi bağımsız olarak tutarlı davranışına dayalıysa, zorlayabilirsiniz <xref:System.Windows.Forms.SendKeys> sınıfı, app.config dosyasına aşağıdaki uygulama ayarı ekleyerek yeni uygulaması kullanın.  
>   
>  `<appSettings>`  
>   
>  `<add key="SendKeys" value="SendInput"/>`  
>   
>  `</appSettings>`  
>   
>  Zorlamak için <xref:System.Windows.Forms.SendKeys> önceki uygulaması, değer kullanmanız için sınıf `"JournalHook"` yerine.  
  
#### <a name="to-send-a-keystroke-to-the-same-application"></a>Aynı uygulamaya bir tuş vuruşu göndermek için  
  
1.  Çağrı <xref:System.Windows.Forms.SendKeys.Send%2A> veya <xref:System.Windows.Forms.SendKeys.SendWait%2A> yöntemi <xref:System.Windows.Forms.SendKeys> sınıfı. Belirtilen tuş vuruşları uygulama etkin denetim alınır. Aşağıdaki kod örneğinde <xref:System.Windows.Forms.SendKeys.Send%2A> kullanıcı formu yüzeyinin tıklattığında ENTER tuşuna basarak benzetimini yapmak için. Bu örnek varsayar bir <xref:System.Windows.Forms.Form> tek bir <xref:System.Windows.Forms.Button> bir sekme dizini 0 olan denetim.  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]  
  
#### <a name="to-send-a-keystroke-to-a-different-application"></a>Farklı bir uygulamaya bir tuş vuruşu göndermek için  
  
1.  Tuş vuruşları almak, ardından çağıran uygulama penceresi etkinleştirme <xref:System.Windows.Forms.SendKeys.Send%2A> veya <xref:System.Windows.Forms.SendKeys.SendWait%2A> yöntemi. Başka bir uygulamayı etkinleştirmek için yönetilen bir yöntem olduğundan, diğer uygulamaları odak zorlamak için yerel Windows yöntemlerini kullanmanız gerekir. Aşağıdaki kod örneği kullanan platform çağırma çağırmak için `FindWindow` ve `SetForegroundWindow` hesaplayıcı uygulama penceresi, ardından çağrıları etkinleştirmek için yöntemleri <xref:System.Windows.Forms.SendKeys.SendWait%2A> hesaplamaları bir dizi hesaplayıcı uygulamaya vermek için.  
  
    > [!NOTE]
    >  Doğru parametreleri `FindWindow` hesaplayıcı uygulama bulur çağrısı Windows sürümüne göre değişir.  Aşağıdaki kod üzerinde hesaplayıcı uygulama bulur [!INCLUDE[win7](../../../includes/win7-md.md)]. Üzerinde [!INCLUDE[windowsver](../../../includes/windowsver-md.md)], ilk parametre "SciCalc" değiştirin. Visual Studio ile dahil Spy ++ araç, doğru parametreleri belirlemek için kullanabilirsiniz.  
  
     [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.SimulateKeyPress#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, yukarıdaki kod örnekleri için tam uygulamasıdır.  
  
 [!code-cpp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.SimulateKeyPress#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'ta Kullanıcı Girdisi](../../../docs/framework/winforms/user-input-in-windows-forms.md)
