---
title: Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış
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
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 792aa8da-918b-458e-b154-9836b97735f3
ms.openlocfilehash: f4aac5afbb13cafa7bb0e9c1eb6bbd92ac41bf8c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289427"
---
# <a name="event-based-asynchronous-pattern-overview"></a>Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış
Aynı anda pek çok görevi gerçekleştiren ve kullanıcı etkileşimine yanıt veren uygulamalar, genellikle birden çok iş parçacığı kullanan bir tasarım gerektirir. <xref:System.Threading>Ad alanı, yüksek performanslı çok iş parçacıklı uygulamalar oluşturmak için gereken tüm araçları sağlar, ancak bu araçların kullanılması çok iş parçacıklı yazılım mühendisliğinde önemli bir deneyim gerektirir. Oldukça basit çok iş parçacıklı uygulamalar için, <xref:System.ComponentModel.BackgroundWorker> bileşen basit bir çözüm sağlar. Daha karmaşık zaman uyumsuz uygulamalarda, olay tabanlı zaman uyumsuz düzene uygun bir sınıf uygulamayı düşünün.  
  
 Olay tabanlı zaman uyumsuz model, çok iş parçacıklı uygulamaların avantajlarından yararlanır ve çok iş parçacıklı tasarımda bulunan karmaşık sorunların çoğunu gizler. Bu kalıbı destekleyen bir sınıf kullanmak şunları yapmanıza izin verebilir:  
  
- Yüklemeler ve veritabanı işlemleri gibi zaman alan görevleri, "arka planda", uygulamanızı kesintiye uğramadan gerçekleştirin.  
  
- Birden çok işlemi aynı anda yürütün, her tamamlandığında bildirim alma.  
  
- Uygulamanızı durdurmadan ("engellenmeden") kaynakların kullanılabilir olmasını bekleyin.  
  
- Tanıdık olayları ve temsilciler modelini kullanarak bekleyen zaman uyumsuz işlemlerle iletişim kurun. Olay işleyicilerini ve temsilcileri kullanma hakkında daha fazla bilgi için bkz. [Olaylar](../events/index.md).  
  
 Olay tabanlı zaman uyumsuz deseninin desteklendiği bir sınıf, _MethodName_**zaman uyumsuz**adlı bir veya daha fazla yöntemlere sahip olur. Bu yöntemler, geçerli iş parçacığında aynı işlemi gerçekleştiren zaman uyumlu sürümleri yansıtabilir. Sınıfta bir _MethodName_**tamamlandı** olayı olabilir ve bir _MethodName_**Asynccancel** (veya yalnızca bir algıladığında **lasync**) yöntemi olabilir.  
  
 <xref:System.Windows.Forms.PictureBox>, olay tabanlı zaman uyumsuz stili destekleyen tipik bir bileşendir. Yöntemini çağırarak bir görüntüyü zaman uyumlu olarak indirebilirsiniz <xref:System.Windows.Forms.PictureBox.Load%2A> , ancak görüntü büyükse veya ağ bağlantısı yavaşsa, yükleme işlemi tamamlanana ve çağrısı geri alınana kadar uygulamanız yanıt vermeyi durdurur <xref:System.Windows.Forms.PictureBox.Load%2A> .  
  
 Görüntü yüklenirken uygulamanızın çalışmaya devam etmesini istiyorsanız, <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> <xref:System.Windows.Forms.PictureBox.LoadCompleted> diğer herhangi bir olayı işlerken olduğu gibi, yöntemi çağırabilir ve olayı işleyebilirsiniz. <xref:System.Windows.Forms.PictureBox.LoadAsync%2A>Yöntemini çağırdığınızda, yükleme işlemi ayrı bir iş parçacığına ("arka planda") devam ederken uygulamanız çalışmaya devam edecektir. Olay işleyiciniz, görüntü yükleme işlemi tamamlandığında çağrılır ve olay işleyiciniz, <xref:System.ComponentModel.AsyncCompletedEventArgs> indirmenin başarıyla tamamlanıp tamamlanmadığını belirleme parametresini inceleyebilir.  
  
 Olay tabanlı zaman uyumsuz model, zaman uyumsuz bir işlemin iptal edilmesine ve <xref:System.Windows.Forms.PictureBox> denetimin yöntemiyle bu gereksinimi desteklediğinden emin olmanızı gerektirir <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> . Çağırma, <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> bekleyen indirmeyi durdurmak için bir istek gönderir ve görev iptal edildiğinde <xref:System.Windows.Forms.PictureBox.LoadCompleted> olay tetiklenir.  
  
