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
ms.openlocfilehash: 6c87419a4d730f72a7ee15fcc3127781a8eaff75
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364220"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Nasıl yapılır: Komut satırından bir Windows Forms uygulaması oluşturma
Aşağıdaki yordamlarda, komut satırından bir Windows Forms uygulaması oluşturmak ve çalıştırmak için gerçekleştirmeniz gereken temel adımlar açıklanır. Visual Studio 'da Bu yordamlar için kapsamlı destek vardır.  Ayrıca bkz [. İzlenecek yol: WPF](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)'de Windows Forms denetimini barındırma.  
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-create-the-form"></a>Formu oluşturmak için  
  
1. Boş bir kod dosyasında aşağıdaki içeri aktarma veya using deyimlerini yazın:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. Form sınıfından devralan adlı `Form1` bir sınıf bildirin.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. İçin `Form1`parametresiz bir Oluşturucu oluşturun.  
  
     Sonraki yordamda oluşturucuya daha fazla kod ekleyeceksiniz.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. Sınıfına bir `Main` yöntem ekleyin.  
  
    1. C# tek iş parçacıklı bir grup olduğunu belirtmek için yöntemine`Main`uygulayın. <xref:System.STAThreadAttribute> (Visual Basic ile geliştirilen Windows Forms uygulamaları varsayılan olarak tek iş parçacıklı bir Grup modeli kullandığından, bu öznitelik Visual Basic için gerekli değildir.)  
  
    2. Uygulamanıza <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> işletim sistemi stilleri uygulamak için çağırın.  
  
    3. Formun bir örneğini oluşturun ve çalıştırın.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Uygulamayı derlemek ve çalıştırmak için  
  
1. .NET Framework komut isteminde, `Form1` sınıfı oluşturduğunuz dizine gidin.  
  
2. Formu derleyin.  
  
    - Kullanıyorsanız C#, şunu yazın:`csc form1.cs`  
  
         `-or-`  
  
    - Visual Basic kullanıyorsanız şunu yazın:`vbc form1.vb`  
  
3. Komut isteminde şunu yazın:`Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Bir denetim ekleme ve olay Işleme  
 Önceki yordam adımları, derlenen ve çalışan basit bir Windows formu oluşturmayı gösteren bir adım. Sonraki yordamda, form üzerinde bir denetim oluşturma ve ekleme ve denetim için bir olay işleme işlemi gösterilir. Windows Forms ekleyebileceğiniz denetimler hakkında daha fazla bilgi için bkz. [Windows Forms denetimleri](./controls/index.md).  
  
 Windows Forms uygulamalarının nasıl oluşturulacağını anlamanın yanı sıra, olay tabanlı programlamayı ve Kullanıcı girişini nasıl işleyeceğinizi anlamanız gerekir. Daha fazla bilgi için bkz. [Windows Forms olay Işleyicileri oluşturma](creating-event-handlers-in-windows-forms.md)ve [Kullanıcı girişini işleme](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Düğme denetimi bildirmek ve Click olayını işlemek için  
  
1. Adlı `button1`bir düğme denetimi bildirin.  
  
2. Oluşturucuda, düğmeyi oluşturun ve <xref:System.Windows.Forms.Control.Size%2A> <xref:System.Windows.Forms.Control.Location%2A> ve <xref:System.Windows.Forms.Control.Text%2A> özelliklerini ayarlayın.  
  
3. Forma düğme ekleyin.  
  
     Aşağıdaki kod örneğinde, düğme denetiminin nasıl bildirildiği gösterilmektedir.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. Düğmenin <xref:System.Windows.Forms.Control.Click> olayını işlemek için bir yöntem oluşturun.  
  
5. Click olay işleyicisinde, "Merhaba Dünya" iletisiyle <xref:System.Windows.Forms.MessageBox> bir ileti görüntüler.  
  
     Aşağıdaki kod örneği, düğme denetiminin Click olayının nasıl işleneceğini gösterir.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. Olayı, <xref:System.Windows.Forms.Control.Click> oluşturduğunuz yöntemle ilişkilendirin.  
  
     Aşağıdaki kod örneği, olayının yöntemiyle nasıl ilişkilendirileceğini gösterir.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. Önceki yordamda açıklandığı gibi uygulamayı derleyin ve çalıştırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, önceki yordamlardan alınan bütün örnektir.  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [Windows Forms’un Görünüşünü Değiştirme](changing-the-appearance-of-windows-forms.md)
- [Windows Forms Uygulamalarını Geliştirme](./advanced/index.md)
- [Windows Forms'a Başlarken](getting-started-with-windows-forms.md)
