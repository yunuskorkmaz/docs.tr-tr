---
title: Önceden tanımlı yapılandırma dosyaları (kod analizi)
description: Belirli kod analizi türlerini hedeflemek için önceden tanımlanmış editorconfig ve kural kümesi dosyalarını kullanma hakkında bilgi edinin.
ms.date: 09/24/2020
ms.topic: conceptual
ms.openlocfilehash: 4937dcab1183fa3f63be4afc71627a7c7c08c6bd
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "96589330"
---
# <a name="predefined-configuration-files"></a>Önceden tanımlı yapılandırma dosyaları

Önceden tanımlanmış EditorConfig ve [kural kümesi](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) dosyaları, güvenlik veya tasarım kuralları gibi kod kalitesi kuralları kategorisini hızlı ve kolay hale getirmek için kullanılabilir. Belirli bir kural kategorisini etkinleştirerek, hedeflenen sorunları ve belirli koşulları belirleyebilirsiniz. Önceden tanımlanmış bu dosyalara erişmek için [Microsoft. CodeAnalysis. Netçözümleyiciler](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet Çözümleyicisi paketini yüklersiniz.

[Microsoft. CodeAnalysis. Netçözümleyiciler](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) aşağıdaki kural kategorileri için önceden tanımlanmış editorconfig dosyalarını ve kural kümelerini içerir:

- Tüm kurallar
- Veri akışı
- Tasarım
- Belgeler
- Genelleştirme
- Birlikte çalışabilirlik
- Bakım
- Adlandırma
- Performans
- FxCop 'den
- Güvenilirlik
- Güvenlik
- Kullanım

Bu kural kategorilerinin her biri bir EditorConfig veya kural kümesi dosyasına sahiptir:

- Kategorideki tüm kuralları etkinleştir (ve diğer tüm kuralları devre dışı bırak)
- Her kuralın varsayılan önem derecesini kullanın ve varsayılan ayar olarak etkindir (ve diğer tüm kuralları devre dışı bırakın)

> [!TIP]
> "Tüm kurallar" kategorisinin tüm kuralları devre dışı bırakmak için ek bir EditorConfig veya kural kümesi dosyası vardır. Bir projedeki hiçbir çözümleyici uyarılarından veya hatalarından kurtulmak için bu dosyayı kullanın.

## <a name="predefined-editorconfig-files"></a>Önceden tanımlanmış EditorConfig dosyaları

Microsoft. CodeAnalysis. Netçözümleyiciler çözümleyici paketinin önceden tanımlanmış EditorConfig dosyaları, NuGet paketinin yüklendiği *EditorConfig* alt dizininde bulunur. Örneğin, tüm güvenlik kurallarını etkinleştirmek için EditorConfig dosyası *editorconfig/SecurityRulesEnabled/. editorconfig* konumunda bulunur.

Seçilen *. editorconfig* dosyasını projenizin kök dizinine kopyalayın.

## <a name="predefined-rule-sets"></a>Önceden tanımlanmış kural kümeleri

Microsoft. CodeAnalysis. Netçözümleyiciler çözümleyici paketi için önceden tanımlanmış kural kümesi dosyaları, NuGet paketinin yüklendiği *RuleSets* alt dizininde bulunur. Örneğin, tüm güvenlik kurallarını etkinleştirmek için kural kümesi dosyası *RuleSets/SecurityRulesEnabled. RuleSet* konumunda bulunur. Kural kümelerinden birini veya birkaçını kopyalayın ve projenizi içeren dizine yapıştırın.

## <a name="see-also"></a>Ayrıca bkz.

- [Çözümleyici yapılandırması](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [EditorConfig için .NET kod stili kural seçenekleri](code-style-rule-options.md)
