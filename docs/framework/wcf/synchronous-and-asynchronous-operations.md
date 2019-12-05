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
ms.openlocfilehash: 143cc0f4566d86f1d42ebd11063f9af3c1ec331f
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802446"
---
# <a name="synchronous-and-asynchronous-operations"></a>Zaman Uyumlu ve Zaman Uyumsuz İşlemler
Bu konuda, zaman uyumsuz hizmet işlemlerini uygulama ve çağırma ele alınmaktadır.  
  
 Birçok uygulama yöntemi zaman uyumsuz olarak çağırır, çünkü Yöntem çağrısı çalıştırılırken uygulamanın faydalı iş yapmaya devam etmesine olanak sağlar. Windows Communication Foundation (WCF) Hizmetleri ve istemcileri, uygulamanın iki farklı düzeyinde zaman uyumsuz işlem çağrılarına katılabilir ve bu da, WCF uygulamalarının etkileşime karşı dengeli hale getirme hızını en üst düzeye çıkarmak için daha fazla esneklik sağlar .  
  
## <a name="types-of-asynchronous-operations"></a>Zaman uyumsuz Işlem türleri  
 WCF 'deki tüm hizmet sözleşmeleri, parametre türleri ve dönüş değerleri ne olduğuna bakılmaksızın, istemci ve hizmet arasında belirli bir ileti değişim modelini belirtmek için WCF özniteliklerini kullanır. WCF gelen ve giden iletileri otomatik olarak uygun hizmet işlemine yönlendirir veya istemci kodu çalıştırır.  
  
 İstemci yalnızca belirli bir işlem için ileti değişim modelini belirten hizmet sözleşmesine sahip olur. Temel alınan ileti değişim modeli gözlemlendiği sürece, istemciler geliştiriciyi istedikleri programlama modeline sunabilir. Bu nedenle, çok sayıda, belirtilen ileti deseninin gözlemlendiği sürece işlemleri herhangi bir şekilde uygulayabilir.  
  
 Hizmet sözleşmesinin hizmet veya istemci uygulamasından bağımsız olması, WCF uygulamalarında aşağıdaki zaman uyumsuz yürütme biçimlerini sunar:  
  
- İstemciler zaman uyumsuz olarak istek/yanıt işlemlerini zaman uyumsuz bir ileti değişimi kullanarak çağırabilir.  
  
- Hizmetler, zaman uyumsuz bir ileti alışverişi kullanarak istek/yanıt işlemini zaman uyumsuz olarak uygulayabilir.  
  
- İleti alışverişi, istemci veya hizmet uygulanmadığına bakılmaksızın tek yönlü olabilir.  
  
### <a name="suggested-asynchronous-scenarios"></a>Önerilen zaman uyumsuz senaryolar  
 İşlem hizmeti kullanımı, g/ç işi gibi bir engelleme çağrısı yapıyorsa, bir hizmet işlemi uygulamasında zaman uyumsuz bir yaklaşım kullanın. Zaman uyumsuz bir işlem uygulamasında olduğunuzda, zaman uyumsuz çağrı yolunu mümkün olduğunca uzatmak için zaman uyumsuz işlemleri ve yöntemleri çağırmayı deneyin. Örneğin, `BeginOperationOne()`içinden bir `BeginOperationTwo()` çağırın.  
  
- Bir istemcide zaman uyumsuz bir yaklaşım kullanın veya aşağıdaki durumlarda uygulama çağırma:  
  
- İşlemleri bir orta katmanlı uygulamadan çağırdıysanız. (Bu senaryolar hakkında daha fazla bilgi için bkz. [Orta katman Istemci uygulamaları](./feature-details/middle-tier-client-applications.md).)  
  
- İşlemleri bir ASP.NET sayfasında çağırdıysanız zaman uyumsuz sayfalar kullanın.  
  
- Windows Forms veya Windows Presentation Foundation (WPF) gibi tek iş parçacıklı herhangi bir uygulamadan işlem çağırdıysanız. Olay tabanlı zaman uyumsuz çağrı modelini kullanırken, sonuç olayı kullanıcı arabirimi iş parçacığında tetiklenir ve birden çok iş parçacığını kendiniz işleyebilmeniz gerekmeden uygulamaya yanıt verme işlemi yapılır.  
  
- Genel olarak, zaman uyumlu ve zaman uyumsuz çağrı arasında seçim yaptıysanız, zaman uyumsuz çağrıyı seçin.  
  
### <a name="implementing-an-asynchronous-service-operation"></a>Zaman uyumsuz bir hizmet Işlemi uygulama  
 Zaman uyumsuz işlemler, aşağıdaki üç yöntemden biri kullanılarak uygulanabilir:  
  
1. Görev tabanlı zaman uyumsuz model  
  
2. Olay tabanlı zaman uyumsuz model  
  
3. IAsyncResult zaman uyumsuz model  
  
