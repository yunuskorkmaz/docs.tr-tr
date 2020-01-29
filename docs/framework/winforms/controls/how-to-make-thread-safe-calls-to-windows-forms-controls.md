---
title: Denetimlere iş parçacığına güvenli çağrılar yapma
ms.date: 02/19/2019
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
ms.openlocfilehash: 101457ab2a02b8de49d06c354ca307e07b690ba2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736155"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Nasıl yapılır: Windows Forms denetimlerine iş parçacığına güvenli çağrılar yapma

Çoklu iş parçacığı Windows Forms uygulamaların performansını iyileştirebilir, ancak Windows Forms denetimlerine erişim, kendiliğinden iş parçacığı açısından güvenli değildir. Çoklu iş parçacığı, kodunuzu çok önemli ve karmaşık hatalara karşı savunmasız bırakabilir. Bir denetimi işleyen iki veya daha fazla iş parçacığı denetimi tutarsız duruma zorlayabilir ve yarış koşullarına, kilitlenmelerine ve donmasına veya askıda kalmasına yol açabilir. Uygulamanıza çoklu iş parçacığı uygularsanız, iş parçacığı denetimlerini iş parçacığı güvenli bir şekilde çağırdığınızdan emin olun. Daha fazla bilgi için bkz. [yönetilen iş parçacığı en iyi yöntemleri](../../../standard/threading/managed-threading-best-practices.md). 

Denetim oluşturamayan bir iş parçacığından Windows Forms denetimini güvenle çağırmanın iki yolu vardır. Ana iş parçacığında oluşturulan bir temsilciyi çağırmak için <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> yöntemini kullanabilirsiniz ve bu da denetimi çağırır. Ya da, sonuçlar üzerinde raporlamadan arka plan iş parçacığında yapılan işi ayırmak için olay odaklı bir model kullanan bir <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>uygulayabilirsiniz. 

## <a name="unsafe-cross-thread-calls"></a>Güvenli olmayan çapraz iş parçacığı çağrıları

Bir denetimi, onu oluşturan bir iş parçacığından doğrudan çağırmak güvenli değildir. Aşağıdaki kod parçacığı, <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> denetimine güvenli olmayan bir çağrı gösterir. `Button1_Click` olay işleyicisi, ana iş parçacığının <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> özelliğini doğrudan ayarlayan yeni bir `WriteTextUnsafe` iş parçacığı oluşturur. 

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

Visual Studio hata ayıklayıcı, bu güvenli olmayan iş parçacığı çağrılarını ileti ile bir <xref:System.InvalidOperationException> yükselterek algılar, **çapraz iş parçacığı işlemi geçerli değildir. "" Denetimine oluşturulduğu iş parçacığı dışında bir iş parçacığından erişildi.** <xref:System.InvalidOperationException>, Visual Studio hata ayıklaması sırasında güvenli olmayan çapraz iş parçacığı çağrıları için her zaman oluşur ve uygulama çalışma zamanında oluşabilir. Sorunu çözmeniz gerekir, ancak <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> özelliğini `false`olarak ayarlayarak özel durumu devre dışı bırakabilirsiniz.

## <a name="safe-cross-thread-calls"></a>Güvenli çapraz iş parçacığı çağrıları 

Aşağıdaki kod örnekleri, kendisini oluşturamayan bir iş parçacığından Windows Forms denetimini güvenle çağırmak için iki yol gösterir: 

1. Denetimi çağırmak için ana iş parçacığından bir temsilci çağıran <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> yöntemi. 
2. Olay odaklı bir model sunan <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> bileşen. 

Her iki örnekte de arka plan iş parçacığı, bu iş parçacığında gerçekleştirilen çalışmanın benzetimini yapmak için bir saniye boyunca uykuya geçer. 

Bu örnekleri C# veya Visual Basic komut satırından .NET Framework uygulamalar olarak oluşturabilir ve çalıştırabilirsiniz. Daha fazla bilgi için bkz. [CSC. exe Ile komut satırı oluşturma](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [komut satırından derleme (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md). 

.NET Core 3,0 ile başlayarak, örnekleri .NET Core Windows Forms *\<klasör adı >. csproj* proje dosyası olan bir klasörden Windows .NET Core uygulamaları olarak oluşturup çalıştırabilirsiniz. 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Örnek: Invoke metodunu bir temsilciyle kullanma

Aşağıdaki örnek, Windows Forms denetimine iş parçacığı açısından güvenli çağrılar sağlamaya yönelik bir model gösterir. Denetimin oluşturma iş parçacığı KIMLIĞINI çağıran iş parçacığı KIMLIĞIYLE karşılaştıran <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> özelliğini sorgular. İş parçacığı kimlikleri aynıysa, denetimi doğrudan çağırır. İş parçacığı kimlikleri farklıysa, ana iş parçacığından bir temsilciyle <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> yöntemini çağırır ve bu, denetime gerçek çağrıyı yapar.

`SafeCallDelegate`, <xref:System.Windows.Forms.TextBox> denetiminin <xref:System.Windows.Forms.TextBox.Text%2A> özelliğini ayarlamayı mümkün. `WriteTextSafe` yöntemi <xref:System.Windows.Forms.Control.InvokeRequired%2A>sorgular. <xref:System.Windows.Forms.Control.InvokeRequired%2A> `true`döndürürse `WriteTextSafe` denetimin gerçek çağrısını yapmak için `SafeCallDelegate` <xref:System.Windows.Forms.Control.Invoke%2A> yöntemine geçirir. <xref:System.Windows.Forms.Control.InvokeRequired%2A> `false`döndürürse `WriteTextSafe` <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> doğrudan ayarlar. `Button1_Click` olay işleyicisi yeni iş parçacığını oluşturur ve `WriteTextSafe` metodunu çalıştırır. 

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Örnek: BackgroundWorker olay işleyicisi kullanın

Çoklu iş parçacıklı uygulama kullanmanın kolay bir yolu, olay odaklı bir model kullanan <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> bileşenidir. Arka plan iş parçacığı, ana iş parçacığıyla etkileşimde bulunmayan <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> olayını çalıştırır. Ana iş parçacığı, ana iş parçacığının denetimlerini çağırabilen <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> ve <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> olay işleyicilerini çalıştırır.

<xref:System.ComponentModel.BackgroundWorker>kullanarak iş parçacığı açısından güvenli bir çağrı yapmak için, işi yapmak için arka plan iş parçacığında bir yöntem oluşturun ve <xref:System.ComponentModel.BackgroundWorker.DoWork> olayına bağlayın. Arka plan işinin sonuçlarını raporlamak ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> veya <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olayına bağlamak için ana iş parçacığında başka bir yöntem oluşturun. Arka plan iş parçacığını başlatmak için <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>çağırın. 

Örnek, <xref:System.Windows.Forms.TextBox> denetiminin <xref:System.Windows.Forms.TextBox.Text%2A> özelliğini ayarlamak için <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay işleyicisini kullanır. <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olayını kullanan bir örnek için bkz. <xref:System.ComponentModel.BackgroundWorker>. 

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.BackgroundWorker>
- [Nasıl yapılır: arka planda işlem çalıştırma](how-to-run-an-operation-in-the-background.md)
- [Nasıl yapılır: arka plan işlemi kullanan bir form uygulama](how-to-implement-a-form-that-uses-a-background-operation.md)
- [.NET Framework ile özel Windows Forms denetimleri geliştirin](developing-custom-windows-forms-controls.md)
