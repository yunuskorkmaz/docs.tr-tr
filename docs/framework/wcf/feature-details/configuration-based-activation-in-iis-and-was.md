---
title: "IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0938b98a3f079d03653df55f10c26a4a62db5bf3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="configuration-based-activation-in-iis-and-was"></a>IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme
Normalde barındırdığında bir [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] hizmeti Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) altında bir .svc dosyası sağlamanız gerekir. .Svc dosya hizmeti ve isteğe bağlı özel hizmet ana bilgisayar üreteci adını içerir. Bu ek dosya yönetilebilirlik yükünü ekler. Yapılandırma temelli etkinleştirme özelliği .svc dosyası ve bu nedenle ilişkili sahip gereksinimini ortadan kaldırır yükü.  
  
## <a name="configuration-based-activation"></a>Yapılandırma Temelli Etkinleştirme  
 Yapılandırma temelli etkinleştirme .svc dosyasında yerleştirilmesi için kullanılır ve Web.config dosyasına yerleştirir meta veriler alır. İçinde <`serviceHostingEnvironment`> öğesi var. bir <`serviceActivations`> öğesi. İçinde <`serviceActivations`> öğesi bir veya daha fazla <`add`> öğeleri, her barındırılan hizmeti için bir. <`add`> Öğesi, hizmet ve hizmet türü veya hizmet ana bilgisayar üreteci için göreli adresi ayarlamanıza olanak tanıyan öznitelikleri içerir. Aşağıdaki kod yapılandırma örneği, bu bölümde nasıl kullanıldığını gösterir.  
  
> [!NOTE]
>  Her <`add`> öğesi, bir hizmet ya da bir Fabrika öznitelik belirtmelisiniz. Hem hizmet hem de Fabrika öznitelikleri belirtme izin verilir.  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 Bu Web.config dosyasında, hizmet kaynak kodu uygulama veya uygulamanın Bin dizinindeki derlenmiş bir derlemeyi App_Code dizinindeki yerleştirebilirsiniz.  
  
> [!NOTE]
>  -   Yapılandırma temelli etkinleştirme kullanırken, satır içi kod .svc dosyalarında desteklenmiyor.  
> -   `relativeAddress` Özniteliği ayarlanmalıdır göreli adresine gibi "\<alt dizini > / service.svc" veya "~ /\<alt directory/service.svc".  
> -   WCF ile ilgili bilinen bir uzantı göreli bir adres kaydederseniz yapılandırma özel durum oluşur.  
> -   Belirtilen göreli adresi sanal uygulama göreli köküdür.  
> -   Hiyerarşik yapılandırma modeli nedeniyle, makine ve site düzeyinde kayıtlı göreli adresleri sanal uygulamalar tarafından devralınır.  
> -   Kayıtlar yapılandırma dosyasında bir .svc, .xamlx, .xoml veya başka bir dosya ayarlarında daha önceliklidir.  
> -   Tüm ' \' (ters eğik çizgi) IIS gönderilen bir URI / olan otomatik olarak dönüştürülür bir '/' (eğik çizgi). Göreli bir adresi eklenirse içeren bir ' \' ve IIS göreli adresini kullanan bir URI göndermek, ters eğik çizgiyi eğik için dönüştürülür ve IIS, göreli adresine eşleşemez. IIS eşleşme olduğunu gösteren izleme bilgilerini gönderir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [Barındırma hizmetleri](../../../../docs/framework/wcf/hosting-services.md)  
 [İş akışı hizmetlerini barındırma genel bakış](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [\<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [Windows Server App Fabric barındırma özellikleri](http://go.microsoft.com/fwlink/?LinkId=201276)
