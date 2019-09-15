---
title: İş akışından OData akışlarını kullanma-WF
ms.date: 03/30/2017
ms.assetid: 1b26617c-53e9-476a-81af-675c36d95919
ms.openlocfilehash: e7cfa138a01719988586f9dce0a9009bea643076
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989765"
---
# <a name="consuming-odata-feeds-from-a-workflow"></a>Bir iş akışından OData akışlarını kullanma

WCF Veri Hizmetleri, temsili durum aktarımı (REST) semantiğini kullanarak Web veya intranet üzerinden veri sunmak ve kullanmak için açık veri Protokolü 'Nü (OData) kullanan hizmetler oluşturmanızı sağlayan bir .NET Framework bileşenidir. OData, verileri URI 'Ler tarafından adreslenebilir kaynaklar olarak kullanıma sunar. Bir HTTP isteği gönderebileceği ve bir veri hizmetinin döndürdüğü OData akışını işlebiliyorsanız, herhangi bir uygulama OData tabanlı bir veri hizmetiyle etkileşim kurabilir. Ayrıca WCF Veri Hizmetleri, .NET Framework uygulamalardan OData akışlarını kullanırken daha zengin bir programlama deneyimi sağlayan istemci kitaplıklarını içerir. Bu konu, istemci kitaplıklarını kullanmadan ve ile bir iş akışında OData akışını kullanmaya genel bir bakış sağlar.

## <a name="using-the-sample-northwind-odata-service"></a>Örnek Northwind OData hizmetini kullanma

Bu konudaki örneklerde konumunda <https://services.odata.org/Northwind/Northwind.svc/>bulunan örnek Northwind veri hizmeti kullanılmaktadır. Bu hizmet [OData SDK 'sının](https://go.microsoft.com/fwlink/?LinkID=185248) bir parçası olarak sağlanır ve örnek Northwind veritabanına salt okuma erişimi sağlar. Yazma erişimi isteniyorsa veya yerel bir WCF veri hizmeti isteniyorsa, Northwind veritabanına erişim sağlayan yerel bir OData hizmeti oluşturmak için [WCF veri hizmetleri hızlı başlangıç](https://go.microsoft.com/fwlink/?LinkID=131076) adımlarını izleyebilirsiniz. Hızlı başlangıcı izlerseniz, bu konudaki örnek kodda belirtilen bir yerel URI 'yi yerine koyun.

## <a name="consuming-an-odata-feed-using-the-client-libraries"></a>İstemci kitaplıklarını kullanarak OData akışını kullanma

WCF Veri Hizmetleri, .NET Framework ve istemci uygulamalarından bir OData akışını daha kolay bir şekilde kullanmanıza olanak tanıyan istemci kitaplıklarını içerir. Bu kitaplıklar HTTP iletileri göndermeyi ve almayı basitleştirir. Ayrıca, ileti yükünü varlık verilerini temsil eden CLR nesnelerine çevirirler. İstemci kitaplıkları iki çekirdek sınıfı <xref:System.Data.Services.Client.DataServiceContext> ve. <xref:System.Data.Services.Client.DataServiceQuery%601> Bu sınıflar bir veri hizmetini sorgulamanızı ve ardından döndürülen varlık verileriyle CLR nesneleri olarak çalışmanızı sağlar. Bu bölümde, istemci kitaplıklarını kullanan etkinlikleri oluşturmaya yönelik iki yaklaşım ele alınmaktadır.

### <a name="adding-a-service-reference-to-the-wcf-data-service"></a>WCF veri hizmetine hizmet başvurusu ekleme

Northwind istemci kitaplıklarını oluşturmak için, Northwind OData hizmetine bir başvuru eklemek üzere Visual Studio 2012 ' deki **hizmet başvurusu Ekle** iletişim kutusunu kullanabilirsiniz.

![Hizmet Başvurusu Ekle iletişim kutusunu gösteren ekran görüntüsü.](./media/consuming-odata-feeds-from-a-workflow/add-service-reference-dialog.gif)

