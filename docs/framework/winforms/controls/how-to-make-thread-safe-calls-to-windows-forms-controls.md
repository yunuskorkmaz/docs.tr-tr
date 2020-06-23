---
title: Denetimlere iş parçacığına güvenli çağrılar yapma
ms.date: 02/19/2019
description: İş parçacığı oluşturma denetimlerini iş parçacığı güvenli bir şekilde çağırarak uygulamanızda çoklu iş parçacığı uygulamayı nasıl uygulayacağınızı öğrenin.
dev_langs:
- csharp
- vb
f1_keywords:
- EHInvalidOperation.WinForms.IllegalCrossThreadCall
helpviewer_keywords:
- thread safety [Windows Forms], calling controls [Windows Forms]
- calling controls [Windows Forms], thread safety [Windows Forms]
- CheckForIllegalCrossThreadCalls property [Windows Forms]
- Windows Forms controls [Windows Forms], multithreading
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], cross-thread calls
- controls [Windows Forms], multithreading
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
ms.openlocfilehash: b5f4de7bd3d8d89de98dbe27e2dbf360763670d0
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904188"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Nasıl yapılır: Windows Forms denetimlerine iş parçacığına güvenli çağrılar yapma

Çoklu iş parçacığı Windows Forms uygulamaların performansını iyileştirebilir, ancak Windows Forms denetimlerine erişim, kendiliğinden iş parçacığı açısından güvenli değildir. Çoklu iş parçacığı, kodunuzu çok önemli ve karmaşık hatalara karşı savunmasız bırakabilir. Bir denetimi işleyen iki veya daha fazla iş parçacığı denetimi tutarsız duruma zorlayabilir ve yarış koşullarına, kilitlenmelerine ve donmasına veya askıda kalmasına yol açabilir. Uygulamanıza çoklu iş parçacığı uygularsanız, iş parçacığı denetimlerini iş parçacığı güvenli bir şekilde çağırdığınızdan emin olun. Daha fazla bilgi için bkz. [yönetilen iş parçacığı en iyi yöntemleri](../../../standard/threading/managed-threading-best-practices.md).

Denetim oluşturamayan bir iş parçacığından Windows Forms denetimini güvenle çağırmanın iki yolu vardır. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>Yöntemi, ana iş parçacığında oluşturulan bir temsilciyi çağırmak için kullanabilirsiniz ve bu da denetimi çağırır. Ya da, <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> sonuçlar üzerinde raporlamadan arka plan iş parçacığında yapılan işleri ayırmak için olay odaklı bir model kullanan bir de uygulayabilirsiniz.

## <a name="unsafe-cross-thread-calls"></a>Güvenli olmayan çapraz iş parçacığı çağrıları

Bir denetimi, onu oluşturan bir iş parçacığından doğrudan çağırmak güvenli değildir. Aşağıdaki kod parçacığı, denetime güvenli olmayan bir çağrı gösterir <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> . `Button1_Click`Olay işleyicisi, `WriteTextUnsafe` ana iş parçacığının özelliğini doğrudan ayarlayan yeni bir iş parçacığı oluşturur <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> .

```csharp
private void Button1_Click(object sender, EventArgs e)
{
    thread2 = new Thread(new ThreadStart(WriteTextUnsafe));
    thread2.Start();
}
private void WriteTextUnsafe()
{
    textBox1.Text = "This text was set unsafely.";
}
```

```vb
Private Sub Button1_Click(ByVal sender As Object, e As EventArgs) Handles Button1.Click
    Thread2 = New Thread(New ThreadStart(AddressOf WriteTextUnsafe))
    Thread2.Start()
End Sub

Private Sub WriteTextUnsafe()
    TextBox1.Text = "This text was set unsafely."
End Sub
```

Visual Studio hata ayıklayıcı bu güvenli olmayan iş parçacığı aramalarını algılar <xref:System.InvalidOperationException> , bu ileti, **çapraz iş parçacığı işlemi geçerli değildir. "" Denetimine oluşturulduğu iş parçacığı dışında bir iş parçacığından erişildi.** <xref:System.InvalidOperationException>Visual Studio hata ayıklaması sırasında güvenli olmayan çapraz iş parçacığı çağrıları için her zaman gerçekleşir ve uygulama çalışma zamanında oluşabilir. Sorunu çözmeniz gerekir, ancak özelliğini olarak ayarlayarak özel durumu devre dışı bırakabilirsiniz <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> `false` .

