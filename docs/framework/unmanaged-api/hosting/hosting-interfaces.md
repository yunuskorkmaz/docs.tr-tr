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
ms.openlocfilehash: 9a32f68566fc6fe53020c4e9b13482355b62ed21
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485960"
---
# <a name="hosting-interfaces"></a><span data-ttu-id="8b1da-102">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8b1da-102">Hosting Interfaces</span></span>
<span data-ttu-id="8b1da-103">Bu bölümde, yönetilmeyen arabirimler açıklanmaktadır. konaklar, ortak dil çalışma zamanı (CLR) uygulamalarıyla tümleştirmeleri için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b1da-103">This section describes the interfaces that unmanaged hosts can use to integrate the common language runtime (CLR) into their applications.</span></span>  
  
 <span data-ttu-id="8b1da-104">.NET Framework sürüm 2.0 barındırma arabirimleri, .NET Framework sürüm 1.0 ve 1.1 arabirimler yerini alır.</span><span class="sxs-lookup"><span data-stu-id="8b1da-104">The .NET Framework version 2.0 hosting interfaces supersede the .NET Framework version 1.0 and 1.1 interfaces.</span></span> <span data-ttu-id="8b1da-105">Arabirimleri iki kümesi arasında önemli farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="8b1da-105">There are significant differences between the two sets of interfaces.</span></span> <span data-ttu-id="8b1da-106">Bunları karıştırma beklenmeyen davranışlara neden olabilir ve önerilmez.</span><span class="sxs-lookup"><span data-stu-id="8b1da-106">Mixing them could cause unexpected behavior and is not recommended.</span></span>  
  
 <span data-ttu-id="8b1da-107">.NET Framework 3.0 ve 3.5 sürümlerini .NET Framework sürüm 2.0 barındırma arabirimleri kullanır ve tüm barındırma özellikleri tanıtan değil.</span><span class="sxs-lookup"><span data-stu-id="8b1da-107">The .NET Framework versions 3.0 and 3.5 use the .NET Framework version 2.0 hosting interfaces, and do not introduce any hosting features.</span></span>  
  
 <span data-ttu-id="8b1da-108">[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Barındırma arabirimleri, .NET Framework 2.0 arabirimleri'ı geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="8b1da-108">The [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] hosting interfaces supersede the .NET Framework 2.0 interfaces.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="8b1da-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8b1da-109">In This Section</span></span>  
 [<span data-ttu-id="8b1da-110">Kullanım Dışı CLR Barındırma Arabirimleri ve Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="8b1da-110">Deprecated CLR Hosting Interfaces and Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 <span data-ttu-id="8b1da-111">.NET Framework sürüm 1.0 ve 1.1 sunulan barındırma arabirimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b1da-111">Describes the hosting interfaces introduced in the .NET Framework versions 1.0 and 1.1.</span></span>  
  
 [<span data-ttu-id="8b1da-112">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8b1da-112">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 <span data-ttu-id="8b1da-113">.NET Framework 2.0 sürümünde sunulan barındırma arabirimleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8b1da-113">Describes the hosting interfaces introduced in the .NET Framework version 2.0.</span></span>  
  
 [<span data-ttu-id="8b1da-114">.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8b1da-114">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 <span data-ttu-id="8b1da-115">Sürümünde barındırma arabirimleri açıklar [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8b1da-115">Describes the hosting interfaces introduced in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8b1da-116">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8b1da-116">Related Sections</span></span>  
 [<span data-ttu-id="8b1da-117">Barındırma Coclassları</span><span class="sxs-lookup"><span data-stu-id="8b1da-117">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="8b1da-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="8b1da-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="8b1da-119">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="8b1da-119">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
  
 [<span data-ttu-id="8b1da-120">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="8b1da-120">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
  
 [<span data-ttu-id="8b1da-121">Barındırma</span><span class="sxs-lookup"><span data-stu-id="8b1da-121">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
  
 [<span data-ttu-id="8b1da-122">Çalışma zamanı ana bilgisayarları</span><span class="sxs-lookup"><span data-stu-id="8b1da-122">Runtime Hosts</span></span>](https://msdn.microsoft.com/library/99d9246a-b994-4fe5-985c-8588d1d59998)
