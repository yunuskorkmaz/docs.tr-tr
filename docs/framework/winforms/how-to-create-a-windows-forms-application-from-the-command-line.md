---
title: 'Nasıl yapılır: komut satırından Windows Forms uygulaması oluşturma'
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
ms.openlocfilehash: da7fdab1cf67ffd47acb75533fcfdb89664c86d3
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834815"
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a>Nasıl yapılır: komut satırından Windows Forms uygulaması oluşturma

Aşağıdaki yordamlarda, komut satırından bir Windows Forms uygulaması oluşturmak ve çalıştırmak için gerçekleştirmeniz gereken temel adımlar açıklanır. Visual Studio 'da Bu yordamlar için kapsamlı destek vardır.  Ayrıca bkz. [Izlenecek yol: WPF 'de Windows Forms denetimi barındırma](../wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md).
  
## <a name="procedure"></a>Yordam  
  
#### <a name="to-create-the-form"></a>Formu oluşturmak için  
  
1. Boş bir kod dosyasında aşağıdaki `Imports` veya `using` deyimlerini yazın:  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2. Form sınıfından devralan `Form1` adlı bir sınıf bildirin:
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3. @No__t-0 için parametresiz Oluşturucu oluşturun.
  
     Sonraki yordamda oluşturucuya daha fazla kod ekleyeceksiniz.
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4. Sınıfa `Main` yöntemi ekleyin.
  
    1. Windows Forms uygulamanızın tek iş parçacıklı bir grup C# olduğunu belirtmek için `Main` yöntemine <xref:System.STAThreadAttribute> uygulayın. (Visual Basic ile geliştirilen Windows Forms uygulamaları varsayılan olarak tek iş parçacıklı bir Grup modeli kullandığından, bu öznitelik Visual Basic için gerekli değildir.)  
  
    2. Uygulamanıza işletim sistemi stilleri uygulamak için <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> çağrısı yapın.  
  
    3. Formun bir örneğini oluşturun ve çalıştırın.  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a>Uygulamayı derlemek ve çalıştırmak için  
  
1. .NET Framework komut isteminde, `Form1` sınıfını oluşturduğunuz dizine gidin.  
  
2. Formu derleyin.  
  
    - Kullanıyorsanız C#, şunu yazın: `csc form1.cs`  
  
         `-or-`  
  
    - Visual Basic kullanıyorsanız, şunu yazın: `vbc form1.vb`  
  
3. Komut istemine şunu yazın: `Form1.exe`  
  
## <a name="adding-a-control-and-handling-an-event"></a>Bir denetim ekleme ve olay işleme

Önceki yordam adımları, derlenen ve çalışan basit bir Windows formu oluşturmayı gösteren bir adım. Sonraki yordamda, form üzerinde bir denetim oluşturma ve ekleme ve denetim için bir olay işleme işlemi gösterilir. Windows Forms ekleyebileceğiniz denetimler hakkında daha fazla bilgi için bkz. [Windows Forms denetimleri](./controls/index.md).
  
 Windows Forms uygulamalarının nasıl oluşturulacağını anlamanın yanı sıra, olay tabanlı programlamayı ve Kullanıcı girişini nasıl işleyeceğinizi anlamanız gerekir. Daha fazla bilgi için bkz. [Windows Forms olay Işleyicileri oluşturma](creating-event-handlers-in-windows-forms.md)ve [Kullanıcı girişini işleme](./controls/handling-user-input.md)  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a>Düğme denetimi bildirmek ve Click olayını işlemek için  
  
1. @No__t-0 adlı bir düğme denetimi bildirin.  
  
2. Oluşturucuda, düğmeyi oluşturun ve <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> ve <xref:System.Windows.Forms.Control.Text%2A> özelliklerini ayarlayın.  
  
3. Forma düğme ekleyin.  
  
     Aşağıdaki kod örneği, düğme denetiminin nasıl bildirileceğini göstermektedir:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4. Düğme için <xref:System.Windows.Forms.Control.Click> olayını işlemek üzere bir yöntem oluşturun.  
  
5. Click olay işleyicisinde, "Merhaba Dünya" iletisiyle birlikte <xref:System.Windows.Forms.MessageBox> ' ı görüntüleyin.  
  
     Aşağıdaki kod örneği, düğme denetiminin Click olayının nasıl işleneceğini göstermektedir:
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6. @No__t-0 olayını, oluşturduğunuz yöntemle ilişkilendirin.  
  
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
- [Windows Forms’un Görünüşünü Değiştirme](changing-the-appearance-of-windows-forms.md)
- [Windows Forms Uygulamalarını Geliştirme](./advanced/index.md)
- [Windows Forms'a Başlarken](getting-started-with-windows-forms.md)
