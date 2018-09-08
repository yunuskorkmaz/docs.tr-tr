---
title: IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: d15202a7d34f3246cd7679687b6a510252fe3541
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44210214"
---
# <a name="configuration-based-activation-in-iis-and-was"></a>IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme
Normalde Internet Information Services (IIS) veya Windows İşlem Etkinleştirme Hizmeti (WAS) altında bir Windows Communication Foundation (WCF) hizmeti barındırırken .svc dosyası sağlamanız gerekir. .Svc dosyası, hizmet ve bir isteğe bağlı bir özel hizmet barındırma ortamı fabrikası adını içerir. Bu ek dosya yönetilebilirlik yükü ekler. Yapılandırma temelli etkinleştirme özelliği .svc dosya ve bu nedenle ilişkili gereksinimini ortadan kaldırır yükü.  
  
## <a name="configuration-based-activation"></a>Yapılandırma Temelli Etkinleştirme  
 Yapılandırma temelli etkinleştirme .svc dosyasında yerleştirilmesi için kullanılır ve Web.config dosyasına yerleştirir meta verileri alır. İçinde <`serviceHostingEnvironment`> öğesi yok bir <`serviceActivations`> öğesi. İçinde <`serviceActivations`> öğesi bir veya daha fazla <`add`> öğeleri, her bir barındırılan hizmet için bir tane. <`add`> Öğesi, hizmet ve hizmet türü veya bir hizmet barındırma ortamı fabrikası için hizmetin göreli adresini ayarlamanıza olanak tanıyan öznitelikleri içeriyor. Aşağıdaki yapılandırma örnek kod, bu bölümde nasıl kullanıldığını gösterir.  
  
> [!NOTE]
>  Her <`add`> öğesi bir hizmeti ya da bir Fabrika özniteliğini belirtmeniz gerekir. Hem hizmet hem de Fabrika öznitelikleri belirterek izin verilir.  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 Bu Web.config dosyasında, hizmet kaynak kodu uygulama veya uygulamanın Bin dizinindeki derlenmiş bir bütünleştirilmiş kod App_Code dizinindeki yerleştirebilirsiniz.  
  
> [!NOTE]
>  -   Yapılandırma temelli etkinleştirme kullanırken, satır içi kod .svc dosyalarında desteklenmiyor.  
> -   `relativeAddress` Özniteliği ayarlanmalıdır göreli bir adrese gibi "\<alt dizini > / service.svc" veya "~ /\<alt-directory/service.svc".  
> -   WCF ile ilgili bilinen bir uzantı yok. bir göreli adres kaydolarak bir yapılandırma özel durum oluşturulur.  
> -   Belirtilen göreli sanal uygulama köküne göreli adresidir.  
> -   Hiyerarşik yapılandırma modeli nedeniyle, makine ve site düzeyinde kayıtlı göreli adresleri sanal uygulamalar tarafından devralınır.  
> -   Bir yapılandırma dosyası kayıtları bir .svc, .xamlx, .xoml veya diğer dosya ayarlarında daha önceliklidir.  
> -   Tüm ' \' (ters eğik çizgi) için IIS gönderilen bir Uri / WAS'da otomatik olarak dönüştürülür bir '/' (eğik çizgi). Göreli adres eklenirse içeren bir ' \' ve IIS göreli adresini kullanan bir URI göndermek, ters eğik çizgiyi eğik çizgi için dönüştürülür ve IIS, göreli adresine eşleşemez. IIS eşleşme olduğunu gösterir izleme bilgilerini gönderir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [Barındırma Hizmetleri](../../../../docs/framework/wcf/hosting-services.md)  
 [İş Akışı Hizmetlerini Barındırmaya Genel Bakış](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [\<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)
