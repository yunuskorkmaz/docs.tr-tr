---
title: Bir iş akışından OData tüketen akışları
ms.date: 03/30/2017
ms.assetid: 1b26617c-53e9-476a-81af-675c36d95919
ms.openlocfilehash: 8d08a58cecead105f6e1f580ea40175cac93e417
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780108"
---
# <a name="consuming-odata-feeds-from-a-workflow"></a>Bir iş akışından OData tüketen akışları

WCF Veri Hizmetleri'nin bir bileşeni olan [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] göstermek ve temsili durum aktarımı (REST) semantiği kullanarak Web veya intranet üzerinden verileri kullanmak için açık veri Protokolü (OData) kullanan hizmetler oluşturmanıza olanak sağlar. OData veri tarafından bir URI'leri adreslenebilir kaynakları olarak kullanıma sunar. HTTP isteği göndermesini ve OData akışına işlem herhangi bir uygulama bir veri hizmeti döndürdüğünü bir OData tabanlı bir veri hizmeti ile etkileşim kurabilir. Ayrıca, WCF Veri Hizmetleri OData Akışları'tükettiğinizde daha zengin bir programlama deneyimi sağlayan istemci kütüphaneleri içerir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uygulamalar. Bu konu, bir iş akışında istemci kitaplıkları kullanarak olmadan ve genel bakış kullanan bir OData akışı sağlar.

## <a name="using-the-sample-northwind-odata-service"></a>Örnek Northwind OData hizmetini kullanma

