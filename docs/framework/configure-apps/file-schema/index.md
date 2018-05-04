---
title: .NET Framework için yapılandırma dosyası şeması
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b227ba343db7996d38d5a485b54629a1f4ed28bd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="configuration-file-schema-for-the-net-framework"></a>.NET Framework için yapılandırma dosyası şeması

Yapılandırma dosyaları ayarlarını değiştirin ve uygulamalarınız için ilkeleri ayarlamak için kullanabileceğiniz standart XML dosyalarıdır. .NET Framework yapılandırma şeması uygulamalarınızın davranışını denetlemek için yapılandırma dosyalarını kullanabilirsiniz öğelerden oluşur. Bu bölümde İçindekiler başlangıç, çalışma zamanı, ağ ve diğer yapılandırma ayarlarını türleri için şema hiyerarşisini yansıtır.

Makaleyi türleri, biçimi ve yapılandırma dosyalarının konumu hakkında daha fazla bilgi için bkz: [yapılandırma uygulamaları](~/docs/framework/configure-apps/index.md). Yapılandırma dosyalarını doğrudan düzenlemek istiyorsanız XML ile edinin.

> [!IMPORTANT]
> XML etiketleri ve öznitelikleri yapılandırma dosyalarında büyük/küçük harf duyarlıdır.

## <a name="in-this-section"></a>Bu bölümde

[**\<Yapılandırma >** öğesi](~/docs/framework/configure-apps/file-schema/configuration-element.md) Describes `<configuration>` tüm yapılandırma dosyaları için üst düzey öğe öğesi.

[**\<assemblyBinding >** öğesi](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) derleme bağlama ilkesi yapılandırma düzeyinde belirtir.

[**\<linkedConfiguration >** öğesi](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) dahil etmek için bir yapılandırma dosyası belirtir.

[Başlangıç Ayarları Şeması](~/docs/framework/configure-apps/file-schema/startup/index.md) hangi sürümünün kullanılacağını ortak dil çalışma zamanı belirtin öğeleri açıklar.

[Çalışma Zamanı Ayarları Şeması](~/docs/framework/configure-apps/file-schema/runtime/index.md) derleme bağlama ve çalışma zamanı davranışını yapılandırma öğeleri açıklar.

[Ağ Ayarları Şeması](~/docs/framework/configure-apps/file-schema/network/index.md) .NET Framework Internet'e nasıl bağlanacağını belirtin öğeleri açıklar.

[Şifreleme Ayarları Şeması](~/docs/framework/configure-apps/file-schema/cryptography/index.md) şifreleme algoritmalarını uygulayan sınıflar için kolay algoritma adlarını eşleme öğeleri açıklar.

[Yapılandırma bölümleri şeması](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) oluşturmak ve yapılandırma bölümlerinin için özel ayarları kullanmak için kullanılan öğeleri açıklar.

[İzleme ve hata ayıklama Ayarları Şeması](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) izleme anahtarları ve dinleyicileri belirtin öğeleri açıklar.

[Derleyici ve dil sağlayıcısı Ayarları Şeması](~/docs/framework/configure-apps/file-schema/compiler/index.md) kullanılabilir dil sağlayıcısı derleyici yapılandırmayı belirtmek öğeleri açıklar.

[Uygulama Ayarları Şeması](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) depolamak ve uygulama kapsamlı ve kullanıcı kapsamlı ayarlarını almak bir Windows Forms ya da ASP.NET uygulaması etkinleştiren öğelerini açıklar.

[Uygulama Ayarları Şeması](~/docs/framework/configure-apps/file-schema/appsettings/index.md) dosya yolları, XML Web hizmeti URL'leri veya diğer özel yapılandırma bilgilerini bir uygulama gibi özel uygulama ayarlarını içerir.

[Web Ayarları Şeması](~/docs/framework/configure-apps/file-schema/web/index.md) ASP.NET IIS gibi bir ana bilgisayar uygulaması ile nasıl çalışır yapılandırma öğeleri içeren Web ayarları şemadaki tüm öğeler. Kullanılan *Aspnet.config* dosyaları.

[Windows Forms yapılandırma şeması](winforms/index.md) tüm öğelerin birden çok monitör ve yüksek DPI desteği gibi özelleştirmeleri içeren Windows Forms uygulaması yapılandırma bölümü.

[WCF yapılandırma şeması](~/docs/framework/configure-apps/file-schema/wcf/index.md) WCF hizmeti ve istemci uygulamaları yapılandırmanızı sağlayan tüm öğeler.

[WCF yönerge söz dizimi](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) Describes `@ServiceHost` .svc derleyici tarafından kullanılan sayfa özel öznitelikleri tanımlar yönergesi.

[WIF yapılandırma şeması](windows-identity-foundation/index.md) Windows Identity Foundation (WIF) yapılandırma şeması tüm öğeleri.

## <a name="related-sections"></a>İlgili bölümler

[Uzaktan iletişim ayarları şeması](http://msdn.microsoft.com/library/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) remoting uygulamak istemci ve sunucu uygulamaları yapılandırma öğeleri açıklar.

[ASP.NET Ayarları Şeması](http://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) ASP.NET Web uygulamalarının davranışını denetleyen öğeleri açıklar.

[Web Hizmetleri ayarları şeması](http://msdn.microsoft.com/library/f84d6d55-1add-4eb7-ae46-33df5833ea2e) ASP.NET Web Hizmetleri ve bunların istemcilerinin davranışını denetleyen öğeleri açıklar.

[.NET Framework uygulamalarını yapılandırma](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) güvenlik, derleme bağlama ve Uzaktan iletişim .NET Framework yapılandırmayı açıklar.
