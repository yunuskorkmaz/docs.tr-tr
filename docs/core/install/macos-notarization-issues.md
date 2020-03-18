---
title: macOS Catalina Noterizasyonu ile çalışma
description: .NET Core çalışma zamanı, SDK ve .NET Core ile oluşturulmuş uygulamaları yüklerken macOS ile noterizasyon ve sertifika sorunları nasıl işlenir.
author: thraka
ms.author: adegeo
ms.date: 02/14/2020
ms.openlocfilehash: be39c1ea56699f84736a2b37bc958507b16e826b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146755"
---
# <a name="macos-catalina-notarization-and-the-impact-on-net-core-downloads-and-projects"></a>macOS Catalina Noterizasyon ve .NET Core indirme ve projeleri üzerindeki etkisi

MACOS Catalina (sürüm 10.15) ile başlayarak, 1 Haziran 2019'dan sonra üretilen ve Geliştirici Kimliği ile dağıtılan tüm yazılımların noter tasdikli olması gerekir. Bu gereksinim .NET Core çalışma zamanı, .NET Core SDK ve .NET Core ile oluşturulan yazılımlar için geçerlidir. Bu makalede, .NET Core ve macOS noterizasyonu ile karşılaşabileceğiniz yaygın senaryolar açıklanmaktadır.

## <a name="installing-net-core"></a>.NET Core kurulumu

