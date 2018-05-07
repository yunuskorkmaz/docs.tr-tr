---
title: 'İzlenecek yol: Arka Plan İşlemi Kullanan Bir Form Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- threading [Windows Forms], walkthroughs
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 4691b796-9200-471a-89c3-ba4c7cc78c03
ms.openlocfilehash: 28b1ac924fb9b6b8cbc09db62ee33c6780bee820
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-implementing-a-form-that-uses-a-background-operation"></a>İzlenecek yol: Arka Plan İşlemi Kullanan Bir Form Uygulama
Tamamlanması uzun zaman yapacağı bir işlem varsa ve kullanıcı arabirimi (UI) yanıt vermemesine istediğiniz değil veya "askıda" kullanabileceğiniz <xref:System.ComponentModel.BackgroundWorker> başka bir iş parçacığı üzerindeki işlemi yürütmek için sınıf.  
  
 Bu kılavuzda nasıl kullanılacağını anlatan <xref:System.ComponentModel.BackgroundWorker> "" arka planda zaman hesaplamalar için sınıf kullanıcı arabiriminin yanıt verebilir durumda kalırken.  Aracılığıyla olduğunda Fibonacci numaraları zaman uyumsuz olarak hesaplar bir uygulamaya sahip olursunuz. Fibonacci sayıda belirgin bir süre alabilir bilgisayar olsa da, ana kullanıcı Arabirimi iş parçacığı tarafından bu gecikme kesilmez ve form hesaplama sırasında yanıt verebilir durumda olacaktır.  
  
 Bu örneklerde gösterilen görevler aşağıdakileri içerir:  
  
-   Windows tabanlı bir uygulama oluşturma  
  
-   Oluşturma bir <xref:System.ComponentModel.BackgroundWorker> formunuzda  
  
-   Zaman uyumsuz olay işleyicileri ekleme  
  
