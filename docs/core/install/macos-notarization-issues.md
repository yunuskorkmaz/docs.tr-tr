---
title: MacOS Catalina Notarle çalışma
description: .NET Core çalışma zamanı, SDK ve .NET Core ile oluşturulan uygulamaları yüklediğinizde macOS ile sertifika sorunlarını ele alma.
author: adegeo
ms.author: adegeo
ms.date: 02/14/2020
ms.openlocfilehash: 905a8b8a4a17836823b1c6574828acb08110d224
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86415948"
---
# <a name="macos-catalina-notarization-and-the-impact-on-net-core-downloads-and-projects"></a>macOS Catalina Notaror .NET Core indirmeleri ve projeleri üzerindeki etki

MacOS Catalina (sürüm 10,15) ile başlayarak, 1 Haziran 2019 ' den sonra oluşturulan ve geliştirici KIMLIĞIYLE dağıtılan tüm yazılımlar, notarlanmış olmalıdır. Bu gereksinim .NET Core çalışma zamanı, .NET Core SDK ve .NET Core ile oluşturulan yazılımlar için geçerlidir. Bu makalede, .NET Core ve macOS notarlama ile yüz yüze olabilecek yaygın senaryolar açıklanmaktadır.

## <a name="installing-net-core"></a>.NET Core yükleniyor

.NET Core (çalışma zamanı ve SDK) yükleyicileri 3,1, 3,0 ve 2,1 sürümleri, 18 Şubat 2020 tarihinden itibaren giderilmiş. Önceki yayınlanmış sürümler yok. Önce yükleyiciyi indirerek ve sonra komutunu kullanarak .NET Core 'un bilinmeyen bir sürümünü el ile yükleyebilirsiniz `sudo installer` . Daha fazla bilgi için bkz. [macOS Için indirme ve el ile yükleme](sdk.md?pivots=os-macos#download-and-manually-install).

Aşağıdaki sürümlerle başlayarak, .NET Core yükleyicileri dikkate alınır:

- .NET Core Runtime
  - 2.1.16
  - 3.0.3
  - 3.1.2

- .NET Core SDK
  - 2.1.512
  - 3.0.103
  - 3.1.102

## <a name="apphost-is-disabled-by-default"></a>appHost varsayılan olarak devre dışıdır

