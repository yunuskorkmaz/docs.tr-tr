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
ms.openlocfilehash: 3cb38cd9d7b27ab28b602e4e4c813d58d904abd3
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2018
ms.locfileid: "47436329"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a>Olay Tabanlı Zaman Uyumsuz Deseni Uygulama
Bir sınıf belirgin gecikmeler kaynaklanabilecek bazı işlemleri yazıyorsanız uygulayarak zaman uyumsuz işlevleri vererek göz önünde bulundurun [olay tabanlı zaman uyumsuz desene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Olay tabanlı zaman uyumsuz desen, zaman uyumsuz özellikler sahip bir sınıf paketlemek için standartlaştırılmış bir yol sağlar. Yardımcı sınıfları ile uygulanması durumunda ister <xref:System.ComponentModel.AsyncOperationManager>, sınıfınızın herhangi bir uygulama modeli altında düzgün çalışması dahil olmak üzere [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], konsol uygulamaları ve Windows Forms uygulamaları.  
  
 Olay tabanlı zaman uyumsuz desen uygulayan bir örnek için bkz: [nasıl yapılır: olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Zaman uyumsuz işlemleri için basit, ilginizi çekebilecek <xref:System.ComponentModel.BackgroundWorker> uygun bileşeni. Hakkında daha fazla bilgi için <xref:System.ComponentModel.BackgroundWorker>, bkz: [nasıl yapılır: arka planda işlem çalıştırma](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
 Aşağıdaki listede, olay tabanlı zaman uyumsuz bu konuda tartışılan düzen özelliklerini açıklar.  
  
-   Olay tabanlı zaman uyumsuz desen uygulamak için fırsatlar  
  
-   Zaman uyumsuz yöntemler Adlandırma  
  
-   İsteğe bağlı olarak, iptal desteği  
  
-   İsteğe bağlı olarak IsBusy özelliği desteği  
  
-   İsteğe bağlı olarak ilerleme durumunu raporlamak için destek sağlar.  
  
-   İsteğe bağlı olarak artımlı sonuçları döndürmek için destek sağlar.  
  
-   Yöntemlerde Ref parametreleri ve çıkış işleme  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>Olay tabanlı zaman uyumsuz desen uygulamak için fırsatlar  
 Olay tabanlı zaman uyumsuz deseni uygulama göz önünde bulundurun olduğunda:  
  
-   Sınıfınızın istemciler gerekmez <xref:System.Threading.WaitHandle> ve <xref:System.IAsyncResult> anlamına gelir, yoklama zaman uyumsuz işlemler için kullanılabilir nesneleri ve <xref:System.Threading.WaitHandle.WaitAll%2A> veya <xref:System.Threading.WaitHandle.WaitAny%2A> istemci tarafından oluşturulması gerekir.  
  
-   Tanıdık olay temsilci modeli ile istemci tarafından yönetilmek üzere zaman uyumsuz işlemler kullanmanız gerekir.  
  
 Herhangi bir işlem zaman uyumsuz bir uygulama için bir aday olsa da bu uzun gecikmeleri uygulanmaya beklediğiniz düşünülmelidir. İstemciler bir yöntemi çağırabilir ve, tamamlanması gereken başka müdahale ile bildirilir operations özellikle uygundur. Ayrıca, düzenli aralıklarla istemcileri ilerleme durumunu, artımlı sonuçları veya durum değişiklikleri bildiren sürekli olarak çalışan işlemleri uygundur.  
  
 Olay tabanlı zaman uyumsuz deseni destekleyen ne zaman karar vermeyle ilgili daha fazla bilgi için bkz: [olay tabanlı zaman uyumsuz desen uygulamak için verirken](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).  
  
## <a name="naming-asynchronous-methods"></a>Zaman uyumsuz yöntemler Adlandırma  
 Her bir zaman uyumlu yöntemin *MethodName* zaman uyumsuz bir karşılığı sağlamak istediğiniz:  
  
 Tanımlayan bir _MethodName_**zaman uyumsuz** yöntemi:  
  
-   Döndürür `void`.  
  
-   Aynı parametreleri alan *MethodName* yöntemi.  
  
-   Birden çok çağrılarını kabul eder.  
  
 İsteğe bağlı olarak tanımlayan bir _MethodName_**zaman uyumsuz** aşırı yükleme, aynı _MethodName_**zaman uyumsuz**, ancak bir ek nesne değerli adlı parametreyi `userState`. Bu durumda birden çok eş zamanlı, yöntem çağrılarını yönetmek için hazır olmanız durumunda bunu `userState` değeri, yöntem çağrılarını ayırt etmek için geri tüm olay işleyicilerine gönderilir. Bunu yapmak de tercih edebilirsiniz sonraki alma için kullanıcı durumunu depolamak için yalnızca bir yer olarak.  
  
 Her ayrı için _MethodName_**zaman uyumsuz** yöntem imzası:  
  
1.  Aşağıdaki olay yöntemi olarak aynı sınıftaki tanımlayın:  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  Aşağıdaki temsilciyi tanımlamasına ve <xref:System.ComponentModel.AsyncCompletedEventArgs>. Bunlar büyük olasılıkla sınıfın kendisi dışında ancak aynı ad alanında tanımlanır.  
  
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
  
    -   Emin _MethodName_**CompletedEventArgs** sınıfı gösterir üyelerine salt okunur özellikler ve alanları değil alanları veri bağlamayı Önle gibi.  
  
    -   Tüm tanımlamazsanız <xref:System.ComponentModel.AsyncCompletedEventArgs>-türetilmiş sınıflar için sonuçlar üretmez yöntemleri. Yalnızca bir örneğini kullanması <xref:System.ComponentModel.AsyncCompletedEventArgs> kendisi.  
  
        > [!NOTE]
        >  Bunun uygulanabilir ve temsilci yeniden kullanmak uygun edilebilir, ve <xref:System.ComponentModel.AsyncCompletedEventArgs> türleri. Bu durumda, adlandırma beri belirli bir temsilci yöntemi adıyla olarak tutarlı olmayacaktır ve <xref:System.ComponentModel.AsyncCompletedEventArgs> tek bir yönteme bağlı olmaz.  
  
## <a name="optionally-support-cancellation"></a>İsteğe bağlı olarak, iptal desteği  
 Zaman uyumsuz işlemleri iptal ediliyor sınıfınıza destekleyecekse, iptal aşağıda açıklandığı gibi istemciye açılmamalıdır. İptal desteği tanımlamadan önce erişilmesi gereken iki karar noktaları olduğuna dikkat edin:  
  
-   Gelecekteki beklenen eklemeler, dahil olmak üzere, kendi sınıfınızı iptali destekler yalnızca tek bir zaman uyumsuz işlem var mı?  
  
-   İptal etme desteği birden fazla bekleyen işlemler zaman uyumsuz işlemleri yapabilirsiniz? Diğer bir deyişle, mu _MethodName_**zaman uyumsuz** yöntemi Al bir `userState` parametresi ve herhangi tamamlanmasını beklemeden birden çok çağrılarına izin vermediğinden?  
  
 Bu iki soruların yanıtlarını aşağıdaki tabloda, iptal için imzası olması gerektiğini belirlemek için kullanın.  
  
### <a name="visual-basic"></a>Visual Basic  
  
||Desteklenen birden çok eşzamanlı operasyonlar|Aynı anda yalnızca tek bir işlem|  
|------|------------------------------------------------|----------------------------------|  
|Sınıfın tamamı tek bir zaman uyumsuz işlemle|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|Sınıfta birden çok zaman uyumsuz işlemler|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a>C#  
  
||Desteklenen birden çok eşzamanlı operasyonlar|Aynı anda yalnızca tek bir işlem|  
|------|------------------------------------------------|----------------------------------|  
|Sınıfın tamamı tek bir zaman uyumsuz işlemle|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|Sınıfta birden çok zaman uyumsuz işlemler|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 Tanımlarsanız `CancelAsync(object userState)` yöntemi, istemcilerin bunları özellikli olan nesne üzerinde çağrılan tüm zaman uyumsuz yöntemler arasında ayrım yapmak için durum değerleri seçerken dikkatli ve yalnızca tek bir zaman uyumsuz yöntemin tüm çağrıları arasında olmalıdır.  
  
 Tek zaman uyumsuz işlem sürüm adı kararı _MethodName_**AsyncCancel** yöntemi Visual Studio IntelliSense gibi bir tasarım ortamında daha kolay bulmak için temel alır. Bu, ilgili üyeleri grupları ve bunları zaman uyumsuz işlevleri ile ilgisi olan diğer üyelerinden ayırır. Olabileceğini ek bekliyorsanız zaman uyumsuz işlemler eklenir sonraki sürümlerinde, onu tanımlamak daha iyi `CancelAsync`.  
  
 Yukarıdaki tabloda birden fazla yöntemleri aynı sınıfta tanımlamaz. Anlam ifade etmez veya sınıf arabirimi yöntemleri bir yaygınlaşmasının ile dağıtmayı.  
  
 Bu yöntemler genellikle hemen döndürür ve işlem olabilir ya da gerçekte iptal. İçin olay işleyicisinde _MethodName_**tamamlandı** olay _MethodName_**CompletedEventArgs** nesne içeren bir `Cancelled` alanı istemciler iptal oluşup oluşmadığını belirlemek için kullanabilirsiniz.  
  
 Tarafından açıklanan iptal semantiği uymayı [olay tabanlı zaman uyumsuz desen uygulamak için en iyi yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-support-the-isbusy-property"></a>İsteğe bağlı olarak IsBusy özelliği desteği  
 Sınıfınız birden çok eş zamanlı çağrılarını desteklemiyor ise kullanıma sunmak isteyebilirsiniz bir `IsBusy` özelliği. Bu hizmet sayesinde geliştiriciler belirlemek için olup olmadığını bir _MethodName_**zaman uyumsuz** yöntemi, bir özel durum yakalama olmadan çalışıyor _MethodName_**zaman uyumsuz**  yöntemi.  
  
 Tarafından uymayı `IsBusy` semantiği açıklanan [olay tabanlı zaman uyumsuz desen uygulamak için en iyi yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-progress-reporting"></a>İsteğe bağlı olarak ilerleme durumunu raporlamak için destek sağlar.  
 Bu, işlemi sırasında ilerlemeyi rapor için zaman uyumsuz bir işlem için sık istenen bir durumdur. Olay tabanlı zaman uyumsuz desen, bunu yapmak için bir kılavuz sağlar.  
  
-   İsteğe bağlı olarak zaman uyumsuz işlemi tarafından oluşturuldu ve uygun iş parçacığında çağrılan bir olay tanımlayın. <xref:System.ComponentModel.ProgressChangedEventArgs> Nesne 0 ile 100 arasında olması beklenir bir tamsayı değerli İlerleme göstergesi taşır.  
  
-   Bu olay şu şekilde adlandırın:  
  
    -   `ProgressChanged` sınıfı birden çok zaman uyumsuz işlemleri vardır (veya gelecek sürümlerde birden çok zaman uyumsuz işlemler içerecek şekilde ulaşması için bekleniyor);  
  
    -   _MethodName_**ProgressChanged** sınıfın tek bir zaman uyumsuz işlem varsa.  
  
     Bu adlandırma seçimi iptal yöntem için yapılan isteğe bağlı olarak destek iptal bölümünde açıklandığı gibi paraleldir.  
  
 Bu olay kullanması gereken <xref:System.ComponentModel.ProgressChangedEventHandler> temsilci imzası ve <xref:System.ComponentModel.ProgressChangedEventArgs> sınıfı. Bir etki alanına özgü daha İlerleme göstergesi (için örnek, okunan bayt ve bir yükleme işlemi için toplam bayt) sağlanabilir, alternatif olarak, ardından, türetilmiş bir sınıf, tanımlamalıdır <xref:System.ComponentModel.ProgressChangedEventArgs>.  
  
 Yalnızca bir tane olduğunu unutmayın `ProgressChanged` veya _MethodName_**ProgressChanged** destekliyorsa, zaman uyumsuz yöntemler sayısından bağımsız olarak, sınıf için olay. İstemciler, kullanılacak beklenir `userState` geçirilen nesne _MethodName_**zaman uyumsuz** birden fazla eşzamanlı işlem üzerinde devam eden güncelleştirmelerin arasında ayrım yapmak için yöntemleri.  
  
 Devam eden birden çok işlem desteği ve her ilerleme durumu için farklı bir göstergesini döndürür durumlar olabilir. Bu durumda, tek bir `ProgressChanged` olay uygun değilse ve birden fazla destekleyici düşünebilirsiniz `ProgressChanged` olayları. Bu durumda, bir adlandırma desenini kullanın _MethodName_**ProgressChanged** her _MethodName_**zaman uyumsuz** yöntemi.  
  
 Açıklanan ilerleme durumunu bildirme semantiği tarafından uymayı [olay tabanlı zaman uyumsuz desen uygulamak için en iyi yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a>İsteğe bağlı olarak artımlı sonuçları döndürmek için destek sağlar.  
 Bazen zaman uyumsuz bir işlemi tamamlama önce artımlı sonuçlar döndürebilir. Bu senaryoyu desteklemek için kullanılan birkaç seçenek vardır. Aşağıda bazı örnekler verilmektedir.  
  
### <a name="single-operation-class"></a>Tek işlem sınıfı  
 Sınıfınıza yalnızca tek bir zaman uyumsuz işlem destekler ve bu işlemin ardından artımlı sonuçları döndürmek için ise:  
  
-   Genişletme <xref:System.ComponentModel.ProgressChangedEventArgs> artımlı sonuç verilerini taşımak için yazın ve tanımlamak bir _MethodName_**ProgressChanged** bu veri genişletilmiş olay.  
  
-   Bu yükseltme _MethodName_**ProgressChanged** rapor için artımlı bir sonuç olduğunda olay.  
  
 Aynı olay olarak "tüm işlemleri", artımlı sonuçları döndürmek için gerçekleşen herhangi bir sorun olduğundan bu çözüm, özellikle bir tek zaman uyumsuz işlemi sınıf için geçerlidir. _MethodName_**ProgressChanged**  olay yok.  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>Artımlı homojen sonuçlarla birden çok işlem sınıfı  
 Bu durumda, sınıfınız birden çok zaman uyumsuz yöntem, artımlı sonuç döndürme özelliği destekler ve bu artımlı sonuçları tüm verilerin aynı türe sahip.  
  
 Aynı olarak tek işlem sınıflar için yukarıda açıklanan modelini <xref:System.EventArgs> yapısı için tüm artımlı sonuçları çalışır. Tanımlayan bir `ProgressChanged` olay yerine bir _MethodName_**ProgressChanged** olduğundan, birden çok zaman uyumsuz yöntemler için geçerli olay.  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>Heterojen artımlı sonuçlarla birden çok işlem sınıfı  
 Birden çok zaman uyumsuz yöntemler sınıfınıza destekliyorsa, her farklı bir veri türü döndüren şunları yapmalısınız:  
  
-   Raporlama, ilerleme durumunu raporlama artımlı sonuç ayırın.  
  
-   Ayrı bir tanımlama _MethodName_**ProgressChanged** olay uygun <xref:System.EventArgs> her zaman uyumsuz yöntemin bu yöntemin sonucu artımlı verileri işlemek.  
  
 Bu olay işleyicisi uygun iş parçacığında içinde açıklanan şekilde çağırır [olay tabanlı zaman uyumsuz desen uygulamak için en iyi yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a>Yöntemlerde Ref parametreleri ve çıkış işleme  
 Ancak kullanımını `out` ve `ref` olduğundan, genel olarak, .NET Framework, burada önerilmez kurallarının mevcut olduğunda izleyin:  
  
 Zaman uyumlu bir yöntem verilen *MethodName*:  
  
-   `out` parametreleri *MethodName* parçası olmamalıdır _MethodName_**zaman uyumsuz**. Bunun yerine, bir parçası olmalıdır _MethodName_**CompletedEventArgs** eşdeğer parametre olarak aynı ada sahip *MethodName* (olmadığı sürece daha uygun adı).  
  
-   `ref` parametreleri *MethodName* parçası olarak görünmesi gereken _MethodName_**zaman uyumsuz**ve bir parçası olarak _MethodName_  **CompletedEventArgs** eşdeğer parametre olarak aynı ada sahip *MethodName* (olmadığı sürece daha uygun bir ad).  
  
 Örneğin, verilen:  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 Zaman uyumsuz yönteminizi ve kendi <xref:System.ComponentModel.AsyncCompletedEventArgs> sınıfı şuna benzeyecektir:  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.ProgressChangedEventArgs>  
- <xref:System.ComponentModel.AsyncCompletedEventArgs>  
- [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
- [Nasıl Yapılır: Arka Planda İşlem Çalıştırma](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
- [Nasıl yapılır: Arka Plan İşlemi Kullanan Bir Form Uygulama](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
- [Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
- [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
