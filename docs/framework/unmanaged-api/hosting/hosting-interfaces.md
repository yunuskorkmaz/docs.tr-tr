---
title: Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
ms.openlocfilehash: d1668f52ff305ec36fb520c7828c822537da0d02
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616105"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="f730a-102">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f730a-102">Hosting Interfaces</span></span>
<span data-ttu-id="f730a-103">Bu bölümde, yönetilmeyen ana bilgisayarların ortak dil çalışma zamanını (CLR) uygulamalarıyla tümleştirmeleri için kullanabileceği arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f730a-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="f730a-104">.NET Framework 2,0 sürümü barındırma arabirimleri, .NET Framework sürüm 1,0 ve 1,1 arabirimlerini yerine alır.</span><span class="sxs-lookup"><span data-stu-id="f730a-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="f730a-105">İki arabirim kümesi arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="f730a-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="f730a-106">Bunları karıştırmak beklenmeyen davranışlara neden olabilir ve önerilmez.</span><span class="sxs-lookup"><span data-stu-id="f730a-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="f730a-107">3,0 ve 3,5 .NET Framework sürümleri, .NET Framework sürüm 2,0 barındırma arabirimlerini kullanır ve herhangi bir barındırma özelliği sunmaz.</span><span class="sxs-lookup"><span data-stu-id="f730a-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="f730a-108">.NET Framework 4 barındırma arabirimleri, .NET Framework 2,0 arabirimlerinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="f730a-108">The .NET Framework 4 hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="f730a-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f730a-109">In This Section</span></span>  
 [<span data-ttu-id="f730a-110">Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="f730a-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="f730a-111">1,0 ve 1,1 .NET Framework sürümlerinde tanıtılan barındırma arabirimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f730a-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="f730a-112">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f730a-112">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="f730a-113">.NET Framework sürüm 2,0 ' de tanıtılan barındırma arabirimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f730a-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="f730a-114">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f730a-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="f730a-115">.NET Framework 4 ' te tanıtılan barındırma arabirimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="f730a-115">Describes the hosting interfaces introduced in the .NET Framework 4.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f730a-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f730a-116">Related Sections</span></span>  
 [<span data-ttu-id="f730a-117">Barındırma Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="f730a-117">Hosting Coclasses</span></span>](hosting-coclasses.md)  
  
 [<span data-ttu-id="f730a-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="f730a-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="f730a-119">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f730a-119">Hosting Enumerations</span></span>](hosting-enumerations.md)  
  
 [<span data-ttu-id="f730a-120">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="f730a-120">Hosting Structures</span></span>](hosting-structures.md)  
  
 [<span data-ttu-id="f730a-121">Barındırma</span><span class="sxs-lookup"><span data-stu-id="f730a-121">Hosting</span></span>](index.md)  
  
 <span data-ttu-id="f730a-122">[Çalışma zamanı Konakları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f730a-122">[Runtime Hosts](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
