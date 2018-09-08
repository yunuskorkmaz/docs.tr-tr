---
title: Kullanım yönergeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04e44a6b58fd334b6a23e113922b980f69de627b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44198653"
---
# <a name="usage-guidelines"></a><span data-ttu-id="f72d4-102">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f72d4-102">Usage guidelines</span></span>

<span data-ttu-id="f72d4-103">Bu bölümde, genel olarak erişilebilir API'leri genel türleri kullanma yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f72d4-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="f72d4-104">Bu yerleşik Framework türlerinin (örneğin, serileştirme öznitelikleri) ve aşırı yükleme işleçleri ortak doğrudan kullanımı ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="f72d4-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>
  
<span data-ttu-id="f72d4-105"><xref:System.IDisposable?displayProperty=nameWithType> Arabirimi bu bölümde kapsamında olmayan, ancak içinde ele alınmıştır [Dispose deseni](../../../docs/standard/design-guidelines/dispose-pattern.md) bölümü.</span><span class="sxs-lookup"><span data-stu-id="f72d4-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>

> [!NOTE]
> <span data-ttu-id="f72d4-106">Yönergeleri ve diğer ortak hakkında ek bilgi için yerleşik .NET Framework türleri, başvuru konuları aşağıdaki için bkz: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f72d4-106">For guidelines and additional information about about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f72d4-107">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="f72d4-107">In this section</span></span>

[<span data-ttu-id="f72d4-108">Diziler</span><span class="sxs-lookup"><span data-stu-id="f72d4-108">Arrays</span></span>](arrays.md)  
[<span data-ttu-id="f72d4-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f72d4-109">Attributes</span></span>](attributes.md)  
[<span data-ttu-id="f72d4-110">Koleksiyonlar</span><span class="sxs-lookup"><span data-stu-id="f72d4-110">Collections</span></span>](guidelines-for-collections.md)  
[<span data-ttu-id="f72d4-111">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="f72d4-111">Serialization</span></span>](serialization.md)  
[<span data-ttu-id="f72d4-112">System.Xml Kullanımı</span><span class="sxs-lookup"><span data-stu-id="f72d4-112">System.Xml Usage</span></span>](system-xml-usage.md)  
[<span data-ttu-id="f72d4-113">Eşitlik İşleçleri</span><span class="sxs-lookup"><span data-stu-id="f72d4-113">Equality Operators</span></span>](equality-operators.md)  

<span data-ttu-id="f72d4-114">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="f72d4-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="f72d4-115">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="f72d4-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f72d4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f72d4-116">See also</span></span>

- [<span data-ttu-id="f72d4-117">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="f72d4-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
