---
title: Windows Mağazası Uygulamaları için Ağ Yalıtımı
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: 34b8865781079f45a68d3dd1aab7fbd66c703d50
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447426"
---
# <a name="network-isolation-for-windows-store-apps"></a>Windows Mağazası Uygulamaları için Ağ Yalıtımı
<xref:System.Net>, <xref:System.Net.Http>ve <xref:System.Net.Http.Headers> ad alanlarında bulunan sınıflar Windows Mağazası uygulamaları veya masaüstü uygulamaları geliştirmek için kullanılabilir. Bir Windows Mağazası uygulamasında kullanıldığında, bu ad alanlarındaki sınıflar, [!INCLUDE[win8](../../../includes/win8-md.md)]tarafından kullanılan uygulama güvenlik modelinin parçası olan ağ yalıtımıyla etkilenir. Sistemin ağ erişimine izin vermek için bir Windows Mağazası uygulamasının uygulama bildiriminde uygun ağ özellikleri etkinleştirilmelidir.  
  
## <a name="checklist-for-network-isolation"></a>Ağ yalıtımı için denetim listesi  
 Windows Mağazası uygulamanız için ağ yalıtımının yapılandırıldığından emin olmak için bu denetim listesini kullanın.  
  
1. Uygulama için gereken ağ erişim isteklerinin yönünü belirleme. Bu, istemci tarafından başlatılan istekler veya gelen istenmeyen istekler olabilir ya da bu ağ isteği türlerinin her ikisinin bir birleşimi olabilir.  
  
2. Uygulamanın iletişim kuracağı ağ kaynaklarının türünü saptayın. Bir uygulamanın ev veya Iş ağı üzerinde güvenilir kaynaklarla iletişim kurması gerekebilir. Bir uygulamanın Internet 'teki kaynaklarla iletişim kurması gerekebilir. Bir uygulamanın her iki tür ağ kaynağına erişmesi gerekebilir.  
  
3. Uygulama bildiriminde gereken en düşük ağ yalıtımı özelliklerini yapılandırın.  
  
4. Sorun giderme için sunulan ağ yalıtımı araçlarını kullanarak test etmek için uygulamanızı dağıtın ve çalıştırın.  
  
 Ağ yalıtımı sorunlarını gidermek için kullanılan ağ yeteneklerini ve yalıtım araçlarını yapılandırma hakkında daha ayrıntılı bilgi için, bkz. Windows 8. x mağaza geliştirici belgelerindeki [ağ yalıtımı yeteneklerini yapılandırma](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10)) .
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir Web hizmetine bağlanma](https://docs.microsoft.com/previous-versions/windows/apps/hh761504(v=win.10))
- [Ağ yalıtımı için yönergeler ve denetim listesi](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10))
- [Hızlı başlangıç: HttpClient kullanarak bağlanma](https://docs.microsoft.com/previous-versions/windows/apps/hh781239(v=win.10))
- [HttpClient işleyicilerini kullanma](https://docs.microsoft.com/previous-versions/windows/apps/hh781241(v=win.10))
- [HttpClient bağlantılarını güvenli hale getirme](https://docs.microsoft.com/previous-versions/windows/apps/hh781240(v=win.10))
- [HttpClient örneği](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
