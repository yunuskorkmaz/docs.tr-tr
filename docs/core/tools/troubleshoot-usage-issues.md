---
title: .NET Core araç kullanımı sorunlarını giderme
description: .NET Core araçları ve olası çözümleri çalıştırırken sık karşılaşılan sorunları öğrenin.
author: kdollard
ms.topic: troubleshooting
ms.date: 02/14/2020
ms.openlocfilehash: db88958e1605fef589c5dbcb12065a6318183705
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608318"
---
# <a name="troubleshoot-net-core-tool-usage-issues"></a>.NET Core araç kullanımı sorunlarını giderme

Küresel bir araç veya yerel araç olabilecek bir .NET Core aracını yüklemeye veya çalıştırmaya çalışırken sorunlarla karşılaşabilirsiniz. Bu makalede, yaygın temel nedenler ve bazı olası çözümler açıklanmaktadır.

## <a name="installed-net-core-tool-fails-to-run"></a>Yüklü .NET Core aracı çalıştırılamıyor

Bir .NET Core aracı çalışamazsa, büyük olasılıkla aşağıdaki sorunlardan biriyle karşılaşdınız:

* Aracın yürütülebilir dosyası bulunamadı.
* .NET Core çalışma zamanının doğru sürümü bulunamadı.

### <a name="executable-file-not-found"></a>Yürütülebilir dosya bulunamadı

Yürütülebilir dosya bulunamazsa aşağıdakine benzer bir ileti görürsünüz:

```console
Could not execute because the specified command or file was not found.
Possible reasons for this include:
  * You misspelled a built-in dotnet command.
  * You intended to execute a .NET Core program, but dotnet-xyz does not exist.
  * You intended to run a global tool, but a dotnet-prefixed executable with this name could not be found on the PATH.
```

Yürütülebilir dosyanın adı, aracı nasıl çağırabileceğinizi belirler. Aşağıdaki tabloda şu biçim açıklanmaktadır:

| Yürütülebilir dosya adı biçimi  | Çağırma biçimi   |
|-------------------------|---------------------|
| `dotnet-<toolName>.exe` | `dotnet <toolName>` |
| `<toolName>.exe`        | `<toolName>`        |

* Genel araçlar

  Genel araçlar varsayılan dizine veya belirli bir konuma yüklenebilir. Varsayılan dizinler şunlardır:

  | İşletim Sistemi          | Yol                          |
  |-------------|-------------------------------|
  | Linux/macOS | `$HOME/.dotnet/tools`         |
  | Windows     | `%USERPROFILE%\.dotnet\tools` |

  Küresel bir araç çalıştırmaya çalışıyorsanız, `PATH` makinenizde ortam değişkeninin genel aracı yüklediğiniz yolu içerdiğini ve yürütülebilir dosyanın o yolda olduğunu kontrol edin.

  .NET Core CLI, ilk kullanımındaki yol ortam değişkenine varsayılan konumu eklemeye çalışır. Ancak, konumun yola otomatik olarak eklenmeyebilir bazı senaryolar vardır:

  * Linux kullanıyorsanız ve *. tar. gz* dosyalarını kullanarak .NET Core SDK yüklediyseniz ve apt-get veya rpm değil.
  * MacOS 10,15 "Catalina" veya sonraki sürümlerini kullanıyorsanız.
  * MacOS 10,14 "Mojave" veya önceki sürümlerini kullanıyorsanız ve. *pkg*değil. *tar. gz* dosyalarını kullanarak .NET Core SDK yüklediyseniz.
  * .NET Core 3,0 SDK 'sını yüklediyseniz ve `DOTNET_ADD_GLOBAL_TOOLS_TO_PATH` ortam değişkenini olarak ayarladıysanız `false` .
  * .NET Core 2,2 SDK veya önceki sürümlerini yüklediyseniz ve `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` ortam değişkenini olarak ayarladıysanız `true` .

  Bu senaryolarda veya `--tool-path` seçeneğini belirlediyseniz, `PATH` makinenizde ortam değişkeni, genel aracı yüklediğiniz yolu otomatik olarak içermez. Bu durumda, `$HOME/.dotnet/tools` `PATH` kabuğunuzun ortam değişkenlerini güncelleştirmek için sağladığı yöntemi kullanarak araç konumunu (örneğin,) ortam değişkenine ekleyin. Daha fazla bilgi için bkz. [.NET Core araçları](global-tools.md).

