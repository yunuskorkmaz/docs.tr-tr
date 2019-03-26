---
title: Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
ms.openlocfilehash: 45a904eb9e38b13fc3502264f4659bfd25465630
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410426"
---
# <a name="using-bindings-to-configure-services-and-clients"></a>Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma
Bağlamaları bir uç noktaya bağlanmak için gereken iletişim ayrıntılarını belirtin nesneleridir. Daha açık belirtmek gerekirse bağlamaları taşımaları, kablo biçimleri (ileti kodlama) ve ilgili uç nokta veya istemci kanal için kullanılacak protokolleri ayrıntılarını tanımlayarak istemci veya hizmet çalışma zamanı oluşturmak için kullanılan yapılandırma bilgilerini içerir. Çalışan bir Windows Communication Foundation (WCF) hizmet oluşturmak için her hizmet uç noktasında bir bağlama gerektirir. Bu konuda, belirli bir bağlama için bir uç nokta nasıl belirtildiğine bağlamaları nedir ve nasıl tanımlandığı açıklanmaktadır.  
  
## <a name="what-a-binding-defines"></a>Bir bağlama tanımlar  
 Bağlama bilgileri çok temel ya da çok karmaşık olabilir. En temel bağlama uç noktaya bağlanmak için kullanılacak Aktarım Protokolü (HTTP gibi) belirtir. Daha genel bir uç noktaya bağlanmak nasıl bilgi içeren bir bağlama aşağıdaki tabloda kategorilerden birini sınıfındadır.  
  
 Protokolleri  
 Kullanılan, güvenlik mekanizması belirler güvenilir Mesajlaşma özelliği ya da işlem bağlamını akış ayarları.  
  
 Taşıma  
 (Örneğin, TCP veya HTTP) kullanmak için temel alınan Aktarım Protokolü belirler.  
  
 Encoding  
 İleti kodlama, örneğin, metin/XML, ikili veya ileti aktarım en iyi duruma getirme mekanizması (iletileri olarak kablo bayt akışlarında nasıl temsil edildiğini belirler MTOM), belirler.  
  
## <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar  
 WCF çoğu uygulama gereksinimlerini ve senaryoları kapsayacak şekilde tasarlanmış sistem tarafından sağlanan bağlamaları kümesini içerir. Aşağıdaki sınıflar, sistem tarafından sağlanan bağlamalar bazı örnekler temsil eder:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>: WS uyan bir HTTP protokolü Web hizmetlerine bağlanmak için uygun bağlama-ı Basic Profile 1.1 belirtimi (örneğin, [ASMX] ASP.NET Web Hizmetleri-tabanlı hizmetler).  
  
-   <xref:System.ServiceModel.WSHttpBinding>: Web uygun Uç noktalara bağlanmak için uygun bağlama bir HTTP protokolü belirtimlerine protokolleri Hizmetleri.  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>: Diğer WCF uç noktaları aynı makineye bağlanmak için kodlama ve adlandırılmış kanal taşıma Windows ile birlikte teknolojileri çerçeveleme .NET ikili kullanır.  
  
-   <xref:System.ServiceModel.NetMsmqBinding>: .NET ikili kodlama ve Message Queuing (MSMQ olarak da bilinir) ile birlikte teknolojileri çerçeveleme diğer WCF uç noktaları ile kuyruğa alınan iletinin bağlantılar oluşturmak için kullanır.  
  
 Sistem tarafından sağlanan bağlamaları, açıklamalar, tam bir listesi için bkz. [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Özel Bağlamalar  
 Sistem tarafından sağlanan bir bağlamayı koleksiyonu doğru birleşimi bir hizmet uygulaması gerektirir özellikleri yoksa, oluşturabileceğiniz bir <xref:System.ServiceModel.Channels.CustomBinding> bağlama. Öğeleri hakkında daha fazla bilgi için bir <xref:System.ServiceModel.Channels.CustomBinding> bağlamayı bkz [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ve [özel bağlamalar](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="using-bindings"></a>Bağlamaları kullanma  
 Bağlamalar kullanılarak iki temel adımları kapsar:  
  
1.  Seçin veya bir bağlama tanımlar. En kolay yöntem, sistem tarafından sağlanan bağlamalar birini seçin ve varsayılan ayarlarına kullanmaktır. Ayrıca, sistem tarafından sağlanan bir bağlamayı seçin ve gereksinimlerinize uyacak şekilde özellik değerlerine sıfırlayın. Alternatif olarak, özel bir bağlama oluşturun ve her özelliği gereken şekilde ayarlayın.  
  
2.  Bu bağlamanın kullandığı bir uç nokta oluşturun.  
  
## <a name="code-and-configuration"></a>Kod ve yapılandırma  
 Tanımlayın veya kod veya yapılandırma yoluyla bağlamaları yapılandırın. Bu iki yaklaşımı, örneğin, bir sistem tarafından sağlanan kullanıp kullanmadığınızı veya kullanılan bağlama türünü bağımsızdır <xref:System.ServiceModel.Channels.CustomBinding> bağlama. Derlediğinizde genel olarak, kod kullanarak, tanımı bağlama üzerinde tam denetim sağlar. Yapılandırmayı kullanarak diğer taraftan, Sistem Yöneticisi veya bir WCF hizmeti veya bağlama parametrelerini değiştirmek için istemci kullanıcı sağlar. Belirli bir makine gereksinimlerini tahmin edip içine dağıtılması için bir WCF uygulaması'nın koşulları ağ yolu olduğundan bu esnekliğin genellikle tercih edilir. Bağlayıcı (ve adresleme) bilgilerin koddan ayıran yeniden derleyin veya uygulama yeniden dağıtmaya gerek olmadan bağlama ayrıntılarını değiştirmek Yöneticiler sağlar. Kod içinde bağlama tanımlanmazsa, yapılandırma dosyasında yapılan herhangi bir yapılandırma temelli tanımı üzerine yazılacağını unutmayın. Bu yaklaşımların örnekler için aşağıdaki konulara bakın:  
  
-   [Nasıl yapılır: Yönetilen bir uygulamada bir WCF Hizmeti barındırma](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md) kod içinde bağlama oluşturma örneği sağlar.  
  
-   [Öğretici: Bir Windows Communication Foundation istemcisi oluşturma](../../../docs/framework/wcf/how-to-create-a-wcf-client.md) yapılandırmayı kullanarak bir istemci oluşturma örneği sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Uç Nokta Oluşturmaya Genel Bakış](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Nasıl yapılır: Yapılandırmada hizmet bağlaması belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Nasıl yapılır: Kodda hizmet bağlama belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
- [Nasıl yapılır: Yapılandırmada istemci bağlama belirtme](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
- [Nasıl yapılır: Kodda istemci bağlama belirtme](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-code.md)
