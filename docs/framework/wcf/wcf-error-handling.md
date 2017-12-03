---
title: "WCF Hata İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e4b1e0f-9598-449d-9d73-90bda62305b8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 26dfea83400b5d601fabc5cfb52bc71a4d5e4f6f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-error-handling"></a>WCF Hata İşleme
Bir WCF uygulaması tarafından karşılaşılan hataları üç gruplardan birine ait:  
  
1.  İletişim hataları  
  
2.  Proxy/kanal hataları  
  
3.  Uygulama hataları  
  
 Ağ kullanılamıyor, istemci yanlış bir adres kullanır ya da hizmet konağı gelen iletiler için dinleme yapmıyor iletişim hataları oluşur. Bu tür hataları istemciye döndürülen <xref:System.ServiceModel.CommunicationException> veya <xref:System.ServiceModel.CommunicationException>-türetilmiş sınıfları.  
  
 Proxy/kanal, kanal veya proxy kendisini içinde oluşan hataları hatalardır. Bu tür hataları şunlardır: bir proxy kullanır veya bu kanal girişimi kapatıldı, istemci ile hizmet arasında bir sözleşme uyumsuzluğu var. veya istemci kimlik bilgileri hizmeti tarafından reddedilir. Farklı türlerde bu kategorideki hataları vardır burada listelemek için çok fazla. Bu tür hataları istemciye döndürülen-olduğu (hiçbir dönüştürme özel durum nesnelerde gerçekleştirilir).  
  
 Uygulama hataları bir hizmet işlemi yürütme sırasında oluşur. Bu tür hataların istemci olarak gönderilen <xref:System.ServiceModel.FaultException> veya <xref:System.ServiceModel.FaultException%601>.  
  
 WCF'de işleme hatası, bir veya daha fazlasını tarafından gerçekleştirilir:  
  
-   Doğrudan oluşturulan özel durum işleme. Bu, yalnızca iletişimi ve proxy/kanal hataları için yapılır.  
  
-   Hataya sözleşmeleri kullanma  
  
-   Uygulama <xref:System.ServiceModel.Dispatcher.IErrorHandler> arabirimi  
  
-   İşleme <xref:System.ServiceModel.ServiceHost> olayları  
  
## <a name="fault-contracts"></a>Hataya sözleşmeleri  
 Hataya sözleşmeleri izin Platform hizmet işlemi sırasında oluşabilecek hataları tanımlamanızı bağımsız şekilde. Varsayılan olarak gelen bir hizmet işlemi içinde oluşturulan tüm özel durumları istemciye döndürülecek bir <xref:System.ServiceModel.FaultException> nesnesi. <xref:System.ServiceModel.FaultException> Nesne çok az bilgileri içerir. Bir arıza sözleşmesi tanımlayarak ve hata olarak döndüren istemciye gönderilen bilgiler denetleyebilirsiniz bir <xref:System.ServiceModel.FaultException%601>. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Belirtme ve sözleşme ve hizmetlerde hataları işleme](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
## <a name="ierrorhandler"></a>IErrorHandler  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler> Arabirimi WCF uygulamanızın hatalarının nasıl yanıt vereceğini üzerinde daha fazla denetim sağlar.  İstemciye döndürülen ve günlüğe kaydetme gibi işlenirken özel hata gerçekleştirmenize olanak sağlayan hata iletisi üzerinde tam denetim verir.  [!INCLUDE[crdefault](../../../includes/crabout-md.md)]<xref:System.ServiceModel.Dispatcher.IErrorHandler> ve [üzerinden hata işleme ve bildirme denetimini genişletme](../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)  
  
## <a name="servicehost-events"></a>ServiceHost olayları  
 <xref:System.ServiceModel.ServiceHost> Sınıfı konakları Hizmetleri ve hataları işlemek için gerekli olabilecek çeşitli olaylarını tanımlar. Örneğin:  
  
1.  <!--zz <xref:System.ServiceModel.ServiceHost.Faulted>-->  `System.ServiceModel.ServiceHost.Faulted`
  
2. <!--zz  <xref:System.ServiceModel.ServiceHost.UnknownMessageReceived>  --> `System.ServiceModel.ServiceHost.UnknownMessageReceived`
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<xref:System.ServiceModel.ServiceHost>
