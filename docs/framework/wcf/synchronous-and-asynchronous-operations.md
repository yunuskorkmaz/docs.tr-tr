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
ms.openlocfilehash: c2948cf76f7763eae51689973346965bc6c720a8
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361569"
---
# <a name="synchronous-and-asynchronous-operations"></a>Zaman Uyumlu ve Zaman Uyumsuz İşlemler
Bu konuda, uygulama ve zaman uyumsuz hizmet işlemleri çağırma anlatılmaktadır.  
  
 Yöntem çağrısının çalışırken yararlı iş yapmadan devam etmek uygulamayı sağladığından, birçok uygulama yöntemler zaman uyumsuz olarak çağırır. Windows Communication Foundation (WCF) hizmet ve istemcileri, WCF uygulamaları göre etkileşim olanağı sunan aktarım hızını en üst düzeye çıkarmak için daha fazla esneklik sağlayan iki farklı düzeyde uygulama zaman uyumsuz işlem çağrıları katılabilir .  
  
## <a name="types-of-asynchronous-operations"></a>Zaman uyumsuz işlemlerin türleri  
 Tüm hizmet ne olursa olsun parametre türleri WCF, sözleşmeler ve dönüş değerleri, WCF öznitelikleri, hizmet ve istemci arasında belirli bir ileti değişim deseni belirtin kullanacağınız. WCF uygun bir hizmet işlemi ya da çalışan istemci kodu gelen ve giden iletileri otomatik olarak yönlendirir.  
  
 İstemci, yalnızca belirli bir işlem için ileti değişim deseni belirtir hizmet sözleşmesini sahiptir. Temel alınan ileti değişim deseni gözlemlenen sürece istemciler Geliştirici tercih ettikleri herhangi bir programlama modeli sunabilir. Belirtilen iletiyi deseni gözlemlenen sürece bu nedenle, çok, hizmetleri işlemleri herhangi bir şekilde uygulayabilir.  
  
 Hizmet sözleşmesinin bağımsızlığı hizmet veya istemci uygulamadan WCF uygulamalarında zaman uyumsuz yürütme aşağıdaki biçimleri sağlar:  
  
-   İstemciler, zaman uyumsuz olarak bir eş zamanlı ileti alışverişi kullanarak istek/yanıt işlemleri çalıştırabilirsiniz.  
  
-   Hizmetleri, zaman uyumsuz olarak bir eş zamanlı ileti alışverişi kullanarak bir istek/yanıt işlemi uygulayabilir.  
  
-   Mesaj tek yönlü istemci veya hizmet ne olursa olsun uygulaması olabilir.  
  
### <a name="suggested-asynchronous-scenarios"></a>Önerilen zaman uyumsuz senaryolar  
 İşlemi hizmet uygulaması g/ç iş yapmak gibi bir engelleme çağrı yaparsa bir hizmet işlemi uygulamasında zaman uyumsuz bir yaklaşım kullanın. Zaman uyumsuz işlem uygulama olduğunda zaman uyumsuz işlemler ve zaman uyumsuz çağrı yolun mümkün olduğunca uzak onaylamaktan genişletmek için yöntemleri çağırmayı deneyin. Örneğin, bir `BeginOperationTwo()` içinden `BeginOperationOne()`.  
  
-   Zaman uyumsuz bir yaklaşım istemcisinde veya çağıran uygulama aşağıdaki durumlarda kullanın:  
  
-   Bir orta katman uygulamasından işlemleri çağırdığınız durumunda. (Bu tür senaryolar hakkında daha fazla bilgi için bkz. [orta katman istemci uygulamaları](../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).)  
  
-   ASP.NET sayfası içinde işlemleri çağırdığınız, zaman uyumsuz sayfalar kullanın.  
  
-   Tek iş parçacıklı, Windows Forms veya Windows Presentation Foundation (WPF) gibi herhangi bir uygulamadan işlemleri çağırdığınız durumunda. Olay tabanlı zaman uyumsuz çağırma modeli kullanılırken, sonuç olay yanıt hızını kendiniz birden çok iş parçacığı işlemeye gerek kalmadan uygulamaya ekleme UI iş parçacığı üzerinde oluşturulur.  
  
-   Genel olarak, zaman uyumlu ve zaman uyumsuz bir çağrı arasında seçim yapma varsa, zaman uyumsuz çağrı'ı seçin.  
  
### <a name="implementing-an-asynchronous-service-operation"></a>Zaman uyumsuz bir hizmet işlemi uygulama  
 Aşağıdaki üç yöntemden birini kullanarak zaman uyumsuz işlemler uygulanabilir:  
  
1.  Görev tabanlı zaman uyumsuz desen  
  
2.  Olay tabanlı zaman uyumsuz desen  
  
3.  IAsyncResult zaman uyumsuz desen  
  
