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
ms.openlocfilehash: 52f89df8d7f28f0e00c3becd9005b46e52b5532c
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960209"
---
# <a name="how-to-simulate-mouse-and-keyboard-events-in-code"></a>Nasıl yapılır: Kodda Fare ve Klavye Olaylarının Benzetimini Yapma

Windows Forms, fare ve klavye girişini programlı bir şekilde taklit etmek için çeşitli seçenekler sağlar. Bu konu, bu seçeneklere genel bir bakış sağlar.

## <a name="simulating-mouse-input"></a>Fare girişinin benzetimini yapma

Fare olaylarının benzetimini yapmanın en iyi yolu, benzetimini yapmak istediğiniz fare olayını oluşturan `On`*EventName* metodunu çağırmakdır. Bu seçenek genellikle yalnızca özel denetimler ve formlarda yapılabilir, çünkü olayları oluşturan Yöntemler korunur ve denetim ya da form dışında erişilemez. Örneğin, aşağıdaki adımlarda kodda sağ fare düğmesine tıklanın simülasyonu gösterilmektedir.

#### <a name="to-programmatically-click-the-right-mouse-button"></a>Programlama yoluyla sağ fare düğmesine tıklama

1. <xref:System.Windows.Forms.MouseEventArgs.Button%2A> özelliği <xref:System.Windows.Forms.MouseButtons.Right?displayProperty=nameWithType> değerine ayarlanmış bir <xref:System.Windows.Forms.MouseEventArgs> oluşturun.

2. Bağımsız değişken olarak bu <xref:System.Windows.Forms.MouseEventArgs> <xref:System.Windows.Forms.Control.OnMouseClick%2A> yöntemi çağırın.

Özel denetimler hakkında daha fazla bilgi için bkz. [tasarım zamanında Windows Forms denetimleri geliştirme](./controls/developing-windows-forms-controls-at-design-time.md).

Fare girişinin benzetimini yapmak için başka yollar vardır. Örneğin, normalde fare girişi (örneğin, <xref:System.Windows.Forms.CheckBox> denetiminin <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği) aracılığıyla ayarlanmış bir durumu temsil eden bir denetim özelliğini program aracılığıyla ayarlayabilir veya benzetimini yapmak istediğiniz olaya bağlı temsilciyi doğrudan çağırabilirsiniz.

## <a name="simulating-keyboard-input"></a>Klavye girişi benzetimi yapma

Fare girişi için yukarıda açıklanan stratejileri kullanarak klavye girişini benzeyseniz de Windows Forms, etkin uygulamaya tuş vuruşları göndermek için <xref:System.Windows.Forms.SendKeys> sınıfı da sağlar.

> [!CAUTION]
> Uygulamanız çeşitli klavyelerde uluslararası kullanım için tasarlanıyorsa <xref:System.Windows.Forms.SendKeys.Send%2A?displayProperty=nameWithType> kullanımı öngörülemeyen sonuçlara neden olabilir ve kaçınılması gerekir.

