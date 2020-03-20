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
ms.openlocfilehash: 75a585efcdf316f407f3617fef8e1e279dcd922d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143219"
---
# <a name="synchronous-and-asynchronous-operations"></a>Zaman Uyumlu ve Zaman Uyumsuz İşlemler
Bu konu, eşzamanlı hizmet işlemlerinin uygulanması ve çağrılma konulmaktadır.  
  
 Yöntem çağrısı çalışırken uygulamanın yararlı işler yapmaya devam etmesini sağladığından, birçok uygulama yöntemleri eşzamanlı olarak çağırır. Windows Communication Foundation (WCF) hizmetleri ve istemcileri, WCF uygulamalarına etkileşime karşı dengeli iş bikisini en üst düzeye çıkarmak için daha fazla esneklik sağlayan uygulamanın iki farklı düzeyindeki eşzamanlı operasyon çağrılarına katılabilirler .  
  
## <a name="types-of-asynchronous-operations"></a>Eşzamanlı İşlem Türleri  
 WCF'deki tüm hizmet sözleşmeleri, parametreler türleri ve iade değerleri ne olursa olsun, istemci ve hizmet arasında belirli bir ileti alışverişi deseni belirtmek için WCF özniteliklerini kullanır. WCF, gelen ve giden iletileri otomatik olarak uygun servis çalışmasına veya çalışan istemci koduna yönlendirir.  
  
 İstemci yalnızca belirli bir işlem için ileti alışverişi deseni belirten hizmet sözleşmesine sahip. İstemciler, temel ileti alışverişi deseni gözlendiği sürece geliştiriciye seçtikleri herhangi bir programlama modelini sunabilir. Bu nedenle, belirtilen ileti deseni gözlendiği sürece hizmetler de işlemleri herhangi bir şekilde uygulayabilir.  
  
 Hizmet sözleşmesinin hizmet veya istemci uygulamasından bağımsızlığı, WCF uygulamalarında aşağıdaki eşzamanlı yürütme biçimlerini sağlar:  
  
- İstemciler, eşzamanlı ileti alışverişi kullanarak istek/yanıt işlemlerini eş senkronize olarak çağırabilir.  
  
- Hizmetler, eşzamanlı ileti alışverişi kullanarak bir istek/yanıt işlemini eşit olarak uygulayabilir.  
  
- İleti alışverişi, istemci veya hizmetin uygulanmasından bağımsız olarak tek yönlü olabilir.  
  
### <a name="suggested-asynchronous-scenarios"></a>Önerilen Eşzamanlı Senaryolar  
 İşlem hizmeti uygulaması G/Ç çalışması yapmak gibi bir engelleme çağrısı yaparsa, hizmet işlemi uygulamasında eşzamanlı bir yaklaşım kullanın. Eşzamanlı bir işlem uygulamasındaolduğunuzda, eşzamanlı çağrı yolunu mümkün olduğunca genişletmek için eşzamanlı işlemler ve yöntemler çağırmayı deneyin. Örneğin, içinden `BeginOperationTwo()` `BeginOperationOne()`bir çağrı .  
  
- Aşağıdaki durumlarda istemcide asenkron bir yaklaşım veya arama uygulaması kullanın:  
  
