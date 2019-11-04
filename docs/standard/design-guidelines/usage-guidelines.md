---
title: Kullanım yönergeleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: KrzysztofCwalina
ms.openlocfilehash: 23b1520a864d41e5ef59377cc9cca34cbdf22b64
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423043"
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

*, Bir yeniden [kullanılabilir .NET kitaplığı Için kurallar, deyimler ve desenler, yeniden kullanılabilir .NET kitaplıkları için, 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abkms, yayınlanmış Eki 22, 2008 Ile Addison-Wesley tarafından yeniden yazdırılmıştır Microsoft Windows geliştirme serisinin bir parçası olarak profesyonel.*
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