#### <a name="task-based-asynchronous-pattern"></a>Görev tabanlı zaman uyumsuz desen  
 Görev tabanlı zaman uyumsuz desen, kolay ve oldukça büyük olduğundan zaman uyumsuz işlemleri uygulamak için tercih edilen yoludur. Bu yöntemi kullanmak için yalnızca, bir hizmet işlemi uygulama ve görev dönüş türü belirtin\<T >, burada T mantıksal işlem tarafından döndürülen türdür. Örneğin:  
  
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
  
 Görev SampleMethodTaskAsync işlemi döndürür\<dizesi > çünkü mantıksal işlemi bir dize döndürür. Görev tabanlı zaman uyumsuz desen hakkında daha fazla bilgi için bkz: [The Task-Based zaman uyumsuz desen](https://go.microsoft.com/fwlink/?LinkId=232504).  
  
> [!WARNING]
>  Üzerinde işlemin tamamlanması beklenirken bir özel durum oluştuğu takdirde görev tabanlı zaman uyumsuz deseni kullanılırken, bir T:System.AggregateException durum. Bu durum istemci veya hizmet oluşabilir.  
  
#### <a name="event-based-asynchronous-pattern"></a>Olay tabanlı zaman uyumsuz desen  
 Olay tabanlı zaman uyumsuz deseni destekleyen bir hizmet MethodNameAsync adlı bir veya daha fazla işlem gerekir. Bu yöntemler, zaman uyumlu sürümler, geçerli iş parçacığında aynı işlemi yansıtma. Sınıfı ayrıca MethodNameCompleted olay olabilir ve bir MethodNameAsyncCancel (veya yalnızca CancelAsync) olabilir yöntemi. İşlem çağırma isteyen bir istemci işlemi tamamlandığında çağrılacak bir olay işleyicisi tanımlar,  
  
 Aşağıdaki kod parçacığı, olay tabanlı zaman uyumsuz deseni kullanarak zaman uyumsuz işlemleri nasıl gösterir.  
  
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
  
 Olay tabanlı zaman uyumsuz desen hakkında daha fazla bilgi için bkz: [The Event-Based zaman uyumsuz desen](https://go.microsoft.com/fwlink/?LinkId=232515).  
  
#### <a name="iasyncresult-asynchronous-pattern"></a>IAsyncResult zaman uyumsuz desen  
 Bir zaman uyumsuz bir biçimde kullanarak bir hizmet işlemi uygulanabilir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zaman uyumsuz desen programlama ve İşaretleme `<Begin>` yöntemiyle <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliğini `true`. Bu durumda, zaman uyumsuz işlemi eşzamanlı bir işlem olarak aynı biçiminde meta veriler de sağlanmaktadır: bir istek iletisi ve ilişkili yanıt iletisi ile tek bir işlem olarak sunulur. İstemci programlama modelleri ardından seçeneğiniz vardır. Hizmet çağrıldığında bir istek-yanıt iletisi exchange gerçekleşmeden sürece, bu düzen eşzamanlı bir işlem veya zaman uyumsuz bir olarak gösterebilir.  
  
 Genel olarak, sistemleri ile zaman uyumsuz yapısı, bir bağımlılık iş parçacıklarında almamalıdır.  En güvenilir veri geçirme işlemi gönderme işleminin çeşitli aşamaları için uzantıları kullanmak için yoludur.  
  
 Bir örnek için bkz. [nasıl yapılır: zaman uyumsuz bir hizmet işlemi uygulama](../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).  
  
 Bir sözleşme işlemi tanımlamak için `X` , yürütüldüğünde zaman uyumsuz olarak istemci uygulamasına nasıl adlandırılır bağımsız olarak:  
  
-   Desenini kullanarak, iki definovat `BeginOperation` ve `EndOperation`.  
  
-   `BeginOperation` İncludes yöntemi `in` ve `ref` döndürür ve işlem parametreleri bir <xref:System.IAsyncResult> türü.  
  
-   `EndOperation` Yöntemi içeren bir <xref:System.IAsyncResult> parametresi hem de `out` ve `ref` parametreleri ve işlemleri döndürür dönüş türü.  
  
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
>  <xref:System.ServiceModel.OperationContractAttribute> Özniteliği yalnızca uygulandığında `BeginDoWork` yöntemi. Elde edilen sözleşmesi adlı tek bir WSDL işlem sahip `DoWork`.  
  
### <a name="client-side-asynchronous-invocations"></a>İstemci tarafı zaman uyumsuz çağrılar  
 WCF istemci uygulaması daha önce açıklanan üç zaman uyumsuz çağırma model dilediğinizi kullanabilirsiniz  
  
 Görev tabanlı modeli kullanılırken, aşağıdaki kod parçacığında gösterildiği gibi await anahtar sözcüğü kullanılarak işlemi çağırarak yeterlidir.  
  
```  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 Olay tabanlı zaman uyumsuz desen kullanma yalnızca yanıt--ve sonuçta elde edilen olay bildirim almak için bir olay işleyicisi kullanıcı arabirimi iş parçacığı üzerinde otomatik olarak oluşturulan ekleme gerektirir. Bu yaklaşımı kullanmak için her ikisini birden belirtin **/async** ve **/tcv:Version35** komutu seçeneklerle [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), aşağıdaki gibi örnek.  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 Bu yapıldığında, bir WCF istemcisi sınıfı uygulamak ve uygun eylemi gerçekleştirin ve yanıt almak için bir olay işleyicisi atamak çağıran uygulama sağlayan bir olay altyapı Svcutil.exe oluşturur. Tam bir örnek için bkz. [nasıl yapılır: hizmet işlemlerini zaman uyumsuz çağrı](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 Olay tabanlı zaman uyumsuz model, ancak yalnızca kullanılabilir [!INCLUDE[netfx35_long](../../../includes/netfx35-long-md.md)]. Ayrıca, bu bile desteklenmez [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] bir WCF istemcisi kanalını oluşturulduğunda kullanarak bir <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. WCF istemci kanal nesneleriyle kullanmalısınız <xref:System.IAsyncResult?displayProperty=nameWithType> işlemlerinizi zaman uyumsuz olarak çağrılacak nesneleri. Bu yaklaşımı kullanmak için belirtin **/async** komut seçeneğiyle [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), aşağıdaki örnekte olduğu gibi.  
  
```  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 Bu hizmet sözleşmesini oluşturur, her bir işlem olarak modellenir içinde bir `<Begin>` yöntemiyle <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliğini `true` ve karşılık gelen `<End>` yöntemi. Kullanarak tam bir örnek için bir <xref:System.ServiceModel.ChannelFactory%601>, bkz: [nasıl yapılır: çağrı işlemlerini zaman uyumsuz olarak kullanarak kanal fabrikası](../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
 Hizmet eşzamanlı olarak, bir uygulama zaman uyumsuz olarak yerel bir zaman uyumlu yöntem çağırmak için aynı yöntemi kullanabileceğiniz aynı şekilde uygulanır olsa bile her iki durumda da, uygulamaları bir işlem zaman uyumsuz olarak çağırabilirsiniz. İşleminin nasıl uygulandığını istemciye önemli değildir; yanıt iletisi geldiğinde içeriğini istemcinin zaman uyumsuz gönderilir <`End`> yöntemi ve istemcinin bilgileri alır.  
  
### <a name="one-way-message-exchange-patterns"></a>Tek yönlü mesaj Exchange desenleri  
 Bir zaman uyumsuz ileti değişim deseni tek yönlü hangi işlemleri oluşturabilirsiniz (hangi işlemleri <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> olduğu `true` bağıntılı yanıt sahip) herhangi bir yönde birbirinden hizmet ve istemci tarafından gönderilen yan. (Bu çift yönlü ileti değişim deseni ile tek yönlü iletilerini kullanır.) Bu durumda, hizmet sözleşmesi zaman uyumsuz çağrıları veya uygulamaları ya da değil, uygun şekilde, her iki tarafında uygulayan bir tek yönlü mesaj exchange belirtir. Sözleşmenin bir exchange tek yönlü bir ileti olduğunda, bir ileti gönderildikten sonra uygulama için bir yanıt beklemez'yı ve başka çalışma yapmaya devam edebilirsiniz genel olarak, uygulamaları büyük ölçüde zaman uyumsuz olabilir.  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a>Olay tabanlı zaman uyumsuz istemcileri ve ileti sözleşmeleri  
 Olay tabanlı zaman uyumsuz model için tasarım yönergeleri birden fazla değer döndürmüyorsa, bir değer olarak döndürülen durum `Result` özelliği ve diğerleri döndürülür özellikleri olarak üzerinde <xref:System.EventArgs> nesne. Bunun bir sonucu olduğundan, bu, bir istemci, olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verilerini içeri aktarır ve işlemin birden fazla değer, varsayılan döndürürse <xref:System.EventArgs> nesnesini bir değer olarak döndürür `Result` özelliği ve kalan özelliklerini <xref:System.EventArgs> nesne.  
  
 İleti nesnesi olarak almak istiyorsanız `Result` özelliği ve o nesnenin özellikleri olarak döndürülen değerlerin **/messageContract** seçeneği komutu. Bu yanıt iletisi olarak döndüren bir imza oluşturur `Result` özelliği <xref:System.EventArgs> nesne. Tüm iç dönüş değerleri ardından yanıt iletisi nesnenin özellikleridir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>  
 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
