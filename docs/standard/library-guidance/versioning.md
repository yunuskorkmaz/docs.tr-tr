---
title: Sürüm ve .NET kitaplıkları
description: .NET kitaplıklarını sürümleme için en iyi uygulama önerileri.
ms.date: 12/10/2018
ms.openlocfilehash: a274410714791e2790da0e3deb2a595390ee9389
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400402"
---
# <a name="versioning"></a>Sürüm oluşturma

Bir yazılım kitaplığı nadiren sürüm 1.0 tamamlanır. İyi kitaplıklar zaman içinde gelişir, özellikler ekleyerek, hataları gidererek ve performansı artırarak. Varolan kullanıcıları bozmadan, her sürümde ek değer sağlayan bir .NET kitaplığın yeni sürümlerini serbest bırakabilirsiniz önemlidir.

## <a name="breaking-changes"></a>Yeni değişiklikler

Sürümler arasındaki son kesme değişikliklerini işleme hakkında bilgi [için](./breaking-changes.md)bkz.

## <a name="version-numbers"></a>Sürüm numaraları

.NET kitaplığı bir sürümü belirtmenin birçok yolu vardır. Bu sürümler en önemlileridir:

### <a name="nuget-package-version"></a>NuGet paket sürümü

[NuGet paket sürümü](/nuget/reference/package-versioning) Visual Studio NuGet paket yöneticisi NuGet.org'da görüntülenir ve paket kullanıldığında kaynak koduna eklenir. NuGet paket sürümü, kullanıcıların sık göreceği sürüm numarasıdır ve kullandıkları kitaplığın sürümühakkında konuştukları zaman bu sürüme atıfta bulunurlar. NuGet paket sürümü NuGet tarafından kullanılır ve çalışma zamanı davranışı üzerinde hiçbir etkisi yoktur.

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

NuGet paket sürümü ile birlikte NuGet paket tanımlayıcısı, NuGet'deki bir paketi tanımlamak için kullanılır. Örneğin, `Newtonsoft.Json` + `11.0.2`. Sonekli bir paket, sürüm öncesi bir pakettir ve bunu sınama için ideal kılan özel bir davranışa sahiptir. Daha fazla bilgi için [ön sürüm paketlerine](./nuget.md#pre-release-packages)bakın.

