---
title: Sürüm oluşturma ve .NET kitaplıkları
description: Sürüm oluşturma .NET kitaplıkları için en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 12/10/2018
ms.openlocfilehash: e6f811039f74649564cbfb42ef67e0a406e4cd70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909785"
---
# <a name="versioning"></a>Sürüm Oluşturma

Yazılım kitaplığı sürüm 1.0 nadiren tamamlanmıştır. İyi kitaplıkları ekleme özellikleri, hataları düzeltiyor ve performansı iyileştirme zamanla evrim. Mevcut kullanıcıları bozmadan her sürümü ile ek değer sağlayan bir .NET Kitaplığı'nın yeni sürümleri serbest bırakabilirsiniz önemlidir.

## <a name="breaking-changes"></a>Yeni değişiklikler

Sürümleri arasında bozucu değişiklikleri işleme hakkında daha fazla bilgi için bkz: [bozucu değişiklikler](./breaking-changes.md).

## <a name="version-numbers"></a>Sürüm numaraları

Bir .NET kitaplığı, bir sürüm belirtmek için çeşitli yolları vardır. Bu sürümleri en önemli şunlardır:

### <a name="nuget-package-version"></a>NuGet Paket sürümü

[NuGet paketi sürüm](/nuget/reference/package-versioning) NuGet.org, Visual Studio NuGet Paket Yöneticisi görüntülenir ve paketi kullanıldığında, kaynak koda eklenir. NuGet Paket sürümü, sürüm numarası kullanıcıların sık bakın ve bunlar kullanmakta olduğunuz kitaplığa sürümü hakkında konuşurken bunlar için başvuracağınız ' dir. NuGet Paket sürümü NuGet tarafından kullanılır ve çalışma zamanı davranışı üzerinde hiçbir etkisi olmaz.

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

