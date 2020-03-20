---
title: Denetimlere iş parçacığı için güvenli aramalar yapma
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
ms.openlocfilehash: 365b1acb693b9ff2be603a3e659ed8d846a7696a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142010"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Nasıl yapılır: Windows Forms denetimlerine iş parçacığı için güvenli aramalar yapma

Çoklu iş parçacığı, Windows Forms uygulamalarının performansını artırabilir, ancak Windows Forms denetimlerine erişim doğal olarak iş parçacığı için güvenli değildir. Multithreading kodunuzu çok ciddi ve karmaşık hatalara maruz bırakabilir. Denetimi manipüle eden iki veya daha fazla iş parçacığı denetimi tutarsız bir duruma zorlayabilir ve yarış koşullarına, kilitlenmelere ve donmalara veya askıda kalmasına yol açabilir. Uygulamanızda çoklu iş parçacığı uygularsanız, iş parçacığı denetimlerini iş parçacığı güvenli bir şekilde aradığınızdan emin olun. Daha fazla bilgi için yönetilen [iş parçacığı en iyi uygulamaları](../../../standard/threading/managed-threading-best-practices.md)bakın.

Bu denetimi oluşturmayan bir iş parçacığından Windows Forms denetimini güvenli bir şekilde aramanın iki yolu vardır. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> Yöntemi, ana iş parçacığında oluşturulan ve denetimi çağıran bir temsilciyi çağırmak için kullanabilirsiniz. Veya, arka plan <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>iş parçacığında yapılan işleri sonuçları raporlamaktan ayırmak için olay odaklı bir model kullanan bir , uygulayabilirsiniz.

## <a name="unsafe-cross-thread-calls"></a>Güvenli olmayan çapraz iş parçacığı çağrıları

Denetimi oluşturmayan bir iş parçacığından doğrudan aramak güvenli değildir. Aşağıdaki kod parçacığı <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> denetime güvenli olmayan bir çağrıyı gösterir. `Button1_Click` Olay işleyicisi, `WriteTextUnsafe` ana iş parçacığının <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> özelliğini doğrudan ayarlayan yeni bir iş parçacığı oluşturur.

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

Visual Studio hata ayıklayıcı iletisi ile yükselterek <xref:System.InvalidOperationException> bu güvenli olmayan iş parçacığı çağrıları algılar, Çapraz iş parçacığı işlemi geçerli **değildir. Oluşturulduğu iş parçacığı dışındaki bir iş parçacığından erişilen "" denetimi.** Her <xref:System.InvalidOperationException> zaman Visual Studio hata ayıklama sırasında güvenli olmayan çapraz iş parçacığı aramaları için oluşur ve uygulama çalışma zamanında oluşabilir. Sorunu gidermelisiniz, ancak <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> özelliği `false`'ne ayarlayarak özel durumu devre dışı kullanabilirsiniz.

## <a name="safe-cross-thread-calls"></a>Güvenli çapraz iş parçacığı çağrıları

Aşağıdaki kod örnekleri, oluşturmayan bir iş parçacığından Windows Forms denetimini güvenli bir şekilde aramanın iki yolunu gösterir:

1. Denetimi <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> çağırmak için ana iş parçacığından bir temsilci çağıran yöntem.
2. Olay <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> odaklı bir model sunan bir bileşen.

Her iki örnekte de, arka plan iş parçacığı bu iş parçacığı yapılan işi simüle etmek için bir saniye uyur.

Bu örnekleri C# veya Visual Basic komut satırından .NET Framework uygulamaları olarak oluşturabilir ve çalıştırabilirsiniz. Daha fazla bilgi için [csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya Build komut [satırı (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)ile Komut satırı binasına bakın.

.NET Core 3.0 ile başlayarak, .NET Core Windows Forms * \<klasör adı>.csproj* proje dosyasına sahip bir klasörden windows .NET Core uygulamaları olarak örnekler oluşturabilir ve çalıştırabilirsiniz.

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Örnek: Bir temsilci ile Invoke yöntemini kullanın

Aşağıdaki örnek, Windows Forms denetimine iş parçacığı için güvenli aramalar sağlamak için bir desen gösterir. Denetimin <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> oluşturma iş parçacığı kimliğini arama iş parçacığı kimliğiyle karşılaştıran özelliği sorgular. İş parçacığı işleri aynı ysa, denetimi doğrudan çağrısır. İş parçacığı işleri farklıysa, <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> ana işparçacığından bir temsilciyle metodu çağrıyor ve bu da gerçek aramayı denetime yapıyor.

Denetimin `SafeCallDelegate` <xref:System.Windows.Forms.TextBox.Text%2A> özelliğini <xref:System.Windows.Forms.TextBox> ayarlamayı sağlar. Yöntem `WriteTextSafe` sorguları <xref:System.Windows.Forms.Control.InvokeRequired%2A>. İade <xref:System.Windows.Forms.Control.InvokeRequired%2A> `true` `WriteTextSafe` edilirse, `SafeCallDelegate` denetime <xref:System.Windows.Forms.Control.Invoke%2A> gerçek aramayı yapmak için yönteme geçer. Döndürürse, <xref:System.Windows.Forms.Control.InvokeRequired%2A> `false` `WriteTextSafe` <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> doğrudan ayarlar. Olay `Button1_Click` işleyicisi yeni iş parçacığı `WriteTextSafe` oluşturur ve yöntemi çalıştırAr.

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Örnek: BackgroundWorker olay işleyicisi kullanma

Çoklu iş parçacığı uygulamanın kolay <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> bir yolu, olay odaklı bir model kullanan bileşenle birliktedir. Arka plan iş <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> parçacığı, ana iş parçacığı ile etkileşime girmez olay çalışır. Ana iş parçacığı, ana iş parçacığının denetimlerini çağırabilen <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> ve <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> olay işleyicilerini çalıştırAr.

Kullanarak <xref:System.ComponentModel.BackgroundWorker>iş parçacığı güvenli bir arama yapmak için, işi yapmak için arka plan iş <xref:System.ComponentModel.BackgroundWorker.DoWork> parçacığı bir yöntem oluşturun ve olaya bağlamak. Arka plan çalışmasının sonuçlarını bildirmek için ana iş parçacığında başka <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> bir <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> yöntem oluşturun ve bunu veya olaya bağla. Arka plan iş parçacığı <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>başlatmak için.

Örnek, denetimin <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.TextBox.Text%2A> özelliğini ayarlamak için olay işleyicisini kullanır. <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> Olayı kullanan bir örnek <xref:System.ComponentModel.BackgroundWorker>için bkz.

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.BackgroundWorker>
- [Nasıl yapılır: Arka planda bir işlem çalıştırma](how-to-run-an-operation-in-the-background.md)
- [Nasıl yapılı: Arka plan işlemi kullanan bir form uygulama](how-to-implement-a-form-that-uses-a-background-operation.md)
- [.NET Framework ile özel Windows Forms denetimleri geliştirin](developing-custom-windows-forms-controls.md)
