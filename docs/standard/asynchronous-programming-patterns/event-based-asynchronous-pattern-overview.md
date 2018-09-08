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
ms.openlocfilehash: 2ef25c3d7db3f445ddf7f925eb73c85760f34dc5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44211937"
---
# <a name="event-based-asynchronous-pattern-overview"></a>Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış
Aynı anda birçok görevi gerçekleştiren henüz kullanıcı etkileşimine yanıt verebilir durumda kalması uygulamalar genellikle birden çok iş parçacığı kullanan bir tasarım gerektirir. <xref:System.Threading> Ad alanı, çok iş parçacıklı yüksek performanslı uygulamalar oluşturmak için gerekli olan tüm araçları sağlar, ancak etkili bir şekilde bu araçları kullanarak, birden çok iş parçacıklı yazılım Mühendisliği önemli deneyimiyle gerektirir. Görece basit birden çok iş parçacıklı uygulamalar için <xref:System.ComponentModel.BackgroundWorker> bileşeni, basit bir çözüm sağlar. Zaman uyumsuz daha gelişmiş uygulamalar için olay tabanlı zaman uyumsuz desene uyar bir class uygulamayı düşünün.  
  
 Olay tabanlı zaman uyumsuz desen çok iş parçacıklı uygulamalar avantajları pek çok iş parçacıklı tasarımında devralınan karmaşık sorunların gizleyerek kullanılabilir hale getirir. Bu deseni destekleyen bir sınıf kullanarak size izin verebilirsiniz:  
  
-   Uygulamanızı kesintiye uğratmadan indirmeleri ve "arka planda," veritabanı işlemleri gibi uzun süren görevleri gerçekleştirin.  
  
-   Birden çok işlem her tamamlandığında bildirim alma eşzamanlı olarak yürütün.  
  
-   Kaynakları ("asılı") durdurmadan kullanılabilir olana kadar bekleyin, uygulamanızın.  
  
-   Bilinen olayları ve temsilci modelini kullanarak zaman uyumsuz işlemleri iletişim. Olay işleyicileri ve temsilcileri kullanma ile ilgili daha fazla bilgi için bkz: [olayları](../../../docs/standard/events/index.md).  
  
 Olay tabanlı zaman uyumsuz deseni destekleyen bir sınıf adlı bir veya daha fazla yöntemi olacaktır *MethodName ***zaman uyumsuz**. Bu yöntemler, zaman uyumlu sürümler, geçerli iş parçacığında aynı işlemi yansıtma. Sınıfı ayrıca olabilir bir *MethodName *** tamamlandı**  olay ve olabilir bir *MethodName *** AsyncCancel** (ya da yalnızca **CancelAsync**) yöntemi.  
  
 <xref:System.Windows.Forms.PictureBox> Olay tabanlı zaman uyumsuz deseni destekleyen tipik bir bileşendir. Çağırarak, zaman uyumlu bir görüntü indirebilirsiniz, <xref:System.Windows.Forms.PictureBox.Load%2A> büyük görüntüdür veya ağ bağlantısı yavaşsa, yükleme işlemi tamamlanana kadar uygulamanız ("Kapat") durdurur ancak yöntemi ve çağrısı <xref:System.Windows.Forms.PictureBox.Load%2A> döndürür.  
  
 Uygulamanızın istiyorsanız görüntünün sırasında çalışmaya devam etmesini yükleniyor, çağırabilirsiniz <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> yöntemi ve tutamacı <xref:System.Windows.Forms.PictureBox.LoadCompleted> olay gibi başka bir olay işleme. Çağırdığınızda <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> yöntemi, uygulamanızın ayrı bir iş parçacığında ("arka planda") indirme devam ederken çalışmaya devam edecek. Resim yükleme işlemi tamamlandıktan ve olayı işleyicinizi inceleyebilirsiniz, olay işleyicisi çağrılacak <xref:System.ComponentModel.AsyncCompletedEventArgs> indirme başarıyla tamamlandı, belirlemek için parametre.  
  
 Zaman uyumsuz bir işlem iptal edilebileceğine, olay tabanlı zaman uyumsuz desen gerektirir ve <xref:System.Windows.Forms.PictureBox> denetimini destekliyorsa bu gereksinimle birlikte kendi <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> yöntemi. Çağırma <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> bekleyen indirme durdurma isteği gönderir ve görev iptal edildiğinde <xref:System.Windows.Forms.PictureBox.LoadCompleted> olayı oluşturulur.  
  
