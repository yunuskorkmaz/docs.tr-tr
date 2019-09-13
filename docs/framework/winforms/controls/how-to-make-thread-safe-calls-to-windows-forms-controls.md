---
title: 'Nasıl yapılır: Windows Forms denetimlerine iş parçacığına güvenli çağrılar yapma'
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
ms.openlocfilehash: 78ad7b16d5220972a61848c0c80cd884afa842d9
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928610"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Nasıl yapılır: Windows Forms denetimlerine iş parçacığına güvenli çağrılar yapma

Çoklu iş parçacığı Windows Forms uygulamaların performansını iyileştirebilir, ancak Windows Forms denetimlerine erişim, kendiliğinden iş parçacığı açısından güvenli değildir. Çoklu iş parçacığı, kodunuzu çok önemli ve karmaşık hatalara karşı savunmasız bırakabilir. Bir denetimi işleyen iki veya daha fazla iş parçacığı denetimi tutarsız duruma zorlayabilir ve yarış koşullarına, kilitlenmelerine ve donmasına veya askıda kalmasına yol açabilir. Uygulamanıza çoklu iş parçacığı uygularsanız, iş parçacığı denetimlerini iş parçacığı güvenli bir şekilde çağırdığınızdan emin olun. Daha fazla bilgi için bkz. [yönetilen iş parçacığı en iyi yöntemleri](../../../standard/threading/managed-threading-best-practices.md). 

Denetim oluşturamayan bir iş parçacığından Windows Forms denetimini güvenle çağırmanın iki yolu vardır. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> Yöntemi, ana iş parçacığında oluşturulan bir temsilciyi çağırmak için kullanabilirsiniz ve bu da denetimi çağırır. Ya da, sonuçlar üzerinde raporlamadan arka plan iş parçacığında yapılan işleri ayırmak için olay odaklı bir model kullanan bir <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>de uygulayabilirsiniz. 

## <a name="unsafe-cross-thread-calls"></a>Güvenli olmayan çapraz iş parçacığı çağrıları

Bir denetimi, onu oluşturan bir iş parçacığından doğrudan çağırmak güvenli değildir. Aşağıdaki kod parçacığı, <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> denetime güvenli olmayan bir çağrı gösterir. Olay işleyicisi, ana iş parçacığının `WriteTextUnsafe` <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> özelliğini doğrudan ayarlayan yeni bir iş parçacığı oluşturur. `Button1_Click` 

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

Visual Studio hata ayıklayıcı bu güvenli olmayan iş parçacığı aramalarını <xref:System.InvalidOperationException> algılar, bu ileti, **çapraz iş parçacığı işlemi geçerli değildir. "" Denetimine oluşturulduğu iş parçacığı dışında bir iş parçacığından erişildi.** Visual Studio hata ayıklaması sırasında güvenli olmayan çapraz iş parçacığı çağrıları için herzamangerçekleşirveuygulamaçalışmazamanındaoluşabilir.<xref:System.InvalidOperationException> Sorunu çözmeniz gerekir, ancak <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> özelliğini olarak `false`ayarlayarak özel durumu devre dışı bırakabilirsiniz.

## <a name="safe-cross-thread-calls"></a>Güvenli çapraz iş parçacığı çağrıları 

Aşağıdaki kod örnekleri, kendisini oluşturamayan bir iş parçacığından Windows Forms denetimini güvenle çağırmak için iki yol gösterir: 

1. Denetimi çağırmak için ana iş parçacığından bir temsilciyi çağıran yöntemi.<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> 
2. Olay <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> odaklı bir model sunan bir bileşen. 

Her iki örnekte de arka plan iş parçacığı, bu iş parçacığında gerçekleştirilen çalışmanın benzetimini yapmak için bir saniye boyunca uykuya geçer. 

Bu örnekleri C# veya Visual Basic komut satırından .NET Framework uygulamalar olarak oluşturabilir ve çalıştırabilirsiniz. Daha fazla bilgi için bkz. [CSC. exe Ile komut satırı oluşturma](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [komut satırından derleme (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md). 

.NET Core 3,0 ile başlayarak, örnekleri .NET Core Windows Forms  *\<klasör adı >. csproj* proje dosyası olan bir klasörden Windows .NET Core uygulamaları olarak oluşturup çalıştırabilirsiniz. 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Örnek: Invoke metodunu bir temsilciyle kullanma

Aşağıdaki örnek, Windows Forms denetimine iş parçacığı açısından güvenli çağrılar sağlamaya yönelik bir model gösterir. Denetimin oluşturma iş <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> parçacığı kimliğini çağıran iş parçacığı kimliğiyle karşılaştıran özelliği sorgular. İş parçacığı kimlikleri aynıysa, denetimi doğrudan çağırır. İş parçacığı kimlikleri farklıysa, bu <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> yöntemi ana iş parçacığından gelen bir temsilciyle çağırır ve bu, denetimin gerçek çağrısını yapar.

, `SafeCallDelegate` <xref:System.Windows.Forms.TextBox> Denetimin özelliğini<xref:System.Windows.Forms.TextBox.Text%2A> ayarlamaya izin vermez. `WriteTextSafe` Yöntemi sorgular<xref:System.Windows.Forms.Control.InvokeRequired%2A>. <xref:System.Windows.Forms.Control.InvokeRequired%2A> <xref:System.Windows.Forms.Control.Invoke%2A> `SafeCallDelegate` Dönerse ,`true`denetime gerçek çağrı yapmak için yöntemini yöntemine geçirir. `WriteTextSafe` <xref:System.Windows.Forms.Control.InvokeRequired%2A> Dönerse `false`, doğrudanayarlar<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> . `WriteTextSafe` Olay işleyicisi yeni iş parçacığını oluşturur ve `WriteTextSafe` metodunu çalıştırır. `Button1_Click` 

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Örnek: BackgroundWorker olay işleyicisi kullanma

Çoklu iş parçacığı <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> kullanmanın kolay bir yolu, olay odaklı bir model kullanan bileşendir. Arka plan iş parçacığı, <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> ana iş parçacığıyla etkileşime giremeyen olayını çalıştırır. Ana iş parçacığı, <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> ve olay işleyicilerini çalıştırır ve <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> bu da ana iş parçacığının denetimlerini çağırabilir.

Kullanarak <xref:System.ComponentModel.BackgroundWorker>iş parçacığı açısından güvenli bir çağrı yapmak için, iş için arka plan iş parçacığında bir yöntem oluşturun ve <xref:System.ComponentModel.BackgroundWorker.DoWork> olaya bağlayın. Arka plan işinin sonuçlarını raporlamak ve <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> veya <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olayına bağlamak için ana iş parçacığında başka bir yöntem oluşturun. Arka plan iş parçacığını başlatmak için çağrısı <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>yapın. 

Örnek, <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> <xref:System.Windows.Forms.TextBox> denetimin özelliğiniayarlamakiçinolayişleyicisinikullanır.<xref:System.Windows.Forms.TextBox.Text%2A> <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Olayı kullanan bir örnek için bkz <xref:System.ComponentModel.BackgroundWorker>. 

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.BackgroundWorker>
- [Nasıl yapılır: Arka planda işlem çalıştırma](how-to-run-an-operation-in-the-background.md)
- [Nasıl yapılır: Arka plan işlemi kullanan bir form uygulama](how-to-implement-a-form-that-uses-a-background-operation.md)
- [.NET Framework ile özel Windows Forms denetimleri geliştirin](developing-custom-windows-forms-controls.md)
