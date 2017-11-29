---
title: "Barındırma Arabirimleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
caps.latest.revision: "23"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a3cad92c204fa10f72d7a9a61460f1234206cb39
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="hosting-interfaces"></a><span data-ttu-id="e0b33-102">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e0b33-102">Hosting Interfaces</span></span>
<span data-ttu-id="e0b33-103">Bu bölümde yönetilmeyen arabirimler açıklanmaktadır konakları ortak dil çalışma zamanı (CLR) uygulamalarına tümleştirmeleri için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0b33-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="e0b33-104">.NET Framework sürüm 2.0 barındırma arabirimleri .NET Framework sürüm 1.0 ve 1.1 arabirimleri yerini alır.</span><span class="sxs-lookup"><span data-stu-id="e0b33-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="e0b33-105">Arabirimlerin iki küme arasındaki önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="e0b33-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="e0b33-106">Bunları karıştırma beklenmeyen davranışlara neden olabilir ve önerilmez.</span><span class="sxs-lookup"><span data-stu-id="e0b33-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="e0b33-107">.NET Framework sürüm 3.0 ve 3.5, .NET Framework sürüm 2.0 barındırma arabirimleri kullanın ve barındırma hiçbir özellikleri tanıtır değil.</span><span class="sxs-lookup"><span data-stu-id="e0b33-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="e0b33-108">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Barındırma arabirimleri .NET Framework 2.0 arabirimleri yerini alır.</span><span class="sxs-lookup"><span data-stu-id="e0b33-108">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="e0b33-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e0b33-109">In This Section</span></span>  
 [<span data-ttu-id="e0b33-110">Kullanım dışı CLR barındırma arabirimleri ve coclass'ları</span><span class="sxs-lookup"><span data-stu-id="e0b33-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="e0b33-111">.NET Framework sürüm 1.0 ve 1.1 sunulan barındırma arabirimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e0b33-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="e0b33-112">CLR barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e0b33-112">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="e0b33-113">.NET Framework 2.0 sürümünde sunulan barındırma arabirimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="e0b33-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="e0b33-114">.NET Framework 4 ve 4.5 eklenen CLR barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e0b33-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="e0b33-115">Sürümünde sunulan barındırma arabirimleri açıklayan [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e0b33-115">Describes the hosting interfaces introduced in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e0b33-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e0b33-116">Related Sections</span></span>  
 [<span data-ttu-id="e0b33-117">Barındırma coclass'ları</span><span class="sxs-lookup"><span data-stu-id="e0b33-117">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="e0b33-118">Kullanım dışı CLR barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="e0b33-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="e0b33-119">Barındırma numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="e0b33-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
  
 [<span data-ttu-id="e0b33-120">Barındırma yapıları</span><span class="sxs-lookup"><span data-stu-id="e0b33-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
  
 [<span data-ttu-id="e0b33-121">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e0b33-121">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
  
 [<span data-ttu-id="e0b33-122">Çalışma zamanı ana bilgisayarlar</span><span class="sxs-lookup"><span data-stu-id="e0b33-122">Runtime Hosts</span></span>](http://msdn.microsoft.com/en-us/99d9246a-b994-4fe5-985c-8588d1d59998)
