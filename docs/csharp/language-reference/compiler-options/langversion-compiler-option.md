---
title: -langversion (C# derleyici seçenekleri)
ms.date: 05/20/2020
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.custom: updateeachrelease
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: fd05802008a20267fea54f14bae4c8deb0e21c65
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656221"
---
# <a name="-langversion-c-compiler-options"></a>-langversion (C# derleyici seçenekleri)

Derleyicinin yalnızca seçili C# dil belirtiminde bulunan sözdizimini kabul etmesine neden olur.

## <a name="syntax"></a>Söz dizimi

```console
-langversion:option
```

## <a name="arguments"></a>Bağımsız değişkenler

`option`

Aşağıdaki değerler geçerlidir:

[!INCLUDE [lang-versions-table](../includes/langversion-table.md)]

Varsayılan dil sürümü, uygulamanız için hedef çerçeveye ve SDK 'nın veya Visual Studio 'nun yüklü olduğu sürüme bağlıdır. Bu kurallar, [dil sürümü yapılandırma](../configure-language-version.md#defaults) makalesinde tanımlanmıştır.

## <a name="remarks"></a>Açıklamalar

C# uygulamanız tarafından başvurulan meta veriler, **-langversion** derleyici seçeneği değildir.

C# derleyicisinin her sürümü dil belirtimine uzantılar içerdiğinden, **-langversion** size derleyicinin önceki bir sürümünün eşdeğer işlevlerini sağlamaz.

Buna ek olarak, C# sürüm güncelleştirmeleri genellikle büyük .NET Framework sürümleriyle aynı olsa da yeni söz dizimi ve Özellikler ilgili çerçeve sürümüne bağlı değildir. Yeni özellikler, C# düzeltmesine göre de yayınlanan yeni bir derleyici güncelleştirmesi gerektirirken, her bir özellik kendi minimum .NET API 'sine veya NuGet paketlerini veya diğer kitaplıkları ekleyerek alt düzey çerçeveler üzerinde çalışmasına izin veren ortak dil çalışma zamanı gereksinimlerine sahiptir.

Kullandığınız dil **sürümü** ayarı ne olursa olsun,. exe veya. dll dosyanızı oluşturmak için ortak dil çalışma zamanının güncel sürümünü kullanın. Tek bir istisna, **-langversion: ISO-1**altında çalışan arkadaş derlemelerdir ve [-moduleassemblyname (C# derleyici seçeneği)](./moduleassemblyname-compiler-option.md).

C# dil sürümünü belirtmenin diğer yolları için bkz. [C# dil sürümünü seçme](../configure-language-version.md) makalesi.

Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A> ..

## <a name="c-language-specification"></a>C# dili belirtimi

| Sürüm          | Bağlantı                       | Açıklama                                                             |
|------------------|----------------------------|-------------------------------------------------------------------------|
| C# 7,0 ve üzeri |                            | Şu anda kullanılamıyor                                                 |
| C# 6,0           | [Bağlantı][csharp-6]           | C# dil belirtimi sürüm 6-resmi olmayan taslak: .NET Foundation |
| C# 5,0           | [PDF’yi İndir][csharp-5]   | Standart ECMA-334 5 sürümü                                           |
| C# 3,0           | [BELGEYI indir][csharp-3]   | C# dil belirtimi sürüm 3,0: Microsoft Corporation            |
| C# 2,0           | [PDF’yi İndir][csharp-2]   | Standart ECMA-334 4 sürümü                                           |
| C# 1,2           | [BELGEYI indir][csharp-1.2] | C# dil belirtimi sürüm 1,2: Microsoft Corporation            |
| C# 1,0           | [BELGEYI indir][csharp-1]   | C# dil belirtimi sürüm 1,0: Microsoft Corporation            |

[csharp-6]: /dotnet/csharp/language-reference/language-specification/introduction
[csharp-5]: https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf
[csharp-3]: https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc
[csharp-2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf
[csharp-1.2]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf
[csharp-1]: https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a>Tüm dil özelliklerini desteklemek için gereken en düşük SDK sürümü

Aşağıdaki tabloda, SDK 'nın en düşük sürümü, ilgili dil sürümünü destekleyen C# derleyicisi ile listelenmektedir:

| C# sürümü | En düşük SDK sürümü                                                                  |
|------------|--------------------------------------------------------------------------------------|
| C# 8.0     | Microsoft Visual Studio/derleme araçları 2019, sürüm 16,3 veya .NET Core 3,0 SDK         |
| C# 7.3     | Microsoft Visual Studio/derleme araçları 2017, sürüm 15,7                               |
| C# 7.2     | Microsoft Visual Studio/derleme araçları 2017, sürüm 15,5                               |
| C# 7.1     | Microsoft Visual Studio/derleme araçları 2017, sürüm 15,3                               |
| C# 7.0     | Microsoft Visual Studio/derleme araçları 2017                                             |
| C# 6       | Microsoft Visual Studio/derleme araçları 2015                                             |
| C# 5       | Microsoft Visual Studio/derleme araçları 2012 veya paketlenmiş .NET Framework 4,5 derleyicisi      |
| C# 4       | Microsoft Visual Studio/derleme araçları 2010 veya paketlenmiş .NET Framework 4,0 derleyicisi      |
| C# 3       | Microsoft Visual Studio/derleme araçları 2008 veya paketlenmiş .NET Framework 3,5 derleyicisi      |
| C# 2       | Microsoft Visual Studio/derleme araçları 2005 veya paketlenmiş .NET Framework 2,0 derleyicisi      |
| C# 1.0/1.2 | Microsoft Visual Studio/derleme araçları .NET 2002 veya paketlenmiş .NET Framework 1,0 derleyicisi |

## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
