---
title: Hataları Gönderme ve Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], sending
ms.assetid: 7be6fb96-ce2a-450b-aebe-f932c6a4bc5d
ms.openlocfilehash: dc9dcb5d8e36984d1e5a2e5c5124e74509de7f3d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320221"
---
# <a name="sending-and-receiving-faults"></a>Hataları Gönderme ve Alma

SOAP hataları bir hizmetten istemciye ve çift yönlü bir şekilde bir istemciden hizmete hata koşulu bilgilerini iletmelidir. Genellikle bir hizmet özel hata içeriğini tanımlar ve hangi işlemlerin bu işlemleri döndürebileceğini belirtir. (Daha fazla bilgi için bkz. [hataları tanımlama ve belirtme](defining-and-specifying-faults.md).) Bu konuda, bir hizmet veya çift yönlü istemcinin ilgili hata koşulu oluştuğunda ve bir istemci ya da hizmet uygulamasının bu hataları nasıl işleyeceği açıklanır. Windows Communication Foundation (WCF) uygulamalarında hata işlemeye genel bir bakış için bkz. [anlaşmalar ve hizmetlerde hataları belirtme ve işleme](specifying-and-handling-faults-in-contracts-and-services.md).

## <a name="sending-soap-faults"></a>SOAP hataları gönderiliyor

Tanımlanan SOAP hataları, bir işlemin özel bir SOAP hata türünü belirten <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> ' dır. Bildirilmemiş SOAP hataları bir işlem için sözleşmede belirtilmemiş olanlardır.

### <a name="sending-declared-faults"></a>Bildirilmeyen hatalar gönderiliyor

Belirtilen bir SOAP hatası göndermek için, SOAP hatasının uygun olduğu hata koşulunu tespit edin ve tür parametresinin bu işlem için <xref:System.ServiceModel.FaultContractAttribute> ' de belirtilen türün yeni bir nesnesi olduğu yeni bir <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> oluşturun. Aşağıdaki kod örneği, `SampleMethod` işleminin `GreetingFault` ayrıntı türüyle bir SOAP hatası döndüre, @no__t belirtmek için-0 ' ın kullanımını gösterir.

