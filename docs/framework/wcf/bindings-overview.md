---
title: "Windows Communication Foundation Bağlamaları Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- bindings [WCF], overview
ms.assetid: cfb5842f-e0f9-4c56-a015-f2b33f258232
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4bc4fc7559872a808c2de87e4926075614351030
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-bindings-overview"></a>Windows Communication Foundation Bağlamaları Genel Bakış
Bağlamaları değil uç noktasına bağlanmak için gereken iletişim ayrıntılarını belirtmek için kullanılan nesneleri bir [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] hizmet. İçindeki her bir uç nokta bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet bağlama iyi belirtilen olmasını gerektirir. Bu konu bağlamaları tanımlamak, iletişim ayrıntılarını hangi bağlamaları içinde yer alan bir bağlama öğelerini türlerini özetler [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], ve bir bağlama için bir uç nokta nasıl belirtilebilir.  
  
## <a name="what-a-binding-defines"></a>Hangi bağlama tanımlar  
 Bağlama bilgileri çok basit ya da çok karmaşık olabilir. En temel bağlama bitiş noktasına bağlanmak için kullanılması gereken Aktarım Protokolü (HTTP gibi) belirtir. Daha fazla genel olarak, bir bağlama içeren bir uç noktasını bağlamak hakkında bilgi aşağıdaki kategoriden döner.  
  
 protokolleri  
 Kullanılan güvenlik mekanizması belirler: güvenilir Mesajlaşma özellik veya işlem bağlamı akış ayarları.  
  
 Kodlama  
 İleti (örneğin, metin veya ikili) kodlamasını belirler.  
  
 Taşıma  
 (Örneğin, TCP veya HTTP) kullanmak için temel Aktarım Protokolü belirler.  
  
## <a name="the-elements-of-a-binding"></a>Bağlama öğeleri  
 Bir bağlama neredeyse her biri bir hizmet uç noktasına bağlanmak için gereken iletişim bilgilerini parçası belirtir bağlama öğelerinin, bir sıralı yığın oluşur. Her ikisi de yığınında iki en düşük katman olan gerekli. Yığın tabanına aktarım bağlama öğe ve yalnızca bu belirtimleri kodlama iletisini içeren bir öğedir. Bir iletişim protokolü belirtmek isteğe bağlı bağlama öğeleri bu iki gerekli öğeler üzerinde katmanlanmış. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Bu bağlama öğeleri ve bunların doğru sipariş, bkz: [özel bağlamaları](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar  
 Bağlama bilgileri karmaşık olabilir ve bazı ayarları başkalarıyla uyumlu olmayabilir. Bu nedenle, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sistem tarafından sağlanan bağlamalar kümesi içerir. Bu bağlamaların çoğu uygulama gereksinimlerini karşılamak üzere tasarlanmıştır. Aşağıdaki sınıflar sistem tarafından sağlanan bağlamalar bazı örnekleri temsil eder:  
  
-   <xref:System.ServiceModel.BasicHttpBinding>: WS uyumlu Web hizmetlerine bağlanmak için uygun bağlama bir HTTP protokolü-ı temel profil belirtimi (örneğin, ASP.NET Web Hizmetleri tabanlı hizmetler).  
  
-   <xref:System.ServiceModel.WSHttpBinding>: WS - için uygun Uç noktalara bağlanmak için uygun birlikte çalışabilir bir bağlama * protokoller.  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>: Kullanır [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] diğer bağlanmak için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bitiş noktaları aynı makine üzerindeki.  
  
-   <xref:System.ServiceModel.NetMsmqBinding>: Kullanır [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] diğer sıraya alınan ileti bağlantıları oluşturmak için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uç noktaları.  
  
 Tüm açıklamalarını tam bir listesi için [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]-bağlamaları, bkz: sağlanan [System-Provided bağlamaları](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="using-your-own-bindings"></a>Kendi bağlamaları kullanma  
 Dahil edilen sistem tarafından sağlanan bağlamalar hiçbiri bir hizmet uygulaması gerektiren özellikleri doğru bileşimini varsa, kendi bağlama oluşturabilirsiniz. Bunu yapmanın iki yolu vardır. Oluşturabilir ya da yeni bir bağlama kullanarak bağlama öğeleri önceden varolan bir <xref:System.ServiceModel.Channels.CustomBinding> nesne veya oluşturabilir tamamen kullanıcı tanımlı bir bağlama türetme tarafından <xref:System.ServiceModel.Channels.Binding> bağlama. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Bu iki yaklaşım kullanarak bağlama bkz kendi oluşturma [özel bağlamaları](../../../docs/framework/wcf/extending/custom-bindings.md) ve [Creating User-Defined bağlamaları](../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="using-bindings"></a>Bağlamaları kullanma  
 Bağlamalar kullanılarak iki temel adımları kapsar:  
  
1.  Seçin veya bir bağlama tanımlayın. İle birlikte gelen sistem tarafından sağlanan bağlamalar birini seçmek için kolay yöntemdir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ve varsayılan ayarlarıyla kullanın. Ayrıca, sistem tarafından sağlanan bir bağlamayı seçin ve gereksinimlerinize uyacak şekilde özellik değerlerini sıfırlayın. Alternatif olarak, Denetim ve özelleştirme yüksek derece özel bağlama veya kullanıcı tanımlı bir bağlama oluşturabilirsiniz.  
  
2.  Seçili veya tanımlı bağlama kullanan bir uç nokta oluşturun.  
  
## <a name="code-and-configuration"></a>Kod ve yapılandırma  
 İki yolla bağlamaları tanımlayabilirsiniz: kod veya yapılandırma aracılığıyla. Bu iki yaklaşım, sistem tarafından sağlanan bir bağlamayı veya özel bağlama kullanma üzerinde güvenmeyin. Genel olarak, kod kullanarak bir bağlama tasarım zamanında tanımı üzerinde tam denetim verir. Yapılandırma, diğer yandan kullanarak sağlayan bir sistem yöneticisi veya kullanıcısı bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hizmet veya hizmet uygulamayı yeniden derlemenize gerek kalmadan bağlaması parametreleri değiştirmek için istemci. Bu esneklik çoğunlukla, belirli bir makine gereksinimlerini tahmin etmenin hiçbir yolu olduğundan tercih edilir. bir [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] uygulamasıdır dağıtılacak. Bağlama (ve adresleme) tutma bilgileri kodu dışında gerektirmeden yeniden derlenmek veya uygulama çözümünüzün yeniden dağıtımını değiştirmek için bunları sağlar. Kod içinde tanımlanan bağlamaları sonra yapılandırma dosyasında belirtilen bağlamaları herhangi bir yapılandırma tanımlanmış bağlamaları üzerine yazmak kod tanımlı bağlamalar izin vererek oluşturulduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
