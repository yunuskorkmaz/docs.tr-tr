---
title: Zaman Uyumlu ve Zaman Uyumsuz İşlemler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], synchronous operations
- service contracts [WCF], asynchronous operations
ms.assetid: db8a51cb-67e6-411b-9035-e5821ed350c9
ms.openlocfilehash: 8f2d962f40f2b56b1d1dda68129f477e4277ae1d
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728358"
---
# <a name="synchronous-and-asynchronous-operations"></a>Zaman Uyumlu ve Zaman Uyumsuz İşlemler
Bu konuda, uygulama ve zaman uyumsuz hizmet işlemlerini çağırma anlatılmaktadır.  
  
 Yöntem çağrısının çalışırken yararlı iş yapmadan devam etmek uygulama sağladığından birçok uygulamaları yöntemleri zaman uyumsuz olarak çağırır. Windows Communication Foundation (WCF) hizmetlerini ve istemcilerin zaman uyumsuz işlem çağrıları düzeylerinde WCF uygulamaları karşı etkileşim dengeli verimliliği en üst düzeye çıkarmak için daha fazla esneklik sağlayan iki ayrı uygulama katılabilir .  
  
## <a name="types-of-asynchronous-operations"></a>Zaman uyumsuz işlemleri türleri  
 Tüm hizmet olsun parametre türü WCF içinde sözleşmeler ve dönüş değerleri, WCF öznitelikleri hizmeti ile istemci arasında belirli ileti değişim deseni belirtmek için kullanın. WCF gelen ve giden iletileri uygun hizmet işlemi ya da çalışan istemci kodu otomatik olarak yönlendirir.  
  
 İstemci, yalnızca belirli bir işlem için ileti değişim deseni belirtir hizmet sözleşmesini sahip olur. Temel alınan ileti değişim deseni gözlenir sürece istemciler Geliştirici tercih ettikleri, herhangi bir programlama modeli sunabilir. Belirtilen ileti deseni gözlenir sürece bu nedenle, çok, hizmetleri işlemleri herhangi bir biçimde uygulayabilirsiniz.  
  
 Hizmet sözleşmesi bağımsızlığı hizmet veya istemci uygulamadan WCF uygulamaları zaman uyumsuz yürütme aşağıdaki biçimlerden sağlar:  
  
-   İstemcilerin zaman uyumsuz olarak zaman uyumlu ileti exchange kullanarak istek/yanıt işlemleri çağırabilirsiniz.  
  
-   Hizmetleri zaman uyumsuz olarak zaman uyumlu ileti exchange ile bir istek/yanıt işlemi uygulayabilirsiniz.  
  
-   İleti alışverişlerinde tek yönlü, bağımsız olarak istemci veya hizmet uygulaması olabilir.  
  
### <a name="suggested-asynchronous-scenarios"></a>Önerilen zaman uyumsuz senaryolar  
 İşlemi hizmet uygulaması g/ç iş yapmadan gibi bir engelleme çağrı yaparsa bir hizmet işlemi uygulamasında zaman uyumsuz bir yaklaşım kullanın. Zaman uyumsuz işlemleri ve zaman uyumsuz çağrı yolu mümkün olduğunca genişletmek için yöntemleri çağırmak bir zaman uyumsuz işlem uygulamasında olduğunda deneyin. Örneğin, bir `BeginOperationTwo()` içinden `BeginOperationOne()`.  
  
-   Bir istemci zaman uyumsuz bir yaklaşım veya çağrı yapan uygulamanın şu durumlarda kullanın:  
  
