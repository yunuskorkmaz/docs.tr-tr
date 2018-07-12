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
ms.openlocfilehash: 0f78ae4b6abacea6fd1240a1472e1de0e625a8e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576213"
---
# <a name="event-based-asynchronous-pattern-overview"></a>Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış
Aynı anda birçok görevi gerçekleştirmenize henüz kullanıcı etkileşimine yanıt verebilir durumda kalması uygulamalar genellikle birden çok iş parçacığı kullanan bir tasarım gerektirir. <xref:System.Threading> Ad alanı, yüksek performanslı birden çok iş parçacıklı uygulamalar oluşturmak için gerekli araçları sağlar, ancak bu araçlarla etkili bir şekilde birden çok iş parçacıklı yazılım mühendislik önemli deneyimiyle gerektirir. Görece basit birden çok iş parçacıklı uygulamalar için <xref:System.ComponentModel.BackgroundWorker> bileşeni, basit bir çözüm sağlar. Daha karmaşık zaman uyumsuz uygulamalar için olay tabanlı zaman uyumsuz desen eklenecek bir sınıf uygulayın.  
  
 Olay tabanlı zaman uyumsuz desen birden çok iş parçacıklı uygulamalar avantajları birçok karmaşık sorunları birden çok iş parçacıklı tasarımında yapısında gizleme çalışırken kullanılabilir hale getirir. Bu deseni destekleyen bir sınıf kullanarak izin:  
  
-   Uygulamanızı kesintiye uğratmadan yüklemeleri ve "" arka planda veritabanı işlemleri gibi uzun süren görevleri gerçekleştirin.  
  
-   Birden çok işlem aynı anda, her tamamlandığında bildirim alma yürütün.  
  
-   Kaynakları ("asılı") durdurmadan kullanılabilir olana kadar bekleyin, uygulamanızın.  
  
-   İle bekleyen zaman uyumsuz işlemler bilinen olaylar ve temsilciler modelini kullanarak iletişim kurar. Olay işleyicileri ve temsilciler kullanma hakkında daha fazla bilgi için bkz: [olayları](../../../docs/standard/events/index.md).  
  
 Olay tabanlı zaman uyumsuz deseni destekleyen bir sınıf adlı bir veya daha fazla yöntemi olacaktır *MethodName ***zaman uyumsuz**. Bu yöntemler, geçerli iş parçacığı üzerinde aynı işlemi zaman uyumlu sürümleri yansıtma. Sınıf de olabilen bir *MethodName *** tamamlandı**  olay ve olabilir bir *MethodName *** AsyncCancel** (ya da yalnızca **CancelAsync**) yöntemi.  
  
 <xref:System.Windows.Forms.PictureBox> Olay tabanlı zaman uyumsuz deseni destekleyen tipik bir bileşendir. Çağırarak bir görüntü zaman uyumlu olarak indirebilirsiniz kendi <xref:System.Windows.Forms.PictureBox.Load%2A> yöntemi, ancak büyük görüntüdür veya ağ bağlantısı yavaş ise, yükleme işlemi tamamlanana kadar uygulamanızın ("askıda") durdurur ve çağrısı <xref:System.Windows.Forms.PictureBox.Load%2A> döndürür.  
  
 Uygulamanızın istiyorsanız görüntünün sırasında çalıştırmaya devam etmesine yüklenirken, çağırabilirsiniz <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> yöntemi ve tanıtıcı <xref:System.Windows.Forms.PictureBox.LoadCompleted> olay, başka bir olay işleme gibi. Çağırdığınızda <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> yöntemi, uygulamanız ("arka planda") ayrı bir iş parçacığı üzerinde indirme devam ederken çalışmaya devam edecek. Olay işleyicisi resim yükleme işlemi tamamlandığında ve olay işleyicisi inceleyebilirsiniz çağrılacağı <xref:System.ComponentModel.AsyncCompletedEventArgs> indirme işlemini başarıyla tamamladığını belirlemek için parametre.  
  
 Zaman uyumsuz bir işlem iptal edilemez olduğunu, olay tabanlı zaman uyumsuz desen gerektirir ve <xref:System.Windows.Forms.PictureBox> denetimi destekler ile bu gereksinim, <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> yöntemi. Çağırma <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> bekleyen indirme durdurma isteği gönderir ve görev iptal ettiğinizde <xref:System.Windows.Forms.PictureBox.LoadCompleted> olayı oluşturulur.  
  
