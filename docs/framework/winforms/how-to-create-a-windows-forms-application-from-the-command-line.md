---
title: Komut satırından Windows Forms uygulaması oluşturma
titleSuffix: ''
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: 7bd3add526a6b60d628b05d46eca22ce407c36b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181980"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Nasıl yapılır: Komut satırından Windows Forms uygulaması oluşturma

Aşağıdaki yordamlar, komut satırından bir Windows Forms uygulaması oluşturmak ve çalıştırmak için tamamlamanız gereken temel adımları açıklar. Visual Studio'da bu prosedürler için kapsamlı bir destek vardır.  Ayrıca [bkz: Walkthrough: WPF'de Windows Formları Denetimi Barındırma.](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-create-the-form"></a>Formu oluşturmak için  
  
1. Boş bir kod dosyasında, `Imports` `using` aşağıdakileri veya ifadeleri yazın:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. Form sınıfından `Form1` devralınan adlandırılmış bir sınıf bildirin:
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. Için `Form1`parametresiz bir oluşturucu oluşturun.
  
     Sonraki yordamda oluşturucuya daha fazla kod eklersiniz.
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. Sınıfa `Main` bir yöntem ekleyin.
  
    1. <xref:System.STAThreadAttribute> Windows Forms uygulamanızın `Main` tek dişli bir daire olduğunu belirtmek için C# yöntemini uygulayın. (Visual Basic ile geliştirilen Windows formları uygulamaları varsayılan olarak tek iş parçacığı daire modeli kullandığından Visual Basic'te öznitelik gerekli değildir.)  
  
    2. Uygulamanız için işletim sistemi stilleri uygulamak için arayın. <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>  
  
    3. Formun bir örneğini oluşturun ve çalıştırın.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Uygulamayı derlemek ve çalıştırmak için  
  
1. .NET Framework komut isteminde, `Form1` sınıfı oluşturduğunuz dizine gidin.  
  
2. Formu derle.  
  
    - C# kullanıyorsanız, yazın:`csc form1.cs`  
  
         `-or-`  
  
    - Visual Basic kullanıyorsanız, yazın:`vbc form1.vb`  
  
3. Komut isteminde, yazın:`Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Denetim ekleme ve olayı işleme

Önceki yordam adımları, derleyen ve çalışan temel bir Windows Formu'nun nasıl oluşturulabildiğini gösterdi. Sonraki yordam, forma nasıl bir denetim oluşturup ekleyeceğiniz ve denetim için bir olayı nasıl işleyeceğiniz gösterecektir. Windows Formlar'a ekleyebileceğiniz denetimler hakkında daha fazla bilgi için [Windows Forms Denetimleri'ne](./controls/index.md)bakın.
  
 Windows Forms uygulamalarının nasıl oluşturulup oluşturulacagın yanı sıra, olay tabanlı programlamayı ve kullanıcı girişini nasıl işleyeceğinizkonusunda da anlamalısınız. Daha fazla bilgi için [Windows Formlarında Olay İşleyicileri Oluşturma](creating-event-handlers-in-windows-forms.md)ve [Kullanıcı Girişi'ni Işleme](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Düğme denetimini bildirmek ve tıklama olayını işlemek için  
  
1. '' adlı `button1`bir düğme denetimi bildirin.  
  
2. Oluşturucuolarak, düğmeyi oluşturun ve <xref:System.Windows.Forms.Control.Size%2A> <xref:System.Windows.Forms.Control.Location%2A> onun <xref:System.Windows.Forms.Control.Text%2A> ve özelliklerini ayarlayın.  
  
3. Düğmeye formun ekleyin.  
  
     Aşağıdaki kod örneği, düğme denetiminin nasıl bildirilen şekli gösterir:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. Düğme için <xref:System.Windows.Forms.Control.Click> olayı işlemek için bir yöntem oluşturun.  
  
5. Tıklama olay işleyicisinde, <xref:System.Windows.Forms.MessageBox> "Merhaba Dünya" iletisiyle bir görüntüle.  
  
     Aşağıdaki kod örneği, düğme denetiminin tıklama olayının nasıl işleyeceğini gösterir:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. <xref:System.Windows.Forms.Control.Click> Olayı oluşturduğunuz yöntemle ilişkilendirin.  
  
     Aşağıdaki kod örneği, olayın yöntemle nasıl ilişkilendirilen gösteriş olduğunu göstermektedir.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. Uygulamayı önceki yordamda açıklandığı şekilde derleyip çalıştırın.  
  
## <a name="example"></a>Örnek  

Aşağıdaki kod örneği önceki yordamlardan tam örnektir:
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [Windows Formlarının Görünüşünü Değiştirme](changing-the-appearance-of-windows-forms.md)
- [Windows Forms Uygulamalarını Geliştirme](./advanced/index.md)
- [Windows Forms'a Başlarken](getting-started-with-windows-forms.md)
