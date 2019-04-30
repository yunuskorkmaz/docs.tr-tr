---
title: <configuration> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 9a7b25c74763c020c0e19c3f6099db9001acf773
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705421"
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
| [**\<System.Runtime.Remoting >** Ayarları Şeması](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) | Uzaktan iletişim ayarları şemasındaki tüm öğeler. |
| [**\<system.Net >** Ayarları Şeması](~/docs/framework/configure-apps/file-schema/network/index.md) | Ağ ayarları şemasındaki tüm öğeler. |
| [**\<cryptographySettings >** Ayarları Şeması](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | Şifreleme ayarları şemasındaki tüm öğeler. |
| [**\<Yapılandırma >** bölümleri şeması](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | Yapılandırma bölümü ayarları şemasındaki tüm öğeler. |
| [İzleme ve Hata Ayıklama Ayarları Şeması](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | İzleme ve hata ayıklama ayarları şemasındaki tüm öğeler. |
| [ASP.NET yapılandırma ayarları şeması](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) | ASP.NET Web siteleri ve uygulamaları yapılandırma öğeleri içeren ASP.NET yapılandırma şemadaki tüm öğelerin. Kullanılan *Web.config* dosyaları. |
| [**\<Veritabanınızdaki >** Ayarları Şeması](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) | Web Hizmetleri ayarları şemasındaki tüm öğeler. |
| [Web Ayarları Şeması](~/docs/framework/configure-apps/file-schema/web/index.md) | Nasıl ASP.NET, IIS gibi ana bilgisayar uygulamasıyla çalışmasını yapılandırmak için öğeler içeren Web ayarları şemasındaki tüm öğeler. Kullanılan *aspnet.config* dosyaları. |

## <a name="remarks"></a>Açıklamalar

Her bir yapılandırma dosyası tam olarak bir içermelidir  **\<yapılandırma >** öğesi.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
