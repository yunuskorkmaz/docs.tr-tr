---
title: İş akışından OData akışlarını kullanma-WF
ms.date: 03/30/2017
ms.assetid: 1b26617c-53e9-476a-81af-675c36d95919
ms.openlocfilehash: ceac2c2d07351fcb79e2345068f07fa22f356411
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743785"
---
# <a name="consuming-odata-feeds-from-a-workflow"></a>Bir iş akışından OData akışlarını kullanma

WCF Veri Hizmetleri, temsili durum aktarımı (REST) semantiğini kullanarak Web veya intranet üzerinden veri sunmak ve kullanmak için açık veri Protokolü 'Nü (OData) kullanan hizmetler oluşturmanızı sağlayan bir .NET Framework bileşenidir. OData, verileri URI 'Ler tarafından adreslenebilir kaynaklar olarak kullanıma sunar. Bir HTTP isteği gönderebileceği ve bir veri hizmetinin döndürdüğü OData akışını işlebiliyorsanız, herhangi bir uygulama OData tabanlı bir veri hizmetiyle etkileşim kurabilir. Ayrıca WCF Veri Hizmetleri, .NET Framework uygulamalardan OData akışlarını kullanırken daha zengin bir programlama deneyimi sağlayan istemci kitaplıklarını içerir. Bu konu, istemci kitaplıklarını kullanmadan ve ile bir iş akışında OData akışını kullanmaya genel bir bakış sağlar.

## <a name="using-the-sample-northwind-odata-service"></a>Örnek Northwind OData hizmetini kullanma

Bu konudaki örneklerde <https://services.odata.org/Northwind/Northwind.svc/>konumunda bulunan örnek Northwind veri hizmeti kullanılmaktadır. Bu hizmet [OData SDK 'sının](https://www.odata.org/ecosystem/#sdk) bir parçası olarak sağlanır ve örnek Northwind veritabanına salt okuma erişimi sağlar. Yazma erişimi isteniyorsa veya yerel bir WCF veri hizmeti isteniyorsa, Northwind veritabanına erişim sağlayan yerel bir OData hizmeti oluşturmak için [WCF veri hizmetleri hızlı başlangıç](../data/wcf/quickstart-wcf-data-services.md) adımlarını izleyebilirsiniz. Hızlı başlangıcı izlerseniz, bu konudaki örnek kodda belirtilen bir yerel URI 'yi yerine koyun.

## <a name="consuming-an-odata-feed-using-the-client-libraries"></a>İstemci kitaplıklarını kullanarak OData akışını kullanma

WCF Veri Hizmetleri, .NET Framework ve istemci uygulamalarından bir OData akışını daha kolay bir şekilde kullanmanıza olanak tanıyan istemci kitaplıklarını içerir. Bu kitaplıklar HTTP iletileri göndermeyi ve almayı basitleştirir. Ayrıca, ileti yükünü varlık verilerini temsil eden CLR nesnelerine çevirirler. İstemci kitaplıkları, <xref:System.Data.Services.Client.DataServiceContext> ve <xref:System.Data.Services.Client.DataServiceQuery%601>iki çekirdek sınıfı özelliğidir. Bu sınıflar bir veri hizmetini sorgulamanızı ve ardından döndürülen varlık verileriyle CLR nesneleri olarak çalışmanızı sağlar. Bu bölümde, istemci kitaplıklarını kullanan etkinlikleri oluşturmaya yönelik iki yaklaşım ele alınmaktadır.

### <a name="adding-a-service-reference-to-the-wcf-data-service"></a>WCF veri hizmetine hizmet başvurusu ekleme

Northwind istemci kitaplıklarını oluşturmak için, Northwind OData hizmetine bir başvuru eklemek üzere Visual Studio 2012 ' deki **hizmet başvurusu Ekle** iletişim kutusunu kullanabilirsiniz.

![Hizmet Başvurusu Ekle iletişim kutusunu gösteren ekran görüntüsü.](./media/consuming-odata-feeds-from-a-workflow/add-service-reference-dialog.gif)

