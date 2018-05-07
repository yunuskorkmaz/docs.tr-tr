---
title: Olay Tabanlı Zaman Uyumsuz Deseni Uygulama
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
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
ms.openlocfilehash: 89de0690c0f9788120f7805b0b63c22ecafa6b9c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a>Olay Tabanlı Zaman Uyumsuz Deseni Uygulama
Belirgin gecikmeler maruz kalabilirsiniz bazı işlemler sınıfıyla yazıyorsanız uygulayarak zaman uyumsuz işlevselliği vermiş göz önünde bulundurun [olay tabanlı zaman uyumsuz desene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Olay tabanlı zaman uyumsuz desen zaman uyumsuz özellikler olan bir sınıfı paketlemek için standartlaştırılmış bir yol sağlar. Yardımcı sınıfları ile uygulanırsa, ister <xref:System.ComponentModel.AsyncOperationManager>, sınıfınızın doğru herhangi bir uygulama modeli altında çalışması dahil olmak üzere [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], konsol uygulamaları ve Windows Forms uygulamaları.  
  
 Olay tabanlı zaman uyumsuz desen uygulayan bir örnek için bkz: [nasıl yapılır: olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Basit zaman uyumsuz işlemleri için size gelebilir <xref:System.ComponentModel.BackgroundWorker> uygun bileşeni. Hakkında daha fazla bilgi için <xref:System.ComponentModel.BackgroundWorker>, bkz: [nasıl yapılır: bir işlemi arka planda çalışan](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
 Aşağıdaki listede, olay tabanlı zaman uyumsuz bu konuda tartışılan desen özelliklerini açıklar.  
  
-   Olay tabanlı zaman uyumsuz desen uygulamak için fırsatlar  
  
-   Zaman uyumsuz yöntemleri adlandırma  
  
-   İsteğe bağlı olarak iptal desteği  
  
-   İsteğe bağlı olarak IsBusy özelliği desteği  
  
-   İsteğe bağlı olarak ilerleme durumunu raporlamak için destek sağlar.  
  
-   İsteğe bağlı olarak artımlı sonuçları döndürmek için destek sağlar.  
  
-   Çıkış işleme ve Ref parametreleri yöntemler  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>Olay tabanlı zaman uyumsuz desen uygulamak için fırsatlar  
 Olay tabanlı zaman uyumsuz deseni uygulama göz önünde bulundurun zaman:  
  
-   İstemcileri sınıfınızın gerek kalmaz <xref:System.Threading.WaitHandle> ve <xref:System.IAsyncResult> nesneleri bu yoklama anlamı zaman uyumsuz işlemleri için kullanılabilir ve <xref:System.Threading.WaitHandle.WaitAll%2A> veya <xref:System.Threading.WaitHandle.WaitAny%2A> istemci tarafından oluşturulması gerekir.  
  
-   Tanıdık olay/temsilci modeli ile istemci tarafından yönetilmek üzere zaman uyumsuz işlemleri istiyor.  
  
 Herhangi bir işlem, zaman uyumsuz uygulaması aday olmakla birlikte bu uzun gecikme tabi beklediğiniz düşünülmelidir. İstemciler bir yöntemini çağırın ve tamamlanma, gerekli başka müdahale ile bildirilir işlemleri özellikle uygundur. Düzenli aralıklarla istemcilere ilerleme, artımlı sonuçları veya durum değişiklikleri bildiren sürekli olarak çalışan işlemlerini de uygundur.  
  
 Olay tabanlı zaman uyumsuz desen desteklemeye karar verme hakkında daha fazla bilgi için bkz: [olay tabanlı zaman uyumsuz desen uygulamak için saptarken](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).  
  
## <a name="naming-asynchronous-methods"></a>Zaman uyumsuz yöntemleri adlandırma  
 Her zaman uyumlu yöntemi için *MethodName* zaman uyumsuz bir karşılık gelen sağlamak istediğiniz:  
  
 Tanımlayan bir *MethodName *** zaman uyumsuz** yöntemi:  
  
-   Döndürür `void`.  
  
-   Aynı parametreleri alır *MethodName* yöntemi.  
  
-   Birden çok çağrılarını kabul eder.  
  
 İsteğe bağlı olarak tanımlayan bir *MethodName *** zaman uyumsuz** aşırı yüklemesi, aynı * MethodName ***zaman uyumsuz**, ancak ek bir nesne değerli parametre olarak adlandırılan `userState`. Yönteminize yönelik birden çok eşzamanlı çağrılarını; bu durumda yönetmek için hazırlanmış bunu `userState` değeri yöntemi çağrılarını ayırt etmek için geri tüm olay işleyicileri için teslim. Bunu yapmak tercih edebilirsiniz sonraki alma için kullanıcı durumunu depolamak için yalnızca bir yer olarak.  
  
 Her ayrı için *MethodName *** zaman uyumsuz** yöntemi imza:  
  
1.  Aşağıdaki olay yöntemi ile aynı sınıfta tanımlayın:  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  Aşağıdaki temsilci tanımlayın ve <xref:System.ComponentModel.AsyncCompletedEventArgs>. Bu büyük olasılıkla sınıfının kendisi dışında ancak aynı ad alanında tanımlanır.  
  
    ```vb  
    Public Delegate Sub MethodNameCompletedEventHandler( _  
        ByVal sender As Object, _  
        ByVal e As MethodNameCompletedEventArgs)  
  
    Public Class MethodNameCompletedEventArgs  
        Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As MyReturnType  
    End Property  
    ```  
  
    ```csharp  
    public delegate void MethodNameCompletedEventHandler(object sender,   
        MethodNameCompletedEventArgs e);  
  
    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
    {  
        public MyReturnType Result { get; }  
    }  
    ```  
  
    -   Emin *MethodName *** CompletedEventArgs** sınıfı üyeleri ortaya koyar, salt okunur özellikler ve olmayan alanlar alanları veri bağlamayı Önle gibi.  
  
    -   Herhangi bir tanımlamayın <xref:System.ComponentModel.AsyncCompletedEventArgs>-türetilmiş sınıfları sonuçlar değil yöntemleri için. Yalnızca bir örneğini kullanması <xref:System.ComponentModel.AsyncCompletedEventArgs> kendisi.  
  
        > [!NOTE]
        >  Bunu uygun ve temsilci yeniden kullanmak uygun edilebilir, olduğunda ve <xref:System.ComponentModel.AsyncCompletedEventArgs> türleri. Bu durumda, adlandırma itibaren belirli bir temsilci yöntemi adıyla olarak tutarlı olmaz ve <xref:System.ComponentModel.AsyncCompletedEventArgs> tek bir yönteme bağlı olmaz.  
  
## <a name="optionally-support-cancellation"></a>İsteğe bağlı olarak iptal desteği  
 Zaman uyumsuz işlemleri iptal ediliyor sınıfınız destekleyecekse iptal istemciye aşağıda açıklandığı gibi açık olmamalıdır. İptal destek tanımlamadan önce erişilmesi gereken iki karar noktaları olduğuna dikkat edin:  
  
-   Gelecekteki beklenen eklemeler, dahil olmak üzere sınıfınız iptal destekleyen tek bir zaman uyumsuz işlem var mı?  
  
-   Birden çok bekleyen işlemler iptal desteği zaman uyumsuz işlemleri kullanabilir? Diğer bir deyişle, mu *MethodName *** zaman uyumsuz** yöntemi Al bir `userState` parametresi ve herhangi bitmesini beklemeden birden çok çağrılarına izin?  
  
 Bu iki sorulara verdiğiniz yanıtlar, iptal yönteminizi imzası olması gerektiğini belirlemek için aşağıdaki tabloyu kullanın.  
  
### <a name="visual-basic"></a>Visual Basic  
  
||Desteklenen birden çok eşzamanlı operasyonlar|Bir defada yalnızca bir işlem|  
|------|------------------------------------------------|----------------------------------|  
|Tüm sınıfında bir zaman uyumsuz işlemi|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|Sınıf içinde birden çok zaman uyumsuz işlemler|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a>C#  
  
||Desteklenen birden çok eşzamanlı operasyonlar|Bir defada yalnızca bir işlem|  
|------|------------------------------------------------|----------------------------------|  
|Tüm sınıfında bir zaman uyumsuz işlemi|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|Sınıf içinde birden çok zaman uyumsuz işlemler|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 Tanımlarsanız `CancelAsync(object userState)` yöntemi, istemciler bir nesne üzerinde çağrılan tüm zaman uyumsuz yöntemleri arasında ayrım yeteneğine yapmak için durumu değerlerine seçerken dikkatli, yalnızca tek bir zaman uyumsuz yöntem yönelik tüm çağrılarını arasında olmalıdır.  
  
 Tek zaman uyumsuz işlemi sürüm adı kararı *MethodName *** AsyncCancel** Visual Studio'nun IntelliSense gibi bir tasarım ortamında yöntemi daha kolay bulmak durum üzerinde temel alır. Bu ilgili üyeleri grupları ve zaman uyumsuz işlevselliği ile ilgisi yoktur diğer üyelerinden bunları birbirinden ayırır. Olabileceğini ek bekliyorsanız, zaman uyumsuz işlemleri eklenen sonraki sürümlerde, onu tanımlamak daha iyi `CancelAsync`.  
  
 Yukarıdaki tabloda birden fazla yöntemleri aynı sınıfta tanımlamayın. Bu anlam ifade etmez veya yöntemleri çoğalmasıdır sınıfı arabirimiyle dağıtmayı.  
  
 Bu yöntemleri genellikle hemen döndürür ve işlem olabilir ya da değil gerçekte iptal edebilirsiniz. Olay işleyicisi içinde *MethodName *** tamamlandı** olay *MethodName *** CompletedEventArgs** nesnesini içeren bir `Cancelled` istemcileri belirlemek için kullanabileceğiniz alan olup olmadığını İptal oluştu.  
  
 Açıklanan iptal semantiği tarafından uymanız [olay tabanlı zaman uyumsuz desen uygulamak için en iyi yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-support-the-isbusy-property"></a>İsteğe bağlı olarak IsBusy özelliği desteği  
 Sınıfınızda birden çok eşzamanlı çağrılarını desteklemiyorsa gösterme göz önünde bulundurun bir `IsBusy` özelliği. Bu belirlemek geliştiriciler sağlar olup bir *MethodName *** zaman uyumsuz** yöntemi bir özel durumundan yakalama olmadan çalıştığı *MethodName *** zaman uyumsuz** yöntemi.  
  
 Tarafından uymanız `IsBusy` semantiği açıklanan [olay tabanlı zaman uyumsuz desen uygulamak için en iyi yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-progress-reporting"></a>İsteğe bağlı olarak ilerleme durumunu raporlamak için destek sağlar.  
 İlerleme durumunu raporlamak zaman uyumsuz bir işlem, işlem sırasında için sık istenen bir durumdur. Olay tabanlı zaman uyumsuz desen, bunu yapmak için bir kılavuz sağlar.  
  
-   İsteğe bağlı olarak zaman uyumsuz işlemi tarafından oluşturulan ve uygun iş parçacığında çağrılan bir olayı tanımlayın. <xref:System.ComponentModel.ProgressChangedEventArgs> Nesne 0 ile 100 arasında olması beklenir bir tamsayı değerli İlerleme göstergesi taşır.  
  
-   Bu olay şu şekilde ad:  
  
    -   `ProgressChanged` sınıfın birden çok zaman uyumsuz işlemler vardır (veya birden çok zaman uyumsuz işlemleri gelecek sürümlerde içerecek şekilde ulaşması için beklenen);  
  
    -   *MethodName *** ProgressChanged** sınıfın tek bir zaman uyumsuz işlemi varsa.  
  
     Bu adlandırma seçim iptal yöntemi için yapılan isteğe bağlı destek iptal bölümünde açıklandığı gibi paraleldir.  
  
 Bu olay kullanması gereken <xref:System.ComponentModel.ProgressChangedEventHandler> temsilci imza ve <xref:System.ComponentModel.ProgressChangedEventArgs> sınıfı. Bir etki alanına özgü daha İlerleme göstergesi (örneği, okunan bayt ve bir yükleme işlemi için toplam bayt sayısı için) sağlanan, alternatif olarak, daha sonra türetilen bir sınıfı tanımlamanız gerekir <xref:System.ComponentModel.ProgressChangedEventArgs>.  
  
 Yalnızca bir tane olduğunu unutmayın `ProgressChanged` veya *MethodName *** ProgressChanged** destekliyorsa zaman uyumsuz yöntemleri sayısından bağımsız olarak sınıfı için olay. İstemciler, kullanılacak beklenir `userState` geçirilir nesne *MethodName *** zaman uyumsuz** ilerleme güncelleştirmeleri birden çok eşzamanlı operasyonlar arasında ayrım yapmak için yöntemleri.  
  
 Devam eden birden çok işlemlerini desteklemek ve her farklı bir İlerleme göstergesi döndürür durumlar olabilir. Bu durumda, tek bir `ProgressChanged` olay uygun değilse ve birden çok destekleme düşünebilirsiniz `ProgressChanged` olaylar. Bu durumda, bir adlandırma desenini kullanarak *MethodName *** ProgressChanged** her *MethodName *** zaman uyumsuz** yöntemi.  
  
 Açıklanan ilerleme durumu raporlama semantiğini tarafından uymanız [olay tabanlı zaman uyumsuz desen uygulamak için en iyi yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a>İsteğe bağlı olarak artımlı sonuçları döndürmek için destek sağlar.  
 Bazen zaman uyumsuz bir işlem tamamlama önce artımlı sonuçlar döndürebilir. Bu senaryoyu desteklemek için kullanılabilir seçenekleri mevcuttur. Bazı örnekler şöyledir.  
  
### <a name="single-operation-class"></a>Tek işlem sınıfı  
 Sınıfınızda yalnızca tek bir zaman uyumsuz işlem destekler ve bu işlem artımlı sonuçları sonra iade etme olanağınız ise:  
  
-   Genişletme <xref:System.ComponentModel.ProgressChangedEventArgs> artımlı sonuç verileri taşımak için yazın ve tanımlayan bir *MethodName *** ProgressChanged** bu genişletilmiş veri olayla.  
  
-   Bu yükseltme *MethodName *** ProgressChanged** rapor için artımlı bir sonuç olduğunda olay.  
  
 Olarak "tüm işlemler", artımlı sonuçları döndürmek için gerçekleşen aynı olay ile herhangi bir sorun olduğundan bu çözüm özellikle tek zaman uyumsuz işlemi sınıfa uygulanır *MethodName *** ProgressChanged** olay yapar.  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>Türdeş artımlı sonuçlarla birden çok işlem sınıfı  
 Bu durumda, birden çok zaman uyumsuz yöntemleri, artımlı sonuçları döndüren her özellikli sınıfınız destekler ve tüm bu artımlı sonuçları aynı veri türüne sahip.  
  
 Aynı olarak tek işlem sınıfları için yukarıda açıklanan modelini izler <xref:System.EventArgs> yapısı için tüm artımlı sonuçları çalışır. Tanımlayan bir `ProgressChanged` olay yerine bir *MethodName *** ProgressChanged** olay bu yana birden çok zaman uyumsuz yöntemleri için geçerlidir.  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>Heterojen artımlı sonuçlarla birden çok işlem sınıfı  
 Sınıfınızda birden çok zaman uyumsuz yöntemleri destekliyorsa, her farklı bir veri türü döndüren yapmanız gerekir:  
  
-   Raporlama, ilerleme durumu raporlama artımlı Sonuç kümenizi ayırın.  
  
-   Ayrı bir tanımlamak *MethodName *** ProgressChanged** uygun olayla <xref:System.EventArgs> için bu yöntemin artımlı sonuç verileri işlemek her zaman uyumsuz yöntem.  
  
 Bölümünde açıklandığı gibi uygun iş parçacığı üzerinde olay işleyicisi çağırma [olay tabanlı zaman uyumsuz desen uygulamak için en iyi yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a>Çıkış işleme ve Ref parametreleri yöntemler  
 Ancak kullanımını `out` ve `ref` olan genel olarak, .NET Framework'teki, burada önerilmez kuralları mevcut olduğunda izleyin:  
  
 Zaman uyumlu yöntemi verilen *MethodName*:  
  
-   `out` parametreleri *MethodName* parçası olmamalıdır *MethodName ***zaman uyumsuz**. Bunun yerine, bir parçası olmalıdır *MethodName *** CompletedEventArgs**  , parametre olarak eşdeğer olarak aynı ada sahip *MethodName* (daha uygun bir ad olmadıkça).  
  
-   `ref` parametreleri *MethodName* parçası olarak görünmesi gereken *MethodName ***zaman uyumsuz**ve bir parçası olarak *MethodName *** CompletedEventArgs**  eşdeğer olarak, parametre olarak aynı ada sahip *MethodName* (daha uygun bir ad olmadıkça).  
  
 Örneğin, verilen:  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 Zaman uyumsuz yöntem ve kendi <xref:System.ComponentModel.AsyncCompletedEventArgs> sınıfı şuna benzeyebilir:  
  
```vb  
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)  
  
Public Class MethodNameCompletedEventArgs  
    Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As Integer   
    End Property  
    Public ReadOnly Property Arg2() As String   
    End Property  
    Public ReadOnly Property Arg3() As String   
    End Property  
End Class  
```  
  
```csharp  
public void MethodNameAsync(string arg1, string arg2);  
  
public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
{  
    public int Result { get; };  
    public string Arg2 { get; };  
    public string Arg3 { get; };  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [Nasıl Yapılır: Arka Planda İşlem Çalıştırma](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [Olay Tabanlı Zaman Uyumsuz Desenle Çok İş Parçacıklı Programlama](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
