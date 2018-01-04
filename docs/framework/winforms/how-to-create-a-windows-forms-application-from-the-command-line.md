---
title: "Nasıl yapılır: komut satırından bir Windows Forms uygulaması oluşturma"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-winforms
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 22acab6ea3912488ae1382ffb42ca5383a7311af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Nasıl yapılır: komut satırından bir Windows Forms uygulaması oluşturma
Aşağıdaki yordamlarda oluşturmak ve komut satırından bir Windows Forms uygulaması çalıştırmak için tamamlamanız gereken temel adımlar açıklanmıştır. Visual Studio'da bu yordamları için kapsamlı destek yoktur.  Ayrıca bkz. [izlenecek yol: basit bir Windows formu oluşturma](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-create-the-form"></a>Form oluşturmak için  
  
1.  Bir boş kod dosyasında aşağıdaki içeri aktarma veya using deyimleri yazın:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2.  Adlı bir sınıf bildirme `Form1` Form sınıfından devralıyor.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3.  İçin varsayılan bir Oluşturucu Oluşturma `Form1`.  
  
     Bir sonraki yordamı oluşturucuda daha fazla kod ekleyeceksiniz.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4.  Ekleme bir `Main` sınıfına yöntemi.  
  
    1.  Uygulama <xref:System.STAThreadAttribute> için `Main` Windows Forms uygulaması belirtmek için yöntemdir bir tek iş parçacıklı.  
  
    2.  Çağrı <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> uygulamanız için bir Windows XP görünüm vermek için.  
  
    3.  Form örneği oluşturun ve çalıştırın.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Uygulamasını derlemek ve çalıştırmak için  
  
1.  .NET Framework komut isteminde, oluşturduğunuz dizine gidin `Form1` sınıfı.  
  
2.  Formun derleyin.  
  
    -   C# kullanıyorsanız yazın:`csc form1.cs`  
  
         `-or-`  
  
    -   Visual Basic kullanıyorsanız, yazın:`vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`  
  
3.  Komut istemine yazın:`Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Denetim ekleme ve bir olay işleme  
 Önceki yordamdaki adımları yalnızca derler ve çalışan temel bir Windows formu oluşturma gösterilmektedir. Sonraki yordam oluşturmak ve forma denetim ekleme ve denetim için bir olay işlemek nasıl yapacağınızı gösterir. Windows Forms'a ekleme yapabilir denetimler hakkında daha fazla bilgi için bkz: [Windows Forms denetimleri](../../../docs/framework/winforms/controls/index.md).  
  
 Windows Forms uygulamaları oluşturmak nasıl anlamanın yanı sıra, olay tabanlı programlama ve kullanıcı girişi nasıl ele alınacağını anlamanız gerekir. Daha fazla bilgi için bkz: [Windows Forms'ta olay işleyicileri oluşturma](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), ve [kullanıcı girişini işleme](../../../docs/framework/winforms/controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Düğme denetimi bildirme ve click olayını işlemek için  
  
1.  Adlı bir düğme denetimi bildirin `button1`.  
  
2.  Oluşturucu, düğme oluşturma ve ayarlama kendi <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> ve <xref:System.Windows.Forms.Control.Text%2A> özellikleri.  
  
3.  Düğme forma ekleyin.  
  
     Aşağıdaki kod örneğinde, düğme denetimi bildirin gösterilmiştir.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4.  İşlemek için bir yöntem oluşturma <xref:System.Windows.Forms.Control.Click> düğme için olay.  
  
5.  Click olay işleyicisi görüntülemek bir <xref:System.Windows.Forms.MessageBox> "Hello World" iletisi.  
  
     Aşağıdaki kod örneğinde düğmesi nasıl ele alınacağını gösteren denetimin, olay'ı tıklatın.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6.  İlişkilendirme <xref:System.Windows.Forms.Control.Click> oluşturduğunuz yöntemiyle olay.  
  
     Aşağıdaki kod örneği, olay yöntemi ile ilişkilendirmek gösterilmiştir.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7.  Derleme ve önceki yordamda açıklandığı şekilde uygulamayı çalıştırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğine, önceki yordamlarda gelen tam örnektir.  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Kodu derlemek için devam etmeden yordamdaki uygulamasını derlemek ve çalıştırmak açıklar yönergeleri izleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Control>  
 [Windows Forms’un Görünüşünü Değiştirme](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 [Windows Forms Uygulamalarını Geliştirme](../../../docs/framework/winforms/advanced/index.md)  
 [Windows Forms'a Başlarken](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