> [!CAUTION]
>  İndirme gibi tamamlaması mümkün <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> isteği yapıldığında, bunu <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> iptal etme isteği yansıtmayabilir. Bu adlı bir *yarış durumu* ve çok iş parçacıklı programlama sık karşılaşılan bir sorundur. Çok iş parçacıklı programlama konuları hakkında daha fazla bilgi için bkz. [yönetilen iş parçacığı oluşturma en iyi yöntemler](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="characteristics-of-the-event-based-asynchronous-pattern"></a>Olay tabanlı zaman uyumsuz desenin özellikleri  
 Olay tabanlı zaman uyumsuz desen, belirli bir sınıf tarafından desteklenen operations karmaşıklığına bağlı olarak birkaç biçimleri alabilir. Tek bir basit sınıfları olabilir *MethodName *** zaman uyumsuz** yöntemi ve karşılık gelen *MethodName *** tamamlandı** olay. Daha karmaşık sınıfları birkaç olabilir *MethodName *** zaman uyumsuz** yöntemleri, karşılık gelen her *MethodName *** tamamlandı** bu yöntemleri zaman uyumlu sürümlerini yanı sıra, olay. Sınıfları isteğe bağlı olarak her zaman uyumsuz bir yöntem için artımlı sonuçları iptal ve ilerleme raporlaması destekleyebilir.  
  
 Zaman uyumsuz bir yöntem herhangi bir sayıda diğer bekleyen işlemler tamamlanmadan önce bir kez çağırmak kodunuzu sağlayan birden fazla bekleyen çağrıları (birden çok eş zamanlı başlatma), aynı zamanda destekleyebilir. Bu durumu doğru şekilde işleme her işlemin tamamlanmasını izlemek için uygulamanızı gerektirebilir.  
  
### <a name="examples-of-the-event-based-asynchronous-pattern"></a>Olay tabanlı zaman uyumsuz desenin örnekleri  
 <xref:System.Media.SoundPlayer> Ve <xref:System.Windows.Forms.PictureBox> bileşenleri, olay tabanlı zaman uyumsuz desenin basit uygulamalar'ı temsil eder. <xref:System.Net.WebClient> Ve <xref:System.ComponentModel.BackgroundWorker> bileşenleri, olay tabanlı zaman uyumsuz desenin daha karmaşık uygulamalar'ı temsil eder.  
  
 Aşağıda, desenine uyduğunu örnek sınıf bildirimi şu şekildedir:  
  
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
  
 Kurgusal `AsyncExample` sınıfı ikisi için de destek zaman uyumlu ve zaman uyumsuz çağrıları, iki yöntem vardır. Zaman uyumlu aşırı herhangi bir yöntem çağrısının gibi davranır ve çağıran iş parçacığında işlemi yürütün; uzun süren bir işlemdir, çağrı döndürmeden önce fark edilebilir bir gecikme olabilir. Zaman uyumsuz aşırı başka bir iş parçacığı üzerinde işlemi başlatın ve işlemi "arka planda." çalışırken devam etmek çağıran iş parçacığına izin vererek hemen döndürür  
  
### <a name="asynchronous-method-overloads"></a>Zaman uyumsuz yöntem aşırı yüklemeleri  
 Zaman uyumsuz işlemler için olası iki aşırı yüklemesi vardır: tek çağırma ve birden çok çağırma. Yöntem imzaları iki yöntemden birini ayırabilirsiniz: adında ek bir parametre birden çok çağrı formundadır `userState`. Bu formu çağırmak, kodunuz için mümkün kılar `Method1Async(string param, object userState)` birden çok kez olmadan bekleyen zaman uyumsuz işlemler, tamamlanması bekleniyor. Öte yandan, çağırmayı deneyin, `Method1Async(string param)` önceki bir çağrı tamamlanmadan önce yöntemi oluşturur bir <xref:System.InvalidOperationException>.  
  
 `userState` Parametresi birden çok çağrı aşırı yüklemeler için zaman uyumsuz işlemler arasında ayrım yapmak olanak sağlar. Her çağrı için benzersiz bir değer (örneğin, bir GUID veya karma kodu) sağladığınız `Method1Async(string param, object userState)`, ve her bir işlem tamamlandığında, olay işleyicisi işlemi hangi örneğinin tamamlanma olayı belirleyebilirsiniz.  
  
### <a name="tracking-pending-operations"></a>Bekleyen işlemleri izleme  
 Birden çok çağrı aşırı yüklemeleri kullanırsanız, kodunuzu izlemek gerekir `userState` nesneler (görev ID'lerini) için bekleyen görevler. Her çağrı için `Method1Async(string param, object userState)`, genellikle yeni bir oluşturur, benzersiz `userState` nesnesi ve bir koleksiyona ekleyin. Zaman için karşılık gelen görev `userState` nesne tamamlama olayını başlatır, tamamlama yöntemi uygulamanız inceleyeceksiniz <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType> ve, koleksiyondan kaldırır. Bu şekilde kullanılan `userState` parametre alan bir görev kimliği rolü  
  
> [!NOTE]
>  İçin benzersiz bir değer sağlamak dikkatli olmanız gerekir `userState` çağrılarınızı çağırma birden fazla aşırı yüküne de. Benzersiz olmayan görev kimliği zaman uyumsuz sınıfı throw neden olacak bir <xref:System.ArgumentException>.  
  
### <a name="canceling-pending-operations"></a>İşlemleri iptal ediliyor  
 Zaman uyumsuz işlemleri, tamamlanmadan önce herhangi bir zamanda iptal etmek önemlidir. Olay tabanlı zaman uyumsuz desen uygulayan sınıflar olacaktır bir `CancelAsync` yöntemi (yalnızca bir zaman uyumsuz yöntem yoksa) veya bir *MethodName *** AsyncCancel** yöntemi (birden çok zaman uyumsuz yöntem varsa).  
  
 Birden çok çağrılarına izin yöntemleri alır bir `userState` her görev ömrünü izlemek için kullanılan parametre. `CancelAsync` alan bir `userState` parametresini iptal Bekleyen Görevler belirli sağlar.  
  
 Tek bir işlem aynı anda bekleyen gibi destekleyen yöntemler `Method1Async(string param)`, iptal edilemez.  
  
### <a name="receiving-progress-updates-and-incremental-results"></a>Devam eden güncelleştirmelerin ve artımlı sonuçlarını alma  
 Olay tabanlı zaman uyumsuz desene uyar bir sınıf, ilerleme ve artımlı sonuçlarını izlemek için bir olay isteğe bağlı olarak sağlayabilir. Bu genellikle adlandırılacağını `ProgressChanged` veya * MethodName ***ProgressChanged**, ve karşılık gelen kendi olay işleyicisine sürecek bir <xref:System.ComponentModel.ProgressChangedEventArgs> parametresi.  
  
 Olay işleyicisi `ProgressChanged` olay inceleyebilirsiniz <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType> özelliği zaman uyumsuz bir görev yüzde tamamlandı belirlemek için. Bu özellik, 0-100 aralığında ve güncelleştirmek için kullanılabilir <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği bir <xref:System.Windows.Forms.ProgressBar>. Birden çok zaman uyumsuz işlemleri bekleme, kullanabileceğiniz <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType> özelliği işlemi ayırt etmek için ilerleme bildirimi.  
  
 Zaman uyumsuz işlemler devam ederken bazı sınıflar artımlı sonuçlarını bildirebilir. Bu sonuçları, türetilen bir sınıf içinde depolanan <xref:System.ComponentModel.ProgressChangedEventArgs> ve türetilmiş sınıftaki bir özellik olarak görünür. Bu sonuçları için olay işleyicisinde erişebileceğiniz `ProgressChanged` olay, erişmek gibi <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> özelliği. Birden çok zaman uyumsuz işlemleri bekleme, kullanabileceğiniz <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A> işlemi ayırt etmek için özellik artımlı sonuçları raporlama.  
  
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