* Yerel Araçlar

  Yerel bir araç çalıştırmaya çalışıyorsanız, geçerli dizinde veya onun üst dizinlerinde *dotnet-tools.js* adlı bir bildirim dosyası olduğunu doğrulayın. Bu dosya Ayrıca, kök klasör yerine proje klasörü hiyerarşisinde *. config* adlı bir klasör altında da bulunabilir. *dotnet-tools.js* varsa, açın ve çalıştırmaya çalıştığınız aracı denetleyin. Dosya için bir giriş içermiyorsa `"isRoot": true` , ek araç bildirim dosyaları için de dosya hiyerarşisini daha da denetleyin.

  Belirtilen bir yol ile yüklenmiş bir .NET Core aracını çalıştırmaya çalışıyorsanız, aracı kullanırken bu yolu eklemeniz gerekir. Araç yolu yüklü aracının kullanılmasına bir örnek:

  ```console
  ..\<toolDirectory>\dotnet-<toolName>
  ```

### <a name="runtime-not-found"></a>Çalışma zamanı bulunamadı

.NET Core araçları, [çerçeveye bağlı uygulamalardır](../deploying/index.md#publish-framework-dependent)ve bu, makinenizde yüklü bir .NET Core çalışma zamanına bağlıdır. Beklenen çalışma zamanı bulunmazsa, normal .NET Core çalışma zamanı alma-iletme kurallarını izler:

* Bir uygulama, belirtilen birincil ve ikincil sürümün en yüksek düzeltme eki sürümüne ileri kaydedilir.
* Eşleşen bir ana ve alt sürüm numarasına sahip eşleşen bir çalışma zamanı yoksa, sonraki en düşük sürüm kullanılır.
* Çalışma zamanının veya önizleme sürümleri ile sürüm sürümlerinin önizleme sürümleri arasında ileri alma gerçekleşmez. Bu nedenle, önizleme sürümleri kullanılarak oluşturulan .NET Core araçlarının, yazar tarafından yeniden oluşturulması ve yeniden yayımlanması ve yeniden yüklenmesi gerekir.

Geri alma iki yaygın senaryoda varsayılan olarak gerçekleşmez:

* Çalışma zamanının yalnızca alt sürümleri kullanılabilir. İlet geri alma yalnızca çalışma zamanının sonraki sürümlerini seçer.
* Çalışma zamanının yalnızca daha yüksek ana sürümleri kullanılabilir. İlet, büyük sürüm sınırları değildir.

Bir uygulama uygun bir çalışma zamanı bulamazsa, çalışmaz ve bir hata bildirir.

Aşağıdaki komutlardan birini kullanarak makinenizde hangi .NET Core çalışma zamanlarının yüklü olduğunu öğrenebilirsiniz:

```dotnetcli
dotnet --list-runtimes
dotnet --info
```

Aracın şu anda yüklü olan çalışma zamanı sürümünü desteklemesi gerektiğini düşünüyorsanız, araç yazarıyla iletişim kurun ve sürüm numarasını veya çoklu hedefi güncelleştirebilir. Araç paketlerini yeniden derlendikten ve güncelleştirilmiş bir sürüm numarasıyla NuGet 'e yeniden yayınladıktan sonra, kopyanızı güncelleştirebilirsiniz. Gerçekleşmediğinden, sizin için en hızlı çözüm, çalıştırmaya çalıştığınız araçla çalışacak çalışma zamanının bir sürümünü yüklemektir. Belirli bir .NET Core çalışma zamanı sürümünü indirmek için [.NET Core indirme sayfasını](https://dotnet.microsoft.com/download/dotnet-core)ziyaret edin.

.NET Core SDK varsayılan olmayan bir konuma yüklerseniz, ortam değişkenini `DOTNET_ROOT` yürütülebilir dosyayı içeren dizine ayarlamanız gerekir `dotnet` .

## <a name="net-core-tool-installation-fails"></a>.NET Core aracı yüklemesi başarısız oluyor

.NET Core küresel veya yerel bir araç yüklemesinin başarısız olması birkaç nedenden kaynaklanabilir. Araç yüklemesi başarısız olduğunda aşağıdakine benzer bir ileti görürsünüz:

```console
Tool '{0}' failed to install. This failure may have been caused by:

* You are attempting to install a preview release and did not use the --version option to specify the version.
* A package by this name was found, but it was not a .NET Core tool.
* The required NuGet feed cannot be accessed, perhaps because of an Internet connection problem.
* You mistyped the name of the tool.

For more reasons, including package naming enforcement, visit https://aka.ms/failure-installing-tool
```

Bu hataların tanılanmasına yardımcı olmak için, NuGet iletileri önceki iletiyle birlikte doğrudan kullanıcıya gösterilir. NuGet iletisi sorunu belirlemenize yardımcı olabilir.

### <a name="package-naming-enforcement"></a>Paket adlandırma zorlaması

Microsoft, araçların paket KIMLIĞI üzerinde rehberlik değiştirdi, bu da tahmin edilen ada sahip bir dizi araç bulunamamıştır. Yeni kılavuzluk, tüm Microsoft araçlarının ön eki olan "Microsoft" Bu ön ek ayrılmıştır ve yalnızca Microsoft yetkili sertifikasıyla imzalanmış paketler için kullanılabilir.

Geçiş sırasında bazı Microsoft araçları paket KIMLIĞI eski biçiminde olacaktır, diğerleri ise yeni biçime sahip olur:

```dotnetcli
dotnet tool install -g Microsoft.<toolName>
dotnet tool install -g <toolName>
```

Paket kimlikleri güncelleştirildiğinden, en son güncelleştirmeleri almak için yeni paket KIMLIĞINE geçmeniz gerekir. Basitleştirilmiş araç adına sahip paketler kullanım dışı olacaktır.

### <a name="preview-releases"></a>Önizleme yayınları

* Bir önizleme sürümü yüklemeye çalışıyorsunuz ve `--version` sürümü belirlemek için bu seçeneği kullanmadınız.

Önizlemedeki .NET Core araçları, önizlemede olduğunu göstermek için adının bir bölümüyle birlikte belirtilmelidir. Tüm önizlemeyi eklemeniz gerekmez. Sürüm numaralarının beklenen biçimde olduğu varsayılarak, aşağıdaki örneğe benzer bir şey kullanabilirsiniz:

```dotnetcli
dotnet tool install -g --version 1.1.0-pre <toolName>
```

### <a name="package-isnt-a-net-core-tool"></a>Paket bir .NET Core aracı değil

* Bu ada sahip bir NuGet paketi bulundu, ancak bir .NET Core aracı değildi.

.NET Core aracı olmayan düzenli bir NuGet paketi olan bir NuGet paketini yüklemeye çalışırsanız, aşağıdakine benzer bir hata görürsünüz:

> NU1212: için geçersiz proje-Package birleşimi `<ToolName>` . DotnetToolReference proje stili yalnızca DotnetTool türündeki başvuruları içerebilir.

### <a name="nuget-feed-cant-be-accessed"></a>NuGet akışına erişilemiyor

* Olası bir Internet bağlantısı sorunu nedeniyle, gerekli NuGet akışına erişilemiyor.

Araç yüklemesi için araç paketini içeren NuGet akışına erişim gerekir. Akış kullanılamıyorsa başarısız olur. Akışları ile değiştirebilir `nuget.config` , belirli bir `nuget.config` dosya isteyebilir veya anahtarla ek akışlar belirtebilirsiniz `--add-source` . NuGet, varsayılan olarak, bağlanamaan herhangi bir akış için bir hata oluşturur. Bayrak, `--ignore-failed-sources` Bu ulaşılabilir olmayan kaynakları atlayabilir.

### <a name="package-id-incorrect"></a>Paket KIMLIĞI yanlış

* Aracın adını yanlış yazmış olursunuz.

Hatanın yaygın bir nedeni, araç adının doğru olmaması. Bu, yanlış yazma veya araç taşınmış ya da kullanım dışı olduğu için oluşabilir. NuGet.org üzerinde Araçlar için, adın doğru olduğundan emin olmanın bir yolu, NuGet.org adresinde aracı aramak ve yükleme komutunu kopyalamaktır.

## <a name="see-also"></a>Ayrıca bkz.

* [.NET Core araçları](global-tools.md)
