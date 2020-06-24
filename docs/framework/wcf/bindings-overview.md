---
title: Windows Communication Foundation Bağlamaları Genel Bakış
description: Bağlamanın öğeleri de dahil olmak üzere bir WCF hizmetine nasıl bağlanacağınızı ve hizmet uç noktası için nasıl bağlama yapılacağını belirten bağlamalar hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], overview
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
ms.openlocfilehash: da8050c4e9aeb111de3a54315b3650bcf09f23ed
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247720"
---
# <a name="windows-communication-foundation-bindings-overview"></a>Windows Communication Foundation Bağlamaları Genel Bakış
Bağlamalar, bir Windows Communication Foundation (WCF) hizmetinin uç noktasına bağlanmak için gereken iletişim ayrıntılarını belirtmek için kullanılan nesnelerdir. Bir WCF hizmetindeki her uç noktanın, bir bağlamanın iyi belirtilmiş olması gerekir. Bu konu, bağlamaların belirlediği iletişim ayrıntılarının türlerini, bir bağlamanın öğelerini, WCF 'de hangi bağlamaların ekleneceğini ve bir uç nokta için bir bağlamanın nasıl belirtilebileceklerini özetler.  
  
## <a name="what-a-binding-defines"></a>Bağlama ne tanımlar  
 Bir bağlamadaki bilgiler çok basit veya çok karmaşık olabilir. En temel bağlama, yalnızca uç noktaya bağlanmak için kullanılması gereken aktarım protokolünü (HTTP gibi) belirtir. Daha genel olarak, bir bağlamanın bir uç noktaya nasıl bağlanacağı hakkında bilgiler aşağıdaki kategorilerden birine girer:  
  
 **Protokoller**  
 Kullanılan güvenlik mekanizmasını belirler: Güvenilir Mesajlaşma özelliği ya da işlem bağlamı akış ayarları.  
  
 **Encoding**  
 İleti kodlamasını belirler (örneğin, metin veya ikili).  
  
 **Aktarım**  
 Kullanılacak temel alınan aktarım protokolünü belirler (örneğin, TCP veya HTTP).  
  
## <a name="the-elements-of-a-binding"></a>Bağlama öğeleri  
 Bir bağlama temelde, her biri bir hizmet uç noktasına bağlanmak için gereken iletişim bilgilerinin bir parçasını belirten, her biri bir sıralı bağlama öğesi yığınından oluşur. Yığındaki iki en düşük katman her ikisi de gereklidir. Yığının tabanında, taşıma bağlama öğesidir ve bu, yalnızca yukarıdaki ileti kodlama belirtimlerini içeren öğedir. Diğer iletişim protokollerini belirten isteğe bağlı bağlama öğeleri, bu iki zorunlu öğenin üzerine katmanlı. Bu bağlama öğeleri ve bunların doğru sıralaması hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](./extending/custom-bindings.md).  
  
## <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar  
 Bir bağlamadaki bilgiler karmaşık olabilir ve bazı ayarlar başkalarıyla uyumlu olmayabilir. Bu nedenle, WCF bir sistem tarafından sağlanmış bağlamalar kümesi içerir. Bu bağlamalar çoğu uygulama gereksinimini kapsayacak şekilde tasarlanmıştır. Aşağıdaki sınıflar sistem tarafından sunulan bağlamaların bazı örneklerini temsil eder:  
  
- <xref:System.ServiceModel.BasicHttpBinding>: WS-ı temel profil belirtimine uyan Web hizmetlerine bağlanmak için uygun bir HTTP protokol bağlaması (örneğin, ASP.NET Web Hizmetleri tabanlı hizmetler).  
  
- <xref:System.ServiceModel.WSHttpBinding>: WS-* protokollerine uygun uç noktalara bağlanmak için uygun bir birlikte çalışabilen bağlama.  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>: Aynı makinedeki diğer WCF uç noktalarına bağlanmak için .NET Framework kullanır.  
  
