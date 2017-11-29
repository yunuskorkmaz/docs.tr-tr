---
title: "Kullanım yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: class library design guidelines [.NET Framework], usage guidelines
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df0d1c5f8bff9d4cb546378f281a44c696246553
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="usage-guidelines"></a><span data-ttu-id="6a4fc-102">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6a4fc-102">Usage Guidelines</span></span>
<span data-ttu-id="6a4fc-103">Bu bölümde, genel olarak erişilebilir API'leri genel türleri kullanma için yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="6a4fc-103">This section contains guidelines for using common types in publicly accessible APIs.</span></span> <span data-ttu-id="6a4fc-104">Yerleşik Framework türleri (örneğin, serileştirme özniteliklerini) ve ortak İşleç aşırı yüklemesi doğrudan kullanımı ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="6a4fc-104">It deals with direct usage of built-in Framework types (e.g., serialization attributes) and overloading common operators.</span></span>  
  
 <span data-ttu-id="6a4fc-105"><xref:System.IDisposable?displayProperty=nameWithType> Arabirimi bu bölümde kapsamında değildir, ancak içinde ele alınmıştır [Dispose düzeni](../../../docs/standard/design-guidelines/dispose-pattern.md) bölümü.</span><span class="sxs-lookup"><span data-stu-id="6a4fc-105">The <xref:System.IDisposable?displayProperty=nameWithType> interface is not covered in this section, but is discussed in the [Dispose Pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) section.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a4fc-106">Yerleşik .NET Framework türleri, yönergeleri ve diğer ortak hakkında hakkında ek bilgi için aşağıdaki başvuru konularına bakın: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType> , <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6a4fc-106">For guidelines and additional information about about other common, built-in .NET Framework types, see the reference topics for the following: <xref:System.DateTime?displayProperty=nameWithType>, <xref:System.DateTimeOffset?displayProperty=nameWithType>, <xref:System.ICloneable?displayProperty=nameWithType>, <xref:System.IComparable%601?displayProperty=nameWithType>, <xref:System.IEquatable%601?displayProperty=nameWithType>, <xref:System.Nullable%601?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6a4fc-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6a4fc-107">In This Section</span></span>  
 [<span data-ttu-id="6a4fc-108">Diziler</span><span class="sxs-lookup"><span data-stu-id="6a4fc-108">Arrays</span></span>](../../../docs/standard/design-guidelines/arrays.md)  
 [<span data-ttu-id="6a4fc-109">Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="6a4fc-109">Attributes</span></span>](../../../docs/standard/design-guidelines/attributes.md)  
 [<span data-ttu-id="6a4fc-110">Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="6a4fc-110">Collections</span></span>](/cpp/mfc/collections)  
 [<span data-ttu-id="6a4fc-111">Seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="6a4fc-111">Serialization</span></span>](../../../docs/standard/design-guidelines/serialization.md)  
 [<span data-ttu-id="6a4fc-112">System.Xml kullanımı</span><span class="sxs-lookup"><span data-stu-id="6a4fc-112">System.Xml Usage</span></span>](../../../docs/standard/design-guidelines/system-xml-usage.md)  
 [<span data-ttu-id="6a4fc-113">Eşitlik işleçleri</span><span class="sxs-lookup"><span data-stu-id="6a4fc-113">Equality Operators</span></span>](../../../docs/standard/design-guidelines/equality-operators.md)  
 <span data-ttu-id="6a4fc-114">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="6a4fc-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6a4fc-115">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="6a4fc-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a4fc-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6a4fc-116">See Also</span></span>  
 [<span data-ttu-id="6a4fc-117">Framework tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6a4fc-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