Hizmet tarafından sunulan hizmet işlemleri olmadığını ve **Hizmetler** listesinde, Northwind Data Service tarafından sunulan varlıkları temsil eden öğeler olduğunu unutmayın. Hizmet başvurusu eklendiğinde, bu varlıklar için sınıflar oluşturulacaktır ve istemci kodunda kullanılabilirler. Bu konudaki örnekler, sorguları gerçekleştirmek için bu sınıfları ve `NorthwindEntities` sınıfını kullanır.

> [!NOTE]
> Daha fazla bilgi için bkz. [veri hizmeti Istemci kitaplığı oluşturma (WCF veri Hizmetleri)](../data/wcf/generating-the-data-service-client-library-wcf-data-services.md).

### <a name="using-asynchronous-methods"></a>Zaman uyumsuz yöntemler kullanma

Web üzerinden kaynaklara erişirken oluşabilecek olası gecikme sorunlarını gidermek için WCF Veri Hizmetleri zaman uyumsuz olarak erişmenizi öneririz. WCF Veri Hizmetleri istemci kitaplıkları sorguları çağırmak için zaman uyumsuz yöntemler içerir ve Windows Workflow Foundation (WF) zaman uyumsuz etkinlikleri yazmak için <xref:System.Activities.AsyncCodeActivity> sınıfını sağlar. <xref:System.Activities.AsyncCodeActivity> türetilmiş etkinlikler, zaman uyumsuz yöntemlere sahip .NET Framework sınıflarından yararlanmak için yazılabilir veya zaman uyumsuz olarak yürütülecek kod bir yönteme yerleştirilebilir ve bir temsilci kullanılarak çağrılabilir. Bu bölümde, <xref:System.Activities.AsyncCodeActivity> türetilmiş bir etkinliğin iki örneği sunulmaktadır; biri, WCF Veri Hizmetleri istemci kitaplıklarının zaman uyumsuz yöntemlerini ve bir temsilciyi kullanan birini kullanır.

> [!NOTE]
> Daha fazla bilgi için bkz. [zaman uyumsuz işlemler (WCF veri Hizmetleri)](../data/wcf/asynchronous-operations-wcf-data-services.md) ve [zaman uyumsuz etkinlikler oluşturma](creating-asynchronous-activities-in-wf.md).

### <a name="using-client-library-asynchronous-methods"></a>İstemci kitaplığı zaman uyumsuz yöntemlerini kullanma

<xref:System.Data.Services.Client.DataServiceQuery%601> sınıfı, bir OData hizmetini zaman uyumsuz olarak sorgulamak için <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> ve <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> yöntemler sağlar. Bu yöntemler <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> çağrılabilir ve <xref:System.Activities.AsyncCodeActivity> türetilen bir sınıfın geçersiz kılmaları <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> geçersiz kılma döndüğünde, iş akışı boşta geçebilir (ancak kalıcı değil) ve zaman uyumsuz iş tamamlandığında, <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> çalışma zamanı tarafından çağrılır.

Aşağıdaki örnekte, iki giriş bağımsız değişkeni olan bir `OrdersByCustomer` etkinliği tanımlanmıştır. `CustomerId` bağımsız değişkeni döndürülecek siparişleri tanımlayan müşteriyi temsil eder ve `ServiceUri` bağımsız değişkeni Sorgulanacak OData hizmetinin URI 'sini temsil eder. Etkinlik `AsyncCodeActivity<IEnumerable<Order>>` türetildiğinden, sorgunun sonuçlarını döndürmek için kullanılan bir <xref:System.Activities.Activity%601.Result%2A> çıkış bağımsız değişkeni de vardır. <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> override, belirtilen müşterinin tüm emirlerini seçen bir LINQ sorgusu oluşturur. Bu sorgu, geçirilen <xref:System.Activities.AsyncCodeActivityContext><xref:System.Activities.AsyncCodeActivityContext.UserState%2A> olarak belirtilir ve sonra sorgunun <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> yöntemi çağrılır. Sorgunun <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> geçirilen geri çağırma ve durumun, etkinliğin <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> yöntemine geçirilmiş olanlardır olduğunu unutmayın. Sorgunun yürütülmesi bittiğinde, etkinliğin <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> yöntemi çağrılır. Sorgu <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>alınır ve ardından sorgunun <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> yöntemi çağırılır. Bu yöntem, belirtilen varlık türünün bir <xref:System.Collections.Generic.IEnumerable%601> döndürür; Bu durumda `Order`. `IEnumerable<Order>` <xref:System.Activities.AsyncCodeActivity%601>genel türü olduğundan, bu <xref:System.Collections.IEnumerable> etkinliğin <xref:System.Activities.Activity%601.Result%2A> <xref:System.Activities.OutArgument%601> olarak ayarlanır.

