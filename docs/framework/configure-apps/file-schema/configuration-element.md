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
ms.openlocfilehash: 40c0ab5f18d5aae2c99dd66747d3435f0826af8b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171276"
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

## <a name="parent-element"></a>Üst öğe

Yok.

## <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| [**\<assemblyBinding >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | Derleme bağlama ilkesini yapılandırma düzeyinde belirtir.|
| [**\<Başlangıç >** Ayarları Şeması](~/docs/framework/configure-apps/file-schema/startup/index.md) | Başlangıç Ayarları Şeması tüm öğeler. |
| [**\<çalışma zamanı >** Ayarları Şeması](~/docs/framework/configure-apps/file-schema/runtime/index.md) | Çalışma zamanı ayarları şemasındaki tüm öğeler. |
| [**\<System.Runtime.Remoting >** Ayarları Şeması](https://msdn.microsoft.com/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) | Uzaktan iletişim ayarları şemasındaki tüm öğeler. |
| [**\<system.Net >** Ayarları Şeması](~/docs/framework/configure-apps/file-schema/network/index.md) | Ağ ayarları şemasındaki tüm öğeler. |
| [**\<cryptographySettings >** Ayarları Şeması](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | Şifreleme ayarları şemasındaki tüm öğeler. |
| [**\<Yapılandırma >** bölümleri şeması](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | Yapılandırma bölümü ayarları şemasındaki tüm öğeler. |
| [İzleme ve Hata Ayıklama Ayarları Şeması](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | İzleme ve hata ayıklama ayarları şemasındaki tüm öğeler. |
| [ASP.NET yapılandırma ayarları şeması](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx) | ASP.NET Web siteleri ve uygulamaları yapılandırma öğeleri içeren ASP.NET yapılandırma şemadaki tüm öğelerin. Kullanılan *Web.config* dosyaları. |
| [**\<Veritabanınızdaki >** Ayarları Şeması](https://msdn.microsoft.com/f84d6d55-1add-4eb7-ae46-33df5833ea2e) | Web Hizmetleri ayarları şemasındaki tüm öğeler. |
| [Web Ayarları Şeması](~/docs/framework/configure-apps/file-schema/web/index.md) | Nasıl ASP.NET, IIS gibi ana bilgisayar uygulamasıyla çalışmasını yapılandırmak için öğeler içeren Web ayarları şemasındaki tüm öğeler. Kullanılan *aspnet.config* dosyaları. |

## <a name="remarks"></a>Açıklamalar

Her bir yapılandırma dosyası tam olarak bir içermelidir  **\<yapılandırma >** öğesi.

## <a name="see-also"></a>Ayrıca bkz.

[.NET Framework yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