Veri hizmeti bulunan Northwind örnek bu konudaki örneklerde [ http://services.odata.org/Northwind/Northwind.svc/ ](https://go.microsoft.com/fwlink/?LinkID=187426). Bu hizmetin bir parçası olarak sağlanan [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185248) ve örnek Northwind veritabanı salt okunur erişim sağlar. Yazma erişimi istenen ya da yerel bir WCF veri hizmeti isteniyorsa adımlarını izleyebilirsiniz [WCF Veri Hizmetleri Hızlı Başlangıç](https://go.microsoft.com/fwlink/?LinkID=131076) Northwind veritabanına erişim sağlayan yerel bir OData hizmeti oluşturmak için. Hızlı başlangıcı takip ediyorsa, bu konudaki örnek kodda sağlanan yerel URI'sini değiştirin.

## <a name="consuming-an-odata-feed-using-the-client-libraries"></a>İstemci kitaplıkları kullanarak bir OData akışı kullanma

WCF Veri Hizmetleri, daha kolay bir OData akışına gelen kullanmasına olanak sağlayan istemci kütüphaneleri içerir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ve istemci uygulamaları. Bu kitaplıklar, HTTP iletileri gönderip basitleştirir. Bunlar ayrıca varlık verilerini temsil eden CLR nesneleri iletisi yüküne çevir. İstemci kitaplıkları iki çekirdek sınıfı özelliği <xref:System.Data.Services.Client.DataServiceContext> ve <xref:System.Data.Services.Client.DataServiceQuery%601>. Bu sınıflar, bir veri hizmetini sorgulama ve CLR nesne olarak döndürülen varlığı verilerle çalışmak etkinleştirin. Bu bölüm, istemci kitaplıkları kullanan bir etkinlik oluşturma için iki yaklaşım kapsar.

### <a name="adding-a-service-reference-to-the-wcf-data-service"></a>WCF veri hizmetine hizmet başvurusu ekleme

Northwind istemci kitaplıkları oluşturmak için kullanabileceğiniz **hizmet Başvurusu Ekle** iletişim kutusunda, Northwind OData hizmetine başvuru eklemek için Visual Studio 2012.

![Hizmet Başvurusu Ekle](../../../docs/framework/windows-workflow-foundation/media/addservicereferencetonorthwindodataservice.gif "AddServiceReferencetoNorthwindODataService")

Hizmet tarafından hem de hiçbir hizmet işlemleri olduğunu unutmayın **Hizmetleri** vardır liste öğelerini temsil eden Northwind verileri hizmeti tarafından kullanıma sunulan varlık. Hizmet başvurusunu eklediğinizde sınıfları bu varlıkları için oluşturulur ve istemci kodu kullanılabilir. Bu konudaki örnekleri bu sınıfları kullanın ve `NorthwindEntities` sorguları gerçekleştirmek için sınıf.

> [!NOTE]
> Daha fazla bilgi için [veri hizmeti istemci Kitaplığı'nı (WCF Data Services) oluşturma](https://go.microsoft.com/fwlink/?LinkID=191611).

### <a name="using-asynchronous-methods"></a>Zaman uyumsuz metotlar kullanma

WCF Veri Hizmetleri zaman uyumsuz olarak erişen öneririz Web üzerinden kaynaklara erişirken oluşabilecek olası gecikme sorunlarını gidermek için. Zaman uyumsuz yöntemleri çağırma sorgular için WCF Veri Hizmetleri istemci kitaplıkları içerir ve Windows Workflow Foundation (WF) sağlayan <xref:System.Activities.AsyncCodeActivity> sınıfı zaman uyumsuz etkinlikler yazma için. <xref:System.Activities.AsyncCodeActivity> türetilmiş etkinlik yararlanmak için yazılabilir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] zaman uyumsuz yöntemler veya zaman uyumsuz olarak yürütülecek kodu olan sınıfları bir yönteme yerleştirin ve temsilci kullanılarak çağrılır. Bu bölümde, iki örnek bir <xref:System.Activities.AsyncCodeActivity> türetilmiş etkinlik; bir WCF Veri Hizmetleri istemci kitaplıkları, zaman uyumsuz yöntemleri kullanır ve bir temsilci kullanan bir.

> [!NOTE]
> Daha fazla bilgi için [zaman uyumsuz işlemler (WCF Data Services)](https://go.microsoft.com/fwlink/?LinkId=193396) ve [zaman uyumsuz etkinlikler oluşturma](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).

### <a name="using-client-library-asynchronous-methods"></a>İstemci Kitaplığı zaman uyumsuz metotlar kullanma

<xref:System.Data.Services.Client.DataServiceQuery%601> Sağlar sınıfını <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> ve <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> zaman uyumsuz olarak bir OData hizmeti sorgulamak için yöntemleri. Bu yöntemler, gelen çağrılabilir <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> ve <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> , geçersiz kılan bir <xref:System.Activities.AsyncCodeActivity> türetilmiş sınıf. Zaman <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> geçersiz kılma döndürür, iş akışı boş Git (ancak kalıcı) ve ne zaman zaman uyumsuz işi tamamlandığında, <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> çalışma zamanı tarafından çağrılır.

Aşağıdaki örnekte, bir `OrdersByCustomer` etkinlik, iki bağımsız değişkenler girişi sahip tanımlanır. `CustomerId` Bağımsız değişkeni hangi siparişleri döndürmek için tanımlayan bir müşteri temsil eder ve `ServiceUri` bağımsız değişken Sorgulanacak OData hizmeti URI'sini temsil eder. Etkinlik öğesinden türetildiği için `AsyncCodeActivity<IEnumerable<Order>>` ayrıca bir <xref:System.Activities.Activity%601.Result%2A> çıkış sorgu sonuçlarını döndürmek için kullanılan bağımsız değişken. <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Geçersiz kılma tüm siparişleri belirtilen müşterinin seçtiği bir LINQ sorgu oluşturur. Bu sorgu olarak belirtilen <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> geçirilen <xref:System.Activities.AsyncCodeActivityContext>ve ardından sorgu <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> yöntemi çağrılır. Unutmayın geri çağırma ve sorgunun geçirilen durumu <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> etkinliğin geçirilir olanlardır <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> yöntemi. Sorgu bittiğinde Etkinlik yürütme <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> yöntemi çağrılır. Sorgu alınır <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>ve ardından sorgu <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> yöntemi çağrılır. Bu yöntem döndürür bir <xref:System.Collections.Generic.IEnumerable%601> belirtilen varlık türü; bu durumda `Order`. Bu yana `IEnumerable<Order>` genel türü <xref:System.Activities.AsyncCodeActivity%601>bu `IEnumerable` olarak ayarlandığından <xref:System.Activities.Activity%601.Result%2A> <xref:System.Activities.OutArgument%601> etkinlik.

[!code-csharp[CFX_WCFDataServicesActivityExample#100](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#100)]

Aşağıdaki örnekte, `OrdersByCustomer` etkinlik belirtilen müşteri siparişlerinin listesi alır ve ardından bir <xref:System.Activities.Statements.ForEach%601> etkinlik döndürülen siparişleri numaralandırır ve her sipariş tarihi konsola yazar.

[!code-csharp[CFX_WCFDataServicesActivityExample#10](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#10)]

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
> OData sunucusuna bağlantı kurulamıyorsa, şu özel durum için benzer bir özel durum alırsınız:
>
> İşlenmeyen özel durum: System.InvalidOperationException: Bu istek işlenirken bir hata oluştu. ---> System.Net.WebException: uzak sunucuya bağlanılamıyor System.Net.Sockets.SocketException--->: başarısız zaman ya da kurulan bağlantı bir süre sonra bağlı taraf düzgün yanıt vermediğinden bağlantı denemesi başarısız oldu bağlı konak yanıt vermedi.

Sorgu tarafından döndürülen verilerin herhangi bir ek işlem gerekiyorsa, bu etkinliğin içinde yapılabilir <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> geçersiz kılar. Her ikisi de <xref:System.Activities.AsyncCodeActivity%601.BeginExecute%2A> ve <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> iş akışı iş parçacığı kullanılarak çağrılır ve bu geçersiz kılmaları herhangi bir kod zaman uyumsuz olarak çalışmaz. Kapsamlı veya uzun ömürlü ek işleme veya sorgu sonuçları disk belleğine alınan sorgu yürütmek ve gerçekleştirmek için bir temsilci kullanan sonraki bölümde tartışılacağı yaklaşım ek zaman uyumsuz olarak işleme düşünmelisiniz.

### <a name="using-a-delegate"></a>Bir temsilcisi kullanma

Ek olarak, zaman uyumsuz yöntemini çağıran bir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sınıfı, bir <xref:System.Activities.AsyncCodeActivity>-tabanlı etkinliği de tanımlayabilirsiniz zaman uyumsuz mantık yöntemlerinden biri. Bu yöntem etkinlik içinde bir temsilci kullanarak belirtilen <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> geçersiz kılar. Yöntem döndürüldüğünde etkinliğin çalışma zamanı çağırır <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> geçersiz kılar. OData hizmetine bir iş akışından çağrılırken, bu yöntem hizmetini sorgulama ve herhangi bir ek işleme sağlamak için kullanılabilir.

Aşağıdaki örnekte, bir `ListCustomers` etkinlik tanımlanır. Bu etkinlik örnek Northwind verileri hizmeti sorgular ve döndüren bir `List<Customer>` Northwind veritabanındaki müşteriler içerir. Zaman uyumsuz işler tarafından gerçekleştirilen `GetCustomers` yöntemi. Bu yöntem, tüm müşteriler için hizmetini sorgular ve içine kopyalar bir `List<Customer>`. Ardından sonuçları disk belleği, görmek için denetler. Bu nedenle, bu hizmet için sonraki sonuç sayfasını sorgular, bunları listeye ekler ve tüm müşteri verileri alınamadı kadar devam eder.

> [!NOTE]
> Disk belleği WCF veri hizmetleri hakkında daha fazla bilgi için bkz. [Nasıl yapılır: Sayfalanmış sonuçları (WCF Veri Hizmetleri) yükleme](https://go.microsoft.com/fwlink/?LinkId=193452).

Tüm müşterileri eklendikten sonra liste döndürülür. `GetCustomers` Yöntemi etkinliğin içinde belirtilen <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> geçersiz kılar. Yöntemin bir dönüş değeri olduğundan bir `Func<string, List<Customer>>` yöntemi belirtmek için oluşturulur.

> [!NOTE]
> Zaman uyumsuz işi gerçekleştiren yöntemin dönüş değeri, yoksa bir <xref:System.Action> yerine kullanılan bir <!--zz <xref:System.Func> --> `System.Func`. Her iki yaklaşım kullanarak zaman uyumsuz örneği oluşturmayı örnekler için bkz. [zaman uyumsuz etkinlikler oluşturma](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).

Bu <!--zz <xref:System.Func> --> `System.Func` atandığı <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, ardından `BeginInvoke` çağrılır. Çağrılacak yöntemin bağımsız değişken değerini etkinliğin ortama erişimi olmadığından `ServiceUri` geri çağırma ve yöntemlere geçirilen durumu ile birlikte birinci parametre olarak geçirilen bağımsız değişken <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Zaman `GetCustomers` döndürür, çalışma zamanı çağırır <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Kodda <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> temsilciyi alır <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, çağrıları `EndInvoke`, müşterilerin listesidir sonuç döndürülmez döndürür `GetCustomers` yöntemi.

[!code-csharp[CFX_WCFDataServicesActivityExample#200](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#200)]

Aşağıdaki örnekte, `ListCustomers` etkinlik, müşterilerin listesini alır ve ardından bir <xref:System.Activities.Statements.ForEach%601> etkinlik bunları numaralandırır ve her müşteri kişi adını ve şirket adı, konsola yazar.

[!code-csharp[CFX_WCFDataServicesActivityExample#20](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#20)]

Bu iş akışı çağrıldığında, aşağıdaki veriler konsoluna yazılır. Bu sorgu, birçok müşteri döndürdüğünden, çıkış yalnızca bir kısmı burada görüntülenir.

```console
Calling WCF Data Service...
Alfreds Futterkiste, Contact: Maria Anders
Ana Trujillo Emparedados y helados, Contact: Ana Trujillo
Antonio Moreno Taquería, Contact: Antonio Moreno
Around the Horn, Contact: Thomas Hardy
Berglunds snabbköp, Contact: Christina Berglund
...
```

## <a name="consuming-an-odata-feed-without-using-the-client-libraries"></a>İstemci kitaplıkları kullanmadan bir OData akışı kullanma

OData veri tarafından bir URI'leri adreslenebilir kaynakları olarak kullanıma sunar. Kullandığınızda bu bir URI'leri sizin için oluşturulur istemci kitaplıkları, ancak istemci kitaplıklarını kullanmanız gerekmez. İsterseniz, OData hizmetlerini istemci kitaplıkları kullanmadan doğrudan erişilebilir. İstemci kitaplıkları kullanılmadığında hizmeti ve istenen veri konumunu belirtilen URI tarafından ve sonuçları HTTP isteğine yanıt olarak döndürülür. Bu ham verilerin işlenmesi veya istenen şekilde yönetilebilir. Bir OData sorgusu sonuçlarını almak için bir yol olan kullanarak <xref:System.Net.WebClient> sınıfı. Bu örnekte, ilgili kişi adı ALFKI anahtar tarafından temsil edilen müşteri için alınır.

[!code-csharp[CFX_WCFDataServicesActivityExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#2)]

Bu kodu çalıştırdığınızda, aşağıdaki çıktıyı konsola görüntülenir:

```console
Raw data returned:
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<ContactName xmlns="http://schemas.microsoft.com/ado/2007/08/dataservices">Maria Anders</ContactName>
```

Bir iş akışında, bu örnekteki kod birleştirilir <xref:System.Activities.CodeActivity.Execute%2A> , geçersiz bir <xref:System.Activities.CodeActivity>-özel etkinlik tabanlı, ancak aynı işlevleri kullanılarak da gerçekleştirilebilir <xref:System.Activities.Expressions.InvokeMethod%601> etkinlik. <xref:System.Activities.Expressions.InvokeMethod%601> Etkinlik iş akışı yazarları statik çağırır ve yöntem bir sınıfın örneği sağlar ve ayrıca zaman uyumsuz olarak belirtilen yöntem çağırmak için bir seçenek vardır. Aşağıdaki örnekte, bir <xref:System.Activities.Expressions.InvokeMethod%601> etkinlik çağırmak için yapılandırılmış <xref:System.Net.WebClient.DownloadString%2A> yöntemi <xref:System.Net.WebClient> sınıfı ve müşterilerin listesini döndürür.

[!code-csharp[CFX_WCFDataServicesActivityExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#3)]

<xref:System.Activities.Expressions.InvokeMethod%601> statik çağırın ve yöntemleri bir sınıfın örneğini kullanabilirsiniz. Bu yana <xref:System.Net.WebClient.DownloadString%2A> bir örnek yöntemi <xref:System.Net.WebClient> sınıfının yeni bir örneğini <xref:System.Net.WebClient> sınıfı için belirtilen <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A>. `DownloadString` olarak belirtilirse <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A>, sorgu içerir URI'yi belirtilen <xref:System.Activities.Expressions.InvokeMethod%601.Parameters%2A> koleksiyonu ve dönüş değeri atanır <xref:System.Activities.Activity%601.Result%2A> değeri. <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> Değeri ayarı `true`, yöntem çağırma iş akışı ile ilgili zaman uyumsuz olarak çalıştırılacak anlamına gelir. Aşağıdaki örnekte, bir iş akışı kullanan oluşturulur <xref:System.Activities.Expressions.InvokeMethod%601> örnek Northwind verileri sorgulamak için etkinlik hizmet belirli bir müşterinin siparişlerinin listesi için ve ardından döndürülen verileri konsoluna yazılır.

[!code-csharp[CFX_WCFDataServicesActivityExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#1)]

Bu iş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir. Bu sorgu çalışanlarına döndürdüğünden, çıkış yalnızca bir kısmı burada görüntülenir.

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

Bu örnek, iş akışı uygulama yazarları bir OData hizmetten döndürülen ham veri tüketmek için kullanabileceğiniz bir yöntem sağlar. WCF veri URI'ler kullanarak hizmetlere erişme hakkında daha fazla bilgi için bkz. [veri hizmeti kaynaklarına erişme (WCF Data Services)](https://go.microsoft.com/fwlink/?LinkId=193397) ve [OData: URI kurallarına](https://go.microsoft.com/fwlink/?LinkId=185564).