Varsayılan olarak, .NET Core SDK 3,0 ve üzeri sürümleri, projeniz derlendiği, yayımladığında veya çalıştırıldığında yerel bir makine-O yürütülebilir dosyası ( **appHost**olarak bilinir) oluşturur. Bu yürütülebilir dosya, uygulamanızı çalıştırmak için kullanışlı bir yoldur. Aksi takdirde, uygulamanız çalıştırılarak başlatılmış olmalıdır `dotnet <filename.dll>` . AppHost etkin olduğunda, `dotnet run` komut apphost bağlamında çağrılır. Daha fazla bilgi için bkz. [apphost bağlamı](#context-of-the-apphost).

.NET Core SDK 3,0 ve üzeri sürümleri ile başlayarak, appHost yürütülebilir dosyası varsayılan olarak oluşturulmaz. Proje dosyasındaki Boolean ayarıyla appHost oluşturma özelliğini açabilirsiniz [`UseAppHost`](../project-sdk/msbuild-props.md#useapphost) . Ayrıca, `-p:UseAppHost` çalıştırmak istediğiniz belirli komut için komut satırındaki parametresiyle appHost öğesini değiştirebilirsiniz `dotnet` :

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

Uygulamanızı [kendi içinde](../deploying/index.md#publish-self-contained)yayımladığınızda her zaman bir appHost oluşturulur.

Ayarı hakkında daha fazla bilgi için `UseAppHost` bkz. [MICROSOFT. net. SDK için MSBuild özellikleri](../project-sdk/msbuild-props.md#useapphost).

### <a name="context-of-the-apphost"></a>AppHost bağlamı

Projede appHost etkin olduğunda ve `dotnet run` uygulamanızı çalıştırmak için komutunu kullandığınızda, uygulama varsayılan ana bilgisayar değil, appHost bağlamında çağrılır (varsayılan ana bilgisayar `dotnet` komuttur). AppHost, projenizde devre dışı bırakılmışsa, `dotnet run` komut uygulamanızı varsayılan ana bilgisayar bağlamında çalıştırır. AppHost devre dışı bırakılmış olsa bile, uygulamanızı kendi içinde yayımlamak bir appHost yürütülebilir dosyası oluşturur ve kullanıcılar bu yürütülebilir dosyayı uygulamanızı çalıştırmak için kullanır. Uygulamanızı ile çalıştırmak `dotnet <filename.dll>` , uygulamayı varsayılan ana bilgisayar olan paylaşılan çalışma zamanına göre çağırır.

AppHost 'yi kullanan bir uygulama çağrıldığında, uygulama tarafından erişilen sertifika bölümü, varsayılan ana bilgisayardan farklıdır. Uygulamanızın varsayılan ana bilgisayar aracılığıyla yüklenen sertifikalara erişmesi gerekiyorsa, `dotnet run` uygulamanızı proje dosyasından çalıştırmak için komutunu kullanın veya `dotnet <filename.dll>` uygulamayı doğrudan başlatmak için komutunu kullanın.

Bu senaryo hakkında daha fazla bilgi [ASP.NET Core ve macOS ve sertifikalar](#aspnet-core-and-macos-and-certificates) bölümünde verilmiştir.

## <a name="aspnet-core-and-macos-and-certificates"></a>ASP.NET Core ve macOS ve sertifikalar

.NET Core, macOS anahtarlarındaki sertifikaları sınıfıyla yönetme yeteneği sağlar <xref:System.Security.Cryptography.X509Certificates> . MacOS anahtarlığınıza erişim, hangi bölüme göz önünde saptarken birincil anahtar olarak uygulamalar kimliğini kullanır. Örneğin imzasız uygulamalar, imzasız bölümde gizli dizileri depolar, ancak imzalı uygulamalar gizli dizileri yalnızca bunlara erişebilen bölümler halinde depolar. Uygulamanızı çağıran yürütmenin kaynağı hangi bölümün kullanılacağını belirler.

.NET Core üç yürütme kaynağı sağlar: [appHost](#apphost-is-disabled-by-default), varsayılan ana bilgisayar ( `dotnet` komut) ve özel bir ana bilgisayar. Her yürütme modelinde, imzalanmış veya imzasız farklı kimliklere sahip olabilir ve anahtarlık içindeki farklı bölümlere erişimi vardır. Bir mod tarafından içeri aktarılan sertifikalara başka bir mod tarafından erişilebilir olmayabilir. Örneğin, .NET Core 'un bilinmeyen sürümlerinin imzalı bir varsayılan ana bilgisayar vardır. Sertifikalar, kimliği temel alınarak güvenli bir bölüme içeri aktarılır. AppHost imzasız olduğundan, Bu sertifikalara oluşturulan bir appHost tarafından erişilemez.

Varsayılan bir örnek olarak, ASP.NET Core varsayılan ana bilgisayar aracılığıyla varsayılan bir SSL sertifikası içeri aktarır. AppHost kullanan ASP.NET Core uygulamalar bu sertifikaya erişemez ve .NET Core sertifikanın erişilebilir olmadığını algıladığında bir hata alır. Hata iletisi, bu sorunu nasıl giderecağınız hakkında yönergeler sağlar.

Sertifika paylaşımı gerekliyse, macOS yardımcı programıyla yapılandırma seçenekleri sağlar `security` .

ASP.NET Core sertifika sorunlarını giderme hakkında daha fazla bilgi için bkz. [ASP.NET Core https 'Yi zorlama](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems).

## <a name="default-entitlements"></a>Varsayılan yetkilendirmeler

.NET Core 'un varsayılan ana bilgisayarı ( `dotnet` komut) varsayılan yetkilendirmeler kümesine sahiptir. Bu yetkilendirmeler, .NET Core 'un düzgün çalışması için gereklidir. Uygulamanızın ek Yetkilendirmelere ihtiyacı olabileceğinden, bu durumda bir [appHost](#apphost-is-disabled-by-default) oluşturup kullanmanız ve ardından gerekli yetkilendirmeleri yerel olarak eklemeniz gerekir.

.NET Core için varsayılan yetkilendirmeler kümesi:

- `com.apple.security.cs.allow-jit`
- `com.apple.security.cs.allow-unsigned-executable-memory`
- `com.apple.security.cs.allow-dyld-environment-variables`
- `com.apple.security.cs.disable-library-validation`

## <a name="notarize-a-net-core-app"></a>.NET Core uygulaması oluşturma

Uygulamanızın macOS Catalina (sürüm 10,15) veya daha yükseği üzerinde çalışmasını istiyorsanız uygulamanızı eklemek isteyeceksiniz. Uygulamanız için uygulamanızla birlikte gönderdiğiniz appHost, .NET Core için en azından aynı [varsayılan Yetkilendirmelerle](#default-entitlements) kullanılmalıdır.

## <a name="next-steps"></a>Sonraki adımlar

- [.NET Core bağımlılıkları ve gereksinimleri](dependencies.md).
- [.NET Core çalışma zamanı ve SDK 'Sını yükler](macos.md).
