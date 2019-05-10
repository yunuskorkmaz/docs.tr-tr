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
ms.openlocfilehash: 1988ebd8c5f46346babe212962b617d30d765385
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211528"
---
# <a name="walkthrough-implementing-a-form-that-uses-a-background-operation"></a>İzlenecek yol: Arka Plan İşlemi Kullanan Bir Form Uygulama

Sahip olduğunuz işleminin tamamlanması uzun sürer ve yanıt vermemesine, kullanıcı arabirimi (UI) istemediğiniz veya kullanabileceğiniz "askıda," <xref:System.ComponentModel.BackgroundWorker> başka bir iş parçacığı üzerindeki işlemi yürütmek için sınıf.

Bu izlenecek yol nasıl kullanılacağını gösterir <xref:System.ComponentModel.BackgroundWorker> sınıfının "arka planda" zaman hesaplamalar gerçekleştirmek için kullanıcı arabirimi yanıt kalırken.  Aracılığıyla işiniz Fibonacci numaraları zaman uyumsuz olarak hesaplayan bir uygulamaya sahip olursunuz. Fibonacci sayıda belirgin bir süre alabilir bilgisayar olsa da, ana UI iş parçacığı tarafından bu gecikme kesilmez ve form hesaplama sırasında hızlı olacaktır.

Bu kılavuzda gösterilen görevler aşağıdakileri içerir:

- Windows tabanlı bir uygulama oluşturma

- Oluşturma bir <xref:System.ComponentModel.BackgroundWorker> formunuza

- Zaman uyumsuz olay işleyicileri ekleme

- İlerleme durumunu raporlama ve iptal için destek ekleme

Bu örnekte kullanılan kod tam listesi için bkz. [nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama](how-to-implement-a-form-that-uses-a-background-operation.md).

## <a name="create-a-form-that-uses-a-background-operation"></a>Arka plan işlemi kullanan bir form oluşturma

1. Visual Studio'da adlı bir Windows tabanlı uygulama projesi oluşturma `BackgroundWorkerExample` (**dosya** > **yeni** > **proje**  >  **Visual C#**  veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms Uygulama**).

2. İçinde **Çözüm Gezgini**, sağ **Form1** seçip **Yeniden Adlandır** kısayol menüsünden. İçin dosya adını değiştirerek `FibonacciCalculator`. Tıklayın **Evet** düğmesini yaptığınız kod öğesi için tüm başvuruları yeniden adlandırmak isteyip istemediğiniz sorulduğunda '`Form1`'.

3. Sürükleme bir <xref:System.Windows.Forms.NumericUpDown> denetimi **araç kutusu** forma. Ayarlama <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> özelliğini `1` ve <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> özelliğini `91`.

4. İki ekleme <xref:System.Windows.Forms.Button> formu için denetimler.

5. İlk Yeniden Adlandır <xref:System.Windows.Forms.Button> denetimi `startAsyncButton` ayarlayıp <xref:System.Windows.Forms.Control.Text%2A> özelliğini `Start Async`. İkinci <xref:System.Windows.Forms.Button> denetimi `cancelAsyncButton`, ayarlayıp <xref:System.Windows.Forms.Control.Text%2A> özelliğini `Cancel Async`. Ayarlama, <xref:System.Windows.Forms.Control.Enabled%2A> özelliğini `false`.

6. Her iki için bir olay işleyicisi oluşturun <xref:System.Windows.Forms.Button> denetimleri <xref:System.Windows.Forms.Control.Click> olayları. Ayrıntılar için bkz [nasıl yapılır: Tasarımcıyı kullanarak olay işleyicileri oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).

7. Sürükleme bir <xref:System.Windows.Forms.Label> denetimi **araç kutusu** forma ve yeniden adlandırmak `resultLabel`.

8. Sürükleme bir <xref:System.Windows.Forms.ProgressBar> denetimi **araç kutusu** forma.

## <a name="create-a-backgroundworker-with-the-designer"></a>Bir BackgroundWorker tasarımcı ile oluşturma

Oluşturabileceğiniz <xref:System.ComponentModel.BackgroundWorker> kullanarak zaman uyumsuz işlem için **Windows** **Form Tasarımcısı**.