Hizmet tarafından sunulan hizmet işlemleri olmadığını ve **Hizmetler** listesinde, Northwind Data Service tarafından sunulan varlıkları temsil eden öğeler olduğunu unutmayın. Hizmet başvurusu eklendiğinde, bu varlıklar için sınıflar oluşturulacaktır ve istemci kodunda kullanılabilirler. Bu konudaki örnekler, sorguları gerçekleştirmek için bu sınıfları ve `NorthwindEntities` sınıfı kullanır.

> [!NOTE]
> Daha fazla bilgi için bkz. [veri hizmeti Istemci kitaplığı oluşturma (WCF veri Hizmetleri)](../data/wcf/generating-the-data-service-client-library-wcf-data-services.md).

### <a name="using-asynchronous-methods"></a>Zaman uyumsuz yöntemler kullanma

Web üzerinden kaynaklara erişirken oluşabilecek olası gecikme sorunlarını gidermek için WCF Veri Hizmetleri zaman uyumsuz olarak erişmenizi öneririz. WCF veri Hizmetleri istemci kitaplıkları sorguları çağırmak için zaman uyumsuz yöntemler içerir ve Windows Workflow Foundation (WF) zaman uyumsuz etkinlikleri <xref:System.Activities.AsyncCodeActivity> yazmak için sınıfını sağlar. <xref:System.Activities.AsyncCodeActivity>türetilmiş etkinlikler, zaman uyumsuz yöntemlere sahip .NET Framework sınıflarından yararlanmak için yazılabilir veya zaman uyumsuz olarak yürütülecek kod bir yönteme yerleştirilebilir ve bir temsilci kullanılarak çağrılabilir. Bu bölümde, bir <xref:System.Activities.AsyncCodeActivity> türetilmiş etkinliğin, WCF veri Hizmetleri istemci kitaplıklarının zaman uyumsuz yöntemlerini ve bir temsilciyi kullanan bir dizi yöntemi kullanan iki örneği verilmiştir.

> [!NOTE]
> Daha fazla bilgi için bkz. [zaman uyumsuz işlemler (WCF veri Hizmetleri)](../data/wcf/asynchronous-operations-wcf-data-services.md) ve [zaman uyumsuz etkinlikler oluşturma](creating-asynchronous-activities-in-wf.md).

### <a name="using-client-library-asynchronous-methods"></a>İstemci kitaplığı zaman uyumsuz yöntemlerini kullanma

Sınıfı <xref:System.Data.Services.Client.DataServiceQuery%601> , ve <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> birODatahizmetinizamanuyumsuzolaraksorgulamak<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> için yöntemler sağlar. Bu yöntemler, <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> türetilmiş bir <xref:System.Activities.AsyncCodeActivity> sınıfın ve <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> geçersiz kılmalardan çağrılabilir. Geçersiz kılma döndüğünde, iş akışı boşta geçebilir (ancak devam etmez) ve <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> zaman uyumsuz iş tamamlandığında, çalışma zamanı tarafından çağrılır. <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>

Aşağıdaki örnekte, iki giriş bağımsız `OrdersByCustomer` değişkeni olan bir etkinlik tanımlanmıştır. Bağımsız değişkeni, hangi siparişlerin dönebileceğini tanımlayan müşteriyi temsil eder `ServiceUri` ve bağımsız değişken Sorgulanacak OData hizmetinin URI 'sini temsil eder. `CustomerId` Etkinlik bundan türediğinden `AsyncCodeActivity<IEnumerable<Order>>` , sorgunun sonuçlarını döndürmek için <xref:System.Activities.Activity%601.Result%2A> kullanılan bir çıkış bağımsız değişkeni de vardır. <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Geçersiz kılma belirtilen müşterinin tüm emirlerini seçen bir LINQ sorgusu oluşturur. Bu sorgu, geçti <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> <xref:System.Activities.AsyncCodeActivityContext>, <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> ve ardından sorgunun yöntemi çağrılır olarak belirtilir. Sorgunun <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> öğesine geçirildiği geri çağırma ve durumun, <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> etkinliğin yöntemine geçirilmiş olduğunu unutmayın. Sorgunun yürütülmesi bittiğinde etkinliğin <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> yöntemi çağrılır. Sorgu öğesinden <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>alınır ve ardından <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> sorgunun yöntemi çağırılır. Bu yöntem, belirtilen <xref:System.Collections.Generic.IEnumerable%601> varlık türünden bir döndürür; bu durumda. `Order` <xref:System.Collections.IEnumerable> Öğesiningenel<xref:System.Activities.Activity%601.Result%2A> türü olduğundan,<xref:System.Activities.OutArgument%601> bu, etkinliğin olarak ayarlanır. `IEnumerable<Order>` <xref:System.Activities.AsyncCodeActivity%601>

