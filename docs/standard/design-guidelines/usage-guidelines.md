---
title: Kullanım yönergeleri
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
ms.openlocfilehash: 03eaba3e52cb25619f65637efb4f414c22770440
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291350"
---
# <a name="usage-guidelines"></a><span data-ttu-id="501f1-102">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="501f1-102">Usage guidelines</span></span>

<span data-ttu-id="501f1-103">Bu bölüm, genel olarak erişilebilen API 'lerde ortak türleri kullanmayla ilgili yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="501f1-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="501f1-104">Yerleşik çerçeve türlerinin doğrudan kullanımı (örn. serileştirme öznitelikleri) ve ortak işleçleri aşırı yükleme ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="501f1-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="501f1-105"><xref:System.IDisposable?displayProperty=nameWithType>Arabirim bu bölümde ele alınmıyor, ancak [Dispose deseninin](../garbage-collection/implementing-dispose.md) bölümünde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="501f1-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../garbage-collection/implementing-dispose.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="501f1-106">Diğer yaygın, yerleşik .NET Framework türleri hakkında yönergeler ve ek bilgiler için, şunlar için başvuru konularına bakın:,,,, <xref:System.DateTime?displayProperty=nameWithType> , <xref:System.DateTimeOffset?displayProperty=nameWithType> <xref:System.ICloneable?displayProperty=nameWithType> <xref:System.IComparable%601?displayProperty=nameWithType> <xref:System.IEquatable%601?displayProperty=nameWithType> <xref:System.Nullable%601?displayProperty=nameWithType> , <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="501f1-106">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="501f1-107">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="501f1-107">In this section</span></span>

[<span data-ttu-id="501f1-108">Diziler</span><span class="sxs-lookup"><span data-stu-id="501f1-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="501f1-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="501f1-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="501f1-110">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="501f1-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="501f1-111">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="501f1-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="501f1-112">System. xml kullanımı</span><span class="sxs-lookup"><span data-stu-id="501f1-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="501f1-113">Eşitlik Işleçleri</span><span class="sxs-lookup"><span data-stu-id="501f1-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="501f1-114">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="501f1-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="501f1-115">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="501f1-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="501f1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="501f1-116">See also</span></span>

- [<span data-ttu-id="501f1-117">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="501f1-117">Framework Design Guidelines</span></span>](index.md)