Gelen **bileşenleri** sekmesinde **araç kutusu**, sürükleyin bir <xref:System.ComponentModel.BackgroundWorker> forma.

## <a name="add-asynchronous-event-handlers"></a>Zaman uyumsuz olay işleyicileri ekleme

Olay işleyicileri eklemek artık hazırsınız <xref:System.ComponentModel.BackgroundWorker> bileşenin zaman uyumsuz olayları. Fibonacci numaraları hesaplar, arka planda çalıştırılacak zaman alıcı bir işlem olay işleyicilere biri tarafından çağrılır.

1. İçinde **özellikleri** penceresinde ile <xref:System.ComponentModel.BackgroundWorker> halen seçiliyken, bileşene tıklayın **olayları** düğmesi. Çift <xref:System.ComponentModel.BackgroundWorker.DoWork> ve <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olayları olay işleyicileri oluşturun. Olay işleyicileri kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Tasarımcıyı kullanarak olay işleyicileri oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100)).

2. Adlı yeni bir yöntem oluşturma `ComputeFibonacci`, formunuzda. Bu yöntem asıl işi yapan ve arka planda çalışır. Bu kod, daha büyük sayılar için tamamlamak için katlanarak uzun zaman ayırdığınız özellikle verimsiz Fibonacci algoritma özyinelemeli uygulamasını gösterir. Uygulamanızdaki gecikmelere neden olabilir bir işlem göstermek için yalnızca tanım amaçlıdır için burada kullanılır.

     [!code-cpp[System.ComponentModel.BackgroundWorker#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]

3. İçinde <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi, bir çağrı ekleyin `ComputeFibonacci` yöntemi. İlk parametre alması `ComputeFibonacci` gelen <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> özelliği <xref:System.ComponentModel.DoWorkEventArgs>. <xref:System.ComponentModel.BackgroundWorker> Ve <xref:System.ComponentModel.DoWorkEventArgs> parametreleri kullanılacak daha sonra ilerleme durumunu raporlama ve iptal için destek. Dönüş değeri atamak `ComputeFibonacci` için <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> özelliği <xref:System.ComponentModel.DoWorkEventArgs>. Bu sonuç için kullanılabilecek <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay işleyicisi.

    > [!NOTE]
    > <xref:System.ComponentModel.BackgroundWorker.DoWork> Olay işleyicisi başvurmuyor `backgroundWorker1` örnek değişkeni, doğrudan bu belirli bir örneği için bu olay işleyicisi eşleştiği gibi <xref:System.ComponentModel.BackgroundWorker>. Bunun yerine, bir başvuru <xref:System.ComponentModel.BackgroundWorker> , oluşturulan bu olay kurtarılan `sender` parametresi. Formun birden fazla barındırdığında, bu önemlidir, <xref:System.ComponentModel.BackgroundWorker>. Tüm kullanıcı arabirimi nesneleri değiştiremez önemlidir, <xref:System.ComponentModel.BackgroundWorker.DoWork> olay işleyicisi. Bunun yerine, kullanıcı arabirimi aracılığıyla iletişim kurmak <xref:System.ComponentModel.BackgroundWorker> olayları.

     [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]

4. İçinde `startAsyncButton` denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi, zaman uyumsuz işlemi başlatan kodu ekleyin.

     [!code-cpp[System.ComponentModel.BackgroundWorker#13](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]

5. İçinde <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> olay işleyicisi hesaplama sonucu atama `resultLabel` denetimi.

     [!code-cpp[System.ComponentModel.BackgroundWorker#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]

## <a name="adding-progress-reporting-and-support-for-cancellation"></a>İlerleme durumunu raporlama ve iptal için destek ekleme

Uzun sürmesi zaman uyumsuz işlemler için çoğunlukla rapor ilerleme kullanıcıya ve kullanıcı işlemi iptal etmek izin vermek için tercih edilir. <xref:System.ComponentModel.BackgroundWorker> Sınıf, arka plan işlemi işlemi ilerleme durumu göndermeye izin veren bir olayı sağlar. Ayrıca, bir çağrı algılamak çalışan kod sağlayan bir bayrak sağlar <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> ve kendisini kesme.

### <a name="implement-progress-reporting"></a>İlerleme durumunu bildirme uygulayın

1. İçinde **özellikleri**, penceresinde `backgroundWorker1`. <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> ve <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> özelliklerini `true` olarak ayarlayın.

2. İki değişken bildirin `FibonacciCalculator` formu. Bu ilerleme durumunu izlemek için kullanılır.

     [!code-cpp[System.ComponentModel.BackgroundWorker#14](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]

3. İçin bir olay işleyicisi ekleme <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay. İçinde <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> olay işleyicisi, güncelleştirme <xref:System.Windows.Forms.ProgressBar> ile <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> özelliği <xref:System.ComponentModel.ProgressChangedEventArgs> parametresi.

     [!code-cpp[System.ComponentModel.BackgroundWorker#7](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]

### <a name="implement-support-for-cancellation"></a>İptal için destek uygular

1. İçinde `cancelAsyncButton` denetimin <xref:System.Windows.Forms.Control.Click> olay işleyicisi, zaman uyumsuz işlemi iptal eden kodu ekleyin.

     [!code-cpp[System.ComponentModel.BackgroundWorker#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]

2. Aşağıdaki kod parça içinde `ComputeFibonacci` yöntemi rapor ilerleme durumu ve Destek iptali.

     [!code-cpp[System.ComponentModel.BackgroundWorker#11](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]

## <a name="checkpoint"></a>Checkpoint

Bu noktada, derleyin ve Fibonacci hesaplayıcı uygulamayı çalıştırın.

Tuşuna **F5** derlemek ve uygulamayı çalıştırın.

Hesaplama arka planda çalışırken göreceğiniz <xref:System.Windows.Forms.ProgressBar> hesaplamanın tamamlanma yönelik ilerleme durumunu görüntüleme. Ayrıca, bekleyen işlemi iptal edebilirsiniz.

Küçük sayılar için hesaplama çok hızlı olması gerekir, ancak daha büyük sayılar için fark edilebilir bir gecikme görmeniz gerekir. 30 veya daha büyük bir değer girerseniz, bilgisayarınızın hızına bağlı olarak birkaç saniye cinsinden gecikme görmeniz gerekir. 40 büyük değerler için dakikalar ya da hesaplama tamamlanması saatler sürebilir. Hesaplayıcı Fibonacci sayıda bilgi işlem yoğun olsa da, serbestçe form taşımak, en aza indirmek, en üst düzeye çıkarmak ve bile Kapat olduğuna dikkat edin. Ana kullanıcı Arabirimi iş parçacığı, hesaplama için beklenmiyor olmasıdır.

## <a name="next-steps"></a>Sonraki adımlar

Kullanan bir form uyguladıysanız göre bir <xref:System.ComponentModel.BackgroundWorker> arka planda bir hesaplama yürütmek için bileşen diğer zaman uyumsuz işlemler olasılıklarını keşfedebilirsiniz:

- Birden çok kullanın <xref:System.ComponentModel.BackgroundWorker> birkaç eşzamanlı operasyonlar için nesneleri.

- Çok iş parçacıklı uygulamanızda hata ayıklamak için bkz: [nasıl yapılır: İş parçacıkları penceresini kullanma](/visualstudio/debugger/how-to-use-the-threads-window).

- Zaman uyumsuz programlama modelini destekleyen kendi bileşeni uygulayın. Daha fazla bilgi için [olay tabanlı zaman uyumsuz desene genel bakış](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).

    > [!CAUTION]
    > Her türlü çoklu iş parçacığı kullanırken, büyük olasılıkla kendiniz çok önemli ve karmaşık hataları ortaya çıkarır. Başvurun [yönetilen iş parçacığı oluşturma en iyi yöntemler](../../../standard/threading/managed-threading-best-practices.md) kullanan herhangi bir çözümü uygulamadan önce çoklu iş parçacığı kullanımı.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- [Yönetilen iş parçacığı oluşturma](../../../standard/threading/index.md)
- [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../../../standard/threading/managed-threading-best-practices.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Nasıl yapılır: Arka plan işlemi kullanan bir Form uygulama](how-to-implement-a-form-that-uses-a-background-operation.md)
- [İzlenecek yol: Arka planda işlem çalıştırma](walkthrough-running-an-operation-in-the-background.md)
- [BackgroundWorker Bileşeni](backgroundworker-component.md)
