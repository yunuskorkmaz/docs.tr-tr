---
title: Kullanım yönergeleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: KrzysztofCwalina
ms.openlocfilehash: 761570b899a2a36391eb81dc7f42e13fff1f14ef
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155411"
---
# <a name="usage-guidelines"></a>Kullanım yönergeleri

Bu bölümde, genel olarak erişilebilir API'leri genel türleri kullanma yönergeleri içerir. Bu yerleşik Framework türlerinin (örneğin, serileştirme öznitelikleri) ve aşırı yükleme işleçleri ortak doğrudan kullanımı ile ilgilidir.
  
<xref:System.IDisposable?displayProperty=nameWithType> Arabirimi bu bölümde kapsamında olmayan, ancak içinde ele alınmıştır [Dispose deseni](../../../docs/standard/design-guidelines/dispose-pattern.md) bölümü.

> [!NOTE]
> Yönergeleri ve diğer ortak hakkında daha fazla bilgi için yerleşik .NET Framework türleri, başvuru konuları aşağıdaki için bkz: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType>.

## <a name="in-this-section"></a>Bu bölümde

[Diziler](arrays.md)  
[Öznitelikler](attributes.md)  
[Koleksiyonlar](guidelines-for-collections.md)  
[Serileştirme](serialization.md)  
[System.Xml Kullanımı](system-xml-usage.md)  
[Eşitlik İşleçleri](equality-operators.md)  

*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
