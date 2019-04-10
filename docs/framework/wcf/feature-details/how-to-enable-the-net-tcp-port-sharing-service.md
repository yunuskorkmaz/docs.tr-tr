---
title: 'Nasıl yapılır: Net.TCP Bağlantı Noktası Payalaşım Hizmetini Etkinleştirme'
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 20db0ef427a5e791bd6b8dcef90bf7911ae0d4a9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343486"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>Nasıl yapılır: Net.TCP Bağlantı Noktası Payalaşım Hizmetini Etkinleştirme
Windows Communication Foundation (WCF) Net.TCP bağlantı noktası paylaşma hizmeti adlı bir Windows hizmeti TCP bağlantı noktaları arasında birden çok işlem paylaşımını kolaylaştırmak için kullanır. Bu hizmet WCF'nin bir parçası yüklenir, ancak hizmet bir güvenlik önlemi olarak varsayılan olarak etkin değildir ve bu nedenle el ile ilk kullanımda önce etkinleştirilmesi gerekir. Bu konuda, Net TCP bağlantı noktası Microsoft Yönetim Konsolu (MMC) ek bileşenini kullanarak paylaşım hizmetinin nasıl yapılandırılacağı açıklanmaktadır.  
  
 Net.TCP bağlantı noktası paylaşım hizmetini etkinleştirme ve el ile başlatın, sonra bakın [nasıl yapılır: Bağlantı noktası paylaşımı kullanmak üzere bir WCF hizmetini yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md) bu hizmeti kullanmak için hizmetinizi yapılandırma hakkında daha fazla bilgi için.  
  
 Bağlantı noktası net.tcp:// Paylaşımı kullanan bir örnek için bkz. [Net.TCP bağlantı noktası paylaşımı örneği](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md).  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>Net.TCP bağlantı noktası paylaşımı kullanarak MMC hizmetini etkinleştirmek için  
  
1. Başlat Menüsü'nden ya da bir komut istemi penceresi açıp ve yazarak Hizmetler Yönetimi konsolunu açın `services.msc` veya Çalıştır'ı açıp yazarak `services.msc` Aç kutusuna.  
  
2. İçinde **adı** hizmetlerin listesi sütuna sağ tıklayın **Net.Tcp Bağlantı noktası paylaşma hizmeti**seçip **özellikleri** menüsünde.  
  
3. Hizmeti el ile başlatma etkinleştirmek için **özellikleri** penceresi seçin **genel** sekmesinde ve **başlangıç türü** select el ile kutusuna ve ardından tıklayın**Uygulamak**.  
  
4. Hizmet hizmet durumu alanında başlatmak için tıklatın **Başlat** düğmesi. Hizmet durumu, artık "Başlarken" görüntülemelidir.  
  
5. Hizmetler listesine dönmek için **Tamam**ve MMC konsolunu çıkın.  
  
## <a name="example"></a>Örnek  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Net.TCP Bağlantı Noktası Paylaşımı](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Net.TCP Bağlantı Noktası Hizmetini Yapılandırma](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
