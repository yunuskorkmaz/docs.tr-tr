---
title: 'Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 9ac98b5c576c065f8944714c72b492539e0d2f05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "61870246"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma
Birçok bileşen, işlerini eşit bir şekilde gerçekleştirme seçeneği sunar. Ve <xref:System.Media.SoundPlayer> <xref:System.Windows.Forms.PictureBox> bileşenleri, örneğin, ana iş parçacığı kesintisiz çalışmaya devam ederken "arka planda" sesleri ve görüntüleri yüklemek için izin.  
  
 [Olay tabanlı Asynchronous Desen Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md) destekleyen bir sınıfta eşzamanlı yöntemler kullanmak, diğer tüm etkinlikte olduğu gibi, bileşenin _MethodName_**Tamamlanan** olayına bir olay işleyicisi eklemek kadar basit olabilir. _MethodName_**Async** yöntemini aradiğinizde, _UygulamaAdı_**Tamamlanan** olay yükseltilene kadar uygulamanız kesintisiz olarak çalışmaya devam edecektir. Olay işleyicinizde, eşzamanlı işlemin <xref:System.ComponentModel.AsyncCompletedEventArgs> başarıyla tamamlanıp tamamlanmadığını veya iptal edilip edilip edilemediğinizi belirlemek için parametreyi inceleyebilirsiniz.  
  
 Olay işleyicilerini kullanma hakkında daha fazla bilgi için [Olay İşleyicilerine Genel Bakış'a](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)bakın.  
  
 Aşağıdaki yordam, bir <xref:System.Windows.Forms.PictureBox> denetimin eşzamanlı görüntü yükleme yeteneğinin nasıl kullanılacağını gösterir.  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>Bir görüntüyü eşit bir şekilde yüklemek için PictureBox denetimini etkinleştirmek için  
  
1. Formunuzda bileşenin <xref:System.Windows.Forms.PictureBox> bir örneğini oluşturun.  
  
2. Olay için bir olay <xref:System.Windows.Forms.PictureBox.LoadCompleted> işleyicisi atayın.  
  
     Burada asynchronous indirme sırasında oluşmuş olabilecek hataları denetleyin. Burası aynı zamanda iptal olup olmadığını kontrol ettiğiniz yerdir.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#5)]  
  
3. Forunuzda iki `loadButton` `cancelLoadButton`düğme ekleyin. İndirme başlatmak ve iptal etmek için olay işleyicileri ekleyin. <xref:System.Windows.Forms.Control.Click>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.PictureBox.LoadAsync/VB/Form1.vb#4)]  
  
4. Başvurunuzu çalıştırın.  
  
     Görüntü indirme ilerledikçe, formu serbestçe taşıyabilir, simge durumuna küçültebilir ve en üst düzeye çıkarabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Arka Planda İşlem Çalıştırma](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
