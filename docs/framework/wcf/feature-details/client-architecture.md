---
title: İstemci Mimarisi
ms.date: 03/30/2017
ms.assetid: 02624403-0d77-41cb-9a86-ab55e98c7966
ms.openlocfilehash: c873368b82551312d203eb28d208eb6e3f50c89b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587007"
---
# <a name="client-architecture"></a>İstemci Mimarisi
Uygulamalar, hizmet işlemlerini çağırmak için Windows Communication Foundation (WCF) istemci nesnelerini kullanır. Bu konuda, WCF istemci nesneleri, WCF istemci kanalları ve bunların temel alınan kanal mimarisine yönelik ilişkileri açıklanmaktadır. WCF istemci nesnelerine temel bir genel bakış için bkz. [WCF Istemcisine genel bakış](../wcf-client-overview.md). Kanal katmanı hakkında daha fazla bilgi için bkz. [Kanal Katmanını Genişletme](../extending/extending-the-channel-layer.md).  
  
## <a name="overview"></a>Genel Bakış  
 Hizmet modeli çalışma zamanı, aşağıdakilerden oluşan WCF istemcileri oluşturur:  
  
- Bir hizmet sözleşmesinin otomatik olarak oluşturulan istemci uygulaması, uygulama kodınızdan giden iletilere yapılan çağrıları etkinleştirir ve yanıt iletilerini çıkış parametrelerine dönüştürür ve uygulamanızın alabileceği değer döndürür.  
  
- <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>Çeşitli arabirimleri birbirine bağlayan ve denetim işlevlerine erişim sağlayan bir denetim arabirimi (), özellikle de istemci oturumunu kapatıp kanalı atma özelliği.  
  
- Kullanılan bağlama tarafından belirtilen yapılandırma ayarlarına bağlı olarak oluşturulan bir istemci kanalı.  
  
 Uygulamalar, <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> ya da <xref:System.ServiceModel.ClientBase%601> [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)tarafından oluşturulan türetilmiş bir sınıfın örneğini oluşturarak bu tür istemcileri isteğe bağlı olarak oluşturabilir. Bu hazır olan bu istemci sınıfları, tarafından dinamik olarak oluşturulan bir istemci kanal uygulamasını kapsüller ve devredebilir <xref:System.ServiceModel.ChannelFactory> . Bu nedenle, istemci kanalı ve bunları üreten kanal fabrikası, bu tartışmayı ilgilendiren odak noktasıdır.  
  
## <a name="client-objects-and-client-channels"></a>İstemci nesneleri ve Istemci kanalları  
 WCF istemcilerinin temel arabirimi, <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> çekirdek istemci işlevlerinin yanı sıra temel iletişim nesne işlevselliği <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> , öğesinin bağlam işlevselliği <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType> ve Genişletilebilir davranışı sunan arabirimdir <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType> .  
  
 <xref:System.ServiceModel.IClientChannel>Ancak arabirim, bir hizmet sözleşmesinin kendisini tanımlamaz. Bunlar, hizmet sözleşmesi arabirimi tarafından bildirilenler (genellikle [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)gibi bir araç kullanılarak hizmet meta verilerinden oluşturulur). WCF istemci türleri <xref:System.ServiceModel.IClientChannel> , uygulamaların işlemleri doğrudan aramasını ve ayrıca istemci tarafı çalışma zamanı işlevselliğine erişmesini sağlamak için hem hem de hedef hizmet sözleşmesi arabirimini genişletir. WCF istemcisi oluşturma, <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> yapılandırılmış hizmet uç noktasıyla bağlantı kurup etkileşime girebilen bir çalışma zamanı oluşturmak için gereken bilgileri IÇEREN WCF nesneleri sağlar.  
  
 Daha önce belirtildiği gibi, bunları kullanabilmeniz için iki WCF istemci türünün yapılandırılması gerekir. En basit WCF istemci türleri, <xref:System.ServiceModel.ClientBase%601> (veya <xref:System.ServiceModel.DuplexClientBase%601> hizmet sözleşmesi bir çift yönlü sözleşme ise) öğesinden türetilen nesnelerdir. Bu türleri bir Oluşturucu kullanarak veya bir yapılandırma dosyası kullanarak oluşturabilir, sonra doğrudan hizmet işlemlerini çağırmak için çağırılır. Nesnelere temel bir genel bakış için <xref:System.ServiceModel.ClientBase%601> bkz. [WCF Istemcisine genel bakış](../wcf-client-overview.md).  
  
 İkinci tür, yönteme yapılan çağrıdan çalışma zamanında oluşturulur <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> . İletişim özelliklerinin sıkı denetimiyle ilgilenen uygulamalar genellikle *istemci kanal nesnesi*olarak adlandırılan bu istemci türünü kullanır, çünkü temeldeki istemci çalışma zamanı ve kanal sisteminden daha fazla doğrudan etkileşim imkanı sunar.  
  