- Orta katmanbir uygulamadan işlem çağrıştırıyorsanız. (Bu tür senaryolar hakkında daha fazla bilgi için [Orta Düzey İstemci Uygulamaları'na](./feature-details/middle-tier-client-applications.md)bakın.)  
  
- ASP.NET bir sayfa içinde işlem çağrıştırıyorsanız, eşzamanlı sayfalar kullanın.  
  
- Windows Forms veya Windows Presentation Foundation (WPF) gibi tek iş parçacığı olan herhangi bir uygulamadan işlem istemiyorsanız. Olay tabanlı eşzamanlı arama modelini kullanırken, sonuç olayı Kullanıcı Arabirimi iş parçacığı üzerinde yükseltilir ve birden çok iş parçacığı kendiniz işlemenize gerek kalmadan uygulamaya yanıt ekler.  
  
- Genel olarak, senkron ve eşzamanlı arama arasında bir seçeneğiniz varsa, eşzamanlı çağrıyı seçin.  
  
### <a name="implementing-an-asynchronous-service-operation"></a>Eşzamanlı Hizmet İşleminin Uygulanması  
 Asynchronous işlemleri aşağıdaki üç yöntemden biri kullanılarak uygulanabilir:  
  
1. Görev tabanlı eşzamanlı desen  
  
2. Olay tabanlı eşzamanlı desen  
  
3. IAsyncResult asynchronous deseni  
  
#### <a name="task-based-asynchronous-pattern"></a>Görev Tabanlı Eşzamanlı Desen  
 Görev tabanlı eşzamanlı desen, en kolay ve en yalındır olduğundan, eşzamanlı işlemleri uygulamanın tercih edilen yoludur. Bu yöntemi kullanmak için yalnızca hizmet işleminizi uygulayın ve T'nin mantıksal işlemtarafından döndürülen tür olduğu Görev\<T>'nin iade türünü belirtin. Örnek:  
  
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
  
 Mantıksal işlem bir dize\<döndürür, çünkü SampleMethodTaskAsync işlemi görev dizesini> döndürür. Görev tabanlı eşenkron desen hakkında daha fazla bilgi için [Görev Tabanlı Asynchronous Deseni'ne](https://go.microsoft.com/fwlink/?LinkId=232504)bakın.  
  
> [!WARNING]
> Görev tabanlı eşsenkronize deseni kullanırken, işlemin tamamlanmasını beklerken bir özel durum oluşursa Bir T:System.AggregateException atılabilir. Bu özel durum istemci veya hizmetler de oluşabilir  
  
#### <a name="event-based-asynchronous-pattern"></a>Olay Tabanlı Asenkron Desen  
 Olay tabanlı Asynchronous Modelini destekleyen bir hizmetin MethodNameAsync adında bir veya daha fazla işlemi olur. Bu yöntemler, geçerli iş parçacığı üzerinde aynı işlemi gerçekleştiren senkron sürümleri yansıtabilir. Sınıfın bir MethodNameCompleted olayı da olabilir ve bir MethodNameAsyncCancel (veya sadece CancelAsync) yöntemi olabilir. İşlemi çağırmak isteyen bir istemci, işlem tamamlandığında çağrılacak bir olay işleyicisi tanımlar,  
  
 Aşağıdaki kod snippet olay tabanlı eşzamanlı desen kullanarak eşzamanlı işlemleri nasıl bildirin gösteriş.  
  
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
  
 Olay tabanlı Asynchronous Deseni hakkında daha fazla bilgi için [Olay Tabanlı Asynchronous Deseni'ne](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)bakın.  
  
#### <a name="iasyncresult-asynchronous-pattern"></a>IAsyncResult Asynchronous Desen  
 Bir hizmet işlemi .NET Framework asynchronous programlama deseni kullanılarak ve `<Begin>` yöntemi <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> `true`'' ye ayarlanan özellik ile işaretleme' kullanılarak eşzamanlı bir şekilde uygulanabilir. Bu durumda, eşzamanlı işlem meta verilerde senkron işlemle aynı biçimde ortaya konur: İstek iletisi ve ilişkili yanıt iletisi ile tek bir işlem olarak ortaya çıkarır. İstemci programlama modelleri daha sonra bir seçim var. Bu deseni eşzamanlı bir işlem olarak veya eşzamanlı bir işlem olarak temsil edebilirler, ancak hizmet çağrıldığı sürece bir istek-yanıt iletisi değişimi gerçekleşir.  
  
 Genel olarak, sistemlerin eşzamanlı doğası ile, iş parçacıkları bir bağımlılık almamalıdır.  Veri işleminin çeşitli aşamalarına veri aktarmanın en güvenilir yolu uzantıları kullanmaktır.  
  
 Örneğin, [bkz.](how-to-implement-an-asynchronous-service-operation.md)  
  
 İstemci uygulamasında `X` nasıl çağrıldığına bakılmaksızın eş senkronize olarak yürütülen bir sözleşme işlemini tanımlamak için:  
  
- Deseni `BeginOperation` kullanarak iki `EndOperation`yöntem tanımlayın ve .  
  
- `BeginOperation` Yöntem, `in` işlem `ref` için parametreleri ve <xref:System.IAsyncResult> parametreleri içerir ve bir tür döndürür.  
  
- Yöntem `EndOperation` bir <xref:System.IAsyncResult> parametre yanı sıra `out` `ref` ve parametreleri içerir ve işlemleri iade türü döndürür.  
  
 Örneğin, aşağıdaki yönteme bakın.  
  
```csharp  
int DoWork(string data, ref string inout, out string outonly)  
```  
  
```vb  
Function DoWork(ByVal data As String, ByRef inout As String, _out outonly As out) As Integer  
```  
  
 Bir eşzamanlı işlem oluşturmak için iki yöntem olacaktır:  
  
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
> Öznitelik <xref:System.ServiceModel.OperationContractAttribute> yalnızca `BeginDoWork` yönteme uygulanır. Ortaya çıkan sözleşmede . `DoWork`  
  
### <a name="client-side-asynchronous-invocations"></a>İstemci Tarafı Asynchronous Çağrıları  
 Bir WCF istemci uygulaması, daha önce açıklanan üç eşzamanlı arama modelinden herhangi birini kullanabilir  
  
 Görev tabanlı modeli kullanırken, aşağıdaki kod snippet'inde gösterildiği gibi bekleme anahtar sözcüklerini kullanarak işlemi aramanız yeterlidir.  
  
```csharp  
await simpleServiceClient.SampleMethodTaskAsync("hello, world");  
```  
  
 Olay tabanlı eşsenkronize deseni kullanmak yalnızca yanıtbildirimi almak için bir olay işleyicisi eklemeyi gerektirir ve ortaya çıkan olay kullanıcı arabirimi iş parçacığında otomatik olarak yükseltilir. Bu yaklaşımı kullanmak için, aşağıdaki örnekte olduğu gibi [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)ile **/async** ve **/tcv:Version35** komut seçeneklerini belirtin.  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async /tcv:Version35  
```  
  
 Bu yapıldığında, Svcutil.exe, çağrı uygulamasının uygulanmasını ve yanıtı alması ve uygun eylemi gerçekleştirmesi için bir olay işleyicisini atamasını sağlayan olay altyapısına sahip bir WCF istemci sınıfı oluşturur. Tam bir örnek için [bkz: Hizmet İşlemleri'ni eşit bir şekilde arayın.](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)  
  
 Ancak olay tabanlı eşzamanlı model yalnızca .NET Framework 3.5'te kullanılabilir. Buna ek olarak, bir WCF istemci kanalı kullanılarak oluşturulduğunda .NET Framework 3.5'te bile <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>desteklenmez. WCF istemci kanal nesneleri ile <xref:System.IAsyncResult?displayProperty=nameWithType> işlemlerinizi eş senkronize olarak çağırmak için nesneleri kullanmanız gerekir. Bu yaklaşımı kullanmak için, aşağıdaki örnekte olduğu gibi [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)ile **/async** komut seçeneğini belirtin.  
  
```console  
svcutil http://localhost:8000/servicemodelsamples/service/mex /async
```  
  
 Bu, her işlemin `<Begin>` ayarlanan <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> özellik `true` ve ilgili `<End>` yöntemle bir yöntem olarak modellendiği bir hizmet sözleşmesi oluşturur. Tam bir <xref:System.ServiceModel.ChannelFactory%601>örnek için , [bkz.](./feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)  
  
 Her iki durumda da, uygulamalar, hizmet eşzamanlı olarak uygulansa bile, aynı şekilde bir uygulama nın eşzamanlı olarak yerel bir eşzamanlı yöntemi çağırmak için aynı deseni kullanabileceği şekilde, eşzamanlı olarak bir işlem başlatabilir. İşlemin nasıl uygulandığı istemci için önemli değildir; Yanıt iletisi geldiğinde, içeriği istemcinin asynchronous <`End`> yöntemine gönderilir ve istemci bilgileri alır.  
  
### <a name="one-way-message-exchange-patterns"></a>Tek Yönlü İleti Değişim Desenleri  
 Ayrıca, tek yönlü işlemlerin <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> (ilişkili `true` yanıtın olmadığı işlemlerin) istemci veya hizmet tarafından diğer taraftan bağımsız olarak her iki yönde de gönderilebildiği bir eşzamanlı ileti değişimi deseni de oluşturabilirsiniz. (Bu, tek yönlü iletilerle çift yönlü ileti alışverişi deseni kullanır.) Bu durumda, hizmet sözleşmesi, her iki tarafın da uygun olduğu şekilde eşzamanlı çağrılar veya uygulamalar olarak uygulayabileceği veya uygulayamayacağı tek yönlü bir ileti alışverişi belirtir. Genellikle, sözleşme tek yönlü iletialışverişi olduğunda, bir ileti gönderildikten sonra uygulama yanıt beklemez ve diğer işleri yapmaya devam edebilir, çünkü uygulamalar büyük ölçüde eşzamanlı olabilir.  
  
### <a name="event-based-asynchronous-clients-and-message-contracts"></a>Olay Tabanlı Asynchronous İstemciler ve İleti Sözleşmeleri  
 Olay tabanlı eşsenkronize modelin tasarım yönergeleri, birden fazla değer döndürülürse, bir `Result` değerin özellik olarak döndürülür <xref:System.EventArgs> ve diğerlerinin nesneüzerinde özellik olarak döndürülür olduğunu belirtir. Bunun bir sonucu, bir istemci olay tabanlı asynchronous komut seçeneklerini kullanarak meta veri aktarırken ve <xref:System.EventArgs> işlem birden fazla `Result` değer döndürürse, varsayılan nesne bir değer döndürür, özellik olarak varsayılan nesne döndürür ve geri kalan <xref:System.EventArgs> nesnenin özellikleridir.  
  
 İleti nesnesini `Result` özellik olarak almak ve döndürülen değerleri bu nesneüzerinde özellik olarak almak istiyorsanız, **/messageContract** komut u seçeneğini kullanın. Bu, `Result` <xref:System.EventArgs> nesneüzerinde özellik olarak yanıt iletisi döndüren bir imza oluşturur. Tüm iç iade değerleri daha sonra yanıt iletisi nesnesinin özellikleridir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A>
- <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A>
