---
title: Yönetilen Bir Uygulamada Barındırma
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: 0210f608be8ef7ff8b2af4b0cc36b308cd3ddbe8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617246"
---
# <a name="hosting-in-a-managed-application"></a>Yönetilen Bir Uygulamada Barındırma
Windows Communication Foundation (WCF) Hizmetleri, tüm barındırılabilir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulama. Dağıtmak için en az bir altyapı gerektirdiğinden kendi kendine barındırma hizmetleri en esnek barındırma seçenektir. Yönetilen uygulamalar, Gelişmiş barındırma ve yönetim özellikleri, WCF, Internet Information Services (IIS) ve Windows Hizmetleri gibi diğer barındırma seçenekleri sağlamaz ancak ayrıca en az sağlam barındırma seçeneği olmasıdır.  
  
 Şirket içinde barındırılan bir hizmet oluşturmak için oluşturma ve bir örneğini açın <xref:System.ServiceModel.ServiceHost>, iletileri dinleyen bir hizmeti başlatır. Daha fazla bilgi için [nasıl yapılır: Yönetilen bir uygulamada bir WCF Hizmeti barındırma](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Yönetilen bir uygulama içinde bir hizmet ana sözleşme tanımlamasına ve sözleşmesini uygulama konusunda tam bir örnek için bkz. [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md) ve [barındırma](../../../../docs/framework/wcf/samples/self-host.md).  
  
 Aşağıdaki bölümlerde bu barındırma seçeneği kullanmak yaygın senaryolar açıklanmaktadır.  
  
## <a name="console-applications"></a>Konsol uygulamaları  
 Kendi kendine barındırma sağlayan ortak senaryolar konsol uygulamaları içinde çalışan WCF hizmetleri verilmiştir. Bir konsol uygulaması içinde bir WCF Hizmeti barındırma hizmeti geliştirme aşamasında genellikle yararlı olur. Bu bunları hata ayıklamak kolay, uygulama içinde neler olup bittiğine bulmak için izleme bilgilerini almak kolay ve bunları yeni konumlara kopyalayarak yerleri daha kolay hale getirir.  
  
## <a name="rich-client-applications"></a>Zengin istemci uygulamaları  
 Kendi kendine barındırma sağlayan diğer yaygın senaryoları Windows Presentation Foundation (WPF) veya Windows Forms (WinForms) göre gibi zengin istemci uygulamalarının ' dir. Bu barındırma seçeneği ayrıca, zengin istemci uygulamaları gibi kolaylaştırır [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] ve dış dünya ile iletişim kurmak için WinForms uygulamaları. Örneğin, kullanan bir eşler arası işbirliği istemci [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] kullanıcı arabirimi için ve ayrıca diğer istemcilerin kendisine bağlanıp bilgi paylaşmak bir WCF hizmetini barındırır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Barındırma Hizmetleri](../../../../docs/framework/wcf/hosting-services.md)
- [Başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md)
