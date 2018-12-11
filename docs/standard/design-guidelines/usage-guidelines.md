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
# <a name="usage-guidelines"></a><span data-ttu-id="45f69-102">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="45f69-102">Usage guidelines</span></span>

<span data-ttu-id="45f69-103">Bu bölümde, genel olarak erişilebilir API'leri genel türleri kullanma yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="45f69-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="45f69-104">Bu yerleşik Framework türlerinin (örneğin, serileştirme öznitelikleri) ve aşırı yükleme işleçleri ortak doğrudan kullanımı ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="45f69-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="45f69-105"><xref:System.IDisposable?displayProperty=nameWithType> Arabirimi bu bölümde kapsamında olmayan, ancak içinde ele alınmıştır [Dispose deseni](../../../docs/standard/design-guidelines/dispose-pattern.md) bölümü.</span><span class="sxs-lookup"><span data-stu-id="45f69-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="45f69-106">Yönergeleri ve diğer ortak hakkında daha fazla bilgi için yerleşik .NET Framework türleri, başvuru konuları aşağıdaki için bkz: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="45f69-106">For guidelines and additional information about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="45f69-107">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="45f69-107">In this section</span></span>

[<span data-ttu-id="45f69-108">Diziler</span><span class="sxs-lookup"><span data-stu-id="45f69-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="45f69-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="45f69-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="45f69-110">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="45f69-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="45f69-111">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="45f69-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="45f69-112">System.Xml Kullanımı</span><span class="sxs-lookup"><span data-stu-id="45f69-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="45f69-113">Eşitlik İşleçleri</span><span class="sxs-lookup"><span data-stu-id="45f69-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="45f69-114">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="45f69-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="45f69-115">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: Kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 Addison Wesley Professional ile Microsoft Windows geliştirme serisi bir parçası olarak yayımlandı.*</span><span class="sxs-lookup"><span data-stu-id="45f69-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="45f69-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45f69-116">See also</span></span>

- [<span data-ttu-id="45f69-117">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="45f69-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
