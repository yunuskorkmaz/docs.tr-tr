---
title: Kullanım yönergeleri
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: d6ea7c7b9ada95e3d0c425aaea18be6cdbb4ce35
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828510"
---
# <a name="usage-guidelines"></a>Kullanım yönergeleri

Bu bölüm, genel olarak erişilebilen API 'lerde ortak türleri kullanmayla ilgili yönergeleri içerir. Yerleşik çerçeve türlerinin doğrudan kullanımı (örn. serileştirme öznitelikleri) ve ortak işleçleri aşırı yükleme ile ilgilidir.
  
<xref:System.IDisposable?displayProperty=nameWithType>Arabirim bu bölümde ele alınmıyor, ancak [Dispose deseninin](../garbage-collection/implementing-dispose.md) bölümünde ele alınmıştır.

> [!NOTE]
> Diğer yaygın, yerleşik .NET Framework türleri hakkında yönergeler ve ek bilgiler için, şunlar için başvuru konularına bakın:,,,, <xref:System.DateTime?displayProperty=nameWithType> , <xref:System.DateTimeOffset?displayProperty=nameWithType> <xref:System.ICloneable?displayProperty=nameWithType> <xref:System.IComparable%601?displayProperty=nameWithType> <xref:System.IEquatable%601?displayProperty=nameWithType> <xref:System.Nullable%601?displayProperty=nameWithType> , <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType> .

## <a name="in-this-section"></a>Bu bölümde

[Diziler](arrays.md)  
[Öznitelikler](attributes.md)  
[Koleksiyonlar](guidelines-for-collections.md)  
[Serileştirme](serialization.md)  
[System.Xml kullanımı](system-xml-usage.md)  
[Eşitlik Işleçleri](equality-operators.md)  

*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