-   İlerleme durumu raporlama ve iptal etme desteği ekleme  
  
 Bu örnekte kullanılan kod tam listesi için bkz: [nasıl yapılır: bir arka plan işlemi kullanan bir Form uygulama](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Projeyi Oluşturma  
 İlk adım, projeyi oluşturmak ve formu ayarlamak için ' dir.  
  
#### <a name="to-create-a-form-that-uses-a-background-operation"></a>Arka plan işlemi kullanan bir form oluşturmak için  
  
1.  Adlı bir Windows tabanlı bir uygulama projesi oluşturun `BackgroundWorkerExample`. Ayrıntılar için bkz [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  İçinde **Çözüm Gezgini**, sağ **Form1** seçip **yeniden adlandırma** kısayol menüsünden. Dosya adını değiştirmek `FibonacciCalculator`. Tıklatın **Evet** düğmesini tüm başvurularını kod öğesini yeniden adlandırmak istediğiniz sorulduğunda '`Form1`'.  
  
3.  Sürükleme bir <xref:System.Windows.Forms.NumericUpDown> gelen denetim **araç** forma. Ayarlama <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> özelliğine `1` ve <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> özelliğine `91`.  
  
4.  İki eklemek <xref:System.Windows.Forms.Button> formu denetimleri.  
  
5.  İlk yeniden adlandırma <xref:System.Windows.Forms.Button> denetim `startAsyncButton` ve <xref:System.Windows.Forms.Control.Text%2A> özelliğine `Start Async`. İkinci yeniden adlandırma <xref:System.Windows.Forms.Button> denetim `cancelAsyncButton`ve <xref:System.Windows.Forms.Control.Text%2A> özelliğine `Cancel Async`. Ayarlama, <xref:System.Windows.Forms.Control.Enabled%2A> özelliğine `false`.  
  
6.  Her iki için bir olay işleyicisi oluşturun <xref:System.Windows.Forms.Button> denetimleri <xref:System.Windows.Forms.Control.Click> olaylar. Ayrıntılar için bkz [nasıl yapılır: olay işleyicileri kullanarak Tasarımcı](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
7.  Sürükleme bir <xref:System.Windows.Forms.Label> gelen denetim **araç** forma ve yeniden adlandırmak `resultLabel`.  
  
8.  Sürükleme bir <xref:System.Windows.Forms.ProgressBar> gelen denetim **araç** forma.  
  
## <a name="creating-a-backgroundworker-in-your-form"></a>Bir BackgroundWorker formunuzda oluşturma  
 Oluşturabileceğiniz <xref:System.ComponentModel.BackgroundWorker> kullanarak zaman uyumsuz işlemi için **Windows** **Forms Tasarımcısı**.  
  
#### <a name="to-create-a-backgroundworker-with-the-designer"></a>Bir BackgroundWorker Tasarımcısı ile oluşturmak için  
  
-   Gelen **bileşenleri** sekmesinde **araç**, sürükleyin bir <xref:System.ComponentModel.BackgroundWorker> forma.  
  
## <a name="adding-asynchronous-event-handlers"></a>Zaman uyumsuz olay işleyicileri ekleme  
 Olay işleyicileri eklemek artık hazırsınız <xref:System.ComponentModel.BackgroundWorker> bileşenin zaman uyumsuz olayları. Fibonacci numaraları hesaplar, arka planda çalışır uzun süren işlem bu olay işleyicileri biri tarafından çağrılır.  
  
#### <a name="to-implement-asynchronous-event-handlers"></a>Zaman uyumsuz olay işleyicileri uygulamak için  
  
1.  İçinde **özellikleri** penceresinde ile <xref:System.ComponentModel.BackgroundWorker> halen seçiliyken, bileşeni tıklatın **olayları** düğmesi. Çift <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olayları olay işleyicileri oluşturma. Olay işleyicileri kullanma hakkında daha fazla bilgi için bkz: [nasıl yapılır: oluşturmak olay işleyicilerini kullanarak Tasarımcı](http://msdn.microsoft.com/library/8461e9b8-14e8-406f-936e-3726732b23d2).  
  
2.  Adlı yeni bir yöntem oluşturma `ComputeFibonacci`, formunuzda. Bu yöntem asıl işi yapar ve arka planda çalışır. Bu kod, büyük sayılar için tamamlamak için katlanarak uzun zaman ayırdığınız özellikle verimsiz Fibonacci algoritmayı özyinelemeli uyarlamasını gösterir. Bunu burada, tanımlayıcı amaçlarla gecikmelere uygulamanızda getirebilir bir işlem göstermek için kullanılır.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]  
  
3.  İçinde <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi için bir çağrı ekleyin `ComputeFibonacci` yöntemi. İlk parametre alması `ComputeFibonacci` gelen <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> özelliği <xref:System.ComponentModel.DoWorkEventArgs>. <xref:System.ComponentModel.BackgroundWorker> Ve <xref:System.ComponentModel.DoWorkEventArgs> parametreleri kullanılacak daha sonra ilerleme durumunu raporlamak ve iptal için destek. Yönteminden döndürülen değer atamak `ComputeFibonacci` için <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> özelliği <xref:System.ComponentModel.DoWorkEventArgs>. Bu sonuç kullanılabilir <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay işleyicisi.  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BackgroundWorker.DoWork> Olay işleyicisi başvurmuyor `backgroundWorker1` örnek değişkeni doğrudan bu belirli bir örneği için bu olay işleyicisi eşleştiği gibi <xref:System.ComponentModel.BackgroundWorker>. Bunun yerine, bir başvuru <xref:System.ComponentModel.BackgroundWorker> bu oluşturuldu olay kurtarılan `sender` parametresi. Formun birden fazla barındırdığında bu önemlidir <xref:System.ComponentModel.BackgroundWorker>. Tüm kullanıcı arabirimi nesneleri değiştiremez önemlidir, <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi. Bunun yerine, kullanıcı arabirimi aracılığıyla iletişim kurar <xref:System.ComponentModel.BackgroundWorker> olaylar.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
4.  İçinde `startAsyncButton` denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi, zaman uyumsuz işlemi başlatır kodu ekleyin.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]  
  
5.  İçinde <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay işleyicisi için hesaplamanın sonucu atamak `resultLabel` denetim.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]  
  
## <a name="adding-progress-reporting-and-support-for-cancellation"></a>İlerleme durumu raporlama ve iptal etme desteği ekleme  
 Uzun sürmesi zaman uyumsuz işlemleri için çoğunlukla rapor ilerleme kullanıcıya ve kullanıcı işlemi iptal etmek izin vermek için iyi bir şeydir. <xref:System.ComponentModel.BackgroundWorker> Sınıfı, arka plan işlemi devam eder ilerleme göndermeye izin veren bir olay sağlar. Ayrıca bir çağrı algılamak çalışan kodunuzu izin veren bir bayrak sağlar <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> ve kendisini kesme.  
  
#### <a name="to-implement-progress-reporting"></a>İlerleme durumu raporlama uygulamak için  
  
1.  İçinde **özellikleri**, penceresinde, seçin `backgroundWorker1`. <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerini `true` olarak ayarlayın.  
  
2.  İki değişken bildirin `FibonacciCalculator` formu. Bunlar, ilerleme durumunu izlemek için kullanılır.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]  
  
