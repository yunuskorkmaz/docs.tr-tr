---
title: Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
ms.openlocfilehash: dd83072d3a1c76279fcc00ea5b0a4a41e278e10a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321504"
---
# <a name="using-bindings-to-configure-services-and-clients"></a>Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma
Bağlamalar, bir uç noktaya bağlanmak için gereken iletişim ayrıntılarını belirten nesnelerdir. Daha belirgin olarak bağlamalar, ilgili uç nokta veya istemci kanalı için kullanılacak aktarımların, hat biçimlerinin (ileti kodlamasının) ve protokollerin özelliklerini tanımlayarak istemci veya hizmet çalışma zamanı oluşturmak için kullanılan yapılandırma bilgilerini içerir. Çalışan bir Windows Communication Foundation (WCF) hizmeti oluşturmak için, hizmette her bir uç nokta için bağlama gerekir. Bu konuda, bağlamaların ne olduğu, nasıl tanımlandığı ve belirli bir bağlamanın bir uç nokta için nasıl belirtildiği açıklanmaktadır.  
  
## <a name="what-a-binding-defines"></a>Bağlama ne tanımlar  
 Bir bağlamadaki bilgiler çok basit veya çok karmaşık olabilir. En temel bağlama, yalnızca uç noktaya bağlanmak için kullanılması gereken aktarım protokolünü (HTTP gibi) belirtir. Daha genel olarak, bir bağlamanın bir uç noktaya nasıl bağlanacağı hakkında bilgiler aşağıdaki tablodaki kategorilerden birine girer.  
  
 Ekledikten  
 Kullanılan güvenlik mekanizmasını, güvenilir mesajlaşma özelliği ya da işlem bağlamı akış ayarları belirler.  
  
 Aktarım  
 Kullanılacak temel alınan aktarım protokolünü belirler (örneğin, TCP veya HTTP).  
  
 Şifreleme  
 İleti kodlamasının (örneğin, metin/XML, ikili veya Ileti Iletimi Iyileştirme mekanizması) (MTOM), iletilerin tel 'daki bayt akışları olarak nasıl temsil edileceğini belirleyen ileti kodlamasını belirler.  
  
## <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar  
 WCF, çoğu uygulama gereksinimini ve senaryosunu kapsayacak şekilde tasarlanan bir sistem tarafından sağlanmış bağlamalar kümesi içerir. Aşağıdaki sınıflar sistem tarafından sunulan bağlamaların bazı örneklerini temsil eder:  
  
- <xref:System.ServiceModel.BasicHttpBinding>: WS-ı temel profil 1,1 belirtimine uyan Web hizmetlerine bağlanmak için uygun bir HTTP protokol bağlaması (örneğin, ASP.NET Web Services [ASMX] tabanlı hizmetler).  
  
- <xref:System.ServiceModel.WSHttpBinding>: Web Hizmetleri belirtim protokollerine uygun uç noktalara bağlanmak için uygun bir HTTP protokol bağlaması.  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>: aynı makinede bulunan diğer WCF uç noktalarına bağlanmak için Windows adlandırılmış kanal aktarımlarıyla birlikte .NET ikili kodlama ve çerçeveleme teknolojilerini kullanır.  
  
- <xref:System.ServiceModel.NetMsmqBinding>: diğer WCF uç noktaları ile sıralanmış ileti bağlantıları oluşturmak için Message Queuing (MSMQ olarak da bilinir) ile birlikte .NET ikili kodlama ve çerçeveleme teknolojilerini kullanır.  
  
 Sistem tarafından sunulan bağlamaların tam listesi, açıklamalar ile birlikte bkz. [sistem tarafından sunulan bağlamalar](system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Özel Bağlamalar  
 Sistem tarafından sağlanmış bağlama koleksiyonu, bir hizmet uygulamasının gerektirdiği doğru özellikler birleşimine sahip değilse, <xref:System.ServiceModel.Channels.CustomBinding> bağlaması oluşturabilirsiniz. @No__t-0 bağlamasının öğeleri hakkında daha fazla bilgi için, bkz. [\<customBinding >](../configure-apps/file-schema/wcf/custombinding.md) ve [Özel Bağlamalar](./extending/custom-bindings.md).  
  
## <a name="using-bindings"></a>Bağlamaları kullanma  
 Bağlamaları kullanmak iki temel adımı kapsar:  
  
1. Bir bağlama seçin veya tanımlayın. En kolay yöntem, sistem tarafından belirtilen bağlamalardan birini seçmek ve varsayılan ayarlarını kullanmaktır. Ayrıca sistem tarafından sağlanmış bir bağlama seçebilir ve özellik değerlerini gereksinimlerinize uyacak şekilde sıfırlayabilirsiniz. Alternatif olarak, özel bir bağlama oluşturabilir ve her özelliği gereken şekilde ayarlayabilirsiniz.  
  
2. Bu bağlamayı kullanan bir uç nokta oluşturun.  
  
## <a name="code-and-configuration"></a>Kod ve yapılandırma  
 Kod veya yapılandırma aracılığıyla bağlamaları tanımlayabilir veya yapılandırabilirsiniz. Bu iki yaklaşım, kullanılan bağlama türünden bağımsızdır, örneğin, sistem tarafından sağlanmış bir veya <xref:System.ServiceModel.Channels.CustomBinding> bağlaması mi kullanıyorsunuz. Genel olarak, kod kullanımı, derleme yaparken bir bağlamanın tanımı üzerinde tüm denetim sağlar. Diğer yandan yapılandırma kullanımı, bir sistem yöneticisinin veya WCF hizmeti ya da istemcisinin Kullanıcı bağlamaların parametrelerini değiştirmesine izin verir. Bu esneklik genellikle tercih edilir çünkü bir WCF uygulamasının dağıtılacağı belirli makine gereksinimlerini ve ağ koşullarını tahmin etmenin bir yolu yoktur. Koddan bağlama (ve adresleme) bilgilerinin ayrılması, yöneticilerin uygulamayı yeniden derlemek veya yeniden dağıtmak zorunda kalmadan bağlama ayrıntılarını değiştirmesine izin verir. Bağlama kodda tanımlanmışsa, yapılandırma dosyasında yapılan yapılandırma tabanlı tanımların üzerine yazar olduğunu unutmayın. Bu yaklaşımların örnekleri için aşağıdaki konulara bakın:  
  
- [Nasıl yapılır: yönetilen bir uygulamada BIR WCF hizmetini barındırma](how-to-host-a-wcf-service-in-a-managed-application.md) , kodda bağlama oluşturma örneği sağlar.  
  
- [Öğretici: Windows Communication Foundation Istemci oluşturma](how-to-create-a-wcf-client.md) , yapılandırma kullanarak istemci oluşturmaya bir örnek sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Uç Nokta Oluşturmaya Genel Bakış](endpoint-creation-overview.md)
- [Nasıl yapılır: Yapılandırmada Hizmet Bağlaması Belirtme](how-to-specify-a-service-binding-in-configuration.md)
- [Nasıl yapılır: Code’da Hizmet Bağlaması Belirtme](how-to-specify-a-service-binding-in-code.md)
- [Nasıl yapılır: Yapılandırmada İstemci Bağlaması Belirtme](how-to-specify-a-client-binding-in-configuration.md)
- [Nasıl yapılır: Code’da İstemci Bağlaması Belirtme](how-to-specify-a-client-binding-in-code.md)
