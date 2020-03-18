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
ms.openlocfilehash: cce01a7c87f6f20b5e6c46881b8c863bb5a72a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160078"
---
# <a name="event-based-asynchronous-pattern-overview"></a>Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış
Aynı anda birçok görevi gerçekleştiren, ancak kullanıcı etkileşimine yanıt vermeye devam eden uygulamalar genellikle birden çok iş parçacığı kullanan bir tasarım gerektirir. Ad <xref:System.Threading> alanı, yüksek performanslı çok iş parçacığı uygulamaları oluşturmak için gerekli tüm araçları sağlar, ancak bu araçları etkin bir şekilde kullanmak çok iş parçacığı yazılım mühendisliği ile önemli bir deneyim gerektirir. Nispeten basit çok iş parçacığı <xref:System.ComponentModel.BackgroundWorker> uygulamaları için bileşen basit bir çözüm sağlar. Daha gelişmiş eşzamanlı uygulamalar için, Olay tabanlı Asynchronous Desenine uyan bir sınıf uygulamayı düşünün.  
  
 Olay tabanlı Asynchronous Pattern, çok iş parçacığı tasarımının doğasında bulunan karmaşık sorunların çoğunu gizlerken çok iş parçacığı uygulamalarının avantajlarını kullanıma sunuyor. Bu deseni destekleyen bir sınıf kullanmak şunları yapabilirsiniz:  
  
- Uygulamanızı kesintiye uğratmadan, "arka planda" indirmeler ve veritabanı işlemleri gibi zaman alan görevleri gerçekleştirin.  
  
- Aynı anda birden çok işlemi yürütün ve her biri tamamlandığında bildirim alın.  
  
- Uygulamanızı durdurmadan ("engelleme") kaynakların kullanılabilir olmasını bekleyin.  
  
- Tanıdık olaylar ve temsilciler modelini kullanarak bekleyen eşzamanlı işlemlerle iletişim kurun. Olay işleyicilerini ve temsilcilerini kullanma hakkında daha fazla bilgi için [Bkz. Olaylar.](../../../docs/standard/events/index.md)  
  
 Olay tabanlı Asynchronous Modelini destekleyen bir sınıfın _MethodName_**Async**adlı bir veya daha fazla yöntemi olacaktır. Bu yöntemler, geçerli iş parçacığı üzerinde aynı işlemi gerçekleştiren senkron sürümleri yansıtabilir. Sınıfın bir _MethodName_**Completed** olayı da olabilir ve bir _MethodName_**AsyncCancel** (veya basitçe **CancelAsync)** yöntemi olabilir.  
  
 <xref:System.Windows.Forms.PictureBox>Olay tabanlı Asynchronous Deseni destekleyen tipik bir bileşendir. Bir görüntüyü <xref:System.Windows.Forms.PictureBox.Load%2A> yöntemini çağırarak eşzamanlı olarak indirebilirsiniz, ancak görüntü büyükse veya ağ bağlantısı yavaşsa, indirme işlemi tamamlanana <xref:System.Windows.Forms.PictureBox.Load%2A> ve geri dönene kadar uygulamanız yanıt vermeyi durdurur.  
  
 Uygulamanızın görüntü yüklenirken çalışmaya devam etmesini istiyorsanız, <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> diğer tüm <xref:System.Windows.Forms.PictureBox.LoadCompleted> olayı işleyeceğiniz gibi yöntemi arayabilir ve olayı işleyebilirsiniz. <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> Yöntemi çağırdığınızda, indirme işlemi ayrı bir iş parçacığında ("arka planda") devam ederken uygulamanız çalışmaya devam eder. Görüntü yükleme işlemi tamamlandığında olay işleyiciniz çağrılacak ve olay işleyiciniz <xref:System.ComponentModel.AsyncCompletedEventArgs> karşıdan yüklemenin başarıyla tamamlanıp tamamlanmadığını belirlemek için parametreyi inceleyebilir.  
  
 Olay tabanlı Asynchronous Pattern bir eşzamanlı işlem iptal edilebilir gerektirir ve <xref:System.Windows.Forms.PictureBox> denetim <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> yöntemi ile bu gereksinimi destekler. Arama, <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> bekleyen karşıdan yüklemeyi durdurmak için bir istek gönderir <xref:System.Windows.Forms.PictureBox.LoadCompleted> ve görev iptal edildiğinde, olay yükseltilir.  
  
