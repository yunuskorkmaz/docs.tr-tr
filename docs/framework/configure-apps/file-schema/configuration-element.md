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
ms.openlocfilehash: 8f79981a55d0bc9b1cd522e45f5606fda102c72c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90544699"
---
# <a name="configuration-element"></a>\<configuration> öğesi

Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.

**\<configuration>**

## <a name="syntax"></a>Syntax

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a>Öznitelikler

Yok

## <a name="parent-element"></a>Üst öğe

Yok

## <a name="child-elements"></a>Alt öğeleri

|     | Description |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | Yapılandırma düzeyinde derleme bağlama ilkesini belirtir.|
| [**\<startup>** Ayarlar Şeması](./startup/index.md) | Başlangıç ayarları şemasındaki tüm öğeler. |
| [**\<runtime>** Ayarlar Şeması](./runtime/index.md) | Çalışma zamanı ayarları şemasındaki tüm öğeler. |
| [**\<system.runtime.remoting>** Ayarlar Şeması](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) | Uzaktan iletişim ayarları şemasındaki tüm öğeler. |
| [**\<system.Net>** Ayarlar Şeması](./network/index.md) | Ağ ayarları şemasındaki tüm öğeler. |
| [**\<cryptographySettings>** Ayarlar Şeması](./cryptography/index.md) | Şifre ayarları şemasındaki tüm öğeler. |
| [**\<configuration>** Bölüm Şeması](configuration-sections-schema.md) | Yapılandırma bölümü ayarları şemasında tüm öğeler. |
| [İzleme ve hata ayıklama ayarları şeması](./trace-debug/index.md) | İzleme ve hata ayıklama ayarları şemasındaki tüm öğeler. |
| [ASP.NET yapılandırma ayarları şeması](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) | ASP.NET yapılandırma şemasında, ASP.NET Web siteleri ve uygulamaları yapılandırma öğelerini içeren tüm öğeler. *Web.config* dosyalarında kullanılır. |
| [**\<webServices>** Ayarlar Şeması](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) | Web Hizmetleri ayarları şemasındaki tüm öğeler. |
| [Web ayarları şeması](./web/index.md) | Web ayarları şemasında, ASP.NET 'in IIS gibi bir konak uygulamasıyla nasıl çalıştığını yapılandırmaya yönelik öğeler içeren tüm öğeler. *aspnet.config* dosyalarında kullanılır. |

## <a name="remarks"></a>Açıklamalar

Her yapılandırma dosyası tam olarak bir **\<configuration>** öğe içermelidir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
