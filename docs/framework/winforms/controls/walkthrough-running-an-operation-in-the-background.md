---
title: "İzlenecek yol: Arka Planda İşlem Çalıştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: de485eb0b9c67ee9c3c897b6521971f50aaf751c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-running-an-operation-in-the-background"></a>İzlenecek yol: Arka Planda İşlem Çalıştırma
Tamamlanması uzun zaman alacağı işleme sahip ve kullanıcı arabiriminde gecikmelere neden istemediğiniz, kullanabileceğiniz <xref:System.ComponentModel.BackgroundWorker> işlemi başka bir iş parçacığında çalıştırmak için sınıf.  
  
 Bu örnekte kullanılan kod tam listesi için bkz: [nasıl yapılır: bir işlemi arka planda çalışan](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-run-an-operation-in-the-background"></a>Bir işlemi arka planda çalıştırmak için  
  
1.  Windows Forms Tasarımcısı'nda etkin formun ile iki <xref:System.Windows.Forms.Button> gelen denetler **araç** form olarak ayarlayın ve ardından için `Name` ve <xref:System.Windows.Forms.Control.Text%2A> aşağıdaki tabloya göre düğmelerin özelliklerini.  
  
    |Düğme|Ad|Metin|  
    |------------|----------|----------|  
    |`button1`|`startBtn`|**Başlat**|  
    |`button2`|`cancelBtn`|**İptal**|  
  
2.  Açık **araç**, tıklatın **bileşenleri** sekmesini tıklatın ve ardından sürükleyin <xref:System.ComponentModel.BackgroundWorker> formunuza bileşen.  
  
     `backgroundWorker1` Bileşen görünür **bileşen**.  
  
3.  İçinde **özellikleri** penceresindeki ayarlayın <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliğine `true`.  
  
4.  İçinde **özellikleri** penceresinde tıklatın **olayları** düğmesine tıklayın ve ardından <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olayları olay işleyicileri oluşturma.  
  
5.  Uzun süren kodunuza eklemek <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi.  
  
6.  İşlemi gerektirdiği herhangi bir parametre ayıklamak <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> özelliği <xref:System.ComponentModel.DoWorkEventArgs> parametresi.  
  
7.  Hesaplama sonucu atamak <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> özelliği <xref:System.ComponentModel.DoWorkEventArgs>.  
  
     Bu olacak olan kullanılabilir <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay işleyicisi.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8.  İşlemin sonucunu almak için kod ekleme <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay işleyicisi.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. Uygulama `TimeConsumingOperation` yöntemi.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. Windows Forms Tasarımcısı'nda çift `startButton` oluşturmak için <xref:System.Windows.Forms.Control.Click> olay işleyicisi.  
  
11. Çağrı <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> yönteminde <xref:System.Windows.Forms.Control.Click> için olay işleyicisini `startButton`.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. Windows Forms Tasarımcısı'nda çift `cancelButton` oluşturmak için <xref:System.Windows.Forms.Control.Click> olay işleyicisi.  
  
13. Çağrı <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> yönteminde <xref:System.Windows.Forms.Control.Click> için olay işleyicisini `cancelButton`.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. Dosyanın üst kısmında, System.ComponentModel ve System.Threading ad içeri aktarın.  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. Çözümü derlemek için F6 tuşuna basın ve hata ayıklayıcı dışında uygulamayı çalıştırmak için CTRL-F5 tuşuna basın.  
  
> [!NOTE]
>  Hata ayıklayıcı altında uygulamayı çalıştırmak için F5 tuşuna basarsanız, özel durum oluşturuldu `TimeConsumingOperation` yöntemi yakalanan ve hata ayıklayıcı tarafından görüntülenir. Hata ayıklayıcı dışında uygulamayı çalıştırdığınızda <xref:System.ComponentModel.BackgroundWorker> özel durumu işler ve içinde önbelleğe <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> özelliği <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.  
  
1.  Tıklatın **Başlat** zaman uyumsuz bir işlem çalıştırmak için düğmesine tıklayın ve ardından **iptal** çalışan zaman uyumsuz işlemi durdurmak için düğmesi.  
  
     Her bir işlemin sonucunu görüntülenen bir <xref:System.Windows.Forms.MessageBox>.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
  
-   Zaman uyumsuz bir işlem devam ettikçe ilerleme raporları bir form uygulayın. Daha fazla bilgi için bkz: [nasıl yapılır: bir arka plan işlemi kullanan bir Form uygulama](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
-   Bileşenleri için zaman uyumsuz deseni destekleyen bir sınıf uygulama. Daha fazla bilgi için bkz: [olay tabanlı zaman uyumsuz deseni uygulama](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [Nasıl yapılır: bir arka plan işlemi kullanan bir Form uygulama](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Nasıl yapılır: bir işlemi arka planda çalıştırma](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [BackgroundWorker bileşeni](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