NuGet paket sürümü geliştiriciler için en görünür sürüm olduğundan, [Anlamsal Sürüm (SemVer)](https://semver.org/)kullanarak güncellemek için iyi bir fikirdir. SemVer, sürüm arasındaki değişikliklerin önemini belirtir ve geliştiricilerin hangi sürümü kullanacaklarını seçerken bilinçli bir karar vermelerine yardımcı olur. Örneğin, gitmek, `1.0` `2.0` büyük ölçüde kırılma değişiklikleri olduğunu gösterir.

✔️ NuGet paketinizi kullanmak için [SemVer 2.0.0'ı](https://semver.org/) kullanmayı düşünün.

✔️ Kullanıcıların sık göreceği sürüm numarası olduğu için NuGet paket sürümünü herkese açık belgelerde kullanın.

✔️ DURAĞAN olmayan bir paket serbest bırakıldığında bir ön sürüm soneki içerir.

> Kullanıcılar, paketin tamamlanmadığını anlayabilmeleri için ön sürüm paketleri almayı seçmelidir.

### <a name="assembly-version"></a>Montaj sürümü

Derleme sürümü, CLR'nin bir derlemenin hangi sürümünün yüklenmesini seçmek için çalışma zamanında kullandığı sürümdür. Sürüm kullanarak bir derleme seçmek yalnızca güçlü bir ada sahip derlemeler için geçerlidir.

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

Windows .NET Framework CLR güçlü bir adlandırılmış derleme yüklemek için tam bir eşleşme gerektirir. Örneğin, `Libary1, Version=1.0.0.0` bir başvuru ile `Newtonsoft.Json, Version=11.0.0.0`derlenmiştir. .NET Framework yalnızca bu tam `11.0.0.0`sürümü yükler. Çalışma zamanında farklı bir sürüm yüklemek için .NET uygulamasının config dosyasına bağlama yönlendirmesi eklenmelidir.

Montaj sürümü ile birlikte güçlü adlandırma [sıkı montaj sürümü yükleme](../assembly/versioning.md)sağlar. Kitaplığı güçlü adlandırmanın bir dizi faydası olsa da, genellikle derlemenin bulunamayacağı çalışma zamanı özel durumları `app.config` / `web.config` ile sonuçlanır ve düzeltilmesi için [bağlama yönlendirmesi gerekir.](../../framework/configure-apps/redirect-assembly-versions.md) .NET Core montaj yüklemesi gevşetildi ve .NET Core CLR montajları çalışma zamanında daha yüksek bir sürümle otomatik olarak yükler.

✔️ Yalnızca AssemblyVersion'da önemli bir sürümü de içeren düşünün.

> örneğin Kütüphane 1.0 ve Kütüphane 1.0.1'in her `1.0.0.0`ikisi de AssemblyVersion'a `2.0.0.0`sahipken, Kütüphane 2.0'ın AssemblyVersion'u vardır. Derleme sürümü daha az sıklıkta değiştiğinde, bağlama yönlendirmelerini azaltır.

✔️ AssemblyVersion ve NuGet paket sürümünün ana sürüm numarasını senkronize tutmayı düşünün.

> AssemblyVersion kullanıcıya görüntülenen bazı bilgilendirme iletileri (örneğin, özel durum iletileri montaj adı ve montaj nitelikli tür adları) dahildir. Sürümler arasındaki ilişkiyi sürdürmek, geliştiricilere hangi sürümü kullandıkları hakkında daha fazla bilgi sağlar.

❌Sabit bir AssemblyVersion'u YOKTUR.

> Değişmeyen Bir AssemblyVersion bağlama yönlendirmeleri gereksinimini önler, ancak derlemenin yalnızca tek bir sürümünün Genel Derleme Önbelleğine (GAC) yüklenebileceği anlamına gelir. Ayrıca, başka bir uygulama GAC derlemesini kesme değişiklikleriyle güncelleştirirse, GAC'deki derlemeye başvuran uygulamalar da bozulur.

### <a name="assembly-file-version"></a>Derleme dosya sürümü

Derleme dosyası sürümü, Windows'ta bir dosya sürümünü görüntülemek için kullanılır ve çalışma zamanı davranışı üzerinde hiçbir etkisi yoktur. Bu sürümü ayarlamak isteğe bağlıdır. Windows Gezgini'ndeki Dosya Özellikleri iletişim kutusunda görülebilir:

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

![Windows Gezgini](./media/versioning/win-properties.png "Windows Gezgini")

✔️ AssemblyFileVersion revizyonu olarak sürekli bir entegrasyon yapı numarası dahil düşünün.

> Örneğin, projenizin 1.0.0 sürümünü oluşturuyorsunuz ve sürekli tümleştirme yapı numarası 99 olduğundan AssemblyFileVersion'unuz 1.0.0.99'dur.

✔️ DO dosya `Major.Minor.Build.Revision` sürümü için biçimini kullanın.

> Dosya sürümü .NET tarafından hiçbir zaman kullanılmazken, Windows `Major.Minor.Build.Revision` dosya sürümünün biçimde olmasını [bekler.](/windows/desktop/menurc/versioninfo-resource) Sürüm bu biçimi izlemezse bir uyarı yükseltilir.

### <a name="assembly-informational-version"></a>Derleme bilgilendirme sürümü

Derleme bilgilendirme sürümü ek sürüm bilgilerini kaydetmek için kullanılır ve çalışma zamanı davranışı üzerinde hiçbir etkisi yoktur. Bu sürümü ayarlamak isteğe bağlıdır. Kaynak Bağlantı kullanıyorsanız, bu sürüm NuGet paket sürümü artı bir kaynak denetim sürümü ile yapıya ayarlanır. Örneğin, `1.0.0-beta1+204ff0a` derlemenin oluşturduğu kaynak kodun işleyiş karmasını içerir. Daha fazla bilgi için [Kaynak Bağlantı'ya](./sourcelink.md)bakın.

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> Visual Studio'nun eski sürümleri, bu sürüm biçimi `Major.Minor.Build.Revision`izlemezse bir yapı uyarısı yükseltir. Uyarı güvenle yoksayılabilir.

❌Derleme bilgilendirme sürümünü kendiniz ayarlamakTAN kaçının.

> SourceLink'in NuGet ve kaynak denetimi meta verilerini içeren sürümü otomatik olarak oluşturmasına izin verin.

>[!div class="step-by-step"]
>[Önceki](publish-nuget-package.md)
>[Sonraki](breaking-changes.md)