#### <a name="task-based-asynchronous-pattern"></a>Görev tabanlı zaman uyumsuz model  
 Görev tabanlı zaman uyumsuz model, zaman uyumsuz işlemleri uygulamak için tercih edilen bir yoldur çünkü en kolay ve en basit yoldur. Bu yöntemi kullanmak için yalnızca hizmet işleminizi uygulayın ve\<T > görevin bir dönüş türünü belirtin; burada T mantıksal işlem tarafından döndürülen türdür. Örneğin:  
  
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
  
 SampleMethodTaskAsync işlemi, mantıksal işlem bir dize döndürdüğünden\<dize > döndürür. Görev tabanlı zaman uyumsuz model hakkında daha fazla bilgi için, bkz. [görev tabanlı zaman uyumsuz model](https://go.microsoft.com/fwlink/?LinkId=232504).  
  
> [!WARNING]
> Görev tabanlı zaman uyumsuz model kullanılırken, işlemin tamamlanması beklenirken bir özel durum oluşursa bir T:System.AggregateException oluşturulabilir. Bu özel durum istemci veya hizmetlerde oluşabilir  
  
#### <a name="event-based-asynchronous-pattern"></a>Olay tabanlı zaman uyumsuz model  
 Olay tabanlı zaman uyumsuz deseninin desteklendiği bir hizmetin MethodNameAsync adlı bir veya daha fazla işlemi olacaktır. Bu yöntemler, geçerli iş parçacığında aynı işlemi gerçekleştiren zaman uyumlu sürümleri yansıtabilir. Sınıfta Ayrıca bir MethodNameCompleted olayı olabilir ve bir MethodNameAsyncCancel (ya da yalnızca bir algıladığında Lasync) yöntemi olabilir. İşlemi çağırmak isteyen bir istemci, işlem tamamlandığında çağrılacak bir olay işleyicisi tanımlar,  
  
 Aşağıdaki kod parçacığında, olay tabanlı zaman uyumsuz model kullanılarak zaman uyumsuz işlemlerin nasıl bildirildiği gösterilmektedir.  
  
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
  
 Olay tabanlı zaman uyumsuz model hakkında daha fazla bilgi için bkz. [olay tabanlı zaman uyumsuz model](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
#### <a name="iasyncresult-asynchronous-pattern"></a>IAsyncResult zaman uyumsuz model  
 Bir hizmet işlemi .NET Framework zaman uyumsuz programlama modelini kullanarak zaman uyumsuz bir biçimde uygulanabilir ve `<Begin>` yöntemi <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliği `true`olarak işaretleniyor. Bu durumda, zaman uyumsuz işlem eşzamanlı bir işlemle aynı biçimde meta verilerde kullanıma sunulur: istek iletisi ve bağıntılı yanıt iletisi ile tek bir işlem olarak sunulur. İstemci programlama modellerinin bir seçimi vardır. Bu model, zaman uyumlu bir işlem olarak veya zaman uyumsuz bir işlem olarak temsil edebilirler, bu nedenle hizmetin bir istek çağrıldığı zaman yanıt iletisi değişimi gerçekleştirilir.  
  
 Genel olarak, sistemlerin zaman uyumsuz doğası ile iş parçacıkları üzerinde bir bağımlılık almanız gerekmez.  İşlem gönderme işleminin çeşitli aşamalarına veri geçirmenin en güvenilir yolu, uzantıları kullanmaktır.  
  
 Bir örnek için bkz. [nasıl yapılır: zaman uyumsuz bir hizmet Işlemi uygulama](how-to-implement-an-asynchronous-service-operation.md).  
  
 İstemci uygulamasında nasıl çağrdığına bakılmaksızın zaman uyumsuz olarak yürütülen `X` bir sözleşme işlemi tanımlamak için:  
  
- `BeginOperation` ve `EndOperation`düzenlerini kullanarak iki yöntem tanımlayın.  
  
- `BeginOperation` yöntemi, işlem için `in` ve `ref` parametrelerini içerir ve bir <xref:System.IAsyncResult> türü döndürür.  
  
- `EndOperation` yöntemi, `out` ve `ref` parametrelerinin yanı sıra <xref:System.IAsyncResult> bir parametre içerir ve işlemler dönüş türünü döndürür.  
  
 Örneğin, aşağıdaki yöntemine bakın.  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 Zaman uyumsuz bir işlem oluşturmak için iki yöntem şöyle olacaktır:  
  
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
> <xref:System.ServiceModel.OperationContractAttribute> özniteliği yalnızca `BeginDoWork` yöntemine uygulanır. Elde edilen sözleşmede `DoWork`adlı bir WSDL işlemi vardır.  
  
### <a name="client-side-asynchronous-invocations"></a>İstemci tarafı zaman uyumsuz çağırmaları  
 WCF istemci uygulaması, daha önce açıklanan üç zaman uyumsuz çağrı modelini kullanabilir  
  
 Görev tabanlı modeli kullanırken, aşağıdaki kod parçacığında gösterildiği gibi await anahtar sözcüğünü kullanarak işlemi çağırmanız yeterlidir.  
  
```csharp  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 Olay tabanlı zaman uyumsuz düzenin kullanılması yalnızca yanıtın bildirimini almak için bir olay işleyicisinin eklenmesini gerektirir ve sonuçta elde edilen olay kullanıcı arabirimi iş parçacığında otomatik olarak oluşturulur. Bu yaklaşımı kullanmak için, aşağıdaki örnekte olduğu gibi, **/Async** ve **/tcv: Version35** komut seçeneklerini [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)ile birlikte belirtin.  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 Bu tamamlandığında, Svcutil. exe, çağıran uygulamanın, yanıtı almak ve uygun eylemi gerçekleştirmek için bir olay işleyicisi uygulayıp atamasını sağlayan olay altyapısına sahip bir WCF istemci sınıfı oluşturur. Tüm bir örnek için bkz. [nasıl yapılır: hizmet Işlemlerini zaman uyumsuz olarak çağırma](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 Ancak, olay tabanlı zaman uyumsuz model yalnızca .NET Framework 3,5 ' de kullanılabilir. Ayrıca, bir <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>kullanılarak WCF istemci kanalı oluşturulduğunda .NET Framework 3,5 ' de de desteklenmez. WCF istemci kanalı nesneleri ile işlemlerinizi zaman uyumsuz olarak çağırmak için <xref:System.IAsyncResult?displayProperty=nameWithType> nesneleri kullanmanız gerekir. Bu yaklaşımı kullanmak için, aşağıdaki örnekte olduğu gibi [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)ile **/Async** komut seçeneğini belirtin.  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async   
```  
  
 Bu, her bir işlemin, <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özelliği `true` ve karşılık gelen bir `<End>` yöntemi olarak ayarlandığı `<Begin>` yöntemi olarak modellendiği bir hizmet sözleşmesi oluşturur. <xref:System.ServiceModel.ChannelFactory%601>kullanan bir örnek için bkz. [nasıl yapılır: bir kanal fabrikası kullanarak Işlemleri zaman uyumsuz olarak çağırma](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).  
  
 Her iki durumda da, bir uygulamanın zaman uyumsuz olarak yerel bir zaman uyumlu yöntemi çağırmak için aynı şekli kullanabilmesi gibi, uygulamalar zaman uyumsuz olarak bir işlemi çağırabilir. İşlemin nasıl uygulandığı, istemci için önemli değildir; Yanıt iletisi geldiğinde, içeriği istemcinin zaman uyumsuz <`End`> yöntemine gönderilir ve istemci bilgileri alır.  
  
### <a name="one-way-message-exchange-patterns"></a>Tek yönlü Ileti değişimi desenleri  
 Ayrıca, tek yönlü işlemlerin (<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> `true` ilişkili yanıt olmayan işlemler) istemci ya da hizmet tarafından diğer taraftan bağımsız olarak gönderilebileceği zaman uyumsuz ileti değişim düzenlerini de oluşturabilirsiniz. (Bu, çift yönlü ileti değişim modelini tek yönlü iletilerle kullanır.) Bu durumda, hizmet sözleşmesi, her iki tarafın da uygun olmayan zaman uyumsuz çağrılar veya uygulamalar olarak uygulayabilirler tek yönlü bir ileti değişimi belirtir. Genellikle, sözleşme tek yönlü bir ileti alışverişi olduğunda, bir ileti gönderildiğinde uygulama bir yanıt beklemez ve diğer işleri yapmaya devam edebileceğinden uygulamalar büyük ölçüde zaman uyumsuz olabilir.  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a>Olay tabanlı zaman uyumsuz Istemciler ve Ileti sözleşmeleri  
 Olay tabanlı zaman uyumsuz model için, birden fazla değer döndürülürse, bir değer `Result` özellik olarak döndürülür ve diğerleri <xref:System.EventArgs> nesnesi üzerinde özellikler olarak döndürülür. Bunun sonucunda, bir istemci, olay tabanlı zaman uyumsuz komut seçeneklerini kullanarak meta verileri içeri aktardığında ve işlem birden fazla değer döndürürse, varsayılan <xref:System.EventArgs> nesnesi bir değeri `Result` özelliği olarak döndürür ve geri kalan <xref:System.EventArgs> nesnesinin özellikleridir.  
  
 İleti nesnesini `Result` özelliği olarak almak ve döndürülen değerlerin bu nesnede özellikler olarak elde etmek istiyorsanız, **/MessageContract** komut seçeneğini kullanın. Bu, <xref:System.EventArgs> nesnesinde `Result` özelliği olarak yanıt iletisini döndüren bir imza oluşturur. Tüm iç dönüş değerleri, yanıt iletisi nesnesinin özellikleridir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
