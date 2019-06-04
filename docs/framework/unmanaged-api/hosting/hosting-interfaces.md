---
title: Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting]
- hosting interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], hosting
ms.assetid: cc64cb05-38da-418e-815a-daac8e8e26e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46ff6032f2cdbd4a5f294198fe3bf71862c67528
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490253"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="1041d-102">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1041d-102">Hosting Interfaces</span></span>
<span data-ttu-id="1041d-103">Bu bölümde, yönetilmeyen arabirimler açıklanmaktadır. konaklar, ortak dil çalışma zamanı (CLR) uygulamalarıyla tümleştirmeleri için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1041d-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="1041d-104">.NET Framework sürüm 2.0 barındırma arabirimleri, .NET Framework sürüm 1.0 ve 1.1 arabirimler yerini alır.</span><span class="sxs-lookup"><span data-stu-id="1041d-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="1041d-105">Arabirimleri iki kümesi arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="1041d-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="1041d-106">Bunları karıştırma beklenmeyen davranışlara neden olabilir ve önerilmez.</span><span class="sxs-lookup"><span data-stu-id="1041d-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="1041d-107">.NET Framework 3.0 ve 3.5 sürümlerini .NET Framework sürüm 2.0 barındırma arabirimleri kullanır ve tüm barındırma özellikleri tanıtan değil.</span><span class="sxs-lookup"><span data-stu-id="1041d-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="1041d-108">.NET Framework 4 barındırma arabirimleri, .NET Framework 2.0 arabirimleri yerini alır.</span><span class="sxs-lookup"><span data-stu-id="1041d-108">The .NET Framework 4 hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="1041d-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1041d-109">In This Section</span></span>  
 [<span data-ttu-id="1041d-110">Kullanım Dışı CLR Barındırma Arabirimleri ve Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="1041d-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="1041d-111">.NET Framework sürüm 1.0 ve 1.1 sunulan barındırma arabirimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="1041d-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="1041d-112">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1041d-112">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="1041d-113">.NET Framework 2.0 sürümünde sunulan barındırma arabirimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="1041d-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="1041d-114">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1041d-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="1041d-115">.NET Framework 4'te tanıtılan barındırma arabirimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="1041d-115">Describes the hosting interfaces introduced in the .NET Framework 4.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1041d-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="1041d-116">Related Sections</span></span>  
 [<span data-ttu-id="1041d-117">Barındırma Coclassları</span><span class="sxs-lookup"><span data-stu-id="1041d-117">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="1041d-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1041d-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="1041d-119">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="1041d-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
  
 [<span data-ttu-id="1041d-120">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="1041d-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
  
 [<span data-ttu-id="1041d-121">Barındırma</span><span class="sxs-lookup"><span data-stu-id="1041d-121">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
  
 <span data-ttu-id="1041d-122">[Çalışma zamanı ana bilgisayarları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1041d-122">[Runtime Hosts](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))</span></span>
