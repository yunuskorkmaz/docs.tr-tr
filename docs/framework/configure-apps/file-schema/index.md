---
title: .NET Framework yapılandırma dosyası şeması
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
ms.openlocfilehash: 37600331ac52add60a98c9fd573591dc34b94f5f
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083970"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>.NET Framework yapılandırma dosyası şeması

Yapılandırma dosyalarını, ayarları değiştirmek ve uygulamalarınız için ilkeleri ayarlamak için kullanabileceğiniz standart XML dosyalarıdır. .NET Framework yapılandırma şeması, yapılandırma dosyalarında uygulamalarınızın davranışını denetlemek için kullanabileceğiniz öğelerden oluşur. Bu bölümün içindekiler tablosu, başlangıç, çalışma zamanı, ağ ve diğer türde yapılandırma ayarları için şema hiyerarşisini yansıtır.

Türleri, biçimi ve yapılandırma dosyalarının konumu hakkında daha fazla bilgi için bkz [yapılandırma uygulamaları](~/docs/framework/configure-apps/index.md). Yapılandırma dosyaları doğrudan düzenlemek istiyorsanız, XML ile kendinizi alıştırın.

> [!IMPORTANT]
> XML etiketleri ve öznitelikleri yapılandırma dosyalarında büyük/küçük harf duyarlıdır.

## <a name="in-this-section"></a>Bu bölümde

[**\<Yapılandırma >** öğesi](~/docs/framework/configure-apps/file-schema/configuration-element.md) Describes `<configuration>` tüm yapılandırma dosyaları için üst düzey öğe olan öğe.

[**\<assemblyBinding >** öğesi](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) derleme bağlama ilkesini yapılandırma düzeyinde belirtir.

[**\<linkedConfiguration >** öğesi](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) dahil edilecek bir yapılandırma dosyası belirtir.

[Başlangıç Ayarları Şeması](~/docs/framework/configure-apps/file-schema/startup/index.md) kullanılacak ortak dil çalışma zamanının hangi sürümünü belirten öğeleri açıklar.

[Çalışma Zamanı Ayarları Şeması](~/docs/framework/configure-apps/file-schema/runtime/index.md) derleme bağlama ve çalışma zamanı davranışını yapılandıran öğeleri açıklar.

[Ağ Ayarları Şeması](~/docs/framework/configure-apps/file-schema/network/index.md) .NET Framework Internet'e nasıl bağlandığını belirten öğeleri açıklar.

[Şifreleme Ayarları Şeması](~/docs/framework/configure-apps/file-schema/cryptography/index.md) şifreleme algoritmalarını uygulayan sınıflar için kolay algoritma adlarını eşleyen öğeleri açıklar.

[Yapılandırma bölümleri şeması](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) oluşturma ve yapılandırma bölümleri için özel ayarlar için kullanılan öğeleri açıklar.

[İzleme ve hata ayıklama Ayarları Şeması](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) izleme anahtarları ve dinleyicileri belirten öğeleri açıklar.

[Derleyici ve dil sağlayıcısı Ayarları Şeması](~/docs/framework/configure-apps/file-schema/compiler/index.md) kullanılabilir dil sağlayıcıları için derleyici yapılandırması belirten öğeleri açıklar.

[Uygulama Ayarları Şeması](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) depolamak ve uygulama kapsamlı ve kullanıcı kapsamlı ayarları almak bir Windows Forms veya ASP.NET uygulaması sağlayan öğeleri açıklar.

[Uygulama Ayarları Şeması](~/docs/framework/configure-apps/file-schema/appsettings/index.md) dosya yolları, XML Web hizmeti URL'leri ya da bir uygulama için diğer özel yapılandırma bilgileri gibi özel uygulama ayarları içerir.

[Web Ayarları Şeması](~/docs/framework/configure-apps/file-schema/web/index.md) nasıl ASP.NET, IIS gibi ana bilgisayar uygulamasıyla çalışmasını yapılandırmak için öğeler içeren Web ayarları şemasındaki tüm öğeler. Kullanılan *Aspnet.config* dosyaları.

[Windows Forms yapılandırma şeması](winforms/index.md) çoklu monitör ve yüksek DPI desteği gibi özelleştirmeleri içerir Windows Forms Uygulama Yapılandırması bölümünde tüm öğeleri.

[WCF yapılandırma şeması](~/docs/framework/configure-apps/file-schema/wcf/index.md) WCF hizmeti ve istemci uygulamaları yapılandırmanıza imkan sağlayan tüm öğeler.

[WCF yönerge söz dizimi](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) Describes `@ServiceHost` .svc derleyici tarafından kullanılan bir sayfaya özgü öznitelikleri tanımlayan yönergesi.

[WIF yapılandırma şeması](windows-identity-foundation/index.md) Windows Identity Foundation (WIF) yapılandırma şeması tüm öğeleri.

## <a name="related-sections"></a>İlgili bölümler

[Uzaktan iletişim ayarları şeması](https://msdn.microsoft.com/library/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) uzak uygulanan istemci ve sunucu uygulamalarını yapılandıran öğeleri açıklar.

[ASP.NET Settings Schema](https://msdn.microsoft.com/library/b5ysx397\(v=vs.100\).aspx) ASP.NET Web uygulamalarının davranışını denetleyen öğeleri açıklar.

[Web Hizmetleri ayarları şeması](https://msdn.microsoft.com/library/f84d6d55-1add-4eb7-ae46-33df5833ea2e) ASP.NET Web Hizmetleri ve bunlarla ilgili istemcilerin davranışını denetleyen öğeleri açıklar.

[.NET Framework uygulamalarını yapılandırma](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42) uzaktan iletişim güvenlik ve derleme bağlamasını .NET Framework'teki yapılandırmayı açıklar.