> [!CAUTION]
> <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> İndirme işlemi, istek yapıldığı gibi bitebilir, <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> bu nedenle iptal etme isteğini yansıtmayabilir. Bu bir *yarış koşulu* denir ve çok iş parçacığı programlama da yaygın bir sorundur. Çok iş parçacığı programlamadaki sorunlar hakkında daha fazla bilgi için Yönetilen [İş Parçacığı En İyi Uygulamaları'na](../../../docs/standard/threading/managed-threading-best-practices.md)bakın.  
  
## <a name="characteristics-of-the-event-based-asynchronous-pattern"></a>Olay Tabanlı Eşzamanlımodelin Özellikleri  
 Olay tabanlı Eşzamanlı desen, belirli bir sınıf tarafından desteklenen işlemlerin karmaşıklığına bağlı olarak çeşitli formlar alabilir. En basit sınıflarda tek bir _MethodName_**Async** yöntemi ve ilgili _MethodName_**Tamamlandı** olayı olabilir. Daha karmaşık sınıflar, her biri karşılık gelen _Metod Adı_**Tamamlanan** olay ve bu yöntemlerin eşzamanlı sürümleri ile birkaç _MethodName_**Async** yöntemleri olabilir. Sınıflar isteğe bağlı olarak her bir eşzamanlı yöntem için iptal, ilerleme raporlamave artımlı sonuçları destekleyebilir.  
  
 Eşzamanlı bir yöntem, bekleyen diğer işlemleri tamamlamadan önce kodunuzun herhangi bir sayıda aramasını sağlayan birden çok bekleyen aramayı (birden çok eşzamanlı çağrı) da destekleyebilir. Bu durumu doğru şekilde işlemek, uygulamanızın her işlemin tamamlanmasını izlemesini gerektirebilir.  
  
### <a name="examples-of-the-event-based-asynchronous-pattern"></a>Olay tabanlı Asenkron Desen Örnekleri  
 <xref:System.Media.SoundPlayer> Ve <xref:System.Windows.Forms.PictureBox> bileşenleri Olay tabanlı Asynchronous Desen basit uygulamalarını temsil eder. <xref:System.Net.WebClient> Ve <xref:System.ComponentModel.BackgroundWorker> bileşenleri Olay tabanlı Asynchronous Desen daha karmaşık uygulamaları temsil eder.  
  
 Aşağıda desene uyan bir örnek sınıf bildirimi verilmiştir:  
  
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
  
 Kurgusal `AsyncExample` sınıfın, her ikisi de senkron ve eşzamanlı çağrıları destekleyen iki yöntemi vardır. Senkron aşırı yüklemeler herhangi bir yöntem çağrısı gibi olur ve çağrı iş parçacığı üzerinde işlemi yürütmek; işlem zaman alıyorsa, arama dönmeden önce gözle görülür bir gecikme olabilir. Asynchronous aşırı yüklemeleri işlemi başka bir iş parçacığı üzerinde başlatacak ve ardından hemen döndürerek işlem "arka planda" yürütülürken çağrı iş parçacığının devam etmesine olanak sağlar.  
  
### <a name="asynchronous-method-overloads"></a>Asynchronous Yöntemi Aşırı Yükler  
 Eşzamanlı işlemler için iki aşırı yükleme olabilir: tek çağırma ve çoklu çağırma. Bu iki formu yöntem imzalarına göre ayırt edebilirsiniz: çoklu çağırma formunun fazladan bir parametresi `userState`vardır. Bu form, bekleyen eşzamanlı işlemlerin tamamlanmasını beklemeden kodunuzun birden çok kez aramasını `Method1Async(string param, object userState)` mümkün kılar. Öte yandan, önceki bir çağrı `Method1Async(string param)` tamamlanmadan aramayı denerseniz, yöntem <xref:System.InvalidOperationException>bir .  
  
 Çoklu `userState` çağırma aşırı yüklemeleri için parametre, eşzamanlı işlemler arasında ayrım yapmanızı sağlar. Her çağrı `Method1Async(string param, object userState)`için benzersiz bir değer (örneğin, GUID veya karma kod) sağlarsınız ve her işlem tamamlandığında, olay işleyiciniz işlemin tamamlanması olayını hangi örneğini yükselttiğini belirleyebilir.  
  
### <a name="tracking-pending-operations"></a>Bekleyen İşlemleri İzleme  
 Birden çok çağrı lı aşırı yükleme kullanırsanız, kodunuzun `userState` bekleyen görevler için nesneleri (görev işleri) izlemesi gerekir. Her arama `Method1Async(string param, object userState)`için, genellikle yeni, benzersiz `userState` bir nesne oluşturur ve bir koleksiyona eklersiniz. Bu `userState` nesneye karşılık gelen görev tamamlama olayını yükselttiğinde, <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType> tamamlama yöntemi uygulamanız onu inceler ve koleksiyonunuzdan kaldırır. Bu şekilde kullanıldığında, `userState` parametre görev kimliği rolünü alır.  
  
> [!NOTE]
> Birden fazla çağrı yüklemesi `userState` için yaptığınız aramalarda benzersiz bir değer sağlamaya dikkat etmelisiniz. Benzersiz olmayan görev işleri asynchronous sınır ısıtımına <xref:System.ArgumentException>neden olur.  
  
### <a name="canceling-pending-operations"></a>Bekleyen İşlemleri İptal Etme  
 Asynchronous işlemlerini tamamlanmadan önce herhangi bir zamanda iptal edebilmek önemlidir. Olay tabanlı Asenkron Deseni uygulayan sınıfların `CancelAsync` bir yöntemi (yalnızca bir eşzamanlı yöntem varsa) veya _MethodName_**AsyncCancel** yöntemi (birden çok eşzamanlı yöntem varsa) olacaktır.  
  
 Birden çok çağrıya izin `userState` veren yöntemler, her görevin kullanım ömrünü izlemek için kullanılabilecek bir parametre alır. `CancelAsync`bekleyen `userState` belirli görevleri iptal etmenizi sağlayan bir parametre alır.  
  
 Aynı anda `Method1Async(string param)`yalnızca bekleyen tek bir işlemi destekleyen yöntemler iptal edilemez.  
  
### <a name="receiving-progress-updates-and-incremental-results"></a>İlerleme Güncelleştirmeleri ve Artımlı Sonuçlar Alma  
 Olay tabanlı Asynchronous Deseni'ne uyan bir sınıf, ilerleme ve artımlı sonuçları izlemek için isteğe bağlı olarak bir olay sağlayabilir. Bu genellikle adlandırılmış `ProgressChanged` veya _MethodName_**ProgressChanged**, ve ilgili <xref:System.ComponentModel.ProgressChangedEventArgs> olay işleyicisi bir parametre alacaktır.  
  
 `ProgressChanged` Olay için olay işleyicisi, eşiş bir görevin yüzde kaçının tamamlandığını belirlemek için <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType> özelliği inceleyebilir. Bu özellik 0 ile 100 arasında değişir ve <xref:System.Windows.Forms.ProgressBar.Value%2A> bir <xref:System.Windows.Forms.ProgressBar>. Birden çok eşzamanlı işlem bekliyorsa, hangi <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType> işlemin ilerlemeyi bildirdiğini ayırt etmek için özelliği kullanabilirsiniz.  
  
 Bazı sınıflar, eşzamanlı işlemler devam ettikçe artımlı sonuçlar bildirebilir. Bu sonuçlar, türetilen bir sınıfta depolanır <xref:System.ComponentModel.ProgressChangedEventArgs> ve türemiş sınıfta özellik olarak görünür. Bu `ProgressChanged` sonuçlara, tıpkı özelliğe erişeceğiniz gibi, olay <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> için olay işleyicisi olarak erişebilirsiniz. Birden çok eşzamanlı işlem bekliyorsa, hangi <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A> işlemin artımlı sonuçlar bildirdiğini ayırt etmek için özelliği kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [Nasıl Yapılır: Arka Planda İşlem Çalıştırma](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