> [!NOTE]
> <xref:System.Windows.Forms.SendKeys> sınıfı, Windows Vista 'da çalışan uygulamalarda kullanımını etkinleştirmek için .NET Framework 3,0 güncelleştirilmiştir. Windows Vista 'nın (Kullanıcı hesabı denetimi veya UAC olarak bilinir) gelişmiş güvenliği, önceki uygulamanın beklendiği gibi çalışmasını engeller.
>
> <xref:System.Windows.Forms.SendKeys> sınıfı, bazı geliştiricilerin geçici bir çözüm sunmasıyla ilgili zamanlama sorunlarıyla açıktır. Güncelleştirilmiş uygulama zamanlama sorunları için hala açıktır, ancak biraz daha hızlıdır ve geçici çözümler üzerinde değişiklik yapılmasını gerektirebilir. <xref:System.Windows.Forms.SendKeys> sınıfı önce önceki uygulamayı kullanmaya çalışır ve bu başarısız olursa yeni uygulamayı kullanır. Sonuç olarak, <xref:System.Windows.Forms.SendKeys> sınıfı farklı işletim sistemlerinde farklı davranabilirler. Ayrıca, <xref:System.Windows.Forms.SendKeys> sınıfı yeni uygulamayı kullandığında, başka bir işleme gönderilirken <xref:System.Windows.Forms.SendKeys.SendWait%2A> yöntemi iletilerin işlenmesini beklemez.
>
> Uygulamanız işletim sisteminden bağımsız olarak tutarlı bir davranış kullanıyorsa, App. config dosyanıza aşağıdaki uygulama ayarını ekleyerek, <xref:System.Windows.Forms.SendKeys> sınıfını yeni uygulamayı kullanmak üzere zorlayabilirsiniz.
>
> ```xml
> <appSettings>
>  <add key="SendKeys" value="SendInput"/>
> </appSettings>
> ```
>
> <xref:System.Windows.Forms.SendKeys> sınıfını önceki uygulamayı kullanacak şekilde zorlamak için, bunun yerine `"JournalHook"` değerini kullanın.

#### <a name="to-send-a-keystroke-to-the-same-application"></a>Aynı uygulamaya bir tuş vuruşu göndermek için

1. <xref:System.Windows.Forms.SendKeys> sınıfının <xref:System.Windows.Forms.SendKeys.Send%2A> veya <xref:System.Windows.Forms.SendKeys.SendWait%2A> yöntemini çağırın. Belirtilen tuş vuruşları, uygulamanın etkin denetimi tarafından alınır. Aşağıdaki kod örneği, Kullanıcı formun yüzeyine çift tıkladığında ENTER tuşuna basmayı taklit etmek için <xref:System.Windows.Forms.SendKeys.Send%2A> kullanır. Bu örnekte, sekme dizini 0 olan tek bir <xref:System.Windows.Forms.Button> denetimine sahip bir <xref:System.Windows.Forms.Form> varsayılır.

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#10)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#10)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#10)]

#### <a name="to-send-a-keystroke-to-a-different-application"></a>Farklı bir uygulamaya tuş vuruşu göndermek için

1. Tuş vuruşlarını alacak uygulama penceresini etkinleştirin ve sonra <xref:System.Windows.Forms.SendKeys.Send%2A> veya <xref:System.Windows.Forms.SendKeys.SendWait%2A> yöntemini çağırın. Başka bir uygulamayı etkinleştirmek için yönetilen bir yöntem olmadığından, başka uygulamalara odaklanmak için yerel Windows yöntemlerini kullanmanız gerekir. Aşağıdaki kod örneği, hesaplayıcı uygulama penceresini etkinleştirmek üzere `FindWindow` ve `SetForegroundWindow` yöntemlerini çağırmak için platform Invoke kullanır ve ardından hesaplayıcı uygulamasına bir dizi hesaplama vermek için <xref:System.Windows.Forms.SendKeys.SendWait%2A> çağırır.

    > [!NOTE]
    > Hesap makinesi uygulamasını bulan `FindWindow` çağrısının doğru parametreleri, Windows sürümünüze bağlı olarak değişiklik gösterir.  Aşağıdaki kod, Windows 7 ' de Hesaplayıcı uygulamasını bulur. Windows Vista 'da, ilk parametreyi "SciCalc" olarak değiştirin. Doğru parametreleri öğrenmek için Visual Studio ile birlikte bulunan Spy + + aracını kullanabilirsiniz.

    [!code-cpp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#5)]
    [!code-csharp[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#5)]
    [!code-vb[System.Windows.Forms.SimulateKeyPress#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#5)]

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, önceki kod örnekleri için tüm uygulamadır.

[!code-cpp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/cpp/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.SimulateKeyPress#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SimulateKeyPress/VB/form1.vb#0)]

## <a name="compiling-the-code"></a>Kod Derleme

Bu örnek şunları gerektirir:

- System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Kullanıcı Girdisi](user-input-in-windows-forms.md)