-   Orta katman uygulama işlemlerinden çağırdığınız durumunda. (Bu tür senaryoları hakkında daha fazla bilgi için bkz: [orta katman istemci uygulamaları](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)  
  
-   Bir ASP.NET sayfasının işlemlerini çağırdığınız, zaman uyumsuz sayfalar kullanın.  
  
-   Tek iş parçacıklı, Windows Forms veya Windows Presentation Foundation (WPF) gibi herhangi bir uygulamadan işlemleri çağırdığınız durumunda. Olay tabanlı zaman uyumsuz çağırma modeli kullanılırken, birden çok iş parçacığı kendiniz işlemek gerek kalmadan uygulama yanıt hızını ekleme kullanıcı Arabirimi iş parçacığı üzerinde sonuç olay tetiklenir.  
  
-   Genel olarak, bir zaman uyumlu ve zaman uyumsuz çağrı arasında bir seçim varsa, zaman uyumsuz çağrı seçin.  
  
### <a name="implementing-an-asynchronous-service-operation"></a>Zaman uyumsuz hizmet işlemi uygulama  
 Zaman uyumsuz işlemleri üç aşağıdaki yöntemlerden birini kullanarak uygulanabilir:  
  
1.  Görev tabanlı zaman uyumsuz desen  
  
2.  Olay tabanlı zaman uyumsuz desen  
  
3.  IAsyncResult zaman uyumsuz desen  
  
#### <a name="task-based-asynchronous-pattern"></a>Görev tabanlı zaman uyumsuz desen  
 Görev tabanlı zaman uyumsuz desen kolay ve çoğu düz İleri olduğundan zaman uyumsuz işlemleri uygulamak için önerilen yöntemdir. Bu yöntemi kullanmak için sadece bir hizmet işlemi uygulama ve görev dönüş türünü belirtmeniz\<T >, burada T mantıksal işlem tarafından döndürülen tür. Örneğin:  
  
```csharp  
public class SampleService:ISampleService   
{   
   // ...  
   public async Task<string> SampleMethodTaskAsync(string msg)   
   {   
      return Task<string>.Factory.StartNew(() =>   
      {   
         return msg;   
      });   
   }  
   // ...  
}  
```  
  
 Görev SampleMethodTaskAsync işlemi döndürür\<dize > çünkü mantıksal işlemi bir dize döndürür. Görev tabanlı zaman uyumsuz desen hakkında daha fazla bilgi için bkz: [The Task-Based zaman uyumsuz desen](http://go.microsoft.com/fwlink/?LinkId=232504).  
  
> [!WARNING]
>  Bir özel durum işleminin tamamlanması beklenirken hata oluşursa görev tabanlı zaman uyumsuz desen kullanırken, bir T:System.AggregateException durum. Bu durum istemci ve hizmetler oluşabilir  
  
#### <a name="event-based-asynchronous-pattern"></a>Olay tabanlı zaman uyumsuz desen  
 Olay tabanlı zaman uyumsuz deseni destekleyen bir hizmet MethodNameAsync adlı bir veya daha fazla işlem sahip olur. Bu yöntemler, geçerli iş parçacığı üzerinde aynı işlemi zaman uyumlu sürümleri yansıtma. Sınıf MethodNameCompleted olay da sahip olabilirsiniz ve MethodNameAsyncCancel (veya yalnızca CancelAsync) olabilir yöntemi. Çağrı işlemi isteyen bir istemci işlem tamamlandığında çağrılacak olay işleyicisi tanımlayacaksınız,  
  
 Aşağıdaki kod parçacığını olay tabanlı zaman uyumsuz desen kullanarak zaman uyumsuz işlemleri bildirmeyi gösterilmektedir.  
  
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
  
 Olay tabanlı zaman uyumsuz desen hakkında daha fazla bilgi için bkz: [The Event-Based zaman uyumsuz desen](http://go.microsoft.com/fwlink/?LinkId=232515).  
  
#### <a name="iasyncresult-asynchronous-pattern"></a>IAsyncResult zaman uyumsuz desen  
 Bir hizmet işlemi kullanarak bir zaman uyumsuz biçimde uygulanabilir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zaman uyumsuz desen programlama ve İşaretleme `<Begin>` yöntemiyle <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliğini `true`. Bu durumda, zaman uyumsuz işlem eşzamanlı bir işlem olarak aynı formda meta verilerde sunulur: bir istek iletisi ve ilişkili yanıt iletisi ile tek bir işlem olarak sunulur. İstemci programlama modelleri sonra bir seçeneğiniz vardır. Hizmet çağrıldığında bir istek-yanıt iletisi exchange gerçekleşir sürece, bu deseni eşzamanlı bir işlem veya zaman uyumsuz bir olarak gösterebilir.  
  
 Genel olarak, sistemleri ile zaman uyumsuz yapısı, bir bağımlılık iş parçacıklarında almamalıdır.  Veri geçirme işlemi gönderme işleminin çeşitli aşamaları için en güvenilir yol uzantıları kullanmaktır.  
  
 Bir örnek için bkz: [nasıl yapılır: zaman uyumsuz bir hizmet işlemi uygulama](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).  
  
 Bir sözleşme işlemi tanımlamak için `X` , yürütüldüğünde zaman uyumsuz olarak istemci uygulamasında nasıl çağrılır bağımsız olarak:  
  
-   Desen kullanan iki yöntem tanımlamak `BeginOperation` ve `EndOperation`.  
  
-   `BeginOperation` Yöntemi içerir `in` ve `ref` parametreleri döndürür ve işlem için bir <xref:System.IAsyncResult> türü.  
  
-   `EndOperation` Yöntemi içeren bir <xref:System.IAsyncResult> parametresi yanı sıra `out` ve `ref` parametreleri ve döndürür işlemleri dönüş türü.  
  
 Örneğin, aşağıdaki yöntemi bakın.  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 Zaman uyumsuz bir işlem oluşturmak için iki yöntem olacaktır:  
  
```csharp  
[OperationContract(AsyncPattern=true)]
IAsyncResult BeginDoWork(string data,
                         ref string inout,
                         AsyncCallback callback,
                         object state);
int EndDoWork(ref string inout, out string outonly, IAsyncResult result);  
```  
  
```vb  
<OperationContract(AsyncPattern := True)>
Function BeginDoWork(ByVal data As String, _
                     ByRef inout As String, _
                     ByVal callback As AsyncCallback, _
                     ByVal state As Object) As IAsyncResult
Function EndDoWork(ByRef inout As String, ByRef outonly As String, ByVal result As IAsyncResult) As Integer  
```  
  
> [!NOTE]
>  <xref:System.ServiceModel.OperationContractAttribute> Özniteliği yalnızca uygulanan `BeginDoWork` yöntemi. Adlı bir WSDL işleminde ortaya çıkan sözleşmeyi var `DoWork`.  
  
### <a name="client-side-asynchronous-invocations"></a>İstemci tarafı zaman uyumsuz çağrıları  
 Bir WCF istemci uygulamasının daha önce açıklanan üç zaman uyumsuz çağırma modellerinden herhangi biri kullanabilirsiniz  
  
 Görev tabanlı modeli kullanılırken, yalnızca aşağıdaki kod parçacığında gösterildiği gibi bekleme anahtar kullanarak işlemini çağırın.  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 Olay tabanlı zaman uyumsuz desen kullanma yalnızca--yanıt ve sonuçta elde edilen olay bildirim almak için bir olay işleyicisi kullanıcı arabirimi iş parçacığı üzerinde otomatik olarak tetiklenir ekleme gerektirir. Bu yaklaşımı kullanmak için her ikisini de belirtin **/async** ve **/tcv:Version35** komutu seçenekleri ile [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), aşağıdaki gibi örnek.  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 Bu yapıldığında, Svcutil.exe WCF istemci sınıfı uygulamak ve yanıtını alma ve uygun eylemi gerçekleştirin olay işleyici atamak çağrı yapan uygulamanın sağlayan olay alt yapısı oluşturur. Tam bir örnek için bkz: [nasıl yapılır: hizmet işlemlerini zaman uyumsuz çağrı](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 Olay tabanlı zaman uyumsuz modeli, ancak yalnızca kullanılabilir [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)]. Ayrıca, bile desteklenmez [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] bir WCF istemcisi kanalını oluşturulduğunda kullanarak bir <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. WCF istemci kanalı nesneleriyle kullanmalısınız <xref:System.IAsyncResult?displayProperty=nameWithType> nesneleri işlemlerinizin zaman uyumsuz olarak çağırma. Bu yaklaşımı kullanmak için belirtmek **/async** komut seçeneğiyle [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), aşağıdaki örnekte olduğu gibi.  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 Bu hizmet sözleşmesini oluşturur, her bir işlem olarak Modellenen içinde bir `<Begin>` yöntemiyle <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliğini `true` ve karşılık gelen `<End>` yöntemi. Tam örnek kullanmak için bir <xref:System.ServiceModel.ChannelFactory%601>, bkz: [nasıl yapılır: çağrı işlemlerini zaman uyumsuz olarak kullanarak bir kanal fabrikası](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
 Hizmet eşzamanlı olarak, bir uygulamanın aynı düzeni zaman uyumsuz olarak yerel bir zaman uyumlu yöntemi çağırmak için kullanabileceği aynı şekilde uygulanır olsa bile her iki durumda da, uygulamalar bir işlem zaman uyumsuz olarak çağırabilirsiniz. İşlemi nasıl uygulandığını istemciye önemli değildir; yanıt iletisi geldiğinde içeriğini istemcinin zaman uyumsuz gönderilir <`End`> yöntemi ve istemci bilgilerini alır.  
  
### <a name="one-way-message-exchange-patterns"></a>Tek yönlü ileti Exchange desenleri  
 Zaman uyumsuz ileti değişim deseni tek yönlü hangi işlemleri de oluşturabilirsiniz (işlemleri için hangi <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> olan `true` bağıntılı yanıt sahip) herhangi bir yönde istemci veya hizmet birbirinden gönderilebilecek yan. (Bu çift yönlü ileti değişim deseni tek yönlü iletilerle kullanır.) Bu durumda, hizmet sözleşmesi zaman uyumsuz çağrılar veya uygulamaları ya da değil, uygun taraflardan uygulayabileceğiniz bir tek yönlü ileti değişimi belirtir. Sözleşme tek yönlü iletilerinin bir exchange olduğunda, bir ileti gönderildikten sonra uygulama yanıt beklemez ve diğer iş yapmadan devam etmek için genellikle, uygulamaları büyük ölçüde zaman uyumsuz olabilir.  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a>Olay tabanlı zaman uyumsuz istemcileri ve ileti sözleşmeleri  
 Olay tabanlı zaman uyumsuz modeli için tasarım yönergeleri birden fazla değer döndürülürse, tek bir değer olarak döndürülen durum `Result` özelliği ve diğerleri döndürülür özellikleri olarak üzerinde <xref:System.EventArgs> nesnesi. Bunun bir sonucu olduğundan, bu, istemci olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verilerini alır ve birden fazla değer, varsayılan işlemi döndürürse <xref:System.EventArgs> nesnesi döndüren bir değer olarak `Result` özelliği ve geri kalan özelliklerini <xref:System.EventArgs> nesnesi.  
  
 İleti nesnesi olarak almak istiyorsanız `Result` özelliği ve bu nesne üzerinde özellikleri kullanma gibi döndürülen değerlere sahip **/messageContract** komut seçeneği. Bu olarak yanıt iletisi döndüren bir imza oluşturur `Result` özellikte <xref:System.EventArgs> nesnesi. Tüm iç dönüş değerleri yanıt iletisi nesnesi sonra özellikleridir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