## <a name="safe-cross-thread-calls"></a>Güvenli çapraz iş parçacığı çağrıları

Aşağıdaki kod örnekleri, kendisini oluşturamayan bir iş parçacığından Windows Forms denetimini güvenle çağırmak için iki yol gösterir:

1. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>Denetimi çağırmak için ana iş parçacığından bir temsilciyi çağıran yöntemi.
2. <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>Olay odaklı bir model sunan bir bileşen.

Her iki örnekte de arka plan iş parçacığı, bu iş parçacığında gerçekleştirilen çalışmanın benzetimini yapmak için bir saniye boyunca uykuya geçer.

Bu örnekleri C# veya Visual Basic komut satırından .NET Framework uygulamalar olarak oluşturabilir ve çalıştırabilirsiniz. Daha fazla bilgi için, komut satırından csc.exeveya derleme [Ile komut satırı oluşturma](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) [(Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)bölümüne bakın.

.NET Core 3,0 ile başlayarak, örnekleri .NET Core Windows Forms * \<folder name> . csproj* proje dosyası olan bir klasörden Windows .NET Core uygulamaları olarak oluşturup çalıştırabilirsiniz.

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Örnek: Invoke metodunu bir temsilciyle kullanma

Aşağıdaki örnek, Windows Forms denetimine iş parçacığı açısından güvenli çağrılar sağlamaya yönelik bir model gösterir. <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName>Denetimin oluşturma iş parçacığı kimliğini çağıran iş parçacığı kimliğiyle karşılaştıran özelliği sorgular. İş parçacığı kimlikleri aynıysa, denetimi doğrudan çağırır. İş parçacığı kimlikleri farklıysa, bu <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> yöntemi ana iş parçacığından gelen bir temsilciyle çağırır ve bu, denetimin gerçek çağrısını yapar.

, `SafeCallDelegate` <xref:System.Windows.Forms.TextBox> Denetimin özelliğini ayarlamaya izin vermez <xref:System.Windows.Forms.TextBox.Text%2A> . `WriteTextSafe`Yöntemi sorgular <xref:System.Windows.Forms.Control.InvokeRequired%2A> . <xref:System.Windows.Forms.Control.InvokeRequired%2A>Dönerse, `true` `WriteTextSafe` `SafeCallDelegate` <xref:System.Windows.Forms.Control.Invoke%2A> denetime gerçek çağrı yapmak için yöntemini yöntemine geçirir. <xref:System.Windows.Forms.Control.InvokeRequired%2A>Dönerse `false` , `WriteTextSafe` doğrudan ayarlar <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> . `Button1_Click`Olay işleyicisi yeni iş parçacığını oluşturur ve `WriteTextSafe` metodunu çalıştırır.

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Örnek: BackgroundWorker olay işleyicisi kullanın

Çoklu iş parçacığı kullanmanın kolay bir yolu, <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> olay odaklı bir model kullanan bileşendir. Arka plan iş parçacığı, <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> ana iş parçacığıyla etkileşime giremeyen olayını çalıştırır. Ana iş parçacığı, <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> ve <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> olay işleyicilerini çalıştırır ve bu da ana iş parçacığının denetimlerini çağırabilir.

Kullanarak iş parçacığı açısından güvenli bir çağrı yapmak için <xref:System.ComponentModel.BackgroundWorker> , iş için arka plan iş parçacığında bir yöntem oluşturun ve <xref:System.ComponentModel.BackgroundWorker.DoWork> olaya bağlayın. Arka plan işinin sonuçlarını raporlamak ve veya olayına bağlamak için ana iş parçacığında başka bir yöntem oluşturun <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> . Arka plan iş parçacığını başlatmak için çağrısı yapın <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType> .

Örnek, <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> denetimin özelliğini ayarlamak için olay işleyicisini kullanır <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.TextBox.Text%2A> . Olayı kullanan bir örnek için <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> bkz <xref:System.ComponentModel.BackgroundWorker> ..

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.BackgroundWorker>
- [Nasıl yapılır: arka planda işlem çalıştırma](how-to-run-an-operation-in-the-background.md)
- [Nasıl yapılır: arka plan işlemi kullanan bir form uygulama](how-to-implement-a-form-that-uses-a-background-operation.md)
- [.NET Framework ile özel Windows Forms denetimleri geliştirin](developing-custom-windows-forms-controls.md)
