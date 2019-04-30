---
title: <add> / <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 2a3ba6d41059a480fe610254c0407df16d149e3b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701469"
---
# <a name="add-of-serviceactivations"></a>\<Ekle >, \<serviceActivations >

Windows Communication Foundation (WCF) hizmet türlerinizi eşleştiren sanal hizmet aktivasyon ayarlarını tanımlamanıza olanak sağlayan bir yapılandırma öğesi. Bu WAS içinde barındırılan hizmetleri etkinleştirmeniz mümkün kılar / IIS .svc dosyası olmadan.

\<sistemi. ServiceModel > \
\<serviceHostingEnvironment >

## <a name="syntax"></a>Sözdizimi

```xml
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|Fabrika|Bir hizmet aktivasyon öğesini üreten üretici CLR tür adını belirten dize.|
|hizmet|(Tam nitelikli tür adı veya kısa Typename (App_Code klasörü içinde yerleştirilir olduğunda). hizmeti uygulayan ServiceType|
|relativeAddress|Geçerli bir IIS uygulama - örneğin "Service.svc" içinde göreli adresi. WCF 4. 0'göreli bu adresi bir bilinen dosya uzantıları (.svc .xamlx,...) içeren var. Fiziksel dosya için relativeUrl var olması|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Aktivasyon ayarlarını tanımlayan bir yapılandırma bölümü.|

## <a name="remarks"></a>Açıklamalar

Aşağıdaki örnekte, web.config dosyasında etkinleştirme ayarlarının nasıl yapılandırılacağı gösterilmektedir.

```xml
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```

Bu yapılandırmayı kullanarak .svc dosyası kullanmadan GreetingService etkinleştirebilirsiniz.

Unutmayın `<serviceHostingEnvironment>` uygulama düzeyinde yapılandırma. Yerleştirmek sahip olduğunuz `web.config` sanal uygulama kökü altındaki yapılandırmasını içeren. Ayrıca, `serviceHostingEnvironment` machineToApplication devralınabilir bölümüdür. Tek bir hizmette makine kökündeki kaydolursanız, uygulamadaki her hizmet bu hizmeti devralır.

Yapılandırma temelli etkinleştirme, etkinleştirme hem http hem de olmayan http protokolü üzerinden destekler. Yani .svc, .xoml veya .xamlx relativeAddress uzantılarında gerektiriyor. Sonra hizmeti uzantıyı etkinleştirmek üzere olanak sağlayacak bilinen buildProviders kendi uzantılarınızı eşleyebilirsiniz. Çakışma, bağlı `<serviceActivations>` bölüm .svc kayıtları geçersiz kılar.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