> [!CAUTION]
> İndirme işlemi, isteğin yapıldığı gibi bitecektir <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> , bu nedenle <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> iptal etme isteğini yansıtmayabilir. Bu, *yarış durumu* olarak adlandırılır ve çok iş parçacıklı programlamada yaygın bir sorundur. Çoklu iş parçacıklı programlamada sorunlar hakkında daha fazla bilgi için bkz. [yönetilen Iş parçacığı En Iyi yöntemleri](../threading/managed-threading-best-practices.md).  
  
## <a name="characteristics-of-the-event-based-asynchronous-pattern"></a>Olay tabanlı zaman uyumsuz düzenin özellikleri  
 Olay tabanlı zaman uyumsuz model, belirli bir sınıf tarafından desteklenen işlemlerin karmaşıklığına bağlı olarak birkaç form alabilir. En basit sınıflarda tek bir _MethodName_**zaman uyumsuz** yöntemi ve karşılık gelen bir _MethodName_**tamamlandı** olayı olabilir. Daha karmaşık sınıfların, her biri karşılık gelen _MethodName_**tamamlandı** olayına ve bu yöntemlerin eşzamanlı sürümlerine sahip birkaç _MethodName_**zaman uyumsuz** yöntemi olabilir. Sınıflar, her zaman uyumsuz yöntem için, isteğe bağlı olarak iptali, ilerleme raporlaması ve artımlı sonuçları destekleyebilir.  
  
 Zaman uyumsuz bir yöntem aynı zamanda birden fazla bekleyen çağrıyı destekleyebilir (birden çok eşzamanlı çağırma), kodunuzun diğer bekleyen işlemleri tamamlamadan önce herhangi bir sayıda çağrı yapmasına izin verir. Bu durumu doğru şekilde işlemek, uygulamanızın her bir işlemin tamamlanmasını izlemesini gerektirebilir.  
  
### <a name="examples-of-the-event-based-asynchronous-pattern"></a>Olay tabanlı zaman uyumsuz model örnekleri  
 <xref:System.Media.SoundPlayer>Ve <xref:System.Windows.Forms.PictureBox> bileşenleri, olay tabanlı zaman uyumsuz düzenin basit uygulamalarını temsil eder. <xref:System.Net.WebClient>Ve <xref:System.ComponentModel.BackgroundWorker> bileşenleri, olay tabanlı zaman uyumsuz düzenin daha karmaşık uygulamalarını temsil eder.  
  
 Aşağıda, düzene uyan örnek bir sınıf bildirimi verilmiştir:  
  
```vb  
Public Class AsyncExample  
    ' Synchronous methods.  
    Public Function Method1(ByVal param As String) As Integer
    Public Sub Method2(ByVal param As Double)
  
    ' Asynchronous methods.  
    Overloads Public Sub Method1Async(ByVal param As String)
    Overloads Public Sub Method1Async(ByVal param As String, ByVal userState As Object)
    Public Event Method1Completed As Method1CompletedEventHandler  
  
    Overloads Public Sub Method2Async(ByVal param As Double)
    Overloads Public Sub Method2Async(ByVal param As Double, ByVal userState As Object)
    Public Event Method2Completed As Method2CompletedEventHandler  
  
    Public Sub CancelAsync(ByVal userState As Object)
  
    Public ReadOnly Property IsBusy () As Boolean  
  
    ' Class implementation not shown.  
End Class  
```  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 Kurgusal `AsyncExample` sınıfta, her ikisi de zaman uyumlu ve zaman uyumsuz çağırmaları destekleyen iki yöntem vardır. Zaman uyumlu aşırı yüklemeler herhangi bir yöntem çağrısı gibi davranır ve işlemi çağıran iş parçacığında yürütür; işlem zaman alıyorsa, çağrı dönüşmeden önce dikkat çekici bir gecikme olabilir. Zaman uyumsuz aşırı yüklemeler işlemi başka bir iş parçacığında başlatır ve ardından hemen geri döner ve bu işlem, çağıran iş parçacığının işlem "arka planda" yürütüldüğü sırada devam etmesine izin verir.  
  
