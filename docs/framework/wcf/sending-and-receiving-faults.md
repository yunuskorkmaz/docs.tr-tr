---
title: Hataları Gönderme ve Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], sending
ms.assetid: 7be6fb96-ce2a-450b-aebe-f932c6a4bc5d
ms.openlocfilehash: 096b56d720a7facce68111a0f46cf05687dc9a34
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945657"
---
# <a name="sending-and-receiving-faults"></a>Hataları Gönderme ve Alma
SOAP hataları bir hizmetten istemciye ve çift yönlü bir şekilde bir istemciden hizmete hata koşulu bilgilerini iletmelidir. Genellikle bir hizmet özel hata içeriğini tanımlar ve hangi işlemlerin bu işlemleri döndürebileceğini belirtir. (Daha fazla bilgi için bkz. [hataları tanımlama ve belirtme](../../../docs/framework/wcf/defining-and-specifying-faults.md).) Bu konuda, bir hizmet veya çift yönlü istemcinin ilgili hata koşulu oluştuğunda ve bir istemci ya da hizmet uygulamasının bu hataları nasıl işleyeceği açıklanır. Windows Communication Foundation (WCF) uygulamalarında hata işlemeye genel bir bakış için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="sending-soap-faults"></a>SOAP hataları gönderiliyor  
 Tanımlanan SOAP hataları, özel bir SOAP hata türünü belirten bir <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> işlemin öğesine sahip olduğu olanlardır. Bildirilmemiş SOAP hataları bir işlem için sözleşmede belirtilmemiş olanlardır.  
  
