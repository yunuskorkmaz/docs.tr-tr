---
description: 'Daha fazla bilgi edinin: barındırma arabirimleri'
title: Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
ms.openlocfilehash: 596de1e74fc9c80e5f8b63f40c91a9ef29abcc6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785191"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="15a5f-103">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="15a5f-103">Hosting Interfaces</span></span>

<span data-ttu-id="15a5f-104">Bu bölümde, yönetilmeyen ana bilgisayarların ortak dil çalışma zamanını (CLR) uygulamalarıyla tümleştirmeleri için kullanabileceği arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15a5f-104">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="15a5f-105">.NET Framework 2,0 sürümü barındırma arabirimleri, .NET Framework sürüm 1,0 ve 1,1 arabirimlerini yerine alır.</span><span class="sxs-lookup"><span data-stu-id="15a5f-105">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="15a5f-106">İki arabirim kümesi arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="15a5f-106">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="15a5f-107">Bunları karıştırmak beklenmeyen davranışlara neden olabilir ve önerilmez.</span><span class="sxs-lookup"><span data-stu-id="15a5f-107">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="15a5f-108">3,0 ve 3,5 .NET Framework sürümleri, .NET Framework sürüm 2,0 barındırma arabirimlerini kullanır ve herhangi bir barındırma özelliği sunmaz.</span><span class="sxs-lookup"><span data-stu-id="15a5f-108">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="15a5f-109">.NET Framework 4 barındırma arabirimleri, .NET Framework 2,0 arabirimlerinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="15a5f-109">The .NET Framework 4 hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="15a5f-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="15a5f-110">In This Section</span></span>  

 [<span data-ttu-id="15a5f-111">Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="15a5f-111">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="15a5f-112">1,0 ve 1,1 .NET Framework sürümlerinde tanıtılan barındırma arabirimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="15a5f-112">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="15a5f-113">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="15a5f-113">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)  
 <span data-ttu-id="15a5f-114">.NET Framework sürüm 2,0 ' de tanıtılan barındırma arabirimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="15a5f-114">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="15a5f-115">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="15a5f-115">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="15a5f-116">.NET Framework 4 ' te tanıtılan barındırma arabirimlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="15a5f-116">Describes the hosting interfaces introduced in the .NET Framework 4.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="15a5f-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="15a5f-117">Related Sections</span></span>  

 [<span data-ttu-id="15a5f-118">Barındırma Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="15a5f-118">Hosting Coclasses</span></span>](hosting-coclasses.md)  
  
 [<span data-ttu-id="15a5f-119">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="15a5f-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="15a5f-120">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="15a5f-120">Hosting Enumerations</span></span>](hosting-enumerations.md)  
  
 [<span data-ttu-id="15a5f-121">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="15a5f-121">Hosting Structures</span></span>](hosting-structures.md)  
  
 [<span data-ttu-id="15a5f-122">Hosting</span><span class="sxs-lookup"><span data-stu-id="15a5f-122">Hosting</span></span>](index.md)  
  
 <span data-ttu-id="15a5f-123">[Çalışma zamanı Konakları](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="15a5f-123">[Runtime Hosts](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
