---
title: Yönetilen Bir Uygulamada Barındırma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4e2afa9e868c1f561aed699a2bdf7d09c17898b3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="hosting-in-a-managed-application"></a>Yönetilen Bir Uygulamada Barındırma
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Hizmetler barındırılması birinde [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulama. Kendi kendine barındırma hizmetleri en esnek barındırma seçenektir; çünkü dağıtmak için en az altyapısı gerektirir. Yönetilen uygulamaların farklı barındırma seçenekleri Gelişmiş barındırma ve yönetim özellikleri sağlıyor mu ancak ayrıca en az sağlam barındırma seçeneği demektir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], Internet Information Services (IIS) ve Windows Hizmetleri gibi.  
  
 Kendini barındıran hizmet oluşturmak için oluşturun ve bir örneği açın <xref:System.ServiceModel.ServiceHost>, iletiler için dinleme bir hizmetini başlatır. Daha fazla bilgi için bkz: [nasıl yapılır: yönetilen bir uygulamada bir WCF Hizmeti barındırma](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).  
  
 Bir sözleşme tanımlama, sözleşmeyi uyguladıktan ve yönetilen bir uygulama içinde bir hizmet barındırmak nasıl tam bir örnek için bkz: [başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md) ve [kendini barındırma](../../../../docs/framework/wcf/samples/self-host.md).  
  
 Aşağıdaki bölümlerde barındırma bu seçeneği kullanın yaygın senaryolar açıklanmaktadır.  
  
## <a name="console-applications"></a>Konsol uygulamaları  
 Kendi kendine barındırma etkinleştirir olan yaygın senaryolar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içinde çalışan Hizmetleri konsol uygulamaları. Barındırma bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmeti bir konsol uygulaması içinde yararlıdır genellikle hizmeti geliştirme aşamasında. Bu onları kolay hata ayıklamak, uygulama içinde neler olduğunu çıkışı bulmak için izleme bilgilerini almak kolay ve yeni konumlara kopyalayarak hareket etmek kolay hale getirir.  
  
## <a name="rich-client-applications"></a>Zengin istemci uygulamaları  
 Kendi kendine barındırma sağlayan diğer yaygın senaryolar, Windows Presentation Foundation (WPF) veya Windows Forms (WinForms) tabanlı olanlar gibi zengin istemci uygulamaları verilmiştir. Barındırma bu seçenek ayrıca zengin istemci uygulamaları gibi kolaylaştırır [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] ve dış dünyayla iletişim kurmak için WinForms uygulamalar. Örneğin, kullanan eşler arası işbirliği istemci [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] kendi kullanıcı arabirimi ve ayrıca ana bilgisayarlar için bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bağlanmak ve bilgi paylaşmak diğer istemciler sağlayan hizmet.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Barındırma Hizmetleri](../../../../docs/framework/wcf/hosting-services.md)  
 [Başlangıç Öğreticisi](../../../../docs/framework/wcf/getting-started-tutorial.md)