[!code-csharp[CFX_WCFDataServicesActivityExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#100)]

Aşağıdaki örnekte, `OrdersByCustomer` etkinlik belirtilen müşteri için siparişlerin bir listesini alır ve ardından bir etkinlik döndürülen siparişleri numaralandırır ve her <xref:System.Activities.Statements.ForEach%601> bir siparişin tarihini konsola yazar.

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
> İşlenmeyen özel durum: System. InvalidOperationException: Bu istek işlenirken bir hata oluştu. ---> System .net. WebException: > System .net. Sockets. SocketException---uzak sunucusuna bağlanılamıyor: Bağlı olan taraf bir süre sonra düzgün bir şekilde yanıt vermediği veya bağlı konak yanıt vermediği için bağlantı başarısız olduğu için bağlantı girişimi başarısız oldu.

Sorgu tarafından döndürülen verilerin herhangi bir ek işlemesi gerekliyse, etkinliğin <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> geçersiz kılması üzerinde gerçekleştirilebilir. Her ikisi de <xref:System.Activities.AsyncCodeActivity%601.BeginExecute%2A> iş akışı iş parçacığı kullanılarak çağrılır ve bu geçersiz Kılmalarda bulunan tüm kodlar zaman uyumsuz olarak çalışmaz. <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> Ek işlem kapsamlı veya uzun süre çalışıyorsa veya sorgu sonuçları disk belleğine alınerirse, sorguyu yürütmek ve zaman uyumsuz olarak ek işlem gerçekleştirmek için bir temsilci kullanan sonraki bölümde ele alınan yaklaşımı göz önünde bulundurmanız gerekir.

### <a name="using-a-delegate"></a>Temsilci kullanma

Bir .NET Framework sınıfın zaman uyumsuz yöntemini çağırmaya ek olarak, tabanlı bir <xref:System.Activities.AsyncCodeActivity>etkinlik, metotlarından birinde zaman uyumsuz mantığı da tanımlayabilir. Bu yöntem, etkinliğin <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> geçersiz kılması içinde bir temsilci kullanılarak belirtilir. Yöntem döndüğünde, çalışma zamanı etkinliğin <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> geçersiz kılmayı çağırır. Bir iş akışından OData hizmeti çağrılırken, bu yöntem hizmeti sorgulamak ve ek işleme sağlamak için kullanılabilir.

Aşağıdaki örnekte bir `ListCustomers` etkinlik tanımlanmıştır. Bu etkinlik, örnek Northwind veri hizmeti 'ni sorgular ve Northwind `List<Customer>` veritabanındaki tüm müşterileri içeren bir döndürür. Zaman uyumsuz iş `GetCustomers` yöntemi tarafından gerçekleştirilir. Bu yöntem, tüm müşteriler için hizmeti sorgular ve ardından bir ' a `List<Customer>`kopyalar. Sonra sonuçların disk belleğine alınmış olup olmadığını denetler. Bu durumda, bir sonraki sonuç sayfasında hizmeti sorgular, bunları listeye ekler ve tüm müşteri verileri alınana kadar devam eder.

> [!NOTE]
> WCF veri Hizmetleri 'de sayfalama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Disk belleğine alınmış sonuçları yükle (](../data/wcf/how-to-load-paged-results-wcf-data-services.md)WCF veri Hizmetleri).

Tüm müşteriler eklendikten sonra liste döndürülür. `GetCustomers` Yöntemi<xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> etkinliğin geçersiz kılmada belirtilir. Yöntemin bir dönüş değeri olduğundan, yöntemi belirtmek için `Func<string, List<Customer>>` bir oluşturulur.

> [!NOTE]
> Zaman uyumsuz çalışmayı gerçekleştiren yöntemin dönüş değeri yoksa, <xref:System.Action> yerine <xref:System.Func%601>bir kullanılır. Her iki yaklaşımı kullanarak zaman uyumsuz bir örnek oluşturma örnekleri için bkz. [zaman uyumsuz etkinlikler oluşturma](creating-asynchronous-activities-in-wf.md).

Bu <xref:System.Func%601> `BeginInvoke` öğesine atanırveardındançağırılır.<xref:System.Activities.AsyncCodeActivityContext.UserState%2A> Çağrılacak yöntemin etkinliğin bağımsız değişken ortamına erişimi olmadığından, `ServiceUri` bağımsız değişkenin değeri ilk parametre olarak geçirilir ve geri çağırma ve durumuyla <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>birlikte gönderilir. Döndüğünde, çalışma zamanı çağırır <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. `GetCustomers` İçindeki <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> kod, <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>' dan temsilciyi alır, çağırır `EndInvoke`ve sonucu döndürür. Bu, `GetCustomers` yönteminden döndürülen müşterilerin listesidir.

[!code-csharp[CFX_WCFDataServicesActivityExample#200](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#200)]

Aşağıdaki örnekte, `ListCustomers` etkinlik müşterilerin bir listesini alır ve bir <xref:System.Activities.Statements.ForEach%601> etkinlik bunları numaralandırır ve her müşterinin şirket adını ve ilgili kişi adını konsola yazar.

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

Bir iş akışında, bu örnekteki kod, bir <xref:System.Activities.CodeActivity.Execute%2A> <xref:System.Activities.CodeActivity>tabanlı özel etkinliğin geçersiz kılması içine eklenebilir, ancak aynı işlevsellik <xref:System.Activities.Expressions.InvokeMethod%601> etkinlik kullanılarak da gerçekleştirilebilir. Etkinlik <xref:System.Activities.Expressions.InvokeMethod%601> , iş akışı yazarlarının bir sınıfın statik ve örnek yöntemlerini çağırmasına ve ayrıca belirtilen yöntemi zaman uyumsuz olarak çağırma seçeneğine sahiptir. Aşağıdaki örnekte, bir <xref:System.Activities.Expressions.InvokeMethod%601> etkinlik, <xref:System.Net.WebClient> sınıfının <xref:System.Net.WebClient.DownloadString%2A> yöntemini çağırmak ve müşterilerin bir listesini döndürmek için yapılandırılmıştır.

[!code-csharp[CFX_WCFDataServicesActivityExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#3)]

<xref:System.Activities.Expressions.InvokeMethod%601>, bir sınıfın hem statik hem de örnek yöntemlerini çağırabilir. , Sınıfının bir örnek <xref:System.Net.WebClient> yöntemi <xref:System.Net.WebClient.DownloadString%2A> <xref:System.Net.WebClient> olduğundan, için <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A>sınıfının yeni bir örneği belirtilir. `DownloadString`olarak <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A>belirtilirse, sorguyu içeren URI <xref:System.Activities.Expressions.InvokeMethod%601.Parameters%2A> koleksiyonda belirtilir ve dönüş <xref:System.Activities.Activity%601.Result%2A> değeri değere atanır. <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> Değer olarak`true`ayarlanır, bu da yöntem çağrısının iş akışıyla ilgili olarak zaman uyumsuz olarak çalışacağı anlamına gelir. Aşağıdaki örnekte, belirli bir müşterinin siparişlerinin listesi için örnek Northwind Data <xref:System.Activities.Expressions.InvokeMethod%601> Service 'i sorgulamak üzere etkinliğini kullanan bir iş akışı oluşturulur ve ardından döndürülen veriler konsola yazılır.

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

Bu örnek, iş akışı uygulama yazarlarının bir OData hizmetinden döndürülen ham verileri tüketmek için kullanabileceği bir yöntem sağlar. URI 'ler kullanarak WCF veri Hizmetleri erişme hakkında daha fazla bilgi için bkz. [veri hizmeti kaynaklarına erişme (WCF veri Hizmetleri)](../data/wcf/accessing-data-service-resources-wcf-data-services.md) ve [OData: URI kuralları](https://go.microsoft.com/fwlink/?LinkId=185564).
