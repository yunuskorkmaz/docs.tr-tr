---
title: 'Nasıl yapılır: Windows Forms denetimlerine iş parçacığı güvenli aramalar yapın'
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
ms.openlocfilehash: ef7836721df6c090a4d09c38c176641331c3e8a4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362571"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>Nasıl yapılır: Windows Forms denetimlerine iş parçacığı güvenli aramalar yapın

Çoklu iş parçacığı kullanımı Windows Forms uygulamalarının performansını artırabilir, ancak Windows Forms denetimleri için erişim kendiliğinden iş parçacığı açısından güvenli değildir. Çoklu iş parçacığı kullanımı, kodunuzu çok önemli ve karmaşık hataları için kullanıma sunabilirsiniz. Bir denetim düzenleme iki veya daha fazla iş parçacığı, tutarsız bir duruma denetimi zorlamak ve yarış durumları, kilitlenmeleri ve donuyor veya kilitlenmelerine neden. Uygularsanız çoklu iş parçacığı kullanımı uygulamanızda çoklu iş parçacığı denetimleri bir iş parçacığı açısından güvenli şekilde çağrılacak emin olun. Daha fazla bilgi için [yönetilen iş parçacığı oluşturma en iyi yöntemleri](../../../../docs/standard/threading/managed-threading-best-practices.md). 

Bir Windows Forms denetimini denetleyen oluşturmamışsınızdır bir iş parçacığından güvenli bir şekilde çağırmak için iki yolu vardır. Kullanabileceğiniz <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> sırayla denetim çağrıları ana iş parçacığı içinde oluşturulan bir temsilci çağrılacak yöntem. Veya, uygulayabileceğiniz bir <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>, arka plan iş parçacığında sonuçları bildiriminden çalışmanın ayırmak için bir olay odaklı modeli kullanır. 

## <a name="unsafe-cross-thread-calls"></a>Güvenli olmayan iş parçacıkları arası çağrılar

Güvenli olmayan bir denetimi doğrudan, oluşturmamışsınızdır bir iş parçacığından çağırın. Aşağıdaki kod parçacığı güvenli olmayan bir çağrıyı gösterir <xref:System.Windows.Forms.TextBox?displayProperty=nameWithType> denetimi. `Button1_Click` Yeni bir olay işleyicisi oluşturur `WriteTextUnsafe` ayarlar ana iş parçacığının iş parçacığı <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> özelliği doğrudan. 

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

Visual Studio hata ayıklayıcı bu güvenli iş parçacığı çağrı yükselterek algılar bir <xref:System.InvalidOperationException> iletisiyle **iş parçacıkları arası işlemi geçerli değil. Denetim "" iş parçacığının oluşturulduğu dışındaki bir iş parçacığından erişilebilir.** <xref:System.InvalidOperationException> Her zaman güvenli olmayan iş parçacıkları arası çağrılar için Visual Studio hata ayıklama sırasında gerçekleşir ve uygulama çalışma zamanında ortaya çıkabilir. Sorunu düzeltmeniz, ancak ayarlayarak özel durumu devre dışı bırakabilirsiniz <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType> özelliğini `false`.

## <a name="safe-cross-thread-calls"></a>Güvenli iş parçacıkları arası çağrılar 

Aşağıdaki kod örnekleri, bir Windows Forms denetimi oluşturma yaramadı bir iş parçacığından güvenli bir şekilde çağırmanın iki yolu gösterilmektedir: 
1. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> Arama denetimi için ana iş parçacığından bir temsilci çağıran yöntem. 
2. A <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> bileşenin bir olay odaklı modeli sunar. 

Örneklerin her ikisi de bu iş parçacığındaki gerçekleştirilen arka plan iş parçacığı uyku benzetimini yapmak bir saniye için çalışır. 

Derleme ve bu örnekler, .NET Framework uygulamaları Çalıştır C# veya Visual Basic komut satırı. Daha fazla bilgi için [csc.exe ile komut satırı derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) veya [(Visual Basic) komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md). 

.NET Core 3.0 ile başlayarak, ayrıca yapı ve örnekler Windows .NET Core uygulamaları .NET Core Windows Forms bir klasörden Çalıştır  *\<klasör adı > .csproj* proje dosyası. 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>Örnek: Invoke yöntemi, bir temsilci ile kullanma

Aşağıdaki örnek, bir Windows Forms denetimi iş parçacığı güvenli aramalar sağlamaya yönelik bir desen gösterir. Bu sorgular <xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> denetim karşılaştıran özelliği çağıran iş parçacığı kimliği için iş parçacığı kimliği oluşturma İş parçacığı kimlikleri aynı ise, denetimi doğrudan çağırır. İş parçacığı kimlikleri farklıysa çağırdığı <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType> gerçek denetim çağrıda ana iş parçacığından bir temsilci yöntemiyle.

`SafeCallDelegate` Sağlayan ayarı <xref:System.Windows.Forms.TextBox> denetimin <xref:System.Windows.Forms.TextBox.Text%2A> özelliği. `WriteTextSafe` Yöntemi sorguları <xref:System.Windows.Forms.Control.InvokeRequired%2A>. Varsa <xref:System.Windows.Forms.Control.InvokeRequired%2A> döndürür `true`, `WriteTextSafe` geçirir `SafeCallDelegate` için <xref:System.Windows.Forms.Control.Invoke%2A> gerçek denetim çağrı yapmak için yöntemi. Varsa <xref:System.Windows.Forms.Control.InvokeRequired%2A> döndürür `false`, `WriteTextSafe` ayarlar <xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> doğrudan. `Button1_Click` Olay işleyicisi yeni iş parçacığı oluşturan ve çalıştıran `WriteTextSafe` yöntemi. 

 [!code-csharp[ThreadSafeCalls#1](../../../../samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](../../../../samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>Örnek: BackgroundWorker olay işleyicisini kullanın

Kolay bir yolu olan uygulama çoklu iş parçacığı kullanımı <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> bileşenin bir olay odaklı modeli kullanır. Arka plan iş parçacığı çalıştırır <xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType> ana iş parçacığı ile etkileşim kurmaz olayı. Ana iş parçacığı çalıştırır <xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType> ve <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType> olay işleyicileri, ana iş parçacığının denetimleri çağırabilirsiniz.

Kullanarak iş parçacığı çağrı yapmak için <xref:System.ComponentModel.BackgroundWorker>, arka plan iş parçacığından işi yapmak için bir yöntem oluşturun ve ona bağlama <xref:System.ComponentModel.BackgroundWorker.DoWork> olay. Arka plan iş sonuçlarını bildirmek için ana iş parçacığında başka bir yöntem oluşturun ve ona bağlama <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> veya <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay. Arka plan iş parçacığı için çağrı <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>. 

Örnekte <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> ayarlamak için olay işleyicisi <xref:System.Windows.Forms.TextBox> denetimin <xref:System.Windows.Forms.TextBox.Text%2A> özelliği. Bir örnek için <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay bkz <xref:System.ComponentModel.BackgroundWorker>. 

 [!code-csharp[ThreadSafeCalls#2](../../../../samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](../../../../samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.BackgroundWorker>
- [Nasıl yapılır: Arka planda işlem çalıştırma](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Nasıl yapılır: Arka plan işlemi kullanan bir form uygulama](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [.NET Framework ile özel Windows Forms denetimleri geliştirme](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
