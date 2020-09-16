---
title: Windows Mağazası Uygulamaları için Ağ Yalıtımı
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: 0f9288b53b969838cac64c24d3c9861a0f841aca
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558465"
---
# <a name="network-isolation-for-windows-store-apps"></a>Windows Mağazası Uygulamaları için Ağ Yalıtımı

<xref:System.Net>, <xref:System.Net.Http> Ve ad alanlarındaki sınıflar, <xref:System.Net.Http.Headers> Windows Mağazası uygulamaları veya masaüstü uygulamaları geliştirmek için kullanılabilir. Bir Windows Mağazası uygulamasında kullanıldığında, bu ad alanlarındaki sınıflar, Windows 8 tarafından kullanılan uygulama güvenlik modelinin parçası olan ağ yalıtımıyla etkilenir. Sistemin ağ erişimine izin vermek için bir Windows Mağazası uygulamasının uygulama bildiriminde uygun ağ özellikleri etkinleştirilmelidir.  
  
## <a name="checklist-for-network-isolation"></a>Ağ yalıtımı için denetim listesi  

Windows Mağazası uygulamanız için ağ yalıtımının yapılandırıldığından emin olmak için bu denetim listesini kullanın.  
  
1. Uygulama için gereken ağ erişim isteklerinin yönünü belirleme. Bu, istemci tarafından başlatılan istekler veya gelen istenmeyen istekler olabilir ya da bu ağ isteği türlerinin her ikisinin bir birleşimi olabilir.  
  
2. Uygulamanın iletişim kuracağı ağ kaynaklarının türünü saptayın. Bir uygulamanın ev veya Iş ağı üzerinde güvenilir kaynaklarla iletişim kurması gerekebilir. Bir uygulamanın Internet 'teki kaynaklarla iletişim kurması gerekebilir. Bir uygulamanın her iki tür ağ kaynağına erişmesi gerekebilir.  
  
3. Uygulama bildiriminde gereken en düşük ağ yalıtımı özelliklerini yapılandırın.  
  
4. Sorun giderme için sunulan ağ yalıtımı araçlarını kullanarak test etmek için uygulamanızı dağıtın ve çalıştırın.  
  
Ağ yalıtımı sorunlarını gidermek için kullanılan ağ yeteneklerini ve yalıtım araçlarını yapılandırma hakkında daha ayrıntılı bilgi için, bkz. Windows 8. x mağaza geliştirici belgelerindeki [ağ yalıtımı yeteneklerini yapılandırma](/previous-versions/windows/apps/hh770532(v=win.10)) .
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir Web hizmetine bağlanma](/previous-versions/windows/apps/hh761504(v=win.10))
- [Ağ yalıtımı için yönergeler ve denetim listesi](/previous-versions/windows/apps/hh770532(v=win.10))
- [Hızlı başlangıç: HttpClient kullanarak bağlanma](/previous-versions/windows/apps/hh781239(v=win.10))
- [HttpClient işleyicilerini kullanma](/previous-versions/windows/apps/hh781241(v=win.10))
- [HttpClient bağlantılarını güvenli hale getirme](/previous-versions/windows/apps/hh781240(v=win.10))
- [HttpClient örneği](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
