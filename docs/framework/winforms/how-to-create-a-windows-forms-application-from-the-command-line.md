---
title: Komut satırından bir Windows Forms uygulaması oluşturma
titleSuffix: ''
description: Komut satırından bir Windows Forms uygulaması oluşturmak ve çalıştırmak için temel adımları tamamlamayı öğrenin.
ms.date: 03/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
ms.openlocfilehash: b63bf884b9fd03a0510c7f240f19d7a14196971a
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903460"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Nasıl yapılır: komut satırından Windows Forms uygulaması oluşturma

Aşağıdaki yordamlarda, komut satırından bir Windows Forms uygulaması oluşturmak ve çalıştırmak için gerçekleştirmeniz gereken temel adımlar açıklanır. Visual Studio 'da Bu yordamlar için kapsamlı destek vardır.  Ayrıca bkz. [Izlenecek yol: WPF 'de Windows Forms denetimi barındırma](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-create-the-form"></a>Formu oluşturmak için  
  
1. Boş bir kod dosyasında aşağıdaki `Imports` veya `using` deyimlerini yazın:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. Form sınıfından devralan adlı bir sınıf bildirin `Form1` :
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. İçin parametresiz bir Oluşturucu oluşturun `Form1` .
  
     Sonraki yordamda oluşturucuya daha fazla kod ekleyeceksiniz.
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. Sınıfına bir `Main` Yöntem ekleyin.
  
    1. <xref:System.STAThreadAttribute> `Main` Windows Forms uygulamanızın tek iş parçacıklı bir grup olduğunu belirtmek için C# yöntemine uygulayın. (Visual Basic ile geliştirilen Windows Forms uygulamaları varsayılan olarak tek iş parçacıklı bir Grup modeli kullandığından, bu öznitelik Visual Basic için gerekli değildir.)  
  
    2. <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>Uygulamanıza işletim sistemi stilleri uygulamak için çağırın.  
  
    3. Formun bir örneğini oluşturun ve çalıştırın.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Uygulamayı derlemek ve çalıştırmak için  
  
1. .NET Framework komut isteminde, sınıfı oluşturduğunuz dizine gidin `Form1` .  
  
2. Formu derleyin.  
  
    - C# kullanıyorsanız şunu yazın:`csc form1.cs`  
  
         `-or-`  
  
    - Visual Basic kullanıyorsanız şunu yazın:`vbc form1.vb`  
  
3. Komut isteminde şunu yazın:`Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Bir denetim ekleme ve olay işleme

Önceki yordam adımları, derlenen ve çalışan basit bir Windows formu oluşturmayı gösteren bir adım. Sonraki yordamda, form üzerinde bir denetim oluşturma ve ekleme ve denetim için bir olay işleme işlemi gösterilir. Windows Forms ekleyebileceğiniz denetimler hakkında daha fazla bilgi için bkz. [Windows Forms denetimleri](./controls/index.md).
  
 Windows Forms uygulamalarının nasıl oluşturulacağını anlamanın yanı sıra, olay tabanlı programlamayı ve Kullanıcı girişini nasıl işleyeceğinizi anlamanız gerekir. Daha fazla bilgi için bkz. [Windows Forms olay Işleyicileri oluşturma](creating-event-handlers-in-windows-forms.md)ve [Kullanıcı girişini işleme](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Düğme denetimi bildirmek ve Click olayını işlemek için  
  
1. Adlı bir düğme denetimi bildirin `button1` .  
  
2. Oluşturucuda, düğmeyi oluşturun ve <xref:System.Windows.Forms.Control.Size%2A> <xref:System.Windows.Forms.Control.Location%2A> ve <xref:System.Windows.Forms.Control.Text%2A> özelliklerini ayarlayın.  
  
3. Forma düğme ekleyin.  
  
     Aşağıdaki kod örneği, düğme denetiminin nasıl bildirileceğini göstermektedir:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. Düğmenin olayını işlemek için bir yöntem oluşturun <xref:System.Windows.Forms.Control.Click> .  
  
5. Click olay işleyicisinde, <xref:System.Windows.Forms.MessageBox> "Merhaba Dünya" iletisiyle bir ileti görüntüler.  
  
     Aşağıdaki kod örneği, düğme denetiminin Click olayının nasıl işleneceğini göstermektedir:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. Olayı, <xref:System.Windows.Forms.Control.Click> oluşturduğunuz yöntemle ilişkilendirin.  
  
     Aşağıdaki kod örneği, olayının yöntemiyle nasıl ilişkilendirileceğini gösterir.  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7. Önceki yordamda açıklandığı gibi uygulamayı derleyin ve çalıştırın.  
  
## <a name="example"></a>Örnek  

Aşağıdaki kod örneği, önceki yordamlardan alınan tüm örnektir:
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Control>
- [Windows Formlarının Görünüşünü Değiştirme](changing-the-appearance-of-windows-forms.md)
- [Windows Forms Uygulamalarını Geliştirme](./advanced/index.md)
- [Windows Forms'a Başlarken](getting-started-with-windows-forms.md)
