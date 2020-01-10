---
title: Kullanım yönergeleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: 57f6600f60e99c72b72c9f82856dc9eb631a9d4b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709003"
---
# <a name="usage-guidelines"></a>Kullanım yönergeleri

Bu bölüm, genel olarak erişilebilen API 'lerde ortak türleri kullanmayla ilgili yönergeleri içerir. Yerleşik çerçeve türlerinin doğrudan kullanımı (örn. serileştirme öznitelikleri) ve ortak işleçleri aşırı yükleme ile ilgilidir.
  
<xref:System.IDisposable?displayProperty=nameWithType> arabirimi bu bölümde kapsanmaz, ancak [Dispose deseninin](../garbage-collection/implementing-dispose.md) bölümünde ele alınmıştır.

> [!NOTE]
> Yönergeler ve diğer yaygın, yerleşik .NET Framework türleri hakkında daha fazla bilgi için, şunlar için başvuru konularına bakın: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.

## <a name="in-this-section"></a>Bu bölümde

[Diziler](arrays.md)  
[Öznitelikler](attributes.md)  
[Koleksiyonlar](guidelines-for-collections.md)  
[Serileştirme](serialization.md)  
[System.Xml Kullanımı](system-xml-usage.md)  
[Eşitlik İşleçleri](equality-operators.md)  

*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
