---
title: WCF Hata İşleme
ms.date: 03/30/2017
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
ms.openlocfilehash: 4fad317d8cb696b29d9c8e4e4d8209abc28410f8
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46473453"
---
# <a name="wcf-error-handling"></a>WCF Hata İşleme
WCF uygulaması tarafından karşılaşılan hataları üç gruplardan birine ait:  
  
1.  İletişim hataları  
  
2.  Proxy/kanal hataları  
  
3.  Uygulama hataları  
  
 İletişim hataları ağ kullanılamıyor, istemci yanlış bir adresi kullanır veya hizmet ana bilgisayarı gelen iletiler için dinleme yapmıyor ortaya çıkar. Bu tür hatalar istemciye döndürülür <xref:System.ServiceModel.CommunicationException> veya <xref:System.ServiceModel.CommunicationException>-türetilmiş sınıflar.  
  
 Proxy/kanal, kanal veya proxy kendisi içinde oluşan hataları hatalardır. Bu tür hatalar vardır: bir ara sunucu kullanmak veya, kanal çalışılıyor kapatıldı, hizmet ve istemci arasında bir anlaşma uyumsuzluğu var. veya istemci kimlik bilgileri hizmet tarafından reddedilir. Farklı türlerde bu kategoriye giren hataları vardır. burada listelemek için çok fazla. Bu tür hatalar istemciye döndürülür-olduğu (hiçbir dönüştürme yapılmadı, özel durum nesnelerinde gerçekleştirilir).  
  
 Bir hizmet işlemi yürütülürken uygulama hataları oluşur. Bu tür hatalar istemciye gönderilen <xref:System.ServiceModel.FaultException> veya <xref:System.ServiceModel.FaultException%601>.  
  
 WCF'de işleme hata, bir veya daha fazlasını tarafından gerçekleştirilir:  
  
-   Doğrudan özel durum işleme. Bu yalnızca iletişimi ve proxy/kanal hataları için gerçekleştirilir.  
  
-   Hata sözleşmeleri kullanma  
  
-   Uygulama <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi  
  
-   İşleme <xref:System.ServiceModel.ServiceHost> olayları  
  
## <a name="fault-contracts"></a>Hata sözleşmeleri  
 Hata sözleşmelerine izin vermek, Platform hizmeti işlemi sırasında oluşabilecek hataları tanımlamak bağımsız bir şekilde. Varsayılan olarak, gelen bir hizmet işlemi içinde oluşturulan tüm özel durumlar istemciye döndürülecek bir <xref:System.ServiceModel.FaultException> nesne. <xref:System.ServiceModel.FaultException> Nesne çok az bilgi içerir. Hatalı sözleşme tanımlayarak ve hata olarak döndüren istemciye gönderilen bilgiler denetleyebilirsiniz bir <xref:System.ServiceModel.FaultException%601>. Daha fazla bilgi için [belirtme ve işleme hataları sözleşme ve hizmetlerde](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="ierrorhandler"></a>Ierrorhandler  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler> Arabirim WCF uygulamanızı hatalara nasıl yanıt vereceğini üzerinde daha fazla denetim sağlar.  Özel Hata günlük kaydı gibi işlem yapmanıza olanak tanır ve istemciye döndürülen hata iletisi üzerinde tam denetim verir.  Hakkında daha fazla bilgi için <xref:System.ServiceModel.Dispatcher.IErrorHandler> ve [genişletme denetiminin üzerine hata işleme ve Raporlama](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)  
  
## <a name="servicehost-events"></a>ServiceHost olayları  
 <xref:System.ServiceModel.ServiceHost> Sınıfı konakları Hizmetleri ve hataları işleme için gerekli olabilecek çeşitli olayları tanımlar. Örneğin:  
  
1. <xref:System.ServiceModel.Channels.CommunicationObject.Faulted>
  
2. <xref:System.ServiceModel.ServiceHostBase.UnknownMessageReceived>
  
 Daha fazla bilgi için bkz. <xref:System.ServiceModel.ServiceHost>
