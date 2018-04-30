---
title: Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 68c8c2c93ce29147247c332848025fd931bf7854
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="using-bindings-to-configure-services-and-clients"></a>Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma
Bağlamaları bir bitiş noktasına bağlanmak için gereken iletişim ayrıntılarını belirtin nesneleridir. Daha açık belirtmek gerekirse bağlamaları taşımaları, bağlantı biçimlerini (ileti kodlama) ve ilgili uç noktası veya istemci kanalı protokolleri ayrıntılarını tanımlayarak istemci veya hizmet çalışma zamanı oluşturmak için kullanılan yapılandırma bilgilerini içerir. Çalışan bir oluşturmak için [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] hizmet, hizmet her bitiş bağlama gerektirir. Bu konuda ne bağlamaları, nasıl tanımlanır ve belirli bir bağlama için bir uç nokta nasıl belirtilen açıklanmaktadır.  
  
## <a name="what-a-binding-defines"></a>Hangi bağlama tanımlar  
 Bağlama bilgileri çok temel veya çok karmaşık olabilir. En temel bağlama bitiş noktasına bağlanmak için kullanılması gereken Aktarım Protokolü (HTTP gibi) belirtir. Daha fazla genel olarak, aşağıdaki tabloda kategorilerde birine bir bağlama içeren bir uç noktasını bağlamak hakkında bilgi döner.  
  
 protokolleri  
 Kullanılan, güvenlik mekanizması belirler güvenilir Mesajlaşma özellik veya işlem bağlamı akış ayarları.  
  
 Taşıma  
 (Örneğin, TCP veya HTTP) kullanmak için temel Aktarım Protokolü belirler.  
  
 Kodlama  
 İleti kodlama, örneğin, text/XML, ikili veya ileti iletim en iyi duruma getirme mekanizmasını (iletileri bayt akışları hattaki olarak nasıl temsil edildiğini belirleyen MTOM), belirler.  
  
## <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] çoğu uygulama gereksinimleri ve senaryolarını kapsamak üzere tasarlanmış sistem tarafından sağlanan bağlamaları kümesi içerir. Aşağıdaki sınıflar sistem tarafından sağlanan bağlamalar bazı örnekleri temsil eder:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>: WS uyumlu Web hizmetlerine bağlanmak için uygun bağlama bir HTTP protokolü-ı temel Profil 1.1 belirtimini (örneğin, [ASMX] ASP.NET Web Hizmetleri-services tabanlı).  
  
-   <xref:System.ServiceModel.WSHttpBinding>: Web'e uygun Uç noktalara bağlanmak için uygun bağlama bir HTTP protokol belirtimleri protokolleri Hizmetleri.  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>: Diğer bağlanmak için .NET ikili kodlama ve kanal taşıma adlı Windows ile birlikte teknolojileri çerçeveleme kullandığı [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bitiş noktaları aynı makine üzerindeki.  
  
-   <xref:System.ServiceModel.NetMsmqBinding>: Kullandığı .NET ikili kodlama ve teknolojileri iletisi oluşturmak için Queuing (MSMQ olarak da bilinir) ile birlikte çerçeveleme kuyruğa ileti diğer bağlantılarla [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uç noktaları.  
  
 Açıklamalarını, sistem tarafından sağlanan bağlamalar tam bir listesi için bkz: [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Özel Bağlamalar  
 Sistem tarafından sağlanan bir bağlamayı koleksiyonu bir hizmet uygulaması gerektiren özellikleri doğru birleşimini yoksa oluşturabileceğiniz bir <xref:System.ServiceModel.Channels.CustomBinding> bağlama. Öğeleri hakkında daha fazla bilgi için bir <xref:System.ServiceModel.Channels.CustomBinding> bağlama, bkz: [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) ve [özel bağlamaları](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="using-bindings"></a>Bağlamaları kullanma  
 Bağlamalar kullanılarak iki temel adımları kapsar:  
  
1.  Seçin veya bir bağlama tanımlayın. En kolay yöntem, sistem tarafından sağlanan bağlamalar birini seçin ve varsayılan ayarlarına kullanmaktır. Ayrıca, sistem tarafından sağlanan bir bağlamayı seçin ve gereksinimlerinize uyacak şekilde özellik değerlerini sıfırlayın. Alternatif olarak, özel bir bağlama oluşturun ve her özellik gerektiği gibi ayarlayın.  
  
2.  Bu bağlamayı kullanan bir uç nokta oluşturun.  
  
## <a name="code-and-configuration"></a>Kod ve yapılandırma  
 Tanımlayın veya kod veya yapılandırma aracılığıyla bağlamaları yapılandırın. Bu iki yaklaşım, örneğin, bir sistem tarafından sağlanan kullanıp kullanmadığınızı veya kullanılabilir bağlama türünü bağımsız <xref:System.ServiceModel.Channels.CustomBinding> bağlama. Derlediğinizde genel olarak, kod kullanarak, bir bağlama tanımı üzerinde tam denetim sağlar. Yapılandırma, diğer yandan kullanarak sağlayan bir sistem yöneticisi veya kullanıcısı bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet veya istemci bağlamaları parametrelerini değiştirin. Bu esneklik genellikle belirli bir makine gereksinimlerini tahmin etmek ve koşullar, ağ yolu olduğundan tercih edilir. bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulamasıdır dağıtılacak. Koddan bağlayıcı (ve adresleme) bilgi ayırarak yeniden derleyin veya uygulamayı yeniden dağıtmak zorunda kalmadan bağlama ayrıntıları değiştirmek Yöneticiler sağlar. Bağlama kodda tanımlanmış olması durumunda, yapılandırma dosyasında yapılan tüm yapılandırma temelli tanımları üzerine yazılacağını unutmayın. Bu yaklaşım örnekler için aşağıdaki konulara bakın:  
  
-   [Nasıl yapılır: yönetilen bir uygulamada bir WCF Hizmeti barındırma](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md) kod içinde bir bağlaması oluşturma bir örnek sağlar.  
  
-   [Nasıl yapılır: bir istemci yapılandırma](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md) Yapılandırması'nı kullanarak bir istemci oluşturma bir örnek sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Uç Nokta Oluşturmaya Genel Bakış](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Nasıl yapılır: Yapılandırmada Hizmet Bağlaması Belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [Nasıl yapılır: Code’da Hizmet Bağlaması Belirtme](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)  
 [Nasıl yapılır: Yapılandırmada İstemci Bağlaması Belirtme](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)  
 [Nasıl yapılır: Code’da İstemci Bağlaması Belirtme](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-code.md)