### <a name="sending-declared-faults"></a>Bildirilmeyen hatalar gönderiliyor  
 Tanımlanmış bir soap hatası göndermek için, SOAP hatasının uygun olduğu hata koşulunu tespit edin ve tür parametresinin, <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> <xref:System.ServiceModel.FaultContractAttribute> bu işlemde belirtilen türün yeni bir nesnesi olduğu yeni bir nesne oluşturun. Aşağıdaki kod örneği, <xref:System.ServiceModel.FaultContractAttribute> `SampleMethod` işlemin ayrıntı türü `GreetingFault`ile bir soap hatası döndüre, belirtmek için öğesinin kullanımını gösterir.  
  
 [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
 [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
 `GreetingFault` Hata bilgilerini istemciye iletmek için, uygun hata koşulunu yakalayın ve aşağıdaki kod örneğinde olduğu gibi, bağımsız <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> değişkeni olarak `GreetingFault` yeni `GreetingFault` bir nesne içeren yeni bir nesne türü oluşturun. İstemci bir WCF istemci uygulaması ise, bu, türün <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> türü `GreetingFault`olduğu yönetilen bir özel durum olarak deneyimdir.  
  
 [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
 [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
### <a name="sending-undeclared-faults"></a>Bildirilmemiş hatalar gönderiliyor  
 Bildirilmemiş hataların gönderilmesi, WCF uygulamalarında sorunları hızlı bir şekilde tanılamak ve hatalarını ayıklamak için çok yararlı olabilir, ancak hata ayıklama aracı olarak kullanışlılığı sınırlıdır. Daha genel olarak, hata ayıklanırken <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliği kullanmanız önerilir. Bu değeri true olarak belirlediğinizde istemciler bu tür hataları türünde <xref:System.ServiceModel.FaultException%601> <xref:System.ServiceModel.ExceptionDetail>özel durumlar olarak deneyime sahiptir.  
  
> [!IMPORTANT]
> Yönetilen özel durumlar iç uygulama bilgilerini kullanıma sunabileceğinden, <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> için `true` ayarı, WCF istemcilerinin kişisel olarak da dahil olmak üzere iç hizmet işlemi özel durumları hakkında bilgi almasına izin verebilir tanımlanabilir veya diğer hassas bilgiler.  
>   
>  Bu nedenle, <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> veya olarak ayarlanması yalnızca bir hizmet uygulamasının geçici olarak hata ayıklamanın bir yolu olarak önerilir. `true` Ayrıca, işlenmemiş yönetilen özel durumları bu şekilde döndüren bir yöntem için WSDL, türü <xref:System.ServiceModel.FaultException%601> <xref:System.ServiceModel.ExceptionDetail>için anlaşma içermez. İstemciler, hata ayıklama bilgilerini düzgün bir şekilde almak için bilinmeyen bir soap hatası (WCF <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> istemcilerine geri döndürülen) olasılığını beklememelidir.  
  
 Bildirilmemiş bir soap hatası göndermek için bir <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> nesne (genel tür <xref:System.ServiceModel.FaultException%601>değil) oluşturun ve dizeyi oluşturucuya geçirin. Bu, <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> yöntemi çağırarak, dizenin kullanılabildiği bir oluşturulan özel durum olarak WCF istemci uygulamalarına sunulur.  
  
> [!NOTE]
> String türünde bir soap hatası bildirirseniz ve bunu hizmetinize <xref:System.ServiceModel.FaultException%601> , Type parametresinin bir <xref:System.String?displayProperty=nameWithType> dize <xref:System.ServiceModel.FaultException%601.Detail%2A?displayProperty=nameWithType> değeri olduğu yerde bir dize değeri olarak oluşturursanız ve ' de kullanılamaz <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType>.  
  
## <a name="handling-faults"></a>Hataları işleme  
 WCF istemcilerinde, istemci uygulamalarına ilgi eden iletişim sırasında oluşan SOAP hataları yönetilen özel durumlar olarak oluşturulur. Herhangi bir programın yürütülmesi sırasında oluşabilecek birçok özel durum olsa da, WCF istemci programlama modelini kullanan uygulamalar, iletişimin sonucu olarak aşağıdaki iki türdeki özel durumları işlemeye bekleyebilir.  
  
- <xref:System.TimeoutException>  
  
- <xref:System.ServiceModel.CommunicationException>  
  
 <xref:System.TimeoutException>bir işlem belirtilen zaman aşımı süresini aştığında nesneler oluşturulur.  
  
 <xref:System.ServiceModel.CommunicationException>hizmet veya istemcide bazı kurtarılabilir iletişim hatası koşulu olduğunda nesneler oluşturulur.  
  
 Sınıfta iki önemli türetilmiş <xref:System.ServiceModel.FaultException> tür ve genel <xref:System.ServiceModel.FaultException%601> tür bulunur. <xref:System.ServiceModel.CommunicationException>  
  
 <xref:System.ServiceModel.FaultException>bir dinleyici, işlem sözleşmesinde beklenmediği veya belirtilmediği bir hata aldığında özel durumlar oluşur; genellikle bu durum, uygulamanın hata ayıklaması yapıldığında ve hizmetin <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliği olarak `true`ayarlandığında oluşur.  
  
 <xref:System.ServiceModel.FaultException%601>işlem sözleşmesinde belirtilen bir hata, iki yönlü bir işleme (yani, olarak <xref:System.ServiceModel.OperationContractAttribute> <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `false`ayarlanmış bir özniteliğe sahip bir yöntem) yanıt olarak alındığında, istemci üzerinde özel durumlar oluşur.  
  
> [!NOTE]
> Bir WCF hizmeti, istemci olarak <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ayarlanan <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> veya özelliği olduğunda `true` , bu, türü bildirilmemiş <xref:System.ServiceModel.FaultException%601> bir tür <xref:System.ServiceModel.ExceptionDetail>olarak deneyim sağlar. İstemciler, bu hatayı yakalayabilir veya bir catch bloğunda <xref:System.ServiceModel.FaultException>hatayı işleyebilir.  
  
 Genellikle, yalnızca <xref:System.ServiceModel.FaultException%601> <xref:System.TimeoutException>, ve <xref:System.ServiceModel.CommunicationException> özel durumlar, istemcileri ve Hizmetleri ilgilenir.  
  
> [!NOTE]
> Tabii ki diğer özel durumlar oluşur. Beklenmeyen özel durumlar gibi <xref:System.OutOfMemoryException?displayProperty=nameWithType>çok önemli hatalardan kaynaklanır; genellikle uygulamalar bu tür yöntemleri yakalayamaz.  
  
### <a name="catch-fault-exceptions-in-the-correct-order"></a>Hata özel durumlarını doğru sırada yakala  
 <xref:System.ServiceModel.FaultException%601> ,Ve<xref:System.ServiceModel.CommunicationException>öğesinden türetildiğinden, bu özel durumları uygun sırada yakalamak önemlidir. <xref:System.ServiceModel.FaultException> <xref:System.ServiceModel.FaultException> Örneğin, ilk olarak yakaladığınız <xref:System.ServiceModel.CommunicationException>bir try/catch bloğuna sahipseniz, belirtilen ve belirtilmeyen tüm SOAP hataları burada işlenir; özel <xref:System.ServiceModel.FaultException%601> bir özel durumu işlemek için sonraki tüm catch blokları hiçbir şekilde çağrılmaz.  
  
 Bir işlemin belirtilen sayıda hata döndürebileceği unutulmamalıdır. Her hata benzersiz bir türdür ve ayrı olarak işlenmelidir.  
  
### <a name="handle-exceptions-when-closing-the-channel"></a>Kanalı kapatırken özel durumları işle  
 Yukarıdaki tartışmanın çoğu, uygulama iletilerini işleme sırasında, diğer bir deyişle istemci uygulama, WCF istemci nesnesi üzerinde işlemler çağırdığında istemci tarafından açıkça gönderilen iletiler ile yapılır.  
  
 Nesneleri elden atan yerel nesneler bile geri dönüşüm işlemi sırasında oluşan özel durumları oluşturabilir veya maskeleyebilir. WCF istemci nesnelerini kullandığınızda benzer bir durum oluşabilir. İşlemleri çağırdığınızda, oluşturulan bir bağlantı üzerinden ileti gönderiyorsunuz. Kanalın kapatılması, bağlantı düzgün şekilde kapatılabilir veya tüm işlemler düzgün şekilde döndürülse bile zaten kapalıysa özel durumlar oluşturabilir.  
  
 Genellikle, istemci nesne kanalları aşağıdaki yollarla kapalıdır:  
  
- WCF istemci nesnesi geri dönüştürüldüğünde.  
  
- İstemci uygulaması çağırdığında <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>.  
  
- İstemci uygulaması çağırdığında <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>.  
  
- İstemci uygulaması, bir oturum için sonlandırma işlemi olan bir işlem çağırdığında.  
  
 Her durumda kanalı kapatmak, kanala, uygulama düzeyinde karmaşık işlevselliği destekleyecek şekilde ileti gönderen temeldeki tüm kanalları kapatmaya başlamasını söyler. Örneğin, bir anlaşma oturum gerektirdiğinde, bir bağlama bir oturum oluşturuluncaya kadar hizmet kanalına sahip iletiler değiş tokuşu yaparak bir oturum kurmaya çalışır. Kanal kapatıldığında, temeldeki oturum kanalı hizmete oturumun sonlandırıldığını bildirir. Bu durumda, kanal önceden durdurulmuş, kapalı veya kullanılamaz durumdaysa (örneğin, bir ağ kablosu kesilmediyse), istemci kanalı, oturum sonlandırıldığı ve bir özel durum ortaya çıkmış olan hizmet kanalına bilgi verebilir.  
  
### <a name="abort-the-channel-if-necessary"></a>Gerekirse kanalı durdur  
 Kanalı kapatmak aynı zamanda özel durumlar da oluşturabileceğinden, hata özel durumlarının doğru sırada yakalanmasıyla ilgili ek olarak, yakalama bloğunda çağrı yapmak için kullanılan kanalı durdurmak önemlidir.  
  
 Hata bilgilerini bir işleme özel olarak ortaya çıkardıysanız ve başkalarının kullanabilmesi mümkün kalırsa, kanalı durdurmaya gerek kalmaz (Bu durumlar nadir olsa da). Diğer tüm durumlarda, kanalı iptal etmeniz önerilir. Tüm bu noktaları gösteren bir örnek için bkz. [Beklenen özel durumlar](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
 Aşağıdaki kod örneği, bir temel istemci uygulamasında, belirtilen bir hata ve bildirilmemiş bir hata da dahil olmak üzere SOAP hata özel durumlarının nasıl işleneceğini gösterir.  
  
> [!NOTE]
> Bu örnek kod, `using` yapısını kullanmaz. Kapatma kanalları özel durumlar oluşturabileceğinden, uygulamaların önce bir WCF istemcisi oluşturması önerilir ve sonra aynı try bloğunda WCF istemcisini açmak, kullanmak ve kapatmak önerilir. Ayrıntılar için bkz. [WCF Istemcisine genel bakış](../../../docs/framework/wcf/wcf-client-overview.md) ve [WCF istemci kaynaklarını serbest bırakmak Için kapat ve iptal kullanma](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[FaultContractAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.FaultException>
- <xref:System.ServiceModel.FaultException%601>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- [Beklenen Özel Durumlar](../../../docs/framework/wcf/samples/expected-exceptions.md)
- [WCF istemci kaynaklarını serbest bırakmak için Kapat ve Durdur kullanın](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)
