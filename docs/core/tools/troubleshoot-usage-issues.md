---
title: Sorun Giderme .NET Core araç kullanım sorunları
description: .NET Core araçlarını ve olası çözümleri çalıştırırken sık karşılaşılan sorunları keşfedin.
author: kdollard
ms.date: 02/14/2020
ms.openlocfilehash: ed6243f802c4d3ce56a742916a1a28676e3cd876
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146456"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a>Sorun Giderme .NET Core araç kullanım sorunları

Genel bir araç veya yerel bir araç olabilecek bir .NET Core aracını yüklemeye veya çalıştırmaya çalışırken sorunlarla karşılaşabilirsiniz. Bu makalede, ortak kök nedenleri ve bazı olası çözümler açıklanır.

## <a name="installed-net-core-tool-fails-to-run"></a>Yüklü .NET Core aracı çalışmaz

Bir .NET Core aracı çalışmadığında, büyük olasılıkla aşağıdaki sorunlardan biriyle karşılaştınız:

* Araç için çalıştırılabilir dosya bulunamadı.
* .NET Core çalışma zamanının doğru sürümü bulunamadı.

### <a name="executable-file-not-found"></a>Çalıştırılabilir dosya bulunamadı

Çalıştırılabilir dosya bulunamazsa, aşağıdakilere benzer bir ileti görürsünüz:

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

Yürütülebilir adı aracı nasıl çağırdığınızı belirler. Aşağıdaki tabloda biçim açıklanmaktadır:

| Çalıştırılabilir ad biçimi  | Çağırma biçimi   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* Genel araçlar

  Genel araçlar varsayılan dizine veya belirli bir konuma yüklenebilir. Varsayılan dizinler şunlardır:

  | İşletim Sistemi          | Yol                          |
  |-------------|-------------------------------|
  | Linux/macOS | `$HOME/.dotnet/tools`         |
  | Windows     | `%USERPROFILE%\.dotnet\tools` |

  Genel bir araç çalıştırmaya çalışıyorsanız, makinenizdeki ortam değişkeninin `PATH` genel aracı yüklediğiniz yolu içerdiğinden ve yürütülebilir aracın bu yolda olduğundan denetleyin.

  .NET Core CLI, ilk kullanımında PATH ortamı değişkenine varsayılan konumu eklemeye çalışır. Ancak, konumun PATH'e otomatik olarak eklenemeyebildiği bazı senaryolar vardır:

  * Linux kullanıyorsanız ve .NET Core SDK'yı *.tar.gz* dosyalarını kullanarak yüklediyseniz ve apt-get veya rpm değil.
  * macOS 10.15 "Catalina" veya daha sonraki sürümleri kullanıyorsanız.
  * macOS 10.14 "Mojave" veya önceki sürümleri kullanıyorsanız ve *.tar.gz* dosyalarını kullanarak .NET Core SDK'yı yüklediyseniz.pkg . *.pkg*
  * .NET Core 3.0 SDK'yı yüklediyseniz ve ortam `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` değişkenini '' olarak `false`ayarladıysanız
  * .NET Core 2.2 SDK veya önceki sürümlerini yüklediyseniz ve `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` ortam `true`değişkenini ' olarak ayarladıysanız.

  Bu senaryolarda veya `--tool-path` seçeneği belirttiyseniz, `PATH` makinenizdeki ortam değişkeni genel aracı yüklediğiniz yolu otomatik olarak içermez. Bu durumda, shell'inizin çevre değişkenlerini güncelleştirmek için sağladığı yöntemi kullanarak araç konumunu (örneğin, `$HOME/.dotnet/tools`çevre değişkenine) `PATH` ekleyerek ortam değişkenine eklayın. Daha fazla bilgi için [bkz.](global-tools.md)

* Yerel araçlar

  Yerel bir aracı çalıştırmaya çalışıyorsanız, geçerli dizinde veya ana dizinde *dotnet-tools.json* adında bir bildirim dosyası olduğundan doğrulayın. Bu dosya, kök klasör ü yerine proje klasörü hiyerarşisinde herhangi bir yerde *.config* adlı bir klasör altında da yaşayabilir. *Dotnet-tools.json* varsa açın ve çalıştırmaya çalıştığınız aracı kontrol edin. Dosya için `"isRoot": true`bir giriş içermiyorsa, ek araç bildirimi dosyaları için dosya hiyerarşisini daha da yukarı kontrol edin.

  Belirli bir yol ile yüklenmiş bir .NET Core aracını çalıştırmaya çalışıyorsanız, aracı kullanırken bu yolu eklemeniz gerekir. Bir araç yolu yüklü araç kullanma nın bir örneği:

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a>Çalışma süresi bulunamadı

