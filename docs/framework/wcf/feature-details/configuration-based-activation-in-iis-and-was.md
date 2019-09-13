---
title: IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: 5b06f474d26b80f955b1508f01da83448a8708a3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928777"
---
# <a name="configuration-based-activation-in-iis-and-was"></a>IIS ve WAS'ta Yapılandırma Temelli Etkinleştirme

Normal olarak, Internet Information Services (IIS) veya Windows Işlem etkinleştirme hizmeti (WAS) altında bir Windows Communication Foundation (WCF) hizmeti barındırdığında bir. svc dosyası sağlamanız gerekir. . Svc dosyası, hizmetin adını ve isteğe bağlı bir özel hizmet ana bilgisayar fabrikası içerir. Bu ek dosya yönetilebilirlik ek yükü ekler. Yapılandırma tabanlı etkinleştirme özelliği, gereksinimi bir. svc dosyasına ve bu nedenle ilişkili ek yüke karşı kaldırır.

## <a name="configuration-based-activation"></a>Yapılandırma Temelli Etkinleştirme

Yapılandırma tabanlı etkinleştirme,. svc dosyasına yerleştirilmesi için kullanılan meta verileri alır ve Web. config dosyasına koyar. <`serviceHostingEnvironment`> Öğesi içinde <`serviceActivations`bir > öğesi vardır. <`serviceActivations`> Öğesi içinde, bir veya daha fazla <`add`> öğesi, her barındırılan hizmet için bir öğedir. <`add`> Öğesi, hizmet ve hizmet türü ya da hizmet ana bilgisayar fabrikası için göreli adresi ayarlamanıza olanak sağlayan öznitelikleri içerir. Aşağıdaki yapılandırma örnek kodu, bu bölümün nasıl kullanıldığını gösterir.

> [!NOTE]
> Her <`add`> öğesi bir hizmet veya bir fabrika özniteliği belirtmelidir. Hem Service hem de Factory özniteliklerinin belirtilmesine izin verilir.

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>
  </serviceActivations>
</serviceHostingEnvironment>
```

 Web. config dosyasında bu, hizmet kaynak kodunu uygulamanın App_Code dizinine ya da uygulamanın bin dizinine bir karmaşıklu derlemeyi yerleştirebilirsiniz.

> [!NOTE]
>
> - Yapılandırma tabanlı etkinleştirme kullanılırken,. svc dosyalarında satır içi kod desteklenmez.
> - Öznitelik `relativeAddress` , "\<alt dizin >/Service.exe" veya "~/\<Sub-Directory/Service. svc" gibi göreli bir adrese ayarlanmalıdır.
> - WCF ile ilişkili bilinen bir uzantısı olmayan göreli bir adresi kaydettiğinizde bir yapılandırma özel durumu oluşturulur.
> - Belirtilen göreli adres, sanal uygulamanın köküne göredir.
> - Yapılandırma hiyerarşik modeli nedeniyle, makine ve site düzeyindeki kayıtlı göreli adresler sanal uygulamalar tarafından devralınır.
> - Bir yapılandırma dosyasındaki kayıtlar, bir. svc,. xamlx,. xoml veya başka bir dosyanın ayarlarından önceliklidir.
> - IIS/WAS 'a gönderilen URI içindeki herhangi bir ' \ ' (ters eğik çizgi), otomatik olarak bir '/' (eğik çizgi) olarak dönüştürülür. ' \ ' İçeren bir göreli adres eklenirse ve IIS 'yi göreli adresi kullanan bir URI gönderirseniz, ters eğik çizgi eğik çizgiye dönüştürülür ve IIS onunla ilgili adresle eşleşemez. IIS, hiçbir eşleşme bulunamadığını belirten izleme bilgilerini gönderir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>
- [Barındırma Hizmetleri](../../../../docs/framework/wcf/hosting-services.md)
- [İş Akışı Hizmetlerini Barındırmaya Genel Bakış](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)
- [\<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)
- [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)
