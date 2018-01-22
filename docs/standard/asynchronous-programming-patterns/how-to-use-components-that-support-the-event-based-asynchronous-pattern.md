---
title: "Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c7fe7d0a959a490893fba2b2fc7faceedee03879
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma
Birçok bileşen işlerine zaman uyumsuz olarak gerçekleştirme seçeneğini içeren sağlar. <xref:System.Media.SoundPlayer> Ve <xref:System.Windows.Forms.PictureBox> bileşenleri, örneğin, yüklemek için ses ve, ana iş parçacığı kesinti olmadan çalışmaya devam ederken "arka planda" görüntüleri etkinleştir.  
  
 Zaman uyumsuz yöntemleri destekleyen bir sınıf kullanarak [olay tabanlı zaman uyumsuz desene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) bileşenin olay işleyicisi ekleme olarak kadar basit olabilir *MethodName *** tamamlandı** olayı herhangi bir olay için yaptığınız gibi. Çağırdığınızda *MethodName *** zaman uyumsuz** yöntemi, uygulamanız çalışmaya devam eder kadar kesintisiz *MethodName *** tamamlandı** olayı oluşturulur. Olay işleyicisi incelemeniz <xref:System.ComponentModel.AsyncCompletedEventArgs> zaman uyumsuz işlemi başarıyla tamamlandı veya iptal edildi belirlemek için parametre.  
  
 Olay işleyicileri kullanma hakkında daha fazla bilgi için bkz: [olay işleyicilerine genel bakış](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md).  
  
 Aşağıdaki yordam zaman uyumsuz resim yükleme yeteneğini kullanmayı gösterir bir <xref:System.Windows.Forms.PictureBox> denetim.  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>Zaman uyumsuz olarak bir görüntü yüklemek PictureBox denetimi etkinleştirmek için  
  
1.  Bir örneğini oluşturmak <xref:System.Windows.Forms.PictureBox> formunuzda bileşen.  
  
2.  Bir olay işleyicisi atamak <xref:System.Windows.Forms.PictureBox.LoadCompleted> olay.  
  
     Zaman uyumsuz indirme sırasında oluşmuş olabilecek hataları denetleyin. Burada iptalleri denetlemek budur.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3.  Adlı iki düğme ekleme `loadButton` ve `cancelLoadButton`, formunuza. Ekleme <xref:System.Windows.Forms.Control.Click> başlatmak ve yüklemeyi iptal etmek için olay işleyicileri.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4.  Uygulamanızı çalıştırın.  
  
     Görüntü yükleme devam ettikçe formun serbestçe hareket, simge durumuna küçültün ve onu en üst düzeye çıkarmak.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır: Arka Planda İşlem Çalıştırma](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [IN derleme değil: Visual Basic'te çoklu iş parçacığı kullanımı](http://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)
