---
title: "NETSDK1045: geçerli .NET SDK, hedef olarak ' yeni sürümü ' desteklemez."
description: Derleme araçları .NET SDK 'nın istenen sürümünü bulamadığında oluşan .NET SDK hatası NETSDK1045 hakkında bilgi edinin.
ms.topic: error-reference
ms.date: 02/12/2021
f1_keywords:
- NETSDK1045
ms.openlocfilehash: 7f21270fdc7c2db862a49302a302bf8121fc86a5
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102104108"
---
# <a name="netsdk1045-the-current-net-sdk-does-not-support-newer-version-as-a-target"></a>NETSDK1045: geçerli .NET SDK, hedef olarak ' yeni sürümü ' desteklemez.

**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2.1.100 SDK ve sonraki sürümleri

Bu hata, derleme araçları bir proje oluşturmak için gereken .NET SDK sürümünü bulamadığında oluşur. Bunun nedeni genellikle .NET Core SDK yükleme veya yapılandırma sorunudur. Tam hata iletisi aşağıdaki örneğe benzer:

> NETSDK1045: geçerli .NET SDK, hedef olarak ' yeni sürümü ' desteklemez. ' Daha eski sürümü ' veya daha düşük bir sürüm ya da ' daha yeni sürümü destekleyen bir .NET SDK sürümü kullanın.

Aşağıdaki bölümlerde bu hatanın bazı olası nedenleri açıklanmaktadır. Her birini işaretleyin ve hangisinin sizin için geçerli olduğunu görün. Ortamda veya yapılandırma dosyalarında değişiklik yaparken, değişikliklerinizin etkili olması için komut pencerelerini yeniden başlatmanız, Visual Studio 'yu yeniden başlatmanız veya makinenizi yeniden başlatmanız gerektiğini aklınızda bulundurun.

## <a name="net-sdk-version"></a>.NET SDK sürümü

Proje dosyasını (. csproj,. vbproj veya. fsproj) açın ve hedef çerçeveyi denetleyin. Bu, uygulamanızın kullanmaya çalıştığı çerçevenin sürümüdür.

```xml
<TargetFramework>netcoreapp3.0</TargetFramework>
```

Listelenen .NET sürümünün makinede yüklü olduğundan emin olun. Yüklü sürümleri aşağıdaki komutu kullanarak listeleyebilir (bir Geliştirici Komut İstemi açın ve bu komutu çalıştırın):

```dotnetcli
dotnet --list-sdks
```

### <a name="x86-or-x64-architecture"></a>x86 veya x64 mimarisi

.NET SDK 'sının her sürümü hem x86 hem de x64 mimarisinde kullanılabilir. Proje, yanlış mimaride .NET SDK 'yı bulmaya çalışıyor veya projenizin ihtiyaç duyacağı mimariye yönelik .NET SDK 'Sı yüklenmemiş olabilir. İhtiyacınız olan mimarinin yükleme klasörlerini denetleyin. Örneğin, Windows 'ta, .NET SDK 'nın x86 sürümü *C:\Program Files (x86) \dotnet* ' ye yüklenir ve x64 sürümü *c:\Program files\dotnet* dizinine yüklenir. Bkz. [.net 'in zaten yüklü olduğunu denetleme](../../install/how-to-detect-installed-versions.md) ve makinenizde nelerin yüklü olduğunu nasıl algılayabileceğinizi öğrenmek için işletim sisteminizi seçin.

İhtiyacınız olan sürüm yüklü değilse, [.net İndirmeleri](https://dotnet.microsoft.com/download/dotnet) sayfasında ihtiyacınız olan birini bulun.

## <a name="preview-not-enabled"></a>Önizleme etkin değil

İstenen .NET SDK sürümünün yüklü olduğu bir önizlemeye sahipseniz, Visual Studio 'da önizlemeleri etkinleştirme seçeneğini de ayarlamanız gerekir. **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **Önizleme özellikleri**' ne gidin ve **.NET Core SDK Önizlemesi ' nin** işaretli olduğundan emin olun.

## <a name="visual-studio-version"></a>Visual Studio sürüm

Örneğin, .NET Core 3,0 ve üzeri Visual Studio 2019 gerektirir. Projenizi derlemek için [Visual Studio 2019 sürüm 16,3](https://visualstudio.microsoft.com/downloads) veya sonraki bir sürüme yükseltin.

## <a name="path-environment-variable"></a>PATH ortam değişkeni

Yapı araçları, .NET derleme araçlarının doğru sürümünü bulmak için PATH ortam değişkenini kullanır. PATH ortam değişkeni eski derleme araçlarına doğrudan yollar içeriyorsa, bu hata iletisi görünebilir. PATH ortam değişkeninde .NET araçlarının tek yolunun en üst düzey *DotNet* klasörüne (örneğin, *C:\Program files\dotnet*) ait olduğundan emin olun. Yanlış bir yol örneği, *C:\Program Files\dotnet\2.1.0\sdks* gibi bir örnektir.

## <a name="msbuildsdkpath-environment-variable"></a>MSBuildSDKPath ortam değişkeni

MSBuildSDKPath ortam değişkenini denetleyin. Bu isteğe bağlı ortam değişkeni MSBuild tarafından tanınır ve ayarlandıysa, varsayılan değeri geçersiz kılar. .NET SDK 'sının belirli bir eski sürümüne ayarlanmış olabilir. Ayarlanırsa, projeyi silmeyi ve projenizi yeniden oluşturmayı deneyin.

## <a name="globaljson-file"></a>Dosya üzerinde global.js

Klasör yapısında herhangi bir yerde olduğundan, projenizdeki kök klasördeki birglobal.jsve Dizin zincirini birimin köküne *göre* denetleyin. Bir SDK sürümü içeriyorsa, `sdk` düğümü ve tüm alt öğelerini silin veya istediğiniz daha yeni .NET Core sürümüne güncelleştirin.

```json
{
  "sdk": {
    "version": "2.1.0"
  }
}
```

Dosyadaki *global.js* gerekli değildir, bu nedenle düğüm dışında bir şey içermiyorsa `sdk` dosyanın tamamını silebilirsiniz.

## <a name="directorybuildprops-file"></a>Directory. Build. props dosyası

*Directory. Build. props* dosyası, genel özellikleri ayarlayasağlayan isteğe bağlı bir MSBuild dosyasıdır. Bu dosyaları çözüm klasöründe ve Dizin zincirini birimin köküne, klasör yapısında herhangi bir yerde olabilecekleri şekilde denetleyin. `TargetFramework` `MSBuildSDKPath` İstediğiniz ayarları geçersiz kılabileceğiniz öğeleri veya ayarlarını bulun.

## <a name="see-also"></a>Ayrıca bkz.

- [Geçerli .NET SDK 'Sı .NET Core 3,0 'yi belirlemeyi desteklemiyor – çözüm](https://www.ryadel.com/current-net-sdk-not-support-net-core-3-0-fix/)