> [!CAUTION]
>  İndirme gibi bitirecek mümkündür <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> istek yapıldığında, bunu <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> iptal isteği yansıtmayabilir. Bu adlı bir *durumunu koşulu* ve birden çok iş parçacıklı programlama içinde yaygın bir sorundur. Birden çok iş parçacıklı programlama sorunları hakkında daha fazla bilgi için bkz: [yönetilen iş parçacığı oluşturma en iyi yöntemler](../../../docs/standard/threading/managed-threading-best-practices.md).  
  
## <a name="characteristics-of-the-event-based-asynchronous-pattern"></a>Olay tabanlı zaman uyumsuz desenin özellikleri  
 Olay tabanlı zaman uyumsuz desen belirli bir sınıf tarafından desteklenen işlemler karmaşıklığına bağlı olarak birden fazla form alabilir. Tek bir basit sınıfları olabilir *MethodName *** zaman uyumsuz** yöntemi ve karşılık gelen *MethodName *** tamamlandı** olay. Daha karmaşık sınıfları birkaç olabilir *MethodName *** zaman uyumsuz** yöntemleri, her bir karşılık gelen *MethodName *** tamamlandı** olay yanı sıra, bu yöntemleri zaman uyumlu sürümleri. Sınıfları isteğe bağlı olarak için her zaman uyumsuz yöntem iptal, raporlama ilerleme ve artımlı sonuçları destekleyebilir.  
  
 Zaman uyumsuz bir yöntem aynı zamanda diğer bekleyen işlemler tamamlanmadan önce kez herhangi bir sayıda çağırmak kodunuzu izin vererek birden çok bekleyen çağrılar (birden çok eşzamanlı başlatma), destekleyebilir. Bu durum doğru şekilde işlememesi her işlemin tamamlanması izlemek için uygulamanızın gerektirebilir.  
  
### <a name="examples-of-the-event-based-asynchronous-pattern"></a>Olay tabanlı zaman uyumsuz desen örnekleri  
 <xref:System.Media.SoundPlayer> Ve <xref:System.Windows.Forms.PictureBox> bileşenleri, olay tabanlı zaman uyumsuz desenin basit uygulamalar'ı temsil eder. <xref:System.Net.WebClient> Ve <xref:System.ComponentModel.BackgroundWorker> bileşenleri daha karmaşık uygulamaları olay tabanlı zaman uyumsuz desenin temsil eder.  
  
 Desen uyumlu bir örnek sınıf bildirimi aşağıdadır:  
  
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
  
 Kurgusal `AsyncExample` sınıfı her ikisi de destek zaman uyumlu ve zaman uyumsuz çağrıları iki yöntem vardır. Zaman uyumlu aşırı herhangi bir yöntem çağrısı gibi davranır ve çağıran iş parçacığı işlemi yürütme; uzun süren bir işlemdir, çağrı döndürmeden önce belirgin bir gecikme olabilir. Zaman uyumsuz aşırı başka bir iş parçacığı işlemi başlatın ve işlemi "arka planda." çalışırken devam etmek çağıran iş parçacığı izin vererek hemen dönün  
  
### <a name="asynchronous-method-overloads"></a>Zaman uyumsuz yöntem aşırı yüklemeleri  
 Potansiyel olarak iki aşırı zaman uyumsuz işlemleri için: tek çağırma ve birden çok çağırma. Kendi yöntemi imzalar iki yöntemden birini ayırabilirsiniz: birden çok çağırma formun adlı ek bir parametreye sahip `userState`. Bu form kodunuzu çağırmak mümkün kılar `Method1Async(string param, object userState)` birden çok kez olmadan beklemede olan tamamlamak için zaman uyumsuz işlemleri bekleniyor. Öte yandan, çağrı çalışırsanız, `Method1Async(string param)` önceki çağrı tamamlanmadan önce yöntemi oluşturur bir <xref:System.InvalidOperationException>.  
  
 `userState` Parametresi birden çok çağırma aşırı yüklemeleri için zaman uyumsuz işlemleri arasında ayrım olanak tanır. Her çağrı için benzersiz bir değer (örneğin, bir GUID veya karma kodu) sağlamak `Method1Async(string param, object userState)`, ve her işlemi tamamlandığında, olay işleyicisi işlemi hangi örneğinin tamamlama olayı belirleyebilirsiniz.  
  
