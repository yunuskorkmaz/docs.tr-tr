---
title: "Nasıl yapılır: Net.TCP Bağlantı Noktası Payalaşım Hizmetini Etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1a64c72a8f69abc220a311c2a204074ea83d0f58
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>Nasıl yapılır: Net.TCP Bağlantı Noktası Payalaşım Hizmetini Etkinleştirme
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]TCP bağlantı noktaları birden çok işlem paylaşımı kolaylaştırmak için Net.TCP bağlantı noktası Paylaşımı hizmeti adlı bir Windows hizmeti kullanır. Bu hizmet parçası olarak yüklenen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ancak hizmet güvenlik önlemi olarak varsayılan olarak etkin değildir ve öncesinde el ile etkinleştirilmesi gerekir böylece ilk olarak kullanın. Bu konuda Net TCP bağlantı noktası Microsoft Yönetim Konsolu (MMC) ek bileşenini kullanarak Paylaşımı hizmetinin nasıl yapılandırılacağı açıklanmaktadır.  
  
 Net.TCP bağlantı noktası Paylaşımı hizmeti etkinleştirmek ve el ile başlatmak sonra bkz [nasıl yapılır: bir WCF Hizmeti bağlantı noktası paylaşımı kullanmak üzere yapılandırmak](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) bu hizmeti kullanmak için hizmetinin nasıl yapılandırılacağı hakkında bilgi için.  
  
 Net.tcp:// bağlantı noktası Paylaşımı kullanan bir örnek için bkz: [Net.TCP bağlantı noktası paylaşımı örneği](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>Net.TCP bağlantı noktası paylaşımı MMC kullanarak hizmeti etkinleştirmek için  
  
1.  Başlat menüsünden ya da bir komut istemi penceresini açarak ve yazarak Hizmetler Yönetimi konsolunu açın `services.msc` veya Çalıştır açarak ve yazarak `services.msc` açık kutusuna.  
  
2.  İçinde **adı** sütun hizmetleri listesinin sağ **Net.Tcp Bağlantı Noktası Paylaşımı hizmeti**ve seçin **özellikleri** menüsünde.  
  
3.  El ile başlatma hizmeti etkinleştirmek için **özellikleri** penceresi seçin **genel** sekmesi hem de **başlangıç türü** select el ile kutusuna ve ardından tıklatın**Uygulamak**.  
  
4.  Hizmet durumu alanında hizmetini başlatmak için tıklatın **Başlat** düğmesi. Hizmet durumu "Başlatıldı" şimdi görüntülemelidir.  
  
5.  Hizmetleri listesine geri dönmek için tıklatın **Tamam**ve MMC konsolunu çıkın.  
  
## <a name="example"></a>Örnek  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Net.TCP bağlantı noktası paylaşımı](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 [Net.TCP bağlantı noktası hizmetini yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
