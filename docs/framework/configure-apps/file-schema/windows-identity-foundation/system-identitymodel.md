---
title: '&lt;System.IdentityModel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e5d26ab2ff3207b0905c33ba237bf71e623a103d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemidentitymodelgt"></a>&lt;System.IdentityModel&gt;
Windows Identity Foundation (WIF) seçenekleri uygulamalarında etkinleştirmek için yapılandırma sağlar.  
  
 \<System.IdentityModel >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<system.identityModel>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Hizmet düzeyi kimlik ayarlarını belirtir.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`<configuration>`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
  
## <a name="remarks"></a>Açıklamalar  
 Ekleme bir `<system.identityModel>` bölümüne bir hizmet veya uygulamayı Windows Identity Foundation (WIF) kullanacak biçimde yapılandırmak için yapılandırma dosyası. `<system.identityModel>` Öğesi ile temsil edilir <xref:System.IdentityModel.Configuration.SystemIdentityModelSection> sınıfı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl ekleneceğini gösterir bir `<system.identityModel>` bölümüne bir yapılandırma dosyası. Yapılandırma bölümü ve ad alanı bildirimi altında ilk eklemelisiniz `<configSections>` öğesi. Ekleyebileceğiniz sonra `<system.IdentityModel>` bir veya daha fazla kimlik yapılandırmaları belirtmek için yapılandırma dosyanızı öğesi.  
  
```xml  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>
