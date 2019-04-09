---
title: Hataları Gönderme ve Alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], sending
ms.assetid: 7be6fb96-ce2a-450b-aebe-f932c6a4bc5d
ms.openlocfilehash: 2757f98066931ca1b5e3ef147cee2c819ee22606
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195065"
---
# <a name="sending-and-receiving-faults"></a>Hataları Gönderme ve Alma
SOAP hatalarının hata durum bilgisini bir hizmetten istemci ve hizmet için bir istemciden çift yönlü durumda birlikte çalışabilen bir biçimde aktarın. Genellikle hizmet özel hata içeriği tanımlar ve hangi işlemlerin döndürülmeleri belirtir. (Daha fazla bilgi için [tanımlama ve belirtme hatası](../../../docs/framework/wcf/defining-and-specifying-faults.md).) Bu konu nasıl bir hizmet ya da çift yönlü istemci bu hataları karşılık gelen hata koşulu olduğunda ve bir istemci nasıl gönderebilir açıklar veya hizmet uygulaması bu hataların işler. Hata işleme Windows Communication Foundation (WCF) uygulamalarında genel bakış için bkz. [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="sending-soap-faults"></a>SOAP hataları gönderme  
 SOAP hataları olan bir işlem olan bildirilmiş bir <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> özel bir SOAP hatası türü belirtir. Bildirilmemiş SOAP hataları sözleşmenin bir işlem için belirtilen değil olanlardır.  
  
### <a name="sending-declared-faults"></a>Bildirilen hataları gönderme  
 Bildirilen bir SOAP hatası göndermek için bir SOAP hatası olduğu uygun hata koşulunu algılamak ve yeni bir throw <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> tür parametresi, belirtilen türde yeni bir nesne olduğu <xref:System.ServiceModel.FaultContractAttribute> bu işlem için. Aşağıdaki kod örneği, kullanımını gösterir <xref:System.ServiceModel.FaultContractAttribute> belirtmek için `SampleMethod` işlemi ayrıntı türüne sahip bir SOAP hatasını döndürebilir `GreetingFault`.  
  
 [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
 [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
 İletmek için `GreetingFault` hata bilgilerini istemciye uygun hata durumunu yakalamak ve yeni bir throw <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> türü `GreetingFault` yeni bir `GreetingFault` aşağıdaki kod örneğinde olduğu gibi bağımsız değişkeni olarak bir nesne. İstemci bir WCF istemci uygulaması ise, bu türü olduğu yönetilen bir istisnası olarak karşılaştığı <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> türü `GreetingFault`.  
  
 [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
 [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
### <a name="sending-undeclared-faults"></a>Bildirilmemiş hataları gönderme  
 Bildirilmemiş gönderme hataları hızlı bir şekilde tanılayın ve hata ayıklama aracı sınırlı olduğu gibi WCF uygulamaları, ancak yararlılığını sorunlarında hata ayıklamak çok kullanışlı olabilir. Daha genel olduğunda, hata ayıklama önerilir kullanmanızı <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliği. Bu değeri true olarak ayarlayın, istemciler bu tür hataları olarak deneyimi <xref:System.ServiceModel.FaultException%601> türündeki özel durumlardan <xref:System.ServiceModel.ExceptionDetail>.  
  
> [!IMPORTANT]
>  Yönetilen özel durumlar iç uygulama bilgileri kullanıma sunabileceğinden, ayarı <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> için `true` kişisel dahil olmak üzere iç hizmet işlemi özel durumları hakkında daha fazla bilgi edinmek için WCF istemcileri izin verebilirsiniz veya diğer hassas bilgilerin.  
>   
>  Bu nedenle, ayarı <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> için `true` yalnızca geçici olarak bir hizmet uygulaması hata ayıklama bir yolu olarak önerilir. Bu şekilde özel durum işlenmemiş döndüren bir yöntem yönetilen ek olarak, WSDL sözleşmesini içermiyor <xref:System.ServiceModel.FaultException%601> türü <xref:System.ServiceModel.ExceptionDetail>. İstemciler, bilinmeyen bir SOAP hatası olasılığını beklemeniz gerekir (WCF istemcileri olarak döndürülen <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> nesneleri) düzgün bir şekilde hata ayıklama bilgileri edinmek için.  
  
 Bildirilmemiş bir SOAP hatası göndermek için throw bir <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> nesne (diğer bir deyişle, genel tür değil <xref:System.ServiceModel.FaultException%601>) dize oluşturucuya geçirin. Bu bir oluşturulan olarak WCF istemci uygulamalarının Internet'e <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> dize kullanılabildiği çağırarak özel durum <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> yöntemi.  
  
> [!NOTE]
>  Dize türünde bir SOAP hatasını bildirir ve hizmet bu durum bir <xref:System.ServiceModel.FaultException%601> tür parametresi olduğu bir <xref:System.String?displayProperty=nameWithType> dize değeri atanır <xref:System.ServiceModel.FaultException%601.Detail%2A?displayProperty=nameWithType> özelliği ve kullanılamaz <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType>.  
  
## <a name="handling-faults"></a>Hataları işleme  
 WCF istemcileri, iletişim sırasında oluşan SOAP hataları ilgilendiren istemci uygulamaları için yönetilen özel durumlar oluşturulur. Herhangi bir program yürütme sırasında oluşabilecek birçok özel durumları olsa da, iletişimin sonucu olarak aşağıdaki iki tür özel durumları işlemek WCF istemci programlama modelini kullanan uygulamalar bekleyebilirsiniz.  
  
-   <xref:System.TimeoutException>  
  
-   <xref:System.ServiceModel.CommunicationException>  
  
 <xref:System.TimeoutException> Belirtilen zaman aşımı süresi işlem aştığında, nesne atılır.  
  
 <xref:System.ServiceModel.CommunicationException> Hizmet veya istemci kurtarılabilir iletişim hata koşulu olduğunda, nesneler atılır.  
  
 <xref:System.ServiceModel.CommunicationException> Sınıfında iki önemli türetilen türler, <xref:System.ServiceModel.FaultException> ve genel <xref:System.ServiceModel.FaultException%601> türü.  
  
 <xref:System.ServiceModel.FaultException> Dinleyici değil beklenen ya da işlem anlaşması içinde belirtilen bir hata aldığında özel durumlar; Genellikle bu uygulamanın ayıklanmakta olan ve hizmetin ortaya çıkar <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliğini `true`.  
  
 <xref:System.ServiceModel.FaultException%601> özel durumlar istemcide yanıt iki yönlü bir işlem olarak da işlem anlaşması içinde belirtilen bir hata alındığında (diğer bir deyişle, bir yöntemle bir <xref:System.ServiceModel.OperationContractAttribute> özniteliğini <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> kümesine `false`).  
  
> [!NOTE]
>  Bir WCF Hizmeti olduğunda <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> veya <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> özelliğini `true` istemci bu bildirilmemiş bir deneyimleri <xref:System.ServiceModel.FaultException%601> türü <xref:System.ServiceModel.ExceptionDetail>. İstemciler bu belirli bir arıza catch veya işlemek için bir catch bloğu içinde hata <xref:System.ServiceModel.FaultException>.  
  
 Genellikle, yalnızca <xref:System.ServiceModel.FaultException%601>, <xref:System.TimeoutException>, ve <xref:System.ServiceModel.CommunicationException> istisnaları istemcileri ve Hizmetleri.  
  
> [!NOTE]
>  Diğer özel durumlar, oluşur. Beklenmeyen özel durumları içerecek gibi yıkıcı hataları <xref:System.OutOfMemoryException?displayProperty=nameWithType>; uygulamaları bu tür yöntemler genellikle yakalamalısınız değil.  
  
### <a name="catch-fault-exceptions-in-the-correct-order"></a>Doğru sırayla hataya özel durumları Yakala  
 Çünkü <xref:System.ServiceModel.FaultException%601> türetildiği <xref:System.ServiceModel.FaultException>, ve <xref:System.ServiceModel.FaultException> türetildiği <xref:System.ServiceModel.CommunicationException>, uygun sırada bu özel durumları yakalamak önemlidir. Örneğin, bir try/catch varsa, hangi, ilk catch içinde block <xref:System.ServiceModel.CommunicationException>, belirtilen tüm ve belirtilmeyen SOAP hatalarının işlenmesini vardır; herhangi bir sonraki yakalama bloğu özel işlemek için <xref:System.ServiceModel.FaultException%601> özel durumu hiçbir zaman çağrılır.  
  
 Tek bir işlem herhangi bir sayıda belirtilen hataları döndürebilir unutmayın. Her hata benzersiz bir türüdür ve ayrı olarak ele alınması gerekir.  
  
### <a name="handle-exceptions-when-closing-the-channel"></a>Kanal kapatılırken özel durumları işleme  
 Yukarıdaki açıklama çoğu uygulama iletileri, diğer bir deyişle, işleme aşamasında gönderilen hatalarıyla istemci uygulaması, WCF istemci nesnesi üzerinde işlemler çağırdığında açıkça istemci tarafından gönderilen iletileri yapmak vardır.  
  
 Bile yerel nesneleriyle nesne disposing yükseltmek veya dönüştürme işlemi sırasında oluşan özel durumları maskeleyebilir. WCF istemci nesneleri kullandığınızda benzer bir sorun ortaya çıkabilir. İşlemleri çağırdığınızda iletileri kurulan bir bağlantı gönderiyorsunuz. Bağlantı düzgün bir şekilde kapatıldı veya zaten kapatılmış bile tüm işlemleri düzgün döndürülen kanal kapatma özel durumlar oluşturabilecek.  
  
 Genellikle, istemci nesnesi kanalları aşağıdaki yollardan biriyle kapalı:  
  
-   WCF istemci nesnesi zaman dönüştürülmeden.  
  
-   İstemci uygulaması çağırdığında <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>.  
  
-   İstemci uygulaması çağırdığında <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType>.  
  
-   İstemci uygulama bir işlem, çağırdığında, bir oturum için Sonlandırıcı bir işlemdir.  
  
 Her durumda, kanal kapatma, uygulama düzeyinde karmaşık işlevselliği desteklemek için iletileri gönderme temel alınan tüm kanalları kapatma başlamak için kanal bildirir. Örneğin, bir sözleşme oturumları gerektirdiğinde bağlama bir oturumu yeniden kurulana kadar hizmet kanalı ile ileti değiş tokuşu ile oturum oluşturmak çalışır. Kanal kapatıldığında, temel alınan oturum kanalı hizmeti, oturum sonlandırılır bildirir. Bu durumda, kanal zaten, kapalı, iptal edilmiş ya da aksi takdirde (örneğin bir ağ kablosu) kullanılamıyor, istemci kanal oturumu sona erer ve bir özel durum sonuçlanabilir hizmet kanalı bildirin olamaz.  
  
### <a name="abort-the-channel-if-necessary"></a>Gerekirse, kanal Durdur  
 Kanal kapatma ayrıca özel durumlar oluşturabilecek çünkü daha sonra doğru sırayla hataya özel durumları yakalama ek olarak, içindeki yakalama bloğunun çağrıyı yapan kullanılan kanalı durdurmak önemlidir, önerilir.  
  
 Hata bilgisi için bir işlemi belirli hata iletmez ve başkalarının bunu kullanabilirsiniz olası kalır, (Bu gibi durumlarda nadir olmasına rağmen) kanal iptal etmek için gerek yoktur. Diğer durumlarda, kanal iptal önerilir. Bu noktaları gösteren bir örnek için bkz: [beklenen özel durumlar](../../../docs/framework/wcf/samples/expected-exceptions.md).  
  
 Aşağıdaki kod örneği, bildirilen hata ve bildirilmemiş bir hata da dahil olmak üzere bir temel istemci uygulaması, SOAP hatası özel durumları işlemek nasıl gösterir.  
  
> [!NOTE]
>  Bu örnek kod kullanmaz `using` oluşturun. Kanal kapatma özel durumlar oluşturabilecek olduğundan, WCF istemci ve ardından açık kullanımı uygulamalar oluşturmak ve Kapat WCF istemcisini aynı blok deneyin önerilir. Ayrıntılar için bkz [WCF istemcisi genel bakış](../../../docs/framework/wcf/wcf-client-overview.md) ve [kullanım Kapat ve iptal WCF istemci kaynaklar serbest bırakılacaksa](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 [!code-csharp[FaultContractAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.FaultException>
- <xref:System.ServiceModel.FaultException%601>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- [Beklenen Özel Durumlar](../../../docs/framework/wcf/samples/expected-exceptions.md)
- [Kapat ve Durdur seçeneklerini kullanarak WCF istemci kaynaklarını serbest bırakma](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)
