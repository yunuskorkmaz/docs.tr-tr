---
title: '&lt;Yapılandırma&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2d75b25734b92df062d3dc46824da44883ab46d5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745948"
---
# <a name="configuration-element"></a>\<Yapılandırma > öğesi

Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.

**\<Yapılandırma >**

## <a name="syntax"></a>Sözdizimi

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a>Öznitelikler

Yok.

## <a name="parent-element"></a>Üst öğesi

Yok.

## <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| [**\<assemblyBinding >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | Derleme bağlama ilkesi yapılandırma düzeyinde belirtir.|
| [**\<Başlangıç >** Ayarları Şeması](~/docs/framework/configure-apps/file-schema/startup/index.md) | Başlangıç Ayarları Şeması tüm öğeler. |
| [**\<çalışma zamanı >** Ayarları Şeması](~/docs/framework/configure-apps/file-schema/runtime/index.md) | Çalışma Zamanı Ayarları Şeması tüm öğeler. |
| [**\<System.Runtime.Remoting >** Ayarları Şeması](http://msdn.microsoft.com/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) | Uzaktan iletişim ayarları şemadaki tüm öğeler. |
| [**\<system.Net >** Ayarları Şeması](~/docs/framework/configure-apps/file-schema/network/index.md) | Ağ ayarları şemadaki tüm öğeler. |
| [**\<cryptographySettings >** Ayarları Şeması](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | Şifreleme ayarları şemadaki tüm öğeler. |
| [**\<Yapılandırma >** bölümleri şeması](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | Yapılandırma bölümü ayarları şemadaki tüm öğeler. |
| [İzleme ve Hata Ayıklama Ayarları Şeması](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | İzleme ve hata ayıklama Ayarları Şeması tüm öğeler. |
| [ASP.NET yapılandırma ayarları şeması](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx) | ASP.NET Web siteleri ve uygulamaları yapılandırma öğeleri içeren ASP.NET yapılandırma şemadaki tüm öğeler. Kullanılan *Web.config* dosyaları. |
| [**\<Webservices'a >** Ayarları Şeması](http://msdn.microsoft.com/f84d6d55-1add-4eb7-ae46-33df5833ea2e) | Web Hizmetleri ayarları şemadaki tüm öğeler. |
| [Web Ayarları Şeması](~/docs/framework/configure-apps/file-schema/web/index.md) | ASP.NET IIS gibi bir ana bilgisayar uygulaması ile nasıl çalışır yapılandırma öğeleri içeren Web ayarları şemadaki tüm öğeler. Kullanılan *aspnet.config* dosyaları. |

## <a name="remarks"></a>Açıklamalar

Her yapılandırma dosyası tam olarak bir içermelidir  **\<configuration >** öğesi.

## <a name="see-also"></a>Ayrıca bkz.

[.NET Framework için yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
