---
title: 'Nasıl yapılır: Net.TCP Bağlantı Noktası Payalaşım Hizmetini Etkinleştirme'
description: Varsayılan olarak devre dışı bırakılan net. TCP ' yi etkinleştirmek için, MMC kullanarak net TCP bağlantı noktası paylaşım hizmetini nasıl yapılandıracağınızı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 0292559e3befde7f0b00b36aa10a2d9615daf049
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247006"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>Nasıl yapılır: Net.TCP Bağlantı Noktası Payalaşım Hizmetini Etkinleştirme
Windows Communication Foundation (WCF), TCP bağlantı noktalarının birden çok işlem arasında paylaşılmasını kolaylaştırmak için net. TCP bağlantı noktası paylaşma hizmeti adlı bir Windows hizmeti kullanır. Bu hizmet, WCF 'nin bir parçası olarak yüklenir, ancak hizmet varsayılan olarak bir güvenlik önlemi olarak etkinleştirilmemiştir ve bu nedenle, ilk kullanılmadan önce el ile etkinleştirilmesi gerekir. Bu konuda, Microsoft Yönetim Konsolu (MMC) ek bileşenini kullanarak net TCP bağlantı noktası paylaşım hizmeti 'nin nasıl yapılandırılacağı açıklanmaktadır.  
  
 Net. TCP bağlantı noktası paylaşım hizmetini etkinleştirip el ile başlattıktan sonra, bu hizmeti kullanmak için hizmetinizi yapılandırma hakkında bilgi için bkz. [nasıl yapılır: WCF hizmetini bağlantı noktası Paylaşımı kullanmak üzere yapılandırma](how-to-configure-a-wcf-service-to-use-port-sharing.md) .  
  
 Net. TCP://bağlantı noktası Paylaşımı kullanan bir örnek için bkz. [net. TCP bağlantı noktası paylaşma örneği](../samples/net-tcp-port-sharing-sample.md).  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>MMC kullanarak net. TCP bağlantı noktası paylaşma hizmetini etkinleştirmek için  
  
1. Başlat menüsünde, bir komut Istemi penceresi açıp `services.msc` ya da Çalıştır ' ı açıp Aç kutusuna yazarak hizmetler yönetimi konsolunu açın `services.msc` .  
  
2. Hizmetler listesinin **ad** sütununda, **net. TCP bağlantı noktası paylaşım hizmeti**' ne sağ tıklayın ve menüden **Özellikler** ' i seçin.  
  
3. Hizmetin el ile başlamasını etkinleştirmek için, **Özellikler** penceresinde **genel** sekmesini seçin ve **Başlangıç türü** kutusunda el Ile ' yi seçin ve ardından **Uygula**' ya tıklayın.  
  
4. Hizmeti başlatmak için, hizmet durumu alanında **Başlat** düğmesine tıklayın. Hizmet durumu şimdi "başlatıldı" olarak görüntülenmelidir.  
  
5. Hizmetler listesine geri dönmek için **Tamam**' a tıklayın ve MMC konsolundan çıkın.  
  
## <a name="example"></a>Örnek  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Net.TCP Bağlantı Noktası Paylaşımı](net-tcp-port-sharing.md)
- [Net.TCP Bağlantı Noktası Hizmetini Yapılandırma](configuring-the-net-tcp-port-sharing-service.md)
