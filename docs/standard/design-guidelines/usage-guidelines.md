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
# <a name="usage-guidelines"></a><span data-ttu-id="dc242-102">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="dc242-102">Usage guidelines</span></span>

<span data-ttu-id="dc242-103">Bu bölüm, genel olarak erişilebilen API 'lerde ortak türleri kullanmayla ilgili yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="dc242-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="dc242-104">Yerleşik çerçeve türlerinin doğrudan kullanımı (örn. serileştirme öznitelikleri) ve ortak işleçleri aşırı yükleme ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="dc242-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="dc242-105"><xref:System.IDisposable?displayProperty=nameWithType> arabirimi bu bölümde kapsanmaz, ancak [Dispose deseninin](../garbage-collection/implementing-dispose.md) bölümünde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="dc242-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../garbage-collection/implementing-dispose.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="dc242-106">Yönergeler ve diğer yaygın, yerleşik .NET Framework türleri hakkında daha fazla bilgi için, şunlar için başvuru konularına bakın: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc242-106">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="dc242-107">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="dc242-107">In this section</span></span>

[<span data-ttu-id="dc242-108">Diziler</span><span class="sxs-lookup"><span data-stu-id="dc242-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="dc242-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dc242-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="dc242-110">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="dc242-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="dc242-111">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="dc242-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="dc242-112">System.Xml Kullanımı</span><span class="sxs-lookup"><span data-stu-id="dc242-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="dc242-113">Eşitlik İşleçleri</span><span class="sxs-lookup"><span data-stu-id="dc242-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="dc242-114">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="dc242-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="dc242-115">*, Bir yeniden [kullanılabilir .NET kitaplığı Için kurallar, deyimler ve desenler, yeniden kullanılabilir .NET kitaplıkları için, 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abkms, yayınlanmış Eki 22, 2008 Ile Addison-Wesley tarafından yeniden yazdırılmıştır Microsoft Windows geliştirme serisinin bir parçası olarak profesyonel.*</span><span class="sxs-lookup"><span data-stu-id="dc242-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="dc242-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc242-116">See also</span></span>

- [<span data-ttu-id="dc242-117">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="dc242-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
