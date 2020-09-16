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
ms.openlocfilehash: c41a695226068615efca5132985e50503060148b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555672"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a>Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma
Birçok bileşen, işlerini zaman uyumsuz gerçekleştirme seçeneğini sağlar. <xref:System.Media.SoundPlayer>Ve <xref:System.Windows.Forms.PictureBox> bileşenleri, örneğin, ana iş parçacığlarınız kesintiye uğramadan çalışmaya devam ederken, "arka planda" sesler ve görüntüler yüklemeye olanak sağlar.  
  
 [Olay tabanlı zaman uyumsuz model genel bakışını](event-based-asynchronous-pattern-overview.md) destekleyen bir sınıfta zaman uyumsuz yöntemlerin kullanılması, diğer herhangi bir olay için yaptığınız gibi bileşenin _MethodName_**tamamlandı** olayına bir olay işleyicisi eklemek kadar basit olabilir. _MethodName_**zaman uyumsuz** yöntemini çağırdığınızda, uygulamanız _MethodName_**tamamlandı** olayı harekete gelinceye kadar kesintiye uğramadan çalışmaya devam edecektir. Olay işleyicinizde, <xref:System.ComponentModel.AsyncCompletedEventArgs> zaman uyumsuz işlemin başarıyla tamamlanıp tamamlanmadığını veya iptal edilip edilmediğine ilişkin parametreyi inceleyebilirsiniz.  
  
 Olay işleyicilerini kullanma hakkında daha fazla bilgi için bkz. [olay Işleyicilerine genel bakış](/dotnet/desktop/winforms/event-handlers-overview-windows-forms).  
  
 Aşağıdaki yordamda, bir denetimin zaman uyumsuz görüntü yükleme yeteneğinin nasıl kullanılacağı gösterilmektedir <xref:System.Windows.Forms.PictureBox> .  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a>PictureBox denetimini bir görüntüyü zaman uyumsuz olarak yüklemek üzere etkinleştirmek için  
  
1. Formunuzda bileşenin bir örneğini oluşturun <xref:System.Windows.Forms.PictureBox> .  
  
2. Olaya bir olay işleyicisi atayın <xref:System.Windows.Forms.PictureBox.LoadCompleted> .  
  
     Zaman uyumsuz indirme sırasında oluşmuş olabilecek hataları kontrol edin. Ayrıca, iptal için kontrol ettiğiniz yerdir.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#5)]  
  
3. Formunuza ve olarak adlandırılan iki düğme ekleyin `loadButton` `cancelLoadButton` . <xref:System.Windows.Forms.Control.Click>Başlamak için olay işleyicileri ekleyin ve indirmeyi iptal edin.  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#4)]  
  
4. Uygulamanızı çalıştırın.  
  
     Görüntü indirme işlemi devam ettikçe formu serbestçe taşıyabilir, simge durumuna küçültebilir ve en üst düzeye çıkarabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Arka Planda İşlem Çalıştırma](/dotnet/desktop/winforms/controls/how-to-run-an-operation-in-the-background)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](event-based-asynchronous-pattern-overview.md)
