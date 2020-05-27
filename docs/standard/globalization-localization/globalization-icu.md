---
title: Genelleştirme ve ıCU
ms.date: 05/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- globalization [.NET Framework], about globalization
- global applications, globalization
- international applications [.NET Framework], globalization
- world-ready applications, globalization
- application development [.NET Framework], globalization
- culture, globalization
- icu, icu on windows, ms-icu
ms.openlocfilehash: 6ea848d4a60069e6702b9d60fd90a55f572fb043
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842529"
---
# <a name="net-globalization-and-icu"></a>.NET Genelleştirme ve ıCU

Geçmişte, .NET Genelleştirme API 'Leri farklı platformlarda farklı temel kitaplıklar kullandı. UNIX üzerinde, API 'Ler, [Unicode (ıCU) Için Uluslararası bileşenleri](http://site.icu-project.org/home)kullanıyordu ve Windows 'Ta [Ulusal DIL desteği (NLS)](/windows/win32/intl/national-language-support)kullanırlar. Bu, uygulamaları farklı platformlarda çalıştırırken genelleştirme API 'Leri ile ilgili bazı davranış farklılıklarıyla sonuçlanır. Davranış farklılıkları bu alanlarda önyüklendi:

- Kültürler ve kültür verileri
- Dize büyük harfleri
- Dize sıralama ve arama
- Anahtarları Sırala
- Dize normalleştirme
- Uluslararası etki alanı adları (ıDN) desteği
- Linux üzerinde saat dilimi görünen adı

.NET 5,0 ' den başlayarak, geliştiricilerin platformlar arası farklılıklara engel olmasını sağlayan temel alınan kitaplığın kullanıldığı daha fazla denetimi vardır.

## <a name="icu-on-windows"></a>Windows üzerinde ıCU

Windows 10 Mayıs 2019 güncelleştirmesi ve sonraki sürümleri, işletim sisteminin bir parçası olarak [ICU. dll dosyasını](/windows/win32/intl/international-components-for-unicode--icu-) içerir ve .NET 5,0 ve sonraki sürümleri varsayılan olarak ICU kullanır. Windows üzerinde çalışırken, .NET 5,0 ve sonraki sürümler yüklemeye çalışır `icu.dll` ve varsa Genelleştirme uygulamasında bu uygulamayı kullanır.  Bu kitaplık bulunamazsa veya yüklenemezse (örneğin, Windows 'un eski sürümlerinde çalışırken), .NET 5,0 ve üzeri sürümler NLS tabanlı uygulamaya geri döner.

> [!NOTE]
> ICU kullanırken bile,, `CurrentCulture` `CurrentUICulture` ve `CurrentRegion` üyeleri Kullanıcı ayarlarını kabul etmek için Windows Işletim sistemi API 'lerini kullanmaya devam eder.

### <a name="using-nls-instead-of-icu"></a>ICU yerine NLS kullanma

NLS yerine ıCU kullanılması, Genelleştirme ile ilgili bazı işlemlerle davranış farklılıkları oluşmasına neden olabilir. Bir geliştirici, NLS 'yi kullanmaya geri dönmek için ıCU uygulamasını devre dışı bırakabilirsiniz. Uygulamalar, aşağıdaki yollarla NLS modunu etkinleştirebilir:

- Proje dosyasında:

```xml
<ItemGroup>
  <RuntimeHostConfigurationOption Include="System.Globalization.UseNls" Value="true" />
</ItemGroup>
```

- `runtimeconfig.json` dosyasında:

```json
{
  "runtimeOptions": {
     "configProperties": {
       "System.Globalization.UseNls": true
      }
  }
}
```

- Ortam değişkenini `DOTNET_SYSTEM_GLOBALIZATION_USENLS` değeri veya değerine ayarlayarak `true` `1` .

> [!NOTE]
> Projede veya dosyada ayarlanan bir değer `runtimeconfig.json` , ortam değişkenine göre önceliklidir.

Daha fazla bilgi için bkz. [çalışma zamanı yapılandırma ayarları](../../core/run-time-config/globalization.md#nls).

## <a name="app-local-icu"></a>Uygulama-yerel ıCU

Her bir ıCU sürümü BT hata düzeltmelerinin yanı sıra dünyanın dillerini açıklayan güncelleştirilmiş ortak yerel ayar veri deposu (CLDR) verilerini de getirebilir. ICU sürümleri arasında geçiş yapmak, Genelleştirme ile ilgili işlemlere geldiğinde uygulama davranışını güvenle etkileyebilir.  Uygulama geliştiricilerinin tüm dağıtımlarda tutarlılığın sağlanmasına yardımcı olmak için, .NET 5,0 ve sonraki sürümleri, hem Windows hem de UNIX üzerinde uygulamaların kendi ıU kopyalarını taşıması ve kullanması için olanak sağlar.

Uygulamalar, aşağıdaki yollarla bir App-Local ıCU uygulama modunu kabul edebilir:

- Proje dosyasında:

```xml
<ItemGroup>
  <RuntimeHostConfigurationOption Include="System.Globalization.AppLocalIcu" Value="<suffix>:<version> or <version>" />
</ItemGroup>
```

- `runtimeconfig.json` dosyasında:

```json
{
  "runtimeOptions": {
     "configProperties": {
       "System.Globalization.AppLocalIcu": "<suffix>:<version> or <version>"
      }
  }
}
```

- Ortam değişkenini `DOTNET_SYSTEM_GLOBALIZATION_APPLOCALICU` değeri veya değerine ayarlayarak `<suffix>:<version>` `<version>` .

`<suffix>`: Genel ıCU paketleme kurallarından sonra, 36 karakterden daha az karakter uzunluğunda isteğe bağlı son ek. Özel bir ıU oluştururken, LIB adlarını ve dışarıya aktarılmış sembol adlarını bir sonek içerecek şekilde (örneğin, sonek) oluşturacak şekilde özelleştirebilirsiniz `libicuucmyapp` `myapp` .

`<version>`: Geçerli bir ıCU sürümü (örneğin, 67,1). Bu sürüm, ikili dosyaları yüklemek ve içe aktarılmış sembolleri almak için kullanılır.

Uygulama yerel anahtarı ayarlandığında ıCU 'yi yüklemek için, .NET <xref:System.Runtime.InteropServices.NativeLibrary.TryLoad%2A?displayProperty=nameWithType> birden çok yolu yoklaan yöntemini kullanır. Yöntemi ilk olarak, `NATIVE_DLL_SEARCH_DIRECTORIES` uygulamanın dosyasını temel alan DotNet ana bilgisayar tarafından oluşturulan özellikte kitaplığı bulmayı dener `deps.json` . Daha fazla bilgi için bkz. [Varsayılan yoklama](../../core/dependency-loading/default-probing.md).

Kendi içinde bulunan uygulamalar için, Kullanıcı tarafından özel bir eylem gerekmez, çünkü ıU 'nin uygulama dizininde olduğundan emin olun (kendi içindeki uygulamalar için, çalışma dizini varsayılan olarak ' dir `NATIVE_DLL_SEARCH_DIRECTORIES` ).

ICU 'yi bir NuGet paketi aracılığıyla kullanıyorsanız, bu, çerçeveye bağımlı uygulamalarda kullanılır. NuGet yerel varlıkları çözer ve bu dosyaları `deps.json` dosya ve uygulamanın çıkış dizinine dahil eder `runtimes` . .NET onu buradan yükler.

IU 'nin yerel bir derlemeden kullanıldığı, çerçeveye bağımlı uygulamalar (kendi içinde olmayan) için ek adımlar gerçekleştirmeniz gerekir. .NET SDK 'Sı henüz "gevşek" yerel ikililerinin içine dahil edilecek bir özelliğe sahip değildir `deps.json` ( [Bu SDK sorununa](https://github.com/dotnet/sdk/issues/11373)bakın). Bunun yerine, uygulamanın proje dosyasına ek bilgiler ekleyerek bunu etkinleştirebilirsiniz. Örnek:

```xml
<ItemGroup>
  <IcuAssemblies Include="icu\*.so*" />
  <RuntimeTargetsCopyLocalItems Include="@(IcuAssemblies)" AssetType="native" CopyLocal="true" DestinationSubDirectory="runtimes/linux-x64/native/" DestinationSubPath="%(FileName)%(Extension)" RuntimeIdentifier="linux-x64" NuGetPackageId="System.Private.Runtime.UnicodeData" />
</ItemGroup>
```

Bu, desteklenen çalışma zamanları için tüm ıCU ikilileri için yapılmalıdır. Ayrıca, `NuGetPackageId` öğe grubundaki meta verilerin `RuntimeTargetsCopyLocalItems` projenin gerçekten başvurduğu bir NuGet paketiyle eşleşmesi gerekir.

### <a name="macos-behavior"></a>macOS davranışı

`macOS`, dosyasında Linux yükleyicinden farklı yükleme komutlarından bağımlı dinamik kitaplıkları çözümlemek için farklı bir davranışa sahiptir `match-o` . Linux yükleyicisinde .NET, `libicudata` `libicuuc` `libicui18n` ICU bağımlılık grafiğini karşılamak için, ve (Bu sırada) deneyebilir. Ancak, macOS üzerinde bu çalışmaz. MacOS üzerinde ıCU oluştururken, varsayılan olarak, ' de bu yükleme komutlarıyla bir dinamik kitaplık alacaksınız `libicuuc` . Örneğin:

```sh
~/ % otool -L /Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib
/Users/santifdezm/repos/icu-build/icu/install/lib/libicuuc.67.1.dylib:
 libicuuc.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 libicudata.67.dylib (compatibility version 67.0.0, current version 67.1.0)
 /usr/lib/libSystem.B.dylib (compatibility version 1.0.0, current version 1281.100.1)
 /usr/lib/libc++.1.dylib (compatibility version 1.0.0, current version 902.1.0)
```

Bu komutlar yalnızca ıCU 'nin diğer bileşenleri için bağımlı kitaplıkların adına başvurur. Yükleyici `dlopen` , bu kitaplıkların sistem dizinlerinde olmasını veya `LD_LIBRARY_PATH` env VARS 'i ayarlamayı ya da uygulama düzeyi dizininde ICU 'nin olmasını kapsayan kuralları takip eden bir arama gerçekleştirir. `LD_LIBRARY_PATH`ICU ikililerinin uygulama düzeyi dizininde olmasını veya emin değilseniz, bazı ek işler yapmanız gerekir.

Yükleyici için, gibi bazı yönergeler vardır. Bu, `@loader_path` yükleyiciye bu yük komutuyla aynı dizinde bu bağımlılığı aramasını söyler. Bunu başarmanın iki yolu vardır:

- `install_name_tool -change`

  Aşağıdaki komutları çalıştırın:

```bash
install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicuuc.67.1.dylib
install_name_tool -change "libicudata.67.dylib" "@loader_path/libicudata.67.dylib" /path/to/libicui18n.67.1.dylib
install_name_tool -change "libicuuc.67.dylib" "@loader_path/libicuuc.67.dylib" /path/to/libicui18n.67.1.dylib
```

- İle yüklenen adları oluşturmak için ıCU Patch`@loader_path`

  Oto conf () çalıştırmadan önce `./runConfigureICU` [Bu satırları şu](https://github.com/unicode-org/icu/blob/ef91cc3673d69a5e00407cda94f39fcda3131451/icu4c/source/config/mh-darwin#L32-L37) şekilde değiştirin:

```
LD_SONAME = -Wl,-compatibility_version -Wl,$(SO_TARGET_VERSION_MAJOR) -Wl,-current_version -Wl,$(SO_TARGET_VERSION) -install_name @loader_path/$(notdir $(MIDDLE_SO_TARGET))
```