## <a name="channel-factories"></a>Kanal fabrikaları  
 İstemci çağırmaları destekleyen temel çalışma süresini oluşturmaktan sorumlu sınıf, <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> sınıftır. Hem WCF istemci nesneleri hem de WCF istemci kanalı nesneleri <xref:System.ServiceModel.ChannelFactory%601> , örnek oluşturmak için bir nesnesi kullanır; <xref:System.ServiceModel.ClientBase%601> türetilmiş istemci nesnesi, kanal fabrikası işlemeyi kapsüller, ancak bir dizi senaryoda, kanal fabrikasını doğrudan kullanmak tam olarak mantıklı olur. Bunun için genel senaryo, var olan bir fabrikada sürekli olarak yeni istemci kanalları oluşturmak isteiyorlarsa. İstemci nesnesi kullanıyorsanız, özelliği çağırarak bir WCF istemci nesnesinden temeldeki kanal fabrikası elde edebilirsiniz <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A?displayProperty=nameWithType> .  
  
 Kanal fabrikaları hakkında hatırlamanız gereken önemli şey, çağrılmadan önce onlara sunulan yapılandırma için yeni istemci kanalları örnekleri oluşturmlarıdır <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> . <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>(Veya <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> , <xref:System.ServiceModel.ClientBase%601.CreateChannel%2A?displayProperty=nameWithType> veya bir WCF istemci nesnesi üzerinde herhangi bir işlem) çağırdıktan sonra, hedef uç nokta adresini yalnızca değiştirseniz bile, kanal fabrikasını değiştiremez ve farklı hizmet örneklerine kanal almayı bekleyebilir. Farklı bir yapılandırmaya sahip bir istemci nesnesi veya istemci kanalı oluşturmak isterseniz, önce yeni bir kanal fabrikası oluşturmanız gerekir.  
  
 WCF istemci nesnelerini ve WCF istemci kanallarını kullanan çeşitli sorunlar hakkında daha fazla bilgi için bkz. [WCF Istemcisi kullanarak hizmetlere erişme](accessing-services-using-a-client.md).  
  
 Aşağıdaki iki bölümde, WCF istemci kanalı nesnelerinin oluşturulması ve kullanılması açıklanır.  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Yeni bir WCF Istemci kanalı nesnesi oluşturma  
 İstemci kanalının kullanımını göstermek için aşağıdaki hizmet sözleşmesinin oluşturulduğunu varsayın.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Bir hizmete bağlanmak için `ISampleService` , oluşturulan sözleşme arabirimini doğrudan bir Channel Factory () ile kullanın <xref:System.ServiceModel.ChannelFactory%601> . Belirli bir sözleşme için bir kanal fabrikası oluşturup yapılandırdıktan sonra, <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> bir hizmetle iletişim kurmak için kullanabileceğiniz istemci kanal nesnelerini döndürmek için yöntemini çağırabilirsiniz `ISampleService` .  
  
 <xref:System.ServiceModel.ChannelFactory%601>Sınıfını bir hizmet sözleşmesi arabirimiyle kullanırken, <xref:System.ServiceModel.IClientChannel> kanalı açıkça açmak, kapatmak veya iptal etmek için arabirimine dönüştürmelisiniz. , İle çalışmayı kolaylaştırmak için, Svcutil. exe aracı, hem hizmet sözleşmesi arabirimini uygulayan hem de <xref:System.ServiceModel.IClientChannel> istemci kanal altyapısına dönüştürme yapmak zorunda kalmadan etkileşim kurmanızı sağlayan bir yardımcı arabirim oluşturur. Aşağıdaki kod, önceki hizmet sözleşmesini uygulayan bir yardımcı istemci kanalının tanımını gösterir.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Yeni bir WCF Istemci kanalı nesnesi oluşturma  
 Bir hizmete bağlanmak üzere bir istemci kanalı kullanmak için `ISampleService` , oluşturulan sözleşme arabirimini (veya yardımcı sürümü) doğrudan bir kanal fabrikası ile kullanın, böylece sözleşme arabiriminin türünü tür parametresi olarak geçirerek. Belirli bir sözleşmenin kanal fabrikası oluşturulduktan ve yapılandırıldıktan sonra, <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> bir hizmetle iletişim kurmak için kullanabileceğiniz istemci kanal nesnelerini döndürmek için yöntemini çağırabilirsiniz `ISampleService` .  
  
 Oluşturulduğunda, istemci kanalı nesneleri <xref:System.ServiceModel.IClientChannel> ve anlaşma arabirimini uygular. Bu nedenle, bu sözleşmeyi destekleyen bir hizmetle etkileşim kuran işlemleri çağırmak için bunları doğrudan kullanabilirsiniz.  
  
 İstemci nesneleri ve istemci kanalı nesneleri kullanma arasındaki fark, geliştiriciler için yalnızca bir denetim ve kullanım kolaylığıdır. Sınıflar ve nesneler ile rahat bir şekilde çalışan çok sayıda geliştirici, WCF istemci kanalı yerine WCF istemci nesnesini kullanmayı tercih edecektir.  
  
 Bir örnek için bkz. [nasıl yapılır: ChannelFactory kullanma](how-to-use-the-channelfactory.md).
