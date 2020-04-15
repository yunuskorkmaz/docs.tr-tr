---
title: 'C# ayrılmış öznitelikler: Genel öznitelikler'
ms.date: 04/09/2020
description: Öznitelikler, derleyicinin programınızın daha fazla anlambilimini anlamak için kullandığı meta verileri sağlar
ms.openlocfilehash: f855f32cd7349da34ffbd20fededdf42c3023938
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389858"
---
# <a name="reserved-attributes-assembly-level-attributes"></a>Ayrılmış öznitelikler: Derleme düzeyi öznitelikleri

Özniteliklerin çoğu sınıflar veya yöntemler gibi belirli dil öğelerine uygulanır; ancak, bazı öznitelikler geneldir— tüm derleme veya modül için geçerlidir. Örneğin, <xref:System.Reflection.AssemblyVersionAttribute> öznitelik sürüm bilgilerini aşağıdaki gibi bir derlemeye yerleştirmek için kullanılabilir:

```csharp
[assembly: AssemblyVersion("1.0.0.0")]
```

Genel öznitelikler kaynak kodunda herhangi `using` bir üst düzey yönergeden sonra ve herhangi bir tür, modül veya ad alanı bildirimlerinden önce görünür. Genel öznitelikler birden çok kaynak dosyada görünebilir, ancak dosyaların tek bir derleme geçişinde derlenmiş olması gerekir. Visual Studio, .NET Framework projelerinde AssemblyInfo.cs dosyasına global öznitelikleri ekler. Bu öznitelikler .NET Core projelerine eklenmez.

Derleme öznitelikleri, derleme hakkında bilgi sağlayan değerlerdir. Aşağıdaki kategorilere ayrılırlar:

- Montaj kimlik öznitelikleri
- Bilgilendirme özellikleri
- Derleme bildirim öznitelikleri

## <a name="assembly-identity-attributes"></a>Montaj kimlik öznitelikleri

Üç öznitelik (varsa güçlü bir adla) bir derlemenin kimliğini belirler: ad, sürüm ve kültür. Bu öznitelikler derlemenin tam adını oluşturur ve kodda başvuru yaptığınızda gereklidir. Öznitelikleri kullanarak derlemenin sürümünü ve kültürünü ayarlayabilirsiniz. Ancak, ad değeri derleyici tarafından ayarlanır, Montaj Bilgileri [İletişim Kutusu'ndaki](/visualstudio/ide/reference/assembly-information-dialog-box)Visual Studio IDE veya derleme oluşturulduğunda Derleme Bağlayıcısı (Al.exe). Derleme adı derleme bildirimine dayanır. Öznitelik, <xref:System.Reflection.AssemblyFlagsAttribute> derlemenin birden çok kopyasının bir arada bulunup bulunamayacağını belirtir.

Aşağıdaki tablo kimlik özniteliklerini gösterir.

|Öznitelik|Amaç|
|---------------|-------------|
|<xref:System.Reflection.AssemblyVersionAttribute>|Derlemenin sürümünü belirtir.|
|<xref:System.Reflection.AssemblyCultureAttribute>|Derlemenin hangi kültürü desteklediğini belirtir.|
|<xref:System.Reflection.AssemblyFlagsAttribute>|Derlemenin aynı bilgisayarda, aynı işlemde veya aynı uygulama etki alanında yan yana yürütmeyi destekleyip desteklemediğini belirtir.|

## <a name="informational-attributes"></a>Bilgilendirme özellikleri

Bir derleme için ek şirket veya ürün bilgileri sağlamak için bilgi özniteliklerini kullanırsınız. Aşağıdaki tabloda <xref:System.Reflection?displayProperty=nameWithType> ad alanında tanımlanan bilgi öznitelikleri gösterilmektedir.

|Öznitelik|Amaç|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|Montaj bildirimi için bir ürün adı belirtir.|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|Derleme bildirimi için bir ticari marka belirtir.|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|Derleme bildirimi için bir bilgi sürümü belirtir.|
|<xref:System.Reflection.AssemblyCompanyAttribute>|Bir derleme bildirimi için bir şirket adını belirtir.|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|Derleme bildiriminin telif hakkını belirten özel bir öznitelik tanımlar.|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|Win32 dosya sürümü kaynağı için belirli bir sürüm numarası ayarlar.|
|<xref:System.CLSCompliantAttribute>|Derlemenin Ortak Dil Belirtimi (CLS) ile uyumlu olup olmadığını gösterir.|

## <a name="assembly-manifest-attributes"></a>Derleme bildirim öznitelikleri

Derleme bildiriminde bilgi sağlamak için derleme bildirimi özniteliklerini kullanabilirsiniz. Öznitelikler, başlık, açıklama, varsayılan diğer ad ve yapılandırma içerir. Aşağıdaki tablo, ad alanında tanımlanan <xref:System.Reflection?displayProperty=nameWithType> derleme bildirimi özniteliklerini gösterir.

|Öznitelik|Amaç|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|Derleme bildirimi için bir derleme başlığı belirtir.|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|Derleme bildirimi için bir derleme açıklaması belirtir.|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|Derleme bildirimi için bir derleme yapılandırması (perakende veya hata ayıklama gibi) belirtir.|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|Derleme bildirimi için uygun bir varsayılan takma ad tanımlar|