3.  Bir olay işleyicisi ekleme <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay. İçinde <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay işleyicisi, güncelleştirme <xref:System.Windows.Forms.ProgressBar> ile <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> özelliği <xref:System.ComponentModel.ProgressChangedEventArgs> parametresi.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]  
  
#### <a name="to-implement-support-for-cancellation"></a>İptal etme desteği uygulamak için  
  
1.  İçinde `cancelAsyncButton` denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi, zaman uyumsuz işlemi iptal kodu ekleyin.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]  
  
2.  Aşağıdaki kod parça `ComputeFibonacci` yöntemi rapor ilerleme ve Destek iptali.  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]  
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]  
  
## <a name="checkpoint"></a>Denetim noktası  
 Bu noktada, derlemek ve Fibonacci hesaplayıcı uygulamayı çalıştırın.  
  
#### <a name="to-test-your-project"></a>Projenizi sınamak için  
  
-   Uygulamasını derlemek ve çalıştırmak için F5 tuşuna basın.  
  
     Hesaplama arka planda çalıştığı sırada göreceğiniz <xref:System.Windows.Forms.ProgressBar> tamamlama doğru hesaplamanın ilerleme durumunu görüntüleme. Ayrıca, bekleyen işlemi iptal edebilirsiniz.  
  
     Küçük sayılar için hesaplama çok hızlı olması gerekir, ancak büyük sayılar için belirgin bir gecikme görmeniz gerekir. 30 veya daha büyük bir değer girerseniz, bilgisayarınızın hızına bağlı olarak birkaç saniye bir gecikme görmeniz gerekir. 40'den büyük değerler için dakika veya hesaplama tamamlanması saatler sürebilir. Hesaplayıcı Fibonacci sayısı çok fazla hesaplama meşgulken, serbestçe formun gezinme, en aza indirmek, en üst düzeye çıkarmak ve bile yok sayın dikkat edin. Ana kullanıcı Arabirimi iş parçacığı hesaplama için beklenmiyor olmasıdır.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Kullanan bir form uyguladık göre bir <xref:System.ComponentModel.BackgroundWorker> arka planda bir hesaplama yürütmek için bileşen zaman uyumsuz işlemleri için diğer özellikleri keşfetmek:  
  
-   Birden çok kullanmak <xref:System.ComponentModel.BackgroundWorker> birkaç eşzamanlı operasyonlar için nesneleri.  
  
-   Birden çok iş parçacıklı uygulamanızda hata ayıklama için bkz: [nasıl yapılır: iş parçacıkları penceresini kullanma](/visualstudio/debugger/how-to-use-the-threads-window).  
  
-   Zaman uyumsuz programlama modelini destekleyen kendi bileşeni uygulayın. Daha fazla bilgi için bkz: [olay tabanlı zaman uyumsuz desene genel bakış](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
    > [!CAUTION]
    >  Her tür çoklu iş parçacığı kullanımı kullanırken, potansiyel olarak kendiniz için çok önemli ve karmaşık hatalar kullanıma sunar. Başvurun [yönetilen iş parçacığı oluşturma en iyi yöntemler](../../../../docs/standard/threading/managed-threading-best-practices.md) kullanan herhangi bir çözümü uygulamadan önce çoklu iş parçacığı kullanımı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../../../../docs/standard/threading/managed-threading-best-practices.md)  
 [Bileşenleri çoklu iş parçacığı kullanımı](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [IN derleme değil: Visual Basic'te çoklu iş parçacığı kullanımı](http://msdn.microsoft.com/library/c731a50c-09c1-4468-9646-54c86b75d269)  
 [Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [İzlenecek yol: Arka Planda İşlem Çalıştırma](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 [BackgroundWorker Bileşeni](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
