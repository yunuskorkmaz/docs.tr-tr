---
title: <add> / <serviceActivations>
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 929773fcb6b6a3ee5c75aa970147277d9dbe7b45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920023"
---
# <a name="add-of-serviceactivations"></a>\<\<serviceetkinleştirmeleri > ekleyin >

Windows Communication Foundation (WCF) hizmet türlerine eşlenen sanal hizmet etkinleştirme ayarlarını tanımlamanızı sağlayan bir yapılandırma öğesi. Bu,. svc dosyası olmadan WAS/IIS ' de barındırılan hizmetlerin etkinleştirilmesi mümkün olur.

\<sistemin. ServiceModel > \
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
|Çar|Bir hizmet etkinleştirme öğesi üreten fabrika 'nin CLR türü adını belirten bir dize.|
|hizmet|Hizmeti uygulayan ServiceType (tam nitelenmiş TypeName veya Short TypeName (App_Code klasörüne yerleştirildiğinde).|
|relativeAddress|Geçerli IIS uygulamasındaki göreli adres (örneğin, "Service. svc"). WCF 4,0 ' de, bu göreli adresin bilinen dosya uzantılarından birini (. svc,. xamlx,...) içermesi gerekir. RelativeUrl 'Si için fiziksel dosya yok|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<serviceHostingEnvironment >](servicehostingenvironment.md)|Etkinleştirme ayarlarını açıklayan bir yapılandırma bölümü.|

## <a name="remarks"></a>Açıklamalar

Aşağıdaki örnek, Web. config dosyanızda etkinleştirme ayarlarının nasıl yapılandırılacağını gösterir.

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

Bu yapılandırmayı kullanarak, bir. svc dosyası kullanmadan, bu hizmetleri etkinleştirebilirsiniz.

Bu `<serviceHostingEnvironment>` , bir uygulama düzeyi yapılandırması olduğunu unutmayın. Yapılandırma `web.config` içeren yapılandırmayı sanal uygulamanın köküne yerleştirmeniz gerekir. Ayrıca, `serviceHostingEnvironment` bir MachineToApplication devralınabilir bölümüdür. Makinenin köküne tek bir hizmet kaydettiğinizde, uygulamadaki her hizmet bu hizmeti devralmasını sağlayacaktır.

Yapılandırma tabanlı etkinleştirme, hem http hem de http olmayan protokol üzerinde etkinleştirmeyi destekler. RelativeAddress, yani. svc,. xoml veya. xamlx için Uzantılar gerektirir. Kendi uzantılarınızı, bilinen bir tür buildProviders ile eşleyebilirsiniz ve bu sayede hizmeti herhangi bir uzantı üzerinden etkinleştirmenizi sağlar. Çakışma sonrasında, `<serviceActivations>` bölüm. svc kayıtlarını geçersiz kılar.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
