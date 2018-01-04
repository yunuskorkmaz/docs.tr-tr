---
title: "Windows mağazası uygulamaları için ağ yalıtımı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: ba7e480f50d3a339648229f17152eb28b28ec159
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="network-isolation-for-windows-store-apps"></a>Windows mağazası uygulamaları için ağ yalıtımı
Sınıfları <xref:System.Net>, <xref:System.Net.Http>, ve <xref:System.Net.Http.Headers> ad alanları, Windows mağazası uygulamaları veya Masaüstü uygulamaları geliştirmek için kullanılabilir. Ağ yalıtımı, uygulama güvenlik modeli tarafından kullanılan bir parçası olarak bu ad alanındaki sınıflar, bir Windows mağazası uygulamasında kullanıldığında, etkilenen [!INCLUDE[win8](../../../includes/win8-md.md)]. Sistem ağ erişimine izin vermek için Windows mağazası uygulaması için uygulama bildiriminde uygun ağ yeteneklerini etkinleştirilmesi gerekir.  
  
## <a name="checklist-for-network-isolation"></a>Ağ yalıtımı için Denetim listesi  
 Ağ yalıtımı Windows mağazası uygulamanız için yapılandırıldığından emin olmak için bu denetim listesini kullanın.  
  
1.  Uygulama tarafından gerekli ağ erişimi isteklerini yönünü belirler. Bu istemci tarafından başlatılan giden istekleri veya gelen istenmeyen istekleri olabilir veya bu ağ isteği türlerinin her ikisinin bir birleşimi olabilir.  
  
2.  Bu uygulama ile iletişim kuracak ağ kaynak türünü belirler. Bir uygulama, bir ev veya iş ağı üzerindeki güvenilen kaynakları ile iletişim kurmak gerekebilir. Bir uygulama, Internet üzerindeki kaynaklara ile iletişim kurmak gerekebilir. Bir uygulama, her iki tür ağ kaynaklarına erişimi gerekebilir.  
  
3.  Ağ yalıtımı gereken en düşük özellikleri uygulama bildiriminde yapılandırın.  
  
4.  Dağıtma ve sorun giderme için sağlanan ağ yalıtımı araçlar kullanılarak test etmek için uygulamanızı çalıştırın.  
  
 Ağ özelliklerini ve ağ yalıtımı sorun giderme için kullanılan yalıtım araçları yapılandırma hakkında daha ayrıntılı bilgi için bkz: [ağ yalıtımı özelliklerini yapılandırmak nasıl](http://go.microsoft.com/fwlink/?LinkID=228265) içinde [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] Geliştirici belgeler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir web hizmetine bağlanma](http://go.microsoft.com/fwlink/?LinkID=245696)  
 [Kılavuzları ve ağ yalıtımı için Denetim listesi](http://go.microsoft.com/fwlink/?LinkID=228265)  
 [Hızlı Başlangıç: HttpClient kullanarak bağlanma](http://go.microsoft.com/fwlink/?LinkId=245697)  
 [HttpClient işleyicileri kullanma](http://go.microsoft.com/fwlink/?LinkId=245699)  
 [HttpClient bağlantıları güvenliğini sağlama](http://go.microsoft.com/fwlink/?LinkId=245698)  
 [HttpClient örnek](http://go.microsoft.com/fwlink/?LinkId=242550)
