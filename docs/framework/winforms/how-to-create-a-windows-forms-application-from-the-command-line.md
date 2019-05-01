---
title: 'Nasıl yapılır: Komut satırından bir Windows Forms uygulaması oluşturma'
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce97089ec71fc910079910957e784605387f3e06
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966887"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Nasıl yapılır: Komut satırından bir Windows Forms uygulaması oluşturma
Aşağıdaki yordamlar oluşturmak ve komut satırından bir Windows Forms uygulaması çalıştırmak için tamamlamanız gereken temel adımlarda açıklar. Visual Studio'da bu yordamları için kapsamlı desteği yoktur.  Ayrıca bkz: [izlenecek yol: WPF içinde Forms Denetimi'ne bir Windows barındırma](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-create-the-form"></a>Form oluşturma  
  
1. Bir boş bir kod dosyasında, aşağıdaki içeri aktarma veya using deyimlerini yazın:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. Adlı bir sınıf bildirme `Form1` Form sınıfından devralır.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. İçin varsayılan oluşturucu oluşturma `Form1`.  
  
     Bir sonraki yordamda Oluşturucusu daha fazla kod ekleyeceksiniz.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. Ekleme bir `Main` sınıfı için yöntemi.  
  
    1. Uygulama <xref:System.STAThreadAttribute> C# `Main` yöntemi, Windows Forms uygulamasının adını belirtin tek kullanımlık apartman. (Windows forms uygulamaları Visual Basic ile kullanılacak tek kullanımlık apartman modeli varsayılan olarak geliştirilen beri öznitelik Visual Basic'te, gerekli değildir.)  
  
    2. Çağrı <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> uygulamanıza işletim sistemi stilleri uygulamak için.  
  
    3. Form örneği oluşturun ve çalıştırın.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Derlemek ve uygulamayı çalıştırmak için  
  
1. .NET Framework komut isteminde, oluşturduğunuz dizine gidin `Form1` sınıfı.  
  
2. Form derleyin.  
  
    - C# kullanıyorsanız yazın: `csc form1.cs`  
  
         `-or-`  
  
    - Visual Basic kullanıyorsanız yazın: `vbc form1.vb`  
  
3. Komut isteminde aşağıdakini yazın: `Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Denetim ekleme ve bir olay işleme  
 Önceki yordamdaki adımları yalnızca derleyen ve çalışan temel bir Windows Form oluşturma gösterilmektedir. Sonraki yordam oluşturmak ve forma denetim ekleme ve denetim için bir olayı işlemek nasıl gösterir. Windows Forms ekleyebileceğiniz denetimler hakkında daha fazla bilgi için bkz. [Windows Forms denetimleri](./controls/index.md).  
  
 Windows Forms uygulamalarının nasıl oluşturulacağını anlamanın yanı sıra, olay tabanlı programlama ve kullanıcı girişini işlemek nasıl anlamanız gerekir. Daha fazla bilgi için [Windows Forms'ta olay işleyicileri oluşturma](creating-event-handlers-in-windows-forms.md), ve [kullanıcı girişini işleme](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Bir düğme denetimi bildirmek ve bunun tıklama olayı işlemek için  
  
1. Adlı bir düğme denetimi bildirin `button1`.  
  
2. Oluşturucu, düğmeyi oluşturmak ve ayarlamak kendi <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> ve <xref:System.Windows.Forms.Control.Text%2A> özellikleri.  
  
3. Forma düğme ekleyin.  
  
     Aşağıdaki kod örneği, düğme denetimini nasıl gösterir.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. İşlemek için bir yöntem oluşturma <xref:System.Windows.Forms.Control.Click> düğmesi için olay.  
  
5. Click olay işleyicisi, görüntüleme bir <xref:System.Windows.Forms.MessageBox> "Hello World" iletisini ile.  
  
     Aşağıdaki kod örneği, düğmeyi işlemek gösterilmiştir denetimin olay'ı tıklatın.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. İlişkilendirme <xref:System.Windows.Forms.Control.Click> oluşturduğunuz yöntemiyle olay.  
  
     Aşağıdaki kod örneği, olay yöntemi ile ilişkilendirilecek gösterilmiştir.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. Derleme ve önceki yordamda açıklanan şekilde uygulamayı çalıştırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğine, önceki yordamlarda gelen tam örnektir.  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Kodu derlemek için derlemek ve uygulamayı çalıştırmak nasıl açıklayan devam etmeden yordam yönergeleri izleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [Windows Forms’un Görünüşünü Değiştirme](changing-the-appearance-of-windows-forms.md)
- [Windows Forms Uygulamalarını Geliştirme](./advanced/index.md)
- [Windows Forms'a Başlarken](getting-started-with-windows-forms.md)
