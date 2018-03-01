---
title: ".NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma"
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
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b7d305adf1810832016cdafbb60fc025f17e0786
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>.NET Uzaktan İletişim Uygulamalarını WCF'ye Taşıma
**Bu konu, mevcut uygulamalarla geriye dönük uyumluluk için tutulmaktadır ve yeni geliştirme projeleri için önerilmez eski bir teknoloji özgüdür. Dağıtılmış uygulamalar şimdi geliştirilen kullanarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**  
  
 Yararlanmak için iki yolla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mevcut .NET uzaktan iletişim uygulamalarla: tümleştirme ve geçiş. Tümleştirme .net sahip olmanızı sağlar Remoting 2.0 ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] çalışan yan yana, olanak tanıyarak, aynı iş nesneleri iki teknolojiyi aynı anda var olan .net değiştirmek zorunda kalmadan ortaya Remoting 2.0 kodu. Tümleştirme gerektirir, çalıştırdığınızı [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 veya daha büyük. Yararlanmak isterseniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] özellikleri ve değil wire Remoting 2.0 sistemleriyle uyumluluk, tüm hizmetinize geçirebilirsiniz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. .NET uzaktan iletişim 2.0 geçişini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uzak nesnesinin arabirimi ve yapılandırma ayarlarına yapılan değişiklikler gerektirir. Bu konular her ikisi de ele alınmaktadır [gelen Windows Communication Foundation Remoting](http://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kavramsal Genel Bakış](../../../../docs/framework/wcf/conceptual-overview.md)