.NET Core (hem çalışma süresi hem de SDK) 3.1, 3.0 ve 2.1 sürümlerinin yükleyicileri 18 Şubat 2020'den beri noter olarak noterolarak verilmiştir. Önceki sürümler noter onaylı değildir. Önce yükleyiciyi indirip sonra komutu `sudo installer` kullanarak .NET Core'un noter onaylı olmayan bir sürümünü el ile yükleyebilirsiniz. Daha fazla bilgi için [macOS için İndir ve el ile yükleyin'](sdk.md?pivots=os-macos#download-and-manually-install)e bakın.

Aşağıdaki sürümlerden başlayarak,.NET Core yükleyiciler noter tasdiklidir:

- .NET Core Runtime
  - 2.1.16
  - 3.0.3
  - 3.1.2

- .NET Core SDK
  - 2.1.512
  - 3.0.103
  - 3.1.102

## <a name="apphost-is-disabled-by-default"></a>appHost varsayılan olarak devre dışı bırakılır

Varsayılan olarak, .NET Core SDK 3.0 ve üzeri noter onaylı olmayan sürümleri, projeniz derlendiğinde, yayımladığında veya çalıştırıldığında yerel bir Mach-O çalıştırılabilir **(appHost**olarak da bilinir) üretir. Bu yürütülebilir uygulamanızı çalıştırmak için kullanışlı bir yoldur. Aksi takdirde, uygulamanız çalıştırılarak `dotnet <filename.dll>`başlatılmalıdır. appHost etkinleştirildiğinde, `dotnet run` komut appHost bağlamında çağrılır. Daha fazla bilgi için [appHost Bağlamı'na](#context-of-the-apphost)bakın.

.NET Core SDK 3.0 ve üzeri noter onaylı sürümlerden başlayarak, appHost çalıştırılabilir varsayılan olarak oluşturulmaz. Proje dosyasındaki [`UseAppHost`](../project-sdk/msbuild-props.md#useapphost) boolean ayarı ile appHost oluşturma açabilirsiniz. Ayrıca, çalıştırdığınız belirli `-p:UseAppHost` `dotnet` komut için komut satırında parametre ile appHost geçiş yapabilirsiniz:

- Proje dosyası

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- Komut satırı parametresi

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

Uygulamanızı [bağımsız](../deploying/index.md#publish-self-contained)olarak yayımladığınızda her zaman bir appHost oluşturulur.

`UseAppHost` Ayar hakkında daha fazla bilgi için [Microsoft.NET.Sdk için MSBuild özelliklerine](../project-sdk/msbuild-props.md#useapphost)bakın.

### <a name="context-of-the-apphost"></a>appHost bağlamı

Projenizde appHost etkinleştirildiğinde ve uygulamanızı `dotnet run` çalıştırmak için komutu kullandığınızda, uygulama varsayılan ana bilgisayar (varsayılan ana bilgisayar `dotnet` komutudur) değil, appHost bağlamında çağrılır. AppHost projenizde devre dışı bırakılırsa, `dotnet run` komut varsayılan ana bilgisayar bağlamında uygulamanızı çalıştırın. appHost devre dışı bırakılmış olsa bile, uygulamanızı bağımsız olarak yayımlamak yürütülebilir bir appHost oluşturur ve kullanıcılar uygulamanızı çalıştırmak için bu yürütülebilir kullanır. Uygulamanızı varsayılan `dotnet <filename.dll>` ana bilgisayar, paylaşılan çalışma süresi ile çağırır.

appHost'u kullanan bir uygulama çağrıldığında, uygulama tarafından erişilen sertifika bölümü noter onaylı varsayılan ana bilgisayardan farklıdır. Uygulamanızın varsayılan ana bilgisayar aracılığıyla yüklenen sertifikalara erişmesi gerekiyorsa, uygulamanızı proje dosyasından çalıştırmak için `dotnet run` komutu kullanın veya uygulamayı doğrudan başlatmak için komutu `dotnet <filename.dll>` kullanın.

Bu senaryo hakkında daha fazla bilgi [ASP.NET Core ve macOS ve sertifikalar](#aspnet-core-and-macos-and-certificates) bölümünde sağlanır.

## <a name="aspnet-core-and-macos-and-certificates"></a>ASP.NET Core ve macOS ve sertifikalar

.NET Core, macOS Anahtarzinciri'ndeki sertifikaları <xref:System.Security.Cryptography.X509Certificates> sınıfla birlikte yönetme olanağı sağlar. macOS Anahtar zincirine erişim, hangi bölümün göz önünde bulundurulacağına karar verirken uygulama kimliğini birincil anahtar olarak kullanır. Örneğin, imzasız uygulamalar gizli bölümleri depolar, ancak imzalı uygulamalar sırlarını yalnızca erişebilecekleri bölümlerde saklar. Uygulamanızı çağıran yürütme kaynağı, hangi bölümün kullanılacağına karar verir.

.NET Core üç yürütme kaynağı sağlar: [appHost,](#apphost-is-disabled-by-default)varsayılan ana bilgisayar `dotnet` (komut) ve özel bir ana bilgisayar. Her yürütme modeli, imzalı veya imzasız farklı kimliklere sahip olabilir ve Anahtarzinciri içindeki farklı bölümlere erişebilir. Bir mod tarafından alınan sertifikalara başka bir moddan erişilemeyebilir. Örneğin, .NET Core'un noter onaylı sürümlerinde imzalanmış varsayılan bir ana bilgisayar vardır. Sertifikalar, kimliğine göre güvenli bir bölüme aktarılır. AppHost imzasız olduğundan, bu sertifikalara oluşturulan bir appHost'tan erişilemez.

Başka bir örnek, varsayılan olarak, ASP.NET Core varsayılan ana bilgisayar aracılığıyla varsayılan bir SSL sertifikası alır. ASP.NET AppHost kullanan Çekirdek uygulamaları bu sertifikaya erişemez ve .NET Core sertifikaya erişilemediğini algıladığında bir hata alır. Hata iletisi, bu sorunun nasıl düzeltilene ilişkin yönergeler sağlar.

Sertifika paylaşımı gerekiyorsa, macOS `security` yardımcı programla yapılandırma seçenekleri sağlar.

ASP.NET Core sertifika sorunlarıyla ilgili daha fazla bilgi için ASP.NET [Core'da HTTPS'yi zorla'ya](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems)bakın.

## <a name="default-entitlements"></a>Varsayılan haklar

.NET Core'un varsayılan `dotnet` ana bilgisayarı (komut) varsayılan yetkilendirmeler kümesine sahiptir. Bu haklar .NET Core'un düzgün çalışması için gereklidir. Uygulamanızın ek haklara ihtiyacı olabilir, bu durumda bir [appHost](#apphost-is-disabled-by-default) oluşturmanız ve kullanmanız ve gerekli yetkileri yerel olarak eklemeniz gerekir.

.NET Core için varsayılan yetkilendirme kümesi:

- `com.apple.security.cs.allow-jit`
- `com.apple.security.cs.allow-unsigned-executable-memory`
- `com.apple.security.cs.allow-dyld-environment-variables`
- `com.apple.security.cs.disable-library-validation`

## <a name="notarize-a-net-core-app"></a>Notarize bir .NET Core uygulaması

Uygulamanızın macOS Catalina (sürüm 10.15) veya daha yüksek bir sürümde çalışmasını istiyorsanız, uygulamanızı notarize etmek istersiniz. Noterleştirme için başvurunuzla birlikte gönderdiğiniz appHost en azından .NET Core için aynı [varsayılan haklarla](#default-entitlements) kullanılmalıdır.

## <a name="next-steps"></a>Sonraki adımlar

- [.NET Temel bağımlılıklar ve gereksinimler.](dependencies.md)
- [.NET Çekirdek SDK'yı yükleyin.](sdk.md)
- [.NET Çekirdek Çalışma Süresini Yükleyin](runtime.md)