### <a name="tracking-pending-operations"></a>Bekleyen işlemler izleme  
 Birden çok çağırma aşırı kullanırsanız, kodunuzu izlemek gerekir `userState` nesneler (görev kimlikleri) için bekleyen görevler. Her çağrı için `Method1Async(string param, object userState)`, genellikle yeni bir oluşturur, benzersiz `userState` nesne ve bir koleksiyona ekleyin. Zaman için karşılık gelen görev `userState` nesne tamamlama olayını başlatır, tamamlama yöntemi uygulamanız inceleyeceksiniz <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType> ve, koleksiyondan kaldırın. Bu şekilde kullanılan `userState` parametresi alan bir görev kimliği rolü  
  
> [!NOTE]
>  İçin benzersiz bir değer sağlamak dikkatli olmanız gerekir `userState` aramalarınız birden çok çağırma aşırı içinde. Benzersiz olmayan görev kimlikleri zaman uyumsuz sınıfı throw neden olacak bir <xref:System.ArgumentException>.  
  
### <a name="canceling-pending-operations"></a>Bekleyen işlemler iptal etme  
 Zaman uyumsuz işlemleri, tamamlanmadan önce herhangi bir zamanda iptal edebilmek önemlidir. Olay tabanlı zaman uyumsuz desen uygulayan sınıflar sahip olacak bir `CancelAsync` (yalnızca bir zaman uyumsuz yöntem varsa) yöntemi veya *MethodName *** AsyncCancel** (birden çok zaman uyumsuz yöntemleri varsa) yöntemi.  
  
 Birden çok çağrılarına izin yöntemlerini ele bir `userState` her görev ömrü izlemek için kullanılan parametre. `CancelAsync` alan bir `userState` iptal etmek belirli görevler bekleyen sağlar parametresi.  
  
 Yalnızca tek bir işlem aynı anda bekleyen gibi destek yöntemleri `Method1Async(string param)`, iptal edilebilen değildir.  
  
### <a name="receiving-progress-updates-and-incremental-results"></a>İlerleme güncelleştirmeleri ve artımlı sonuçları alma  
 Olay tabanlı zaman uyumsuz desen eklenecek bir sınıf, ilerleme ve artımlı sonuçlarını izlemek için bir olay isteğe bağlı olarak sağlayabilir. Bu genellikle adlandırılacağını `ProgressChanged` veya * MethodName ***ProgressChanged**, ve kendi karşılık gelen olay işleyicisi sürecek bir <xref:System.ComponentModel.ProgressChangedEventArgs> parametresi.  
  
 Olay işleyicisi `ProgressChanged` olay inceleyin <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType> zaman uyumsuz bir görevi yüzdesini tamamlanmış belirlemek için özellik. Bu özellik 0-100 aralığında ve güncelleştirmek için kullanılabilir <xref:System.Windows.Forms.ProgressBar.Value%2A> özelliği bir <xref:System.Windows.Forms.ProgressBar>. Birden çok zaman uyumsuz işlemleri bekleyen yoksa kullanabileceğiniz <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType> hangi işlemi ayırt etmek için özellik ilerleme durumu raporlama.  
  
 Zaman uyumsuz işlemleri devam gibi bazı sınıfları artımlı sonuçlar bildirebilir. Türetilen bir sınıfta bu Sonuçların depolanacağı <xref:System.ComponentModel.ProgressChangedEventArgs> ve türetilmiş sınıf özellikleri olarak görüntülenir. Bu olay işleyicisi sonuçlarında erişebilirsiniz `ProgressChanged` olay, erişim gibi <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> özelliği. Birden çok zaman uyumsuz işlemleri bekleyen yoksa kullanabileceğiniz <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A> hangi işlemi ayırt etmek için özellik artımlı sonuçları raporlama.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 [Nasıl Yapılır: Arka Planda İşlem Çalıştırma](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Olay Tabanlı Zaman Uyumsuz Desenle Çok İş Parçacıklı Programlama](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
