---
title: Bir iş akışından akışları OData kullanma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b26617c-53e9-476a-81af-675c36d95919
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ce7d7812eadea2d9472a62bd007d2eca6ae07891
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="consuming-odata-feeds-from-a-workflow"></a>Bir iş akışından akışları OData kullanma
WCF Veri Hizmetleri bir bileşenidir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] temsili durum aktarımı (REST) semantiği kullanarak Web veya intranet üzerinden verileri kullanmak ve kullanıma sunmak için açık veri Protokolü (OData) kullanan hizmetler oluşturmak etkinleştirir. OData veri URI tarafından adreslenebilir kaynaklar olarak kullanıma sunar. Bir HTTP isteği göndermek ve OData akışı işlem herhangi bir uygulama veri hizmeti döndürdüğünü bir OData tabanlı veri hizmetiyle etkileşim kurabilirsiniz. Ayrıca, WCF Veri Hizmetleri OData Akışları'kullandığında daha zengin bir programlama deneyimi sağlayan istemci kitaplıklarını içerir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uygulamalar. Bu konu, bir iş akışında istemci kitaplıkları kullanılarak ve kullanılmadan bir OData tüketen genel bir bakış akışı sağlar.  
  
## <a name="using-the-sample-northwind-odata-service"></a>Örnek Northwind OData hizmetini kullanma  
 Bu konudaki örnekler veri hizmeti bulunan Northwind örnek kullanmak [ http://services.odata.org/Northwind/Northwind.svc/ ](http://go.microsoft.com/fwlink/?LinkID=187426). Bu hizmetin bir parçası olarak sağlanan [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185248) ve örnek Northwind veritabanı salt okunur erişim sağlar. Yazma erişimi istenen ya da yerel bir WCF veri hizmeti istenirse, adımları takip edebilirsiniz [WCF Veri Hizmetleri Quickstart](http://go.microsoft.com/fwlink/?LinkID=131076) Northwind veritabanına erişim sağlayan yerel bir OData hizmet oluşturmak için. Hızlı Başlangıç izlerseniz, bu konudaki örnek kodda sağlanan yerel URI'sini değiştirin.  
  
## <a name="consuming-an-odata-feed-using-the-client-libraries"></a>İstemci kitaplıkları kullanarak bir OData akışı kullanma  
 WCF veri hizmetleri içeren bir OData gelen akışı daha kolayca kullanmalarını sağlayan istemci kitaplıkları [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ve istemci uygulamaları. Bu kitaplıklar, HTTP ileti gönderme ve alma basitleştirir. Bunlar ayrıca varlık verilerini temsil eden CLR nesneleri içine ileti yükü çevir. İstemci kitaplıkları iki çekirdek sınıfları özellik <xref:System.Data.Services.Client.DataServiceContext> ve <xref:System.Data.Services.Client.DataServiceQuery%601>. Bu sınıfları, veri hizmeti sorgulamak ve CLR nesneler olarak döndürülen varlığı verilerle çalışmak etkinleştirin. Bu bölüm, istemci kitaplıkları kullanan etkinlikleri oluşturmak için iki yaklaşım kapsar.  
  
### <a name="adding-a-service-reference-to-the-wcf-data-service"></a>WCF veri hizmetine hizmet başvurusu ekleme  
 Northwind istemci kitaplıkları oluşturmak için kullanabileceğiniz **hizmet Başvurusu Ekle** iletişim kutusunda [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] Northwind OData hizmetine başvuru eklemek için.  
  
 ![Hizmet Başvurusu Ekle](../../../docs/framework/windows-workflow-foundation/media/addservicereferencetonorthwindodataservice.gif "AddServiceReferencetoNorthwindODataService")  
  
 Hizmeti tarafından ve de kullanıma sunulan hiçbir hizmet işlemleri olduğuna dikkat edin **Hizmetleri** vardır liste öğelerini Northwind veri hizmeti tarafından sunulan varlıkları temsil eden. Hizmet başvurusu eklendiğinde, sınıflar bu varlıklar için oluşturulur ve istemci kodu kullanılabilir. Bu konudaki örnekler bu sınıfları kullanır ve `NorthwindEntities` sorguları gerçekleştirmek için sınıf.  
  
> [!NOTE]
>  Daha fazla bilgi için bkz: [veri hizmeti istemci kitaplığı (WCF Veri Hizmetleri) oluşturma](http://go.microsoft.com/fwlink/?LinkID=191611).  
  
### <a name="using-asynchronous-methods"></a>Zaman uyumsuz yöntemler kullanma  
 WCF Veri Hizmetleri zaman uyumsuz olarak erişme öneririz kaynaklara Web üzerinden erişirken oluşabilecek olası gecikme sorunlarına yönelik. WCF Veri Hizmetleri istemci kitaplıkları sorguları çalıştırma zaman uyumsuz yöntemleri içerir ve Windows Workflow Foundation (WF) sağlar <xref:System.Activities.AsyncCodeActivity> zaman uyumsuz etkinlikleri yazma sınıfı. <xref:System.Activities.AsyncCodeActivity> türetilen etkinlikleri yararlanmak için yazılabilir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] , zaman uyumsuz yöntemleri veya zaman uyumsuz olarak yürütülecek kod olan sınıf bir yönteme koy ve temsilci kullanarak çağrılır. Bu bölümde, iki örnek bir <xref:System.Activities.AsyncCodeActivity> türetilmiş etkinlik; WCF Veri Hizmetleri istemci kitaplıkları zaman uyumsuz yöntemleri kullanan diğeri, bir temsilci kullanır.  
  
> [!NOTE]
>  Daha fazla bilgi için bkz: [zaman uyumsuz işlemleri (WCF Veri Hizmetleri)](http://go.microsoft.com/fwlink/?LinkId=193396) ve [oluşturma zaman uyumsuz etkinlikleri](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).  
  
### <a name="using-client-library-asynchronous-methods"></a>İstemci Kitaplığı zaman uyumsuz yöntemler kullanma  
 <xref:System.Data.Services.Client.DataServiceQuery%601> SAX <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> ve <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> OData hizmetine zaman uyumsuz olarak sorgulamak için yöntemleri. Bu yöntemlerin gelen çağrılabilir <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> ve <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> , geçersiz kılan bir <xref:System.Activities.AsyncCodeActivity> türetilmiş sınıf. Zaman <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> geçersiz kılma döndürür, iş akışı boşta gidin (ancak devam) ve zaman uyumsuz iş tamamlandığında, <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> çalışma zamanı tarafından çağrılır.  
  
 Aşağıdaki örnekte, bir `OrdersByCustomer` etkinlik, iki bağımsız değişken giriş sahip tanımlanır. `CustomerId` Bağımsız değişkeni döndürmek için hangi siparişleri tanımlayan müşteri temsil eder ve `ServiceUri` bağımsız değişkeni Sorgulanacak OData hizmeti URI'sini temsil eder. Etkinlik türetilen çünkü `AsyncCodeActivity<IEnumerable<Order>>` ayrıca bir <xref:System.Activities.Activity%601.Result%2A> çıkış sorgu sonuçlarını döndürmek için kullanılan bağımsız değişkeni. <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> Geçersiz kılma belirtilen müşterinin tüm siparişleri seçer LINQ sorgusu oluşturur. Bu sorgu olarak belirtilen <xref:System.Activities.AsyncCodeActivityContext.UserState%2A> geçirilen, <xref:System.Activities.AsyncCodeActivityContext>ve ardından sorgunun <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> yöntemi çağrılır. Unutmayın geri çağırma ve sorgunun geçirilen durumu <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> etkinliğin iletilen olanlardır <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> yöntemi. Sorgu bittiği yürütme, etkinliğin <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> yöntemi çağrılır. Sorgu alınır <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>ve ardından sorgunun <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> yöntemi çağrılır. Bu yöntem bir <xref:System.Collections.Generic.IEnumerable%601> belirtilen varlık türü; bu durumda `Order`. Bu yana `IEnumerable<Order>` genel türü <xref:System.Activities.AsyncCodeActivity%601>, bu `IEnumerable` olarak ayarlanmış olan <xref:System.Activities.Activity%601.Result%2A> <xref:System.Activities.OutArgument%601> etkinliğin.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#100](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#100)]  
  
 Aşağıdaki örnekte, `OrdersByCustomer` etkinlik belirtilen müşteri siparişleri listesini alır ve ardından bir <xref:System.Activities.Statements.ForEach%601> etkinlik döndürülen siparişleri numaralandırır ve her sipariş sonu konsola yazar.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#10](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#10)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki veri konsola yazılır:  
  
 **WCF veri hizmeti çağrılırken...**  
**8/25/1997**   
**10/3/1997**   
**10/13/1997**   
**1/15/1998**   
**3/16/1998**   
**4/9/1998**    
> [!NOTE]
>  OData sunucusuna bağlantı kurulamıyorsa, bir özel durum şu özel durum benzer alırsınız:  
>   
>  İşlenmeyen özel durum: System.InvalidOperationException: Bu istek işlenirken bir hata oluştu. System.Net.WebException--->: uzak sunucuya bağlanılamıyor System.Net.Sockets.SocketException--->: zaman ya da kurulan bağlantı bir süre başarısız olduktan sonra bağlanılan düzgün yanıt vermediği için bir bağlantı girişimi başarısız oldu ana bilgisayar bağlı olduğundan yanıtlamak başarısız oldu.  
  
 Sorgu tarafından döndürülen verilerin herhangi bir ek işlem gerekiyorsa, bu etkinliğin içinde yapılabilir <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> geçersiz kılar. Her ikisi de <xref:System.Activities.AsyncCodeActivity%601.BeginExecute%2A> ve <xref:System.Activities.AsyncCodeActivity%601.EndExecute%2A> iş akışı, iş parçacığı kullanarak çağrılır ve bu geçersiz kılmaları herhangi kodda zaman uyumsuz olarak çalıştırmaz. Kapsamlı veya uzun süre çalışan ek işleme veya sorgu sonuçlarını disk belleğine alınan sorgu yürütün ve gerçekleştirmek için bir temsilci kullanır sonraki bölümde açıklanan yaklaşım ek zaman uyumsuz olarak işleme düşünmelisiniz.  
  
### <a name="using-a-delegate"></a>Bir temsilci kullanarak  
 Zaman uyumsuz yöntemini çağırma yanı sıra bir [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sınıfı, bir <xref:System.Activities.AsyncCodeActivity>-tabanlı etkinlik de tanımlayabilirsiniz zaman uyumsuz mantığı yöntemlerinden biri. Bu yöntem etkinliğin içinde bir temsilci kullanarak belirtilen <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> geçersiz kılar. Yöntem döndürüldüğünde etkinliğe ilişkin çalışma zamanı çağırır <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> geçersiz kılar. Bir OData hizmeti bir iş akışından çağrılırken, bu yöntem hizmet sorgulamak ve herhangi bir ek işleme sağlamak için kullanılabilir.  
  
 Aşağıdaki örnekte, bir `ListCustomers` etkinlik tanımlanır. Bu etkinlik örnek Northwind veri hizmeti sorgular ve döndüren bir `List<Customer>` Northwind veritabanındaki tüm müşteriler içerir. Zaman uyumsuz iş tarafından gerçekleştirilen `GetCustomers` yöntemi. Bu yöntem hizmeti tüm müşteriler için sorgular ve bunların içine kopyalar bir `List<Customer>`. Ardından sonuçları havuzda olmadığını görmek için denetler. Bu nedenle, hizmet sonraki sonuç sayfasını için sorgular, listeye ekler ve tüm müşteri verilerinin alınamadı kadar devam eder.  
  
> [!NOTE]
>  WCF Veri Hizmetleri disk belleği hakkında daha fazla bilgi için bkz. [Nasıl yapılır: yük, sonuçları (WCF Veri Hizmetleri) disk belleğine alınan](http://go.microsoft.com/fwlink/?LinkId=193452).  
  
 Tüm müşteriler eklendikten sonra listesi döndürülür. `GetCustomers` Yöntemi etkinliğin içinde belirtilen <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A> geçersiz kılar. Yöntemin dönüş değeri olduğundan bir `Func<string, List<Customer>>` yöntemini belirtmek için oluşturulur.  
  
> [!NOTE]
>  Zaman uyumsuz iş gerçekleştirir yöntemin dönüş değeri, yoksa bir <xref:System.Action> yerine kullanılan bir <!--zz <xref:System.Func> --> `System.Func`. Her iki yaklaşım kullanarak zaman uyumsuz bir örnek oluşturma örnekler için bkz: [oluşturma zaman uyumsuz etkinlikleri](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).  
  
 Bu <!--zz <xref:System.Func> --> `System.Func` atandığı <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>ve ardından `BeginInvoke` olarak adlandırılır. Çağrılacak yöntemin bağımsız değişken değeri etkinliğin ortamına erişimi olmadığından `ServiceUri` geri çağırma ve içine geçirilen durumu ile birlikte ilk parametre olarak geçirilen bağımsız değişken <xref:System.Activities.AsyncCodeActivity.BeginExecute%2A>. Zaman `GetCustomers` döndürür, çalışma zamanı çağırır <xref:System.Activities.AsyncCodeActivity.EndExecute%2A>. Kodda <xref:System.Activities.AsyncCodeActivity.EndExecute%2A> temsilciyi alır <xref:System.Activities.AsyncCodeActivityContext.UserState%2A>, çağrıları `EndInvoke`, müşterilerin listesi sonucu döndürdü döndürür `GetCustomers` yöntemi.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#200](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#200)]  
  
 Aşağıdaki örnekte, `ListCustomers` etkinlik müşteriler, listesini alır ve ardından bir <xref:System.Activities.Statements.ForEach%601> etkinlik bunları numaralandırır ve her bir müşteri irtibat adını ve şirket adı konsola yazar.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#20](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#20)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki veri konsoluna yazılır. Bu sorgu birçok müşteri döndürdüğünden, çıktı yalnızca bir kısmını burada görüntülenir.  
  
 **WCF veri hizmeti çağrılırken...**  
**Alfreds Futterkiste, kişi: Maria Anders**   
**Ana Trujillo Emparedados y helados, kişi: Ana Trujillo**   
**Antonio Moreno Taquería, kişi: Antonio Moreno**   
**Horn başvurun: Thomas Hardy**   
**Berglunds snabbköp, kişi: Çiğdem Berglund**   
**...**    
## <a name="consuming-an-odata-feed-without-using-the-client-libraries"></a>İstemci kitaplıkları kullanmadan bir OData akışı kullanma  
 OData veri URI tarafından adreslenebilir kaynaklar olarak kullanıma sunar. Ne zaman bu URI sizin için oluşturulan istemci kitaplıkları kullanabilirsiniz, ancak istemci kitaplıkları kullanmak zorunda değil. İsterseniz, OData Hizmetleri istemci kitaplıkları kullanmadan doğrudan erişilebilir. İstemci kitaplıkları kullanmadığınızda konumunu hizmet ve istenen verileri Belirtilen URI tarafından ve sonuçları HTTP isteğine yanıt olarak döndürülür. Bu ham verileri işlenen veya istenen şekilde yönetilebilir. Bir OData sorgu sonuçlarını almak için bir yoldur kullanarak <xref:System.Net.WebClient> sınıfı. Bu örnekte, ilgili kişi adı ALFKI anahtar tarafından temsil edilen müşteri için alınır.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#2)]  
  
 Bu kodu çalıştırdığınızda, aşağıdaki çıktıyı konsola görüntülenir:  
  
 **Döndürülen ham veriler:**  
**\<? xml sürümü "1.0" kodlama = "utf-8" tek başına = = "yes"? >**   
**\<ContactName xmlns = "http://schemas.microsoft.com/ado/2007/08/dataservices" > Maria Anders\</ContactName >** bir iş akışında, bu örnek kodu birleştirilir <xref:System.Activities.CodeActivity.Execute%2A> , geçersiz bir <xref:System.Activities.CodeActivity>-özel etkinlik, ancak aynı temel işlevselliği de gerçekleştirilebilir kullanarak <xref:System.Activities.Expressions.InvokeMethod%601> etkinlik. <xref:System.Activities.Expressions.InvokeMethod%601> Etkinlik statik çağırma ve yöntemleri bir sınıfın örneği iş akışı yazarları sağlar ve belirtilen yöntemini zaman uyumsuz olarak çağırma seçeneği de vardır. Aşağıdaki örnekte, bir <xref:System.Activities.Expressions.InvokeMethod%601> etkinliği çağırmak için yapılandırılmış <xref:System.Net.WebClient.DownloadString%2A> yöntemi <xref:System.Net.WebClient> sınıfı ve müşterilerin listesini döndürür.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#3)]  
  
 <xref:System.Activities.Expressions.InvokeMethod%601> hem statik çağırın ve yöntemleri bir sınıfın örneğini kullanabilirsiniz. Bu yana <xref:System.Net.WebClient.DownloadString%2A> bir örnek yöntemi <xref:System.Net.WebClient> sınıfı, yeni bir örneğini <xref:System.Net.WebClient> sınıfı için belirtilen <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A>. `DownloadString` olarak belirtilen <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A>, sorguyu içeren URI belirtilen <xref:System.Activities.Expressions.InvokeMethod%601.Parameters%2A> toplama ve dönüş değeri atanması <xref:System.Activities.Activity%601.Result%2A> değeri. <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> Değeri ayarı `true`, yöntem çağırma iş akışı ile zaman uyumsuz olarak çalıştıracak anlamına gelir. Aşağıdaki örnekte, kullanan bir iş akışı oluşturulan <xref:System.Activities.Expressions.InvokeMethod%601> örnek Northwind verileri sorgulamak için etkinlik hizmet siparişleri belirli bir müşteri için bir listesi için ve daha sonra döndürülen verileri konsola yazılır.  
  
 [!code-csharp[CFX_WCFDataServicesActivityExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_WCFDataServicesActivityExample/cs/Program.cs#1)]  
  
 Bu iş akışı çağrıldığında, aşağıdaki çıktıyı konsola görüntülenir. Bu sorgu çalışanlarına döndürdüğünden, çıktı yalnızca bir kısmını burada görüntülenir.  
  
 **WCF veri hizmeti çağrılırken...**  
**Döndürülen ham veriler:**   
**\<? xml sürümü "1.0" kodlama = "utf-8" tek başına = = "yes"? >**   
**\<Akış**   
 **XML:Base = "http://services.odata.org/Northwind/Northwind.svc/"**  
 **xmlns:d = "http://schemas.microsoft.com/ado/2007/08/dataservices"**  
 **xmlns:m = "http://schemas.microsoft.com/ado/2007/08/dataservices/metadata"**  
 **xmlns = "http://www.w3.org/2005/Atom" >**  
 **\<türü title = "text" > siparişleri \< /title >**  
 **\<Kimliği >http://services.odata.org/Northwind/Northwind.svc/Customers('ALFKI') / siparişleri\</ID >**  
 **\<güncelleştirilmiş > 2010-05-19T19:37:07Z\</ güncelleştirilmiş >**  
 **\<İlişki bağlantı "Otomatik" title = "Siparişler" href = "Siparişler" = / >**  
 **\<Giriş >**  
 **\<Kimliği >http://services.odata.org/Northwind/Northwind.svc/Orders(10643)\</ID >**  
 **\<türü title = "text" > \< /title >**  
 **\<güncelleştirilmiş > 2010-05-19T19:37:07Z\</ güncelleştirilmiş >**  
 **\<Yazar >**  
 **\<Ad / >**  
 **\</ author >**  
 **\<İlişki bağlantı "Düzenle" title = "Order" href="Orders(10643) =" / >**  
 **\<İlişki bağlantı = "http://schemas.microsoft.com/ado/2007/08/dataservices/related/Customer"**  
 **türü = "uygulama/atom + xml yazın; Giriş =" title = "Müşteri" href = "(10643) / müşteri sipariş" = / >**  
**...**  Bu örnek iş akışı uygulama yazarları bir OData hizmetten döndürülen ham verileri kullanmak üzere kullanabileceğiniz bir yöntem sağlar. WCF veri URI'ler kullanarak hizmetlere erişme hakkında daha fazla bilgi için bkz: [veri hizmeti kaynaklar (WCF Veri Hizmetleri) erişim](http://go.microsoft.com/fwlink/?LinkId=193397) ve [OData: URI kuralları](http://go.microsoft.com/fwlink/?LinkId=185564).
