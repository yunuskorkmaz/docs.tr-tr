---
title: Windows Communication Foundation Bağlamaları Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], overview
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
ms.openlocfilehash: 90da8f4a2b4efeb684cbe9e5513084e6d1c6f515
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703692"
---
# <a name="windows-communication-foundation-bindings-overview"></a>Windows Communication Foundation Bağlamaları Genel Bakış
Bağlamaları bir Windows Communication Foundation (WCF) hizmet uç noktasını bağlamak için gerekli olan iletişim ayrıntılarını belirtmek için kullanılan nesneleridir. Her bir WCF Hizmeti uç noktası bağlama iyi belirtilen olmasını gerektirir. Bu konuda bağlarını tanımlamak, iletişim ayrıntılarını bağlama, hangi bağlamaları WCF'de dahil edilir ve bir bağlama için bir uç nokta nasıl belirtilebilir öğelerin türleri açıklanmaktadır.  
  
## <a name="what-a-binding-defines"></a>Bir bağlama tanımlar  
 Bağlama bilgileri çok temel ya da çok karmaşık olabilir. En temel bağlama uç noktaya bağlanmak için kullanılacak Aktarım Protokolü (HTTP gibi) belirtir. Daha genel bir uç noktaya bağlanmak nasıl bilgi içeren bir bağlama aşağıdaki kategorilerden birine döner.  
  
 Protokolleri  
 Kullanılan güvenlik mekanizması belirler: güvenilir Mesajlaşma özelliği ya da işlem bağlamını akış ayarları.  
  
 Encoding  
 İleti (örneğin, metin veya ikili) kodlamasını belirler.  
  
 Taşıma  
 (Örneğin, TCP veya HTTP) kullanmak için temel alınan Aktarım Protokolü belirler.  
  
## <a name="the-elements-of-a-binding"></a>Bağlama öğeleri  
 Bir bağlama her biri bir hizmet uç noktasına bağlanmak için gereken iletişim bilgileri bölümünde belirten bağlama öğelerinin, bir sıralı yığını temelde oluşur. İki en düşük katman yığınında hem de olması gerekir. Yığın tabanına aktarım bağlama öğesinin ve yalnızca bu belirtimleri kodlamasını içeren öğe. Bir iletişim protokolleri belirten isteğe bağlı bağlama öğeleri, bu iki gerekli öğeye katmanlıdır. Bu bağlama öğeleri ve bunların doğru sıralama hakkında daha fazla bilgi için bkz. [özel bağlamalar](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar  
 Bağlama bilgileri karmaşık olabilir ve bazı ayarları başkalarıyla uyumlu olmayabilir. Bu nedenle, WCF, sistem tarafından sağlanan bağlamaları kümesini içerir. Bu bağlamalar, çoğu uygulama gereksinimlerini karşılamak üzere tasarlanmıştır. Aşağıdaki sınıflar, sistem tarafından sağlanan bağlamalar bazı örnekler temsil eder:  
  
- <xref:System.ServiceModel.BasicHttpBinding>: WS uyan bir HTTP protokolü Web hizmetlerine bağlanmak için uygun bağlama-ı temel profil belirtimi (örneğin, ASP.NET Web hizmeti tabanlı Hizmetleri).  
  
- <xref:System.ServiceModel.WSHttpBinding>: WS - için uygun Uç noktalara bağlanmak için uygun bir birlikte çalışabilen bağlama * protokoller.  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>: Kullanan [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] diğer WCF uç noktaları aynı makineye bağlanmak için.  
  
- <xref:System.ServiceModel.NetMsmqBinding>: Kullanan [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] diğer WCF uç noktaları ile kuyruğa alınan iletinin bağlantılar oluşturmak için.  

- <xref:System.ServiceModel.NetTcpBinding>: Bu bağlama HTTP bağlamaları daha yüksek performans sunar ve yerel ağ kullanım için idealdir.
  
 Tüm WCF tarafından sağlanan bağlamalar, açıklamalarını ile tam bir listesi için bkz. [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="using-your-own-bindings"></a>Kendi bağlamaları kullanma  
 Dahil sistem tarafından sağlanan bağlamalar hiçbiri doğru birleşimi bir hizmet uygulaması gerektirir özellikler varsa, kendi bağlama oluşturabilirsiniz. Bunu yapmanın iki yolu vardır. Kullanarak bağlama öğeleri önceden varolan ya da yeni bir bağlama oluşturabilirsiniz bir <xref:System.ServiceModel.Channels.CustomBinding> nesne veya oluşturabilir tamamen kullanıcı tanımlı bir bağlama türeterek <xref:System.ServiceModel.Channels.Binding> bağlama. Bu iki yaklaşımı kullanarak kendi bağlama oluşturma hakkında daha fazla bilgi için bkz. [özel bağlamalar](../../../docs/framework/wcf/extending/custom-bindings.md) ve [Creating User-Defined bağlamaları](../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="using-bindings"></a>Bağlamaları kullanma  
 Bağlamalar kullanılarak iki temel adımları kapsar:  
  
1. Seçin veya bir bağlama tanımlar. WCF ile dahil sistem tarafından sağlanan bağlamalar birini seçin ve kendi varsayılan ayarlarla kullanmak için en kolay yöntemdir bakın. Ayrıca, sistem tarafından sağlanan bir bağlamayı seçin ve gereksinimlerinize uyacak şekilde özellik değerlerine sıfırlayın. Alternatif olarak, Denetim ve özelleştirme daha yüksek derece özel bağlama veya kullanıcı tanımlı bir bağlama oluşturabilirsiniz.  
  
2. Seçili veya tanımlı bağlama kullanan bir uç nokta oluşturun.  
  
## <a name="code-and-configuration"></a>Kod ve yapılandırma  
 Bağlama iki yolla tanımlayabilirsiniz: yapılandırma veya kod aracılığıyla. Bu iki yaklaşımı, sistem tarafından sağlanan bir bağlamayı veya özel bir bağlama kullanarak üzerinde güvenmeyin. Genel olarak, kod kullanarak bir bağlama tasarım zamanında tanımı üzerinde tam denetim verir. Yapılandırmayı kullanarak diğer taraftan, Sistem Yöneticisi veya bir WCF hizmeti veya hizmeti uygulamayı yeniden derlemenize gerek kalmadan bir bağlama parametreleri değiştirmek için istemci kullanıcı sağlar. WCF uygulaması, dağıtılacak olduğu belirli makine gereksinimlerini tahmin etmenin yolu olduğundan bu esnekliğin genellikle tercih edilir. Bağlama (ve adresleme) tutma bilgi kodunun dışında yeniden derleme veya yeniden dağıtma işlemi uygulamanın gerek kalmadan değiştirmek sağlar. Kod içinde tanımlanan bağlamaları sonra yapılandırma dosyasında belirtilen bağlamaları yapılandırma tanımlı bağlamalar üzerine yazmak kod tanımlı bağlamalar izin vererek oluşturulduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
