---
title: Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
ms.openlocfilehash: f82301da1813b8d50deebf4452d8c07809c186c5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721809"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="de6e3-102">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="de6e3-102">Hosting Interfaces</span></span>

<span data-ttu-id="de6e3-103">Bu bölümde, yönetilmeyen ana bilgisayarların ortak dil çalışma zamanını (CLR) uygulamalarıyla tümleştirmeleri için kullanabileceği arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="de6e3-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="de6e3-104">.NET Framework 2,0 sürümü barındırma arabirimleri, .NET Framework sürüm 1,0 ve 1,1 arabirimlerini yerine alır.</span><span class="sxs-lookup"><span data-stu-id="de6e3-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="de6e3-105">İki arabirim kümesi arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="de6e3-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="de6e3-106">Bunları karıştırmak beklenmeyen davranışlara neden olabilir ve önerilmez.</span><span class="sxs-lookup"><span data-stu-id="de6e3-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="de6e3-107">3,0 ve 3,5 .NET Framework sürümleri, .NET Framework sürüm 2,0 barındırma arabirimlerini kullanır ve herhangi bir barındırma özelliği sunmaz.</span><span class="sxs-lookup"><span data-stu-id="de6e3-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="de6e3-108">.NET Framework 4 barındırma arabirimleri, .NET Framework 2,0 arabirimlerinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="de6e3-108">The .NET Framework 4 hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="de6e3-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="de6e3-109">In This Section</span></span>  

 [<span data-ttu-id="de6e3-110">Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="de6e3-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="de6e3-111">1,0 ve 1,1 .NET Framework sürümlerinde tanıtılan barındırma arabirimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="de6e3-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="de6e3-112">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="de6e3-112">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="de6e3-113">.NET Framework sürüm 2,0 ' de tanıtılan barındırma arabirimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="de6e3-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="de6e3-114">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="de6e3-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="de6e3-115">.NET Framework 4 ' te tanıtılan barındırma arabirimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="de6e3-115">Describes the hosting interfaces introduced in the .NET Framework 4.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="de6e3-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="de6e3-116">Related Sections</span></span>  

 [<span data-ttu-id="de6e3-117">Barındırma Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="de6e3-117">Hosting Coclasses</span></span>](hosting-coclasses.md)  
  
 [<span data-ttu-id="de6e3-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="de6e3-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="de6e3-119">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="de6e3-119">Hosting Enumerations</span></span>](hosting-enumerations.md)  
  
 [<span data-ttu-id="de6e3-120">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="de6e3-120">Hosting Structures</span></span>](hosting-structures.md)  
  
 [<span data-ttu-id="de6e3-121">Hosting</span><span class="sxs-lookup"><span data-stu-id="de6e3-121">Hosting</span></span>](index.md)  
  
 <span data-ttu-id="de6e3-122">[Çalışma zamanı Konakları](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="de6e3-122">[Runtime Hosts](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
