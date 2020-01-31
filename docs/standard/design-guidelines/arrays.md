---
title: Diziler
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: d4a1f379a88231654c710b1df7b505316377c915
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741798"
---
# <a name="arrays"></a>Diziler
✔️ ortak API 'lerde diziler üzerinde koleksiyonları kullanmayı tercih eder. [Koleksiyonlar](../../../docs/standard/design-guidelines/guidelines-for-collections.md) bölümü koleksiyonlar ve diziler arasında nasıl seçim yapılacağı hakkında ayrıntılar sağlar.

 ❌ salt okuma dizisi alanları kullanmayın. Alanın kendisi salt okunurdur ve değiştirilemez, ancak dizideki öğeler değiştirilebilir.

 ✔️ çok boyutlu diziler yerine pürüzlü Diziler kullanmayı düşünün.

 Sivri dizi öğeleri de diziler olan bir dizidir. Öğeleri oluşturan diziler farklı boyutlarda olabilir ve çok boyutlu dizilere kıyasla bazı veri kümeleri (örn. seyrek matris) için daha az harcanan alana sahiptir. Ayrıca, CLR, basit diziler üzerinde dizin işlemlerini iyileştirir, bu nedenle bazı senaryolarda çalışma zamanı daha iyi bir performans sergilebilirler.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array>
- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)