[!code-csharp[CFX_WCFDataServicesActivityExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#100)]

Aşağıdaki örnekte, `OrdersByCustomer` etkinliği belirtilen müşteri için siparişlerin bir listesini alır ve ardından <xref:System.Activities.Statements.ForEach%601> bir etkinlik döndürülen siparişleri numaralandırır ve her bir siparişin tarihini konsola yazar.

[!code-csharp[CFX_WCFDataServicesActivityExample#10](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#10)]

Bu iş akışı çağrıldığında, konsola aşağıdaki veriler yazılır:

```console
Calling WCF Data Service...
8/25/1997
10/3/1997
10/13/1997
1/15/1998
3/16/1998
4/9/1998
```

> [!NOTE]
> OData sunucusuyla bağlantı kurulamazsa, aşağıdaki özel duruma benzer bir özel durum alırsınız:
>
> İşlenmeyen özel durum: System. InvalidOperationException: Bu istek işlenirken bir hata oluştu. ---> System .net. WebException: uzak sunucuya bağlanılamıyor---> System .net. Sockets. SocketException: bağlı olan taraf bir süre sonra düzgün bir şekilde yanıt vermediğinden veya bağlantı kurulamadığı için bağlantı girişimi başarısız oldu bağlı konak yanıt veremediği için.

Sorgu tarafından döndürülen verilerin herhangi bir ek işlemesi gerekliyse, etkinliğin <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> geçersiz kılması durumunda yapılabilir. Hem <xref:System.Activities.AsyncCodeActivity%601.BeginExecute%2A> hem de <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> iş akışı iş parçacığı kullanılarak çağrılır ve bu geçersiz Kılmalarda bulunan tüm kodlar zaman uyumsuz olarak çalışmaz. Ek işlem kapsamlı veya uzun süre çalışıyorsa veya sorgu sonuçları disk belleğine alınerirse, sorguyu yürütmek ve zaman uyumsuz olarak ek işlem gerçekleştirmek için bir temsilci kullanan sonraki bölümde ele alınan yaklaşımı göz önünde bulundurmanız gerekir.

### <a name="using-a-delegate"></a>Temsilci kullanma

Bir .NET Framework sınıfın zaman uyumsuz yöntemini çağırmaya ek olarak, <xref:System.Activities.AsyncCodeActivity>tabanlı bir etkinlik, yöntemlerinden birindeki zaman uyumsuz mantığı da tanımlayabilir. Bu yöntem, etkinliğin <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> geçersiz kılmada bir temsilci kullanılarak belirtilir. Yöntem döndüğünde, çalışma zamanı etkinliğin <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> geçersiz kılmayı çağırır. Bir iş akışından OData hizmeti çağrılırken, bu yöntem hizmeti sorgulamak ve ek işleme sağlamak için kullanılabilir.

Aşağıdaki örnekte, bir `ListCustomers` etkinliği tanımlanmıştır. Bu etkinlik, örnek Northwind veri hizmetini sorgular ve Northwind veritabanındaki tüm müşterileri içeren bir `List<Customer>` döndürür. Zaman uyumsuz çalışma `GetCustomers` yöntemi tarafından gerçekleştirilir. Bu yöntem, tüm müşteriler için hizmeti sorgular ve sonra bunları bir `List<Customer>`kopyalar. Sonra sonuçların disk belleğine alınmış olup olmadığını denetler. Bu durumda, bir sonraki sonuç sayfasında hizmeti sorgular, bunları listeye ekler ve tüm müşteri verileri alınana kadar devam eder.

> [!NOTE]
> WCF Veri Hizmetleri disk belleği hakkında daha fazla bilgi için bkz. [nasıl yapılır: disk belleğine yükleme (WCF veri Hizmetleri)](../data/wcf/how-to-load-paged-results-wcf-data-services.md).

Tüm müşteriler eklendikten sonra liste döndürülür. `GetCustomers` Yöntemi etkinliğin <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> geçersiz kılmada belirtilir. Yöntemin bir dönüş değeri olduğundan, yöntemi belirtmek için bir `Func<string, List<Customer>>` oluşturulur.

> [!NOTE]
> Zaman uyumsuz çalışmayı gerçekleştiren yöntemin dönüş değeri yoksa, <xref:System.Func%601>yerine bir <xref:System.Action> kullanılır. Her iki yaklaşımı kullanarak zaman uyumsuz bir örnek oluşturma örnekleri için bkz. [zaman uyumsuz etkinlikler oluşturma](creating-asynchronous-activities-in-wf.md).

Bu <xref:System.Func%601> <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>atanır ve `BeginInvoke` çağrılır. Çağrılacak yöntemin etkinliğin bağımsız değişken ortamına erişimi olmadığından, `ServiceUri` bağımsız değişkeninin değeri ilk parametre olarak geçirilir, geri çağırma ve <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>iletilen durumuyla birlikte. `GetCustomers` döndüğünde, çalışma zamanı <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>çağırır. <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> kod, <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>temsilciyi alır, `EndInvoke`çağırır ve `GetCustomers` yönteminden döndürülen müşterilerin listesi olan sonucu döndürür.

[!code-csharp[CFX_WCFDataServicesActivityExample#200](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#200)]

Aşağıdaki örnekte, `ListCustomers` etkinliği müşterilerin bir listesini alır ve ardından <xref:System.Activities.Statements.ForEach%601> bir etkinlik bunları numaralandırır ve her müşterinin şirket adını ve iletişim adını konsola yazar.

[!code-csharp[CFX_WCFDataServicesActivityExample#20](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#20)]

Bu iş akışı çağrıldığında, konsola aşağıdaki veriler yazılır. Bu sorgu birçok müşteri döndürdüğünden, burada çıktının yalnızca bir kısmı görüntülenir.

```console
Calling WCF Data Service...
Alfreds Futterkiste, Contact: Maria Anders
Ana Trujillo Emparedados y helados, Contact: Ana Trujillo
Antonio Moreno Taquería, Contact: Antonio Moreno
Around the Horn, Contact: Thomas Hardy
Berglunds snabbköp, Contact: Christina Berglund
...
```

## <a name="consuming-an-odata-feed-without-using-the-client-libraries"></a>İstemci kitaplıklarını kullanmadan bir OData akışını kullanma

OData, verileri URI 'Ler tarafından adreslenebilir kaynaklar olarak kullanıma sunar. İstemci kitaplıklarını kullandığınızda bu URI 'Ler sizin için oluşturulur, ancak istemci kitaplıklarını kullanmak zorunda değilsiniz. İsterseniz, OData hizmetlerine istemci kitaplıkları kullanılmadan doğrudan erişilebilir. İstemci kitaplıklarını kullanmadığınız durumlarda hizmetin konumu ve istenen veriler URI tarafından belirtilir ve sonuçlar HTTP isteğine yanıt olarak döndürülür. Bu ham veriler daha sonra, istenen şekilde işlenebilir veya yönetilebilir. Bir OData sorgusunun sonuçlarını almanın bir yolu <xref:System.Net.WebClient> sınıfını kullanmaktır. Bu örnekte, anahtar ALFKI tarafından temsil edilen müşterinin iletişim adı alınır.

[!code-csharp[CFX_WCFDataServicesActivityExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#2)]

Bu kod çalıştırıldığında, konsola aşağıdaki çıktı görüntülenir:

```console
Raw data returned:
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<ContactName xmlns="http://schemas.microsoft.com/ado/2007/08/dataservices">Maria Anders</ContactName>
```

Bir iş akışında, bu örnekteki kod <xref:System.Activities.CodeActivity>tabanlı bir özel etkinliğin <xref:System.Activities.CodeActivity.Execute%2A> geçersiz kılması içine eklenebilir, ancak aynı işlevsellik <xref:System.Activities.Expressions.InvokeMethod%601> etkinliği kullanılarak da gerçekleştirilebilir. <xref:System.Activities.Expressions.InvokeMethod%601> etkinliği, iş akışı yazarlarının bir sınıfın statik ve örnek yöntemlerini çağırmasına ve ayrıca belirtilen yöntemi zaman uyumsuz olarak çağırma seçeneğine sahiptir. Aşağıdaki örnekte, bir <xref:System.Activities.Expressions.InvokeMethod%601> etkinliği <xref:System.Net.WebClient> sınıfının <xref:System.Net.WebClient.DownloadString%2A> yöntemini çağıracak ve müşterilerin listesini döndürecek şekilde yapılandırılmıştır.

[!code-csharp[CFX_WCFDataServicesActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#3)]

<xref:System.Activities.Expressions.InvokeMethod%601>, bir sınıfın hem statik hem de örnek yöntemlerini çağırabilir. <xref:System.Net.WebClient.DownloadString%2A>, <xref:System.Net.WebClient> sınıfının bir örnek yöntemi olduğundan, <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A>için <xref:System.Net.WebClient> sınıfının yeni bir örneği belirtilir. `DownloadString` <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A>olarak belirtilir, sorguyu içeren URI <xref:System.Activities.Expressions.InvokeMethod%601.Parameters%2A> koleksiyonda belirtilir ve dönüş değeri <xref:System.Activities.Activity%601.Result%2A> değere atanır. <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> değeri `true`olarak ayarlanır, bu da yöntem çağrısının iş akışıyla ilgili olarak zaman uyumsuz olarak çalışacağı anlamına gelir. Aşağıdaki örnekte, belirli bir müşterinin siparişlerinin listesi için örnek Northwind veri hizmetini sorgulamak üzere <xref:System.Activities.Expressions.InvokeMethod%601> etkinliğini kullanan bir iş akışı oluşturulur ve ardından döndürülen veriler konsola yazılır.

[!code-csharp[CFX_WCFDataServicesActivityExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#1)]

Bu iş akışı çağrıldığında, konsola aşağıdaki çıktı görüntülenir. Bu sorgu birkaç sipariş döndürdüğünden, burada çıktının yalnızca bir kısmı görüntülenir.

```console
Calling WCF Data Service...
Raw data returned:

<?xml version="1.0" encoding="utf-8" standalone="yes"?>*
<feed
xml:base="http://services.odata.org/Northwind/Northwind.svc/"
xmlns:d="http://schemas.microsoft.com/ado/2007/08/dataservices"
xmlns:m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"
xmlns="http://www.w3.org/2005/Atom">
<title type="text">Orders\</title>
<id>http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI')/Orders\</id>
<updated>2010-05-19T19:37:07Z\</updated>
<link rel="self" title="Orders" href="Orders" />
<entry>
<id>http://services.odata.org/Northwind/Northwind.svc/Orders(10643)\</id>
<title type="text">\</title>
<updated>2010-05-19T19:37:07Z\</updated>
<author>
<name />
</author>
<link rel="edit" title="Order" href="Orders(10643)" />
<link rel="http://schemas.microsoft.com/ado/2007/08/dataservices/related/Customer" type="application/atom+xml;type=entry" title="Customer" href="Orders(10643)/Customer" />
...
```

Bu örnek, iş akışı uygulama yazarlarının bir OData hizmetinden döndürülen ham verileri tüketmek için kullanabileceği bir yöntem sağlar. URI 'Ler kullanarak WCF Veri Hizmetleri erişme hakkında daha fazla bilgi için bkz. [veri hizmeti kaynaklarına erişme (WCF veri Hizmetleri)](../data/wcf/accessing-data-service-resources-wcf-data-services.md) ve [OData: URI kuralları](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).
