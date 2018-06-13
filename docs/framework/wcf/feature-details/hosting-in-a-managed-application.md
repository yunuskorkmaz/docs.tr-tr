---
title: Yönetilen Bir Uygulamada Barındırma
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: f374c199fb1982ab8854e41c0c8308f46451d9d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489748"
---
# <a name="hosting-in-a-managed-application"></a>Yönetilen Bir Uygulamada Barındırma
Windows Communication Foundation (WCF) hizmetlerini barındırılması birinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulama. Kendi kendine barındırma hizmetleri en esnek barındırma seçenektir; çünkü dağıtmak için en az altyapısı gerektirir. Yönetilen uygulamalar Gelişmiş barındırma ve WCF, Internet Information Services (IIS) ve Windows Hizmetleri gibi diğer barındırma seçenekleri yönetim özellikleri sağlıyor mu ancak ayrıca en az sağlam barındırma seçeneği demektir.  
  
 Kendini barındıran hizmet oluşturmak için oluşturun ve bir örneği açın <xref:System.ServiceModel.ServiceHost>, iletiler için dinleme bir hizmetini başlatır. Daha fazla bilgi için bkz: [nasıl yapılır: yönetilen bir uygulamada bir WCF Hizmeti barındırma](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Bir sözleşme tanımlama, sözleşmeyi uyguladıktan ve yönetilen bir uygulama içinde bir hizmet barındırmak nasıl tam bir örnek için bkz: [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md) ve [kendini barındırma](../../../../docs/framework/wcf/samples/self-host.md).  
  
 Aşağıdaki bölümlerde barındırma bu seçeneği kullanın yaygın senaryolar açıklanmaktadır.  
  
## <a name="console-applications"></a>Konsol uygulamaları  
 Kendi kendine barındırma sağlayan ortak senaryolar WCF Hizmetleri konsol uygulamaları çalıştıran verilmiştir. Bir konsol uygulaması içindeki bir WCF Hizmeti barındırma hizmeti geliştirme aşamasında genellikle yararlıdır. Bu onları kolay hata ayıklamak, uygulama içinde neler olduğunu çıkışı bulmak için izleme bilgilerini almak kolay ve yeni konumlara kopyalayarak hareket etmek kolay hale getirir.  
  
## <a name="rich-client-applications"></a>Zengin istemci uygulamaları  
 Kendi kendine barındırma sağlayan diğer yaygın senaryolar, Windows Presentation Foundation (WPF) veya Windows Forms (WinForms) tabanlı olanlar gibi zengin istemci uygulamaları verilmiştir. Barındırma bu seçenek ayrıca zengin istemci uygulamaları gibi kolaylaştırır [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] ve dış dünyayla iletişim kurmak için WinForms uygulamalar. Örneğin, kullanan eşler arası işbirliği istemci [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] kendi kullanıcı arabirimi için ve ayrıca bağlanmak ve bilgi paylaşmak diğer istemcilerin bir WCF hizmetini barındırır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Hizmetleri](../../../../docs/framework/wcf/hosting-services.md)  
 [Başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md)
