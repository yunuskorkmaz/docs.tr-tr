---
title: Windows Mağazası Uygulamaları için Ağ Yalıtımı
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: 390a0281f03b08322cc1bee469b601fd5a1547c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74802168"
---
# <a name="network-isolation-for-windows-store-apps"></a>Windows Mağazası Uygulamaları için Ağ Yalıtımı

<xref:System.Net>Windows Mağazası <xref:System.Net.Http>uygulamaları <xref:System.Net.Http.Headers> veya masaüstü uygulamaları geliştirmek için , , ve ad alanlarındaki sınıflar kullanılabilir. Bir Windows Mağazası uygulamasında kullanıldığında, bu ad alanlarındaki sınıflar, Windows 8 tarafından kullanılan uygulama güvenliği modelinin bir parçası olan ağ yalıtımı tarafından etkilenir. Sistemin ağ erişimine izin vermesi için bir Windows Mağazası uygulaması için uygulama bildiriminde uygun ağ özellikleri etkinleştirilmelidir.  
  
## <a name="checklist-for-network-isolation"></a>Ağ Yalıtımı için Denetim Listesi  

Windows Mağazası uygulamanız için ağ yalıtımı yapılandırıldığından emin olmak için bu denetim listesini kullanın.  
  
1. Uygulamanın ihtiyaç duyduğu ağ erişim isteklerinin yönünü belirleyin. Bu, giden istemci tarafından başlatılan istekler veya gelen istenmeyen istekler olabilir veya bu ağ istek türlerinin her ikisinin de bir leşimi olabilir.  
  
2. Uygulamanın iletişim kuracağı ağ kaynaklarının türünü belirleyin. Bir uygulamanın Ev veya İş ağındaki güvenilir kaynaklarla iletişim kurması gerekebilir. Bir uygulamanın Internet'teki kaynaklarla iletişim kurması gerekebilir. Bir uygulamanın her iki ağ kaynağı türüne de erişmeleri gerekebilir.  
  
3. Uygulama bildiriminde gereken minimum ağ yalıtımı özelliklerini yapılandırın.  
  
4. Sorun giderme için sağlanan ağ yalıtım araçlarını kullanarak uygulamanızı test etmek için uygulamanızı dağıtın ve çalıştırın.  
  
Sorun giderme ağı yalıtımı için kullanılan ağ özelliklerinin ve yalıtım araçlarının nasıl yapılandırılabildiğini hakkında daha ayrıntılı bilgi için Windows 8.x Store geliştirici belgelerinde [ağ yalıtımı yeteneklerini nasıl yapılandırılabilirsiniz.](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10))
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir web hizmetine bağlanma](https://docs.microsoft.com/previous-versions/windows/apps/hh761504(v=win.10))
- [Ağ yalıtımı için yönergeler ve denetim listesi](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10))
- [Quickstart: HttpClient kullanarak bağlanma](https://docs.microsoft.com/previous-versions/windows/apps/hh781239(v=win.10))
- [Httpİste işleyicileri nasıl kullanılır?](https://docs.microsoft.com/previous-versions/windows/apps/hh781241(v=win.10))
- [HttpClient bağlantıları nasıl güvenli hale](https://docs.microsoft.com/previous-versions/windows/apps/hh781240(v=win.10))
- [httpClient Örnek](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