- <xref:System.ServiceModel.NetMsmqBinding>: Diğer WCF uç noktalarıyla sıraya alınmış ileti bağlantıları oluşturmak için .NET Framework kullanır.  

- <xref:System.ServiceModel.NetTcpBinding>: Bu bağlama HTTP bağlamalarından daha yüksek performans sunar ve yerel bir ağda kullanılmak üzere idealdir.
  
 Tüm WCF tarafından sağlanmış bağlamaların açıklamaları içeren tam bir liste için bkz. [sistem tarafından sunulan bağlamalar](system-provided-bindings.md).  
  
## <a name="using-your-own-bindings"></a>Kendi bağlamalarınızı kullanma  
 Dahil edilen sistem tarafından sağlanan bağlamalardan hiçbiri bir hizmet uygulamasının gerektirdiği özelliklerin doğru birleşimine sahip değilse, kendi bağlamalarınızı oluşturabilirsiniz. Bunu yapmanın iki yolu vardır. Önceden var olan bağlama öğelerinden bir nesne kullanarak yeni bir bağlama oluşturabilir <xref:System.ServiceModel.Channels.CustomBinding> veya bağlamadan türeterek, tümüyle Kullanıcı tanımlı bir bağlama oluşturabilirsiniz <xref:System.ServiceModel.Channels.Binding> . Bu iki yaklaşımı kullanarak kendi bağlamalarınızı oluşturma hakkında daha fazla bilgi için bkz. [Özel Bağlamalar](./extending/custom-bindings.md) ve [Kullanıcı Tanımlı Bağlamalar Oluşturma](./extending/creating-user-defined-bindings.md).  
  
## <a name="using-bindings"></a>Bağlamaları kullanma  
 Bağlamaları kullanmak iki temel adımı kapsar:  
  
1. Bir bağlama seçin veya tanımlayın. En kolay yöntem, WCF 'ye dahil edilen sistem tarafından sağlanan bağlamalardan birini seçmek ve varsayılan ayarlarıyla kullanmaktır. Ayrıca sistem tarafından sağlanmış bir bağlama seçebilir ve özellik değerlerini gereksinimlerinize uyacak şekilde sıfırlayabilirsiniz. Alternatif olarak, daha yüksek düzeyde denetim ve özelleştirme derecesi sağlamak için özel bir bağlama veya Kullanıcı tanımlı bir bağlama oluşturabilirsiniz.  
  
2. Seçili veya tanımlı bağlamayı kullanan bir uç nokta oluşturun.  
  
## <a name="code-and-configuration"></a>Kod ve yapılandırma  
 Bağlamaları iki şekilde tanımlayabilirsiniz: kod aracılığıyla veya yapılandırma yoluyla. Bu iki yaklaşım, sistem tarafından sağlanmış bir bağlama veya özel bir bağlama kullanıp kullanmayacağınızı temel değildir. Genel olarak, kod kullanımı, tasarım zamanında bir bağlamanın tanımı üzerinde tüm denetim sağlar. Diğer yandan yapılandırma kullanımı, bir sistem yöneticisinin veya bir WCF hizmeti ya da istemcisinin, hizmet uygulamasını yeniden derlemek zorunda kalmadan bir bağlamanın parametrelerini değiştirmesine izin verir. Bu esneklik genellikle tercih edilir çünkü bir WCF uygulamasının dağıtılacağı belirli makine gereksinimlerini tahmin etmenin bir yolu yoktur. Bağlama (ve adresleme) bilgisinin koddan tutulması, uygulamanın yeniden derlenmesi veya yeniden dağıtılması gerekmeden değiştirilmesine izin verir. Kodda tanımlanan bağlamaların yapılandırmada belirtilen bağlamalardan sonra oluşturulduğunu ve kod tanımlı bağlamaların yapılandırma tanımlı bağlamaların üzerine yazılmasına izin vermesini unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](using-bindings-to-configure-services-and-clients.md)
