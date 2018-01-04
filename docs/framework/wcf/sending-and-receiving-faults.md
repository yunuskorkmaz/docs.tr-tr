---
title: "Hataları Gönderme ve Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: handling faults [WCF], sending
ms.assetid: 7be6fb96-ce2a-450b-aebe-f932c6a4bc5d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 248202e07d3b74f5d71b40155ae8f617f7ed15ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="sending-and-receiving-faults"></a>Hataları Gönderme ve Alma
SOAP hatalarının istemciye ve durumda çift yönlü bir istemciden bir hizmete hata koşulu bilgi hizmet birlikte çalışabilir bir şekilde aktarın. Genellikle bir hizmet özel hata içeriği tanımlar ve hangi işlemleri geri dönebilirsiniz belirtir. (Daha fazla bilgi için bkz: [tanımlama ve belirtme hataları](../../../docs/framework/wcf/defining-and-specifying-faults.md).) Bu konuda ele alınmıştır nasıl bir hizmet ya da çift yönlü istemci bu hataları karşılık gelen hata koşulu oluştu ne zaman ve bir istemci nasıl gönderebilir veya hizmet uygulaması bu hataları işleme. Hata işleme, genel bir bakış için [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] uygulamalar, bkz [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="sending-soap-faults"></a>SOAP hataları gönderme  
 SOAP hataları olan bir işlem olduğu bildirildiğinde bir <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> özel bir SOAP hatası türü belirtir. Bildirilmemiş SOAP hatalarının bir işlem için bir sözleşmede belirtilen değil izinlerdir.  
  
### <a name="sending-declared-faults"></a>Bildirilen hataları gönderme  
 Bildirilen bir SOAP hatası göndermek için bir SOAP hatası olduğu uygun hata koşulunu algılamak ve yeni bir throw <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> burada tür parametresi, belirtilen türdeki yeni bir nesne <xref:System.ServiceModel.FaultContractAttribute> bu işlem için. Aşağıdaki kod örneğinde kullanımı gösterilmiştir <xref:System.ServiceModel.FaultContractAttribute> belirtmek için `SampleMethod` işlemi, bir SOAP hatası ayrıntı türüyle dönebilirsiniz `GreetingFault`.  
  
 [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
 [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
 İletmek için `GreetingFault` hata bilgilerini istemciye uygun hata durumunu yakalamak ve yeni bir throw <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> türü `GreetingFault` yeni bir `GreetingFault` nesnesi aşağıdaki kod örneğinde olduğu gibi bağımsız değişkeni olarak. İstemci ise bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci uygulaması karşılaştığı bu türünün olduğu yönetilen bir özel durum <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> türü `GreetingFault`.  
  
 [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
 [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
### <a name="sending-undeclared-faults"></a>Bildirilmemiş hataları gönderme  
 Bildirilmemiş hataları gönderme hızla tanılamak ve sorunları hata ayıklamak çok kullanışlı olabilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulamalar, ancak bir hata ayıklama aracı olarak kendi yararlılığını sınırlıdır. Daha fazla genel olarak, ne zaman, hata ayıklama önerilir, kullandığınız <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliği. Bu değeri true olarak ayarlayın, istemciler bu tür hataları olarak karşılaşıyorsunuz <xref:System.ServiceModel.FaultException%601> özel durum türü <xref:System.ServiceModel.ExceptionDetail>.  
  
> [!IMPORTANT]
>  Yönetilen özel durumlar iç uygulama bilgileri kullanıma sunabileceğinden ayarı <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> için `true` izin verebilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kişisel dahil olmak üzere iç hizmet işlemi özel durumlar hakkında bilgi edinmek için istemciler Kişisel ya da diğer hassas bilgiler.  
>   
>  Bu nedenle, ayarı <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> için `true` yalnızca geçici olarak bir hizmet uygulaması hata ayıklama bir yolu olarak önerilir. İşlenmemiş döndüren bir yöntem yönetilen özel durumları bu şekilde ek olarak, WSDL sözleşmesi içermiyor <xref:System.ServiceModel.FaultException%601> türü <xref:System.ServiceModel.ExceptionDetail>. İstemciler, bilinmeyen bir SOAP hatası olasılığını beklediğiniz gerekir (döndürülen [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemcileri olarak <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> nesneler) hata ayıklama bilgilerini düzgün şekilde alınamadı.  
  
 Bildirilmemiş bir SOAP hatası göndermek için throw bir <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> nesne (diğer bir deyişle, değil genel tür <xref:System.ServiceModel.FaultException%601>) ve dize oluşturucuya geçirin. Bu maruz [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci uygulamaları bir atılmış olarak <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> dize olduğu kullanılabilir çağırarak özel durum <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> yöntemi.  
  
> [!NOTE]
>  Dize türünde bir SOAP hatası bildirme ve bu, hizmet olarak throw bir <xref:System.ServiceModel.FaultException%601> tür parametresi olduğu bir <xref:System.String?displayProperty=nameWithType> dize değeri atandığı <xref:System.ServiceModel.FaultException%601.Detail%2A?displayProperty=nameWithType> özelliği ve kullanılamaz <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType>.  
  
## <a name="handling-faults"></a>Hata işleme  
 İçinde [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemciler, istemci uygulamalarının ilgi iletişim sırasında oluşan SOAP hataları yönetilen özel durumlar olarak gerçekleşti. Kullanarak uygulamalar programlarından yürütülmesi sırasında oluşan birçok özel durumlarını varken [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci programlama modeli iletişim sonucu olarak aşağıdaki iki türlerde özel durumları işleme olasıdır.  
  
-   <xref:System.TimeoutException>  
  
-   <xref:System.ServiceModel.CommunicationException>  
  
 <xref:System.TimeoutException>bir işlemi belirtilen zaman aşımı süresi aştığında nesneleri atılır.  
  
 <xref:System.ServiceModel.CommunicationException>Bazı hizmet veya istemci kurtarılabilir iletişimi hata koşulu olduğunda nesneleri atılır.  
  
 <xref:System.ServiceModel.CommunicationException> Sınıfına sahip iki önemli türetilen türlerin, <xref:System.ServiceModel.FaultException> ve genel <xref:System.ServiceModel.FaultException%601> türü.  
  
 <xref:System.ServiceModel.FaultException>Dinleyici değil beklenmeyen veya işlemi sözleşmede belirtilen bir arıza aldığında özel durumlar; Genellikle bu uygulamanın hata ayıklaması ve hizmet bulunduğunda oluşur <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliğini `true`.  
  
 <xref:System.ServiceModel.FaultException%601>özel durumlar istemcide işlemi sözleşmede belirtilen bir arıza yanıt iki yönlü bir işlem olarak alındığında (diğer bir deyişle, bir yöntemle bir <xref:System.ServiceModel.OperationContractAttribute> ile öznitelik <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> kümesine `false`).  
  
> [!NOTE]
>  Zaman bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliğini `true` istemci bu bildirilmemiş karşılaştığında <xref:System.ServiceModel.FaultException%601> türü <xref:System.ServiceModel.ExceptionDetail>. İstemciler bu belirli bir arıza catch veya işlemek için catch bloğu içinde hata <xref:System.ServiceModel.FaultException>.  
  
 Genellikle, yalnızca <xref:System.ServiceModel.FaultException%601>, <xref:System.TimeoutException>, ve <xref:System.ServiceModel.CommunicationException> istisnaları istemciler ve hizmetler için ilgi.  
  
> [!NOTE]
>  Elbette, diğer özel durumlar oluşur. Beklenmeyen özel durumları içerecek yıkıcı hataları gibi <xref:System.OutOfMemoryException?displayProperty=nameWithType>; genellikle uygulamalar gibi yöntemleri catch değil.  
  
### <a name="catch-fault-exceptions-in-the-correct-order"></a>Doğru sırayla hataya özel durumlarını yakalama  
 Çünkü <xref:System.ServiceModel.FaultException%601> türetilen <xref:System.ServiceModel.FaultException>, ve <xref:System.ServiceModel.FaultException> türetilen <xref:System.ServiceModel.CommunicationException>, doğru sırayla bu özel durumları yakalamak önemlidir. Örneğin, bir try/catch varsa, hangi, ilk catch engelleme <xref:System.ServiceModel.CommunicationException>, tüm belirtilen ve belirtilmeyen SOAP hatalarının işlenmesini vardır; herhangi bir sonraki catch bloğu bir özel işlemek için <xref:System.ServiceModel.FaultException%601> özel durumu hiçbir zaman çağrılır.  
  
 Tek bir işlemle belirtilen hataları herhangi bir sayıda döndürebilir unutmayın. Her hata benzersiz türü ve ayrı ayrı ele alınması gerekir.  
  
### <a name="handle-exceptions-when-closing-the-channel"></a>Kanal kapatılırken özel durumları işleme  
 Yukarıdaki açıklama çoğunu sahip başka bir deyişle, uygulama iletileri işleme aşamasında gönderilen hatalarıyla istemci uygulaması işlemleri çağırdığında açıkça istemci tarafından gönderilen iletileri yapmak [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci nesnesi.  
  
 Bile yerel nesneleriyle nesne atma yükseltmek ya da geri dönüştürme işlemi sırasında oluşan özel durumlar maske. Kullandığınızda benzer bir şey oluşabilir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci nesneleri. Operations çağırdığınızda iletileri kurulan bir bağlantı gönderiyor. Bağlantı düzgün bir şekilde kapatılamaz veya zaten kapatılmış, tüm işlemleri düzgün döndürülen olsa bile kanal kapatma özel durumları atabilirsiniz.  
  
 Genellikle, istemci nesnesi kanalları aşağıdaki yollardan biriyle kapalı:  
  
-   Zaman [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] istemci nesnesi dönüştürülmeden.  
  
-   İstemci uygulaması çağırdığında <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>.  
  
-   İstemci uygulaması çağırdığında <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>.  
  
-   İstemci uygulaması bir işlem, çağırdığında bir oturum için sonlandırma bir işlemdir.  
  
 Her durumda, uygulama düzeyinde karmaşık işlevleri desteklemek için ileti gönderilirken herhangi temel kanalları kapatmayı başlatmak için kanal kanal kapatma bildirir. Örneğin, bir sözleşme oturumları gerektirdiğinde bağlama oturumu kurulana kadar iletileri hizmet kanalı ile değiştirerek bir oturumu çalışır. Kanal kapatıldığında, temel alınan oturum kanalı hizmeti, oturum sonlandırılır bildirir. Bu durumda, istemci kanal oturum sonlandırılır ve bir özel durum sonuçlanabilir hizmet kanal bildirin olamaz. kanal zaten, kapalı, iptal edilmiş ya da aksi takdirde (örneğin bir ağ kablosu) kullanılamaz.  
  
### <a name="abort-the-channel-if-necessary"></a>Kanal gerekirse iptal  
 Ardından, kanal kapatma özel durumları da atabilirsiniz olduğundan, doğru sırayla hataya özel durumları yakalama ek olarak, içindeki yakalama bloğunun arama yaparken kullanılan kanal iptal etmek önemli olduğunu önerilir.  
  
 Hata bilgisi için bir işlemi belirli hataya iletir ve diğerleri bunu kullanabilirsiniz olası kalır, (Bu durumda nadir olmasına rağmen) kanal iptal etmek için gerek yoktur. Diğer durumlarda, kanal abort önerilir. Tüm bu noktalarına gösteren bir örnek için bkz: [beklenen özel durumlar](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
 Aşağıdaki kod örneğinde bildirilen hata ve bildirilmemiş bir hataya dahil olmak üzere bir temel istemci uygulamasında SOAP hataya özel durumları işleme gösterir.  
  
> [!NOTE]
>  Bu örnek kod kullanmayan `using` oluşturun. Kanallar kapatma özel durumları throw çünkü uygulamaları oluşturmanız önerilir bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ilk ve sonra istemci, kullanım ve Kapat [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aynı try bloğundaki istemci. Ayrıntılar için bkz [WCF istemcisi genel bakış](../../../docs/framework/wcf/wcf-client-overview.md) ve [Using deyimi sorunlarını önleme](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
 [!code-csharp[FaultContractAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.FaultException>  
 <xref:System.ServiceModel.FaultException%601>  
 <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>  
 [Beklenen Özel Durumlar](../../../docs/framework/wcf/samples/expected-exceptions.md)  
 [Using Deyimi Sorunlarını Önleme](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)