NuGet Paket sürümü ile birleştirilmiş NuGet paket tanımlayıcısı, bir NuGet paketi tanımlamak için kullanılır. Örneğin, `Newtonsoft.Json`  +  `11.0.2`. Bir sonekine sahip bir paketi bir yayın öncesi paketidir ve test için ideal kılan Özel davranışa sahiptir. Daha fazla bilgi için [yayın öncesi paketleri](./nuget.md#pre-release-packages).

NuGet Paket sürümü geliştiriciler için en çok görünen sürümü olduğundan, onu kullanarak güncelleştirmek için iyi bir fikirdir [Semantic Versioning (SemVer)](https://semver.org/). SemVer sürümü arasındaki değişiklikleri önemini gösterir ve geliştiricilerin bilinçli bir karar, hangi sürümün kullanılacağını seçerken olun yardımcı olur. Örneğin, gitmek `1.0` için `2.0` potansiyel olarak en son değişiklikleri gösterir.

**✔️ DÜŞÜNÜN** kullanarak [SemVer 2.0.0](https://semver.org/) sürümüne NuGet paketinizi.

**✔️ YAPMAK** kullanıcıların yaygın olarak göreceği sürüm numarası olduğu gibi genel belgelerinde NuGet Paket sürümü kullanın.

**✔️ YAPMAK** yayın öncesi son kararlı olmayan paket yayınlarken içerir.

> Kullanıcılar, yayın öncesi paketleri paket tamamlanmadı anlayabileceği şekilde almak için etmeniz gerekir.

### <a name="assembly-version"></a>Derleme sürümü

Derleme sürümü hangi CLR çalışma zamanında hangi sürümünü yüklemek için bir derleme seçin için kullanılır. Tanımlayıcı bir ada sahip derlemeleri sürüm oluşturma yalnızca bir derlemeyi seçme geçerlidir.

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

Windows .NET Framework CLR adlı derleme güçlü yüklemek için tam bir eşleşme ihtiyaç duyar. Örneğin, `Libary1, Version=1.0.0.0` başvuru ile derlenen `Newtonsoft.Json, Version=11.0.0.0`. .NET Framework yalnızca o tam sürümünü yükler `11.0.0.0`. Çalışma zamanında farklı bir sürümünü yüklemek için bir bağlama yeniden yönlendirmesi .NET uygulama yapılandırma dosyasına eklenmelidir.

Derleme sürümü ile birleştirilmiş bir tanımlayıcı adlandırma sağlayan [katı derleme sürümü yükleme](../../framework/app-domains/assembly-versioning.md). Bir kitaplık tanımlayıcı adlandırma çok sayıda fayda olsa da bir derleme bulunamıyor çalışma zamanı özel durumları genellikle sonuç ve [bağlama yönlendirmeleri gerektirir](../../framework/configure-apps/redirect-assembly-versions.md) içinde `app.config` / `web.config` düzeltilmesi için. .NET core derleme yükleme gevşek olmuştur ve .NET Core CLR derlemeleri daha yüksek bir sürüm ile çalışma zamanında otomatik olarak yüklenecektir.

**✔️ DÜŞÜNÜN** yalnızca bir ana sürüm AssemblyVersion dahil olmak üzere.

> Örneğin, bir AssemblyVersion kitaplığı 1.0 ve kitaplık 1.0.1 hem sahip `1.0.0.0`, kitaplığı 2.0, AssemblyVersion sahipken `2.0.0.0`. Daha az sıklıkta derleme sürümü değiştiğinde, bağlama yeniden yönlendirmeleri azaltır.

**✔️ DÜŞÜNÜN** AssemblyVersion ve NuGet Paket sürümü ana sürüm numarasını eşitlenmiş durumda kalmasını.

> Kullanıcıya görüntülenen bazı bilgi iletilerini AssemblyVersion dahildir ve örn bütünleştirilmiş kod ve derleme adı Tür adları içinde özel durum iletileri. Sürümleri arasında bir ilişki koruma sürümden kullandıkları geliştiriciler için daha fazla bilgi sağlar.

**❌ SAĞLAMADIĞI** sabit bir AssemblyVersion sahip.

> Değişmeyen bir AssemblyVersion bağlama yönlendirmeleri gereksinimini ortadan kaldırır, ancak yalnızca tek bir sürüm derlemenin Genel Derleme Önbelleği'ne (GAC) yüklenmesi anlamına gelir. Ayrıca, başka bir uygulama derlemeyi GAC bozucu değişiklikler güncelleştiriyorsa derlemenin GAC'deki başvuruda bulunan uygulamaları çalışmamasına neden olur.

### <a name="assembly-file-version"></a>Derleme dosyası sürümü

Derleme dosyası sürümü Windows dosya sürümünü görüntülemek için kullanılır ve çalışma zamanı davranışı üzerinde hiçbir etkisi olmaz. Bu sürümü isteğe bağlıdır. Windows Gezgini'nde dosya özellikleri iletişim kutusu görünür:

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

![Windows Gezgini](./media/versioning/win-properties.png "Windows Gezgini")

**✔️ DÜŞÜNÜN** sürekli tümleştirme dahil olmak üzere, yapı numarası olarak AssemblyFileVersion düzeltme.

> Örneğin, sürüm 1.0.0 projenizin oluşturuyorsanız ve, AssemblyFileVersion 1.0.0.99 sürekli tümleştirme yapı numarası 99 olduğundan.

**✔️ YAPMAK** biçimini kullanın `Major.Minor.Build.Revision` dosya sürümü için.

> Dosya sürümü .NET tarafından hiçbir zaman kullanılırken [Windows dosya sürümünü bekliyor](/windows/desktop/menurc/versioninfo-resource) olması `Major.Minor.Build.Revision` biçimi. Sürüm şu biçimi takip değil, bir uyarı oluşturulur.

### <a name="assembly-informational-version"></a>Derleme Bilgilendirme sürümü

Derleme Bilgilendirme sürümü ek sürüm bilgileri kaydetmek için kullanılır ve çalışma zamanı davranışı üzerinde hiçbir etkisi olmaz. Bu sürümü isteğe bağlıdır. Kaynak bağlantısı kullanıyorsanız, bu sürüm derleme NuGet Paket sürümü Ayrıca kaynak denetimi sürümü ile ayarlanır. Örneğin, `1.0.0-beta1+204ff0a` işleme karması gelen derlemenin derlendiği kaynak kodu içerir. Daha fazla bilgi için [kaynak bağlantısı](./sourcelink.md).

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> Bu sürüm biçimi izleyin değil, bir yapı uyarısı Visual Studio'nun eski sürümlerini yükseltmek `Major.Minor.Build.Revision`. Uyarıyı güvenle yoksayılabilir.

**❌ KAÇININ** derleme Bilgilendirme sürümü kendiniz ayarlama.

> NuGet ve kaynak denetimi meta verilerini içeren sürüm otomatik olarak oluşturulacak SourceLink izin verir.

>[!div class="step-by-step"]
>[Önceki](publish-nuget-package.md)
>[İleri](breaking-changes.md)
