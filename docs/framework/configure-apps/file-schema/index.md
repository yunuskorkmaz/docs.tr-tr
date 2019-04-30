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
ms.openlocfilehash: 6ebb6487136bff567c57143e3000a20270c1f87e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705291"
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

[Uzaktan iletişim ayarları şeması](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) uzak uygulanan istemci ve sunucu uygulamalarını yapılandıran öğeleri açıklar.

[ASP.NET Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) ASP.NET Web uygulamalarının davranışını denetleyen öğeleri açıklar.

[Web Hizmetleri ayarları şeması](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) ASP.NET Web Hizmetleri ve bunlarla ilgili istemcilerin davranışını denetleyen öğeleri açıklar.

[.NET Framework uygulamalarını yapılandırma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) uzaktan iletişim güvenlik ve derleme bağlamasını .NET Framework'teki yapılandırmayı açıklar.