### <a name="asynchronous-method-overloads"></a>Zaman uyumsuz yöntem aşırı yüklemeleri  
 Zaman uyumsuz işlemler için olası iki aşırı yükleme vardır: tek çağrı ve Çoklu çağrı. Bu iki formu Yöntem imzalarına göre ayırabilirsiniz: birden çok çağırma formunda, adlı ek bir parametre bulunur `userState` . Bu form, kodunuzun `Method1Async(string param, object userState)` bekleyen zaman uyumsuz işlemlerin bitmesini beklemeden birden çok kez çağrı yapmayı olanaklı kılar. Diğer taraftan, `Method1Async(string param)` önceki bir çağırma tamamlanmadan önce çağırmayı denerseniz Yöntem bir oluşturur <xref:System.InvalidOperationException> .  
  
 `userState`Çoklu çağrı aşırı yüklemelerinin parametresi, zaman uyumsuz işlemler arasında ayrım yapmanıza olanak tanır. Her bir çağrı için benzersiz bir değer (örneğin, bir GUID veya karma kod) sağlarsınız `Method1Async(string param, object userState)` ve her işlem tamamlandığında, olay işleyiciniz işlemin hangi örneğinin tamamlanma olayını gerçekleştirdiğini belirleyebilir.  
  
### <a name="tracking-pending-operations"></a>Bekleyen Işlemleri izleme  
 Çoklu çağrı yüklerini kullanırsanız, kodunuzun `userState` bekleyen görevler için nesneleri (görev kimlikleri) izlemesi gerekir. Her yapılan çağrı için `Method1Async(string param, object userState)` genellikle yeni, benzersiz bir `userState` nesne oluşturup bir koleksiyona eklersiniz. Bu nesneye karşılık gelen görev `userState` tamamlanma olayını harekete geçirirse, tamamlama yöntemi uygulamanız <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType> onu inceleyerek ve koleksiyonunuzdan kaldırır. Bu şekilde kullanılırsa `userState` parametresi bir görev kimliği rolünü alır.  
  
> [!NOTE]
> Birden çok çağırma aşırı yüküne yönelik çağrılarınız için benzersiz bir değer sağlamanız dikkat etmeniz gerekir `userState` . Benzersiz olmayan görev kimlikleri, zaman uyumsuz sınıfın oluşturmasına neden olur <xref:System.ArgumentException> .  
  
### <a name="canceling-pending-operations"></a>Bekleyen Işlemleri iptal etme  
 Her zaman zaman uyumsuz işlemleri tamamlanmadan önce iptal edebilmek önemlidir. Olay tabanlı zaman uyumsuz model uygulayan sınıflar bir `CancelAsync` yöntemine (yalnızca bir zaman uyumsuz yöntem varsa) veya _MethodName_**asynccancel** yöntemine (birden çok zaman uyumsuz yöntem varsa) sahip olur.  
  
 Birden çok çağırma yöntemine izin veren Yöntemler bir `userState` parametre alır ve her görevin ömrünü izlemek için kullanılabilir. `CancelAsync``userState`belirli bekleyen görevleri iptal etmenizi sağlayan bir parametre alır.  
  
 Aynı anda yalnızca tek bir bekleyen işlemi destekleyen metotlar, örneğin `Method1Async(string param)` , iptal edilemez.  
  
### <a name="receiving-progress-updates-and-incremental-results"></a>Ilerleme güncellemeleri ve artımlı sonuçlar alınıyor  
 Olay tabanlı zaman uyumsuz düzene uygun bir sınıf, isteğe bağlı olarak ilerleme durumunu ve artımlı sonuçları izlemek için bir olay sağlayabilir. Bu, genellikle adlandırılmış `ProgressChanged` veya _MethodName_**ProgressChanged & lt**ve buna karşılık gelen olay işleyicisi bir <xref:System.ComponentModel.ProgressChangedEventArgs> parametre alır.  
  
 Olayın olay işleyicisi, `ProgressChanged` <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType> zaman uyumsuz bir görevin tamamlanan yüzdesini belirlemek için özelliğini inceleyebilir. Bu özellik 0 ile 100 arasında değişir ve <xref:System.Windows.Forms.ProgressBar.Value%2A> bir öğesinin özelliğini güncelleştirmek için kullanılabilir <xref:System.Windows.Forms.ProgressBar> . Birden çok zaman uyumsuz işlem beklendiğinde, <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType> hangi işlemin ilerleme durumunu ayırt etmek için özelliğini kullanabilirsiniz.  
  
 Bazı sınıflar, zaman uyumsuz işlemler devam edecek şekilde artımlı sonuçlar bildirebilir. Bu sonuçlar, öğesinden türetilen bir sınıfta saklanır <xref:System.ComponentModel.ProgressChangedEventArgs> ve türetilmiş sınıfta özellikler olarak görünürler. Bu sonuçlara `ProgressChanged` , olaya erişmek istediğiniz gibi olay işleyicisindeki erişebilirsiniz <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> . Birden çok zaman uyumsuz işlem beklendiğinde, <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A> hangi işlemin artımlı sonuçlar raporlanmasını ayırt etmek için özelliğini kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [Nasıl Yapılır: Arka Planda İşlem Çalıştırma](../../framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama](../../framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