.NET Core araçları [çerçeveye bağımlı uygulamalardır,](../deploying/index.md#publish-runtime-dependent)bu da makinenize yüklenen bir .NET Core çalışma süresine güvendikleri anlamına gelir. Beklenen çalışma süresi bulunamazsa, aşağıdakiler gibi normal .NET Core runtime roll-forward kurallarına uyarlar:

* Bir uygulama, belirtilen ana ve küçük sürümün en yüksek yama sürümüne doğru ilerler.
* Eşleşen bir büyük ve küçük sürüm numarasıyla eşleşen çalışma zamanı yoksa, bir sonraki yüksek küçük sürüm kullanılır.
* Roll forward, çalışma zamanının önizleme sürümleri veya önizleme sürümleri ve sürüm sürümleri arasında gerçekleşmez. Bu nedenle, önizleme sürümleri kullanılarak oluşturulan .NET Core araçlarının yazar tarafından yeniden oluşturulup yeniden yayımlanmalıdır ve yeniden yüklenmelidir.

Roll-forward varsayılan olarak iki yaygın senaryoda oluşmaz:

* Yalnızca çalışma zamanının daha düşük sürümleri kullanılabilir. Roll-forward yalnızca çalışma zamanının sonraki sürümlerini seçer.
* Yalnızca çalışma zamanının daha yüksek ana sürümleri kullanılabilir. Roll-forward ana sürüm sınırlarını geçmez.

Bir uygulama uygun bir çalışma zamanı bulamazsa, çalışmaz ve bir hata bildirir.

Aşağıdaki komutlardan birini kullanarak makinenize hangi .NET Core çalışma saatlerinin takıldığı öğrenebilirsiniz:

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

Aracın şu anda yüklediğiniz çalışma zamanı sürümünü desteklemesi gerektiğini düşünüyorsanız, araç yazarına başvurabilir ve sürüm numarasını veya çoklu hedefi güncelleştirip güncelleştiremediklerini görebilirsiniz. Araç paketlerini güncelleştirilmiş bir sürüm numarasıyla NuGet'e yeniden derleyip yeniden yayımladıktan sonra kopyanızı güncelleştirebilirsiniz. Bu gerçekleşmese de, sizin için en hızlı çözüm, çalıştırmaya çalıştığınız araçla çalışacak çalışma zamanının bir sürümünü yüklemektir. Belirli bir .NET Core çalışma zamanı sürümünü indirmek için [.NET Core indirme sayfasını](https://dotnet.microsoft.com/download/dotnet-core)ziyaret edin.

.NET Core SDK'yı varsayılan olmayan bir konuma yüklerseniz, ortam `DOTNET_ROOT` değişkenini `dotnet` yürütülebilir içeren dizine ayarlamanız gerekir.

## <a name="net-core-tool-installation-fails"></a>.NET Core araç kurulumu başarısız oldu

.NET Core global veya yerel bir aracın yüklenmesinin başarısız olmasının birkaç nedeni vardır. Araç yüklemesi başarısız olduğunda, aşağıdakine benzer bir ileti görürsünüz:

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

Bu hataları tanılamaya yardımcı olmak için, NuGet iletileri önceki iletiyle birlikte doğrudan kullanıcıya gösterilir. NuGet iletisi sorunu belirlemenize yardımcı olabilir.

### <a name="package-naming-enforcement"></a>Paket adlandırma zorlama

Microsoft, araçlar için Paket Kimliği kılavuzunu değiştirerek, bir dizi araçta öngörülen adla birlikte bulunamadı. Yeni kılavuz, tüm Microsoft araçlarının "Microsoft" ile önceden belirlenmiş olmasıdır. Bu önek ayrılmıştır ve yalnızca Microsoft yetkili sertifikasıyla imzalanmış paketler için kullanılabilir.

Geçiş sırasında, bazı Microsoft araçları paket kimliğinin eski biçimine sahip olurken, diğerleri yeni forma sahip olur:

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

Paket kimlikleri güncelleştirildikçe, en son güncelleştirmeleri almak için yeni paket kimliğine değiştirmeniz gerekir. Basitleştirilmiş araç adı taşıyan paketler amortismana sokulacaktır.

### <a name="preview-releases"></a>Önizleme bültenleri

* Bir önizleme sürümü yüklemeye çalışıyorsunuz ve sürümü `--version` belirtme seçeneğini kullanmadınız.

.NET Core araçları önizlemede olduklarını belirtmek için adın bir bölümüyle belirtilmelidir. Önizlemenin tamamını eklemeniz gerekmez. Sürüm numaralarının beklenen biçimde olduğunu varsayarsak, aşağıdaki örnek gibi bir şey kullanabilirsiniz:

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-core-tool"></a>Paket bir .NET Core aracı değildir

* Bu ada göre bir NuGet paketi bulundu, ancak bir .NET Core aracı değildi.

Bir .NET Core aracı değil de normal bir NuGet paketi yüklemeye çalışırsanız, aşağıdakilere benzer bir hata görürsünüz:

> NU1212: Geçersiz proje paketi `<ToolName>`kombinasyonu. DotnetToolReference proje stili yalnızca DotnetTool türüne ait referanslar içerebilir.

### <a name="nuget-feed-cant-be-accessed"></a>NuGet akışına erişilenemiyor

* Gerekli NuGet akışına, internet bağlantısı sorunu nedeniyle erişilememektedir.

Araç yükleme, araç paketini içeren NuGet akışına erişim gerektirir. Özet akışı kullanılamıyorsa başarısız olur. Akışlarını `nuget.config`değiştirebilir, belirli `nuget.config` bir dosya yı isteyebilir veya `--add-source` anahtarla ek akışlar belirtebilirsiniz. Varsayılan olarak, NuGet bağlanamayan tüm akışlar için bir hata atar. Bayrak `--ignore-failed-sources` bu erişilemez kaynakları atlayabilir.

### <a name="package-id-incorrect"></a>Paket kimliği yanlış

* Aracın adını yanlış yazdınız.

Hatanın yaygın bir nedeni, araç adının doğru olmamasıdır. Bu, yanlış yazım nedeniyle veya araç taşındığı veya küçümdelenmiş olması nedeniyle olabilir. NuGet.org araçlar için, adı doğru olduğundan emin olmak için bir yolu NuGet.org aracı aramak ve yükleme komutunu kopyalamaktır.

## <a name="see-also"></a>Ayrıca bkz.

* [.NET Çekirdek araçları](global-tools.md)