[!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
[!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]

@No__t-0 hata bilgilerini istemciye iletmek için, uygun hata koşulunu yakalayın ve bağımsız değişkeni olarak yeni bir `GreetingFault` nesnesi ile `GreetingFault` türünde yeni bir <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> ' i oluşturun (Aşağıdaki kod örneğinde olduğu gibi). İstemci bir WCF istemci uygulaması ise, bu, türün `GreetingFault` türünde <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> olduğu yönetilen bir özel durum olarak karşılaşır.

[!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
[!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]

### <a name="sending-undeclared-faults"></a>Bildirilmemiş hatalar gönderiliyor

Bildirilmemiş hataların gönderilmesi, WCF uygulamalarında sorunları hızlı bir şekilde tanılamak ve hatalarını ayıklamak için çok yararlı olabilir, ancak hata ayıklama aracı olarak kullanışlılığı sınırlıdır. Daha genel olarak, hata ayıklarken, <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliğini kullanmanız önerilir. Bu değeri true olarak belirlediğinizde, istemciler bu tür hataları <xref:System.ServiceModel.ExceptionDetail> türünde <xref:System.ServiceModel.FaultException%601> özel durum olarak deneyimlidir.

> [!IMPORTANT]
> Yönetilen özel durumlar iç uygulama bilgilerini kullanıma sunabileceğinden, <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ayarı `true` ' ye ayarlandığında, WCF istemcilerinin kişisel olarak tanımlanabilir veya diğer duyarlı gibi iç hizmet işlemi özel durumları hakkında bilgi almasına izin verebilir bilgi.
>
> Bu nedenle, <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> ' i `true` ' ye ayarlamak yalnızca bir hizmet uygulamasında geçici olarak hata ayıklamanın bir yolu olarak önerilir. Ayrıca, işlenmemiş yönetilen özel durumları bu şekilde döndüren bir yöntem için WSDL, <xref:System.ServiceModel.ExceptionDetail> türündeki <xref:System.ServiceModel.FaultException%601> için sözleşme içermez. İstemciler, hata ayıklama bilgilerini doğru şekilde almak için bilinmeyen bir SOAP hatası (WCF istemcilerine <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> nesnesi olarak döndürülen) olasılığını beklememelidir.

Bildirilmemiş bir SOAP hatası göndermek için, <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> nesnesi oluşturun (yani, genel tür <xref:System.ServiceModel.FaultException%601>) ve dizeyi oluşturucuya geçirin. Bu, <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> metodunu çağırarak, dizenin kullanılabildiği bir <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> özel durumu olarak WCF istemci uygulamalarına sunulur.

> [!NOTE]
> String türünde bir SOAP hatası bildirirseniz ve bunu hizmetinize <xref:System.ServiceModel.FaultException%601> olarak, tür parametresinin <xref:System.String?displayProperty=nameWithType> olduğu bir @no__t oluşturursanız, dize değeri-2 özelliğine atanır ve <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> ' ten kullanılamaz.

## <a name="handling-faults"></a>Hataları işleme

WCF istemcilerinde, istemci uygulamalarına ilgi eden iletişim sırasında oluşan SOAP hataları yönetilen özel durumlar olarak oluşturulur. Herhangi bir programın yürütülmesi sırasında oluşabilecek birçok özel durum olsa da, WCF istemci programlama modelini kullanan uygulamalar, iletişimin sonucu olarak aşağıdaki iki türdeki özel durumları işlemeye bekleyebilir.

- <xref:System.TimeoutException>

- <xref:System.ServiceModel.CommunicationException>

<xref:System.TimeoutException> nesne, bir işlem belirtilen zaman aşımı süresini aştığında oluşturulur.

<xref:System.ServiceModel.CommunicationException> nesneleri, hizmette veya istemcide bazı kurtarılabilir iletişim hatası koşulu olduğunda oluşturulur.

@No__t-0 sınıfında iki önemli türetilmiş tür ve <xref:System.ServiceModel.FaultException> ve genel <xref:System.ServiceModel.FaultException%601> türü vardır.

<xref:System.ServiceModel.FaultException> özel durum, bir dinleyici işlem sözleşmesinde beklenmez veya belirtilen bir hata aldığında oluşur; genellikle bu durum, uygulamanın hataları ayıklandığında ve hizmetin <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliği `true` ' ye ayarlı olduğunda meydana gelir.

<xref:System.ServiceModel.FaultException%601> özel durum, işlem sözleşmesinde belirtilen bir hata iki yönlü bir işleme yanıt olarak alındığında (diğer bir deyişle, <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> `false` olarak ayarlanan <xref:System.ServiceModel.OperationContractAttribute> özniteliğine sahip bir yöntem) istemci üzerinde oluşturulur.

> [!NOTE]
> Bir WCF hizmeti <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliği `true` ' ye ayarlandığında, istemci bunu <xref:System.ServiceModel.ExceptionDetail> türünde bildirilmemiş bir <xref:System.ServiceModel.FaultException%601> olarak deneyimler. İstemciler, bu hatayı yakalayabilir veya <xref:System.ServiceModel.FaultException> için bir catch bloğunda hatayı işleyebilir.

Genellikle, istemci ve hizmetlere yalnızca <xref:System.ServiceModel.FaultException%601>, <xref:System.TimeoutException> ve <xref:System.ServiceModel.CommunicationException> özel durum ilgi alanıdır.

> [!NOTE]
> Tabii ki diğer özel durumlar oluşur. Beklenmeyen özel durumlar <xref:System.OutOfMemoryException?displayProperty=nameWithType>; gibi çok zararlı arızalardır. genellikle uygulamalar bu tür yöntemleri yakalayamaz.

### <a name="catch-fault-exceptions-in-the-correct-order"></a>Hata özel durumlarını doğru sırada yakala

@No__t-0 <xref:System.ServiceModel.FaultException> ' den türediğinden ve <xref:System.ServiceModel.FaultException> <xref:System.ServiceModel.CommunicationException> ' ten türetildiğinden, bu özel durumların uygun sırada yakalanmaları önemlidir. Örneğin, <xref:System.ServiceModel.CommunicationException> ' ı ilk yakalayacak bir try/catch bloğuna sahipseniz, belirtilen ve belirtilmeyen tüm SOAP hataları orada işlenir; Özel <xref:System.ServiceModel.FaultException%601> özel durumunu işlemek için sonraki tüm catch blokları hiçbir şekilde çağrılmaz.

Bir işlemin belirtilen sayıda hata döndürebileceği unutulmamalıdır. Her hata benzersiz bir türdür ve ayrı olarak işlenmelidir.

### <a name="handle-exceptions-when-closing-the-channel"></a>Kanalı kapatırken özel durumları işle

Yukarıdaki tartışmanın çoğu, uygulama iletilerini işleme sırasında, diğer bir deyişle istemci uygulama, WCF istemci nesnesi üzerinde işlemler çağırdığında istemci tarafından açıkça gönderilen iletiler ile yapılır.

Nesneleri elden atan yerel nesneler bile geri dönüşüm işlemi sırasında oluşan özel durumları oluşturabilir veya maskeleyebilir. WCF istemci nesnelerini kullandığınızda benzer bir durum oluşabilir. İşlemleri çağırdığınızda, oluşturulan bir bağlantı üzerinden ileti gönderiyorsunuz. Kanalın kapatılması, bağlantı düzgün şekilde kapatılabilir veya tüm işlemler düzgün şekilde döndürülse bile zaten kapalıysa özel durumlar oluşturabilir.

Genellikle, istemci nesne kanalları aşağıdaki yollarla kapalıdır:

- WCF istemci nesnesi geri dönüştürüldüğünde.

- İstemci uygulaması <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType> ' yı çağırdığında.

- İstemci uygulaması <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> ' yı çağırdığında.

- İstemci uygulaması, bir oturum için sonlandırma işlemi olan bir işlem çağırdığında.

Her durumda kanalı kapatmak, kanala, uygulama düzeyinde karmaşık işlevselliği destekleyecek şekilde ileti gönderen temeldeki tüm kanalları kapatmaya başlamasını söyler. Örneğin, bir anlaşma oturum gerektirdiğinde, bir bağlama bir oturum oluşturuluncaya kadar hizmet kanalına sahip iletiler değiş tokuşu yaparak bir oturum kurmaya çalışır. Kanal kapatıldığında, temeldeki oturum kanalı hizmete oturumun sonlandırıldığını bildirir. Bu durumda, kanal önceden durdurulmuş, kapalı veya kullanılamaz durumdaysa (örneğin, bir ağ kablosu kesilmediyse), istemci kanalı, oturum sonlandırıldığı ve bir özel durum ortaya çıkmış olan hizmet kanalına bilgi verebilir.

### <a name="abort-the-channel-if-necessary"></a>Gerekirse kanalı durdur

Kanalı kapatmak aynı zamanda özel durumlar da oluşturabileceğinden, hata özel durumlarının doğru sırada yakalanmasıyla ilgili ek olarak, yakalama bloğunda çağrı yapmak için kullanılan kanalı durdurmak önemlidir.

Hata bilgilerini bir işleme özel olarak ortaya çıkardıysanız ve başkalarının kullanabilmesi mümkün kalırsa, kanalı durdurmaya gerek kalmaz (Bu durumlar nadir olsa da). Diğer tüm durumlarda, kanalı iptal etmeniz önerilir. Tüm bu noktaları gösteren bir örnek için bkz. [Beklenen özel durumlar](./samples/expected-exceptions.md).

Aşağıdaki kod örneği, bir temel istemci uygulamasında, belirtilen bir hata ve bildirilmemiş bir hata da dahil olmak üzere SOAP hata özel durumlarının nasıl işleneceğini gösterir.

> [!NOTE]
> Bu örnek kod `using` yapısını kullanmaz. Kapatma kanalları özel durumlar oluşturabileceğinden, uygulamaların önce bir WCF istemcisi oluşturması önerilir ve sonra aynı try bloğunda WCF istemcisini açmak, kullanmak ve kapatmak önerilir. Ayrıntılar için bkz. [WCF Istemcisine genel bakış](wcf-client-overview.md) ve [WCF istemci kaynaklarını serbest bırakmak Için kapat ve iptal kullanma](./samples/use-close-abort-release-wcf-client-resources.md).

[!code-csharp[FaultContractAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
[!code-vb[FaultContractAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.FaultException>
- <xref:System.ServiceModel.FaultException%601>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- [Beklenen Özel Durumlar](./samples/expected-exceptions.md)
- [WCF istemci kaynaklarını serbest bırakmak için Kapat ve Durdur kullanın](./samples/use-close-abort-release-wcf-client-resources.md)
