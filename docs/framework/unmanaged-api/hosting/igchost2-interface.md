---
description: 'Daha fazla bilgi edinin: IGCHost2 Interface'
title: IGCHost2 Arabirimi
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
ms.openlocfilehash: e32a4894fcff3600c9385f0f559443e23b2bc307
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709327"
---
# <a name="igchost2-interface"></a><span data-ttu-id="c25a7-103">IGCHost2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c25a7-103">IGCHost2 Interface</span></span>

<span data-ttu-id="c25a7-104">Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c25a7-104">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c25a7-105">Yeni geliştirme için, bunun yerine [ICLRGCManager2](iclrgcmanager2-interface.md) arabirimini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="c25a7-105">For new development, we recommend that you use the [ICLRGCManager2](iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c25a7-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c25a7-106">Methods</span></span>  
  
|<span data-ttu-id="c25a7-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c25a7-107">Method</span></span>|<span data-ttu-id="c25a7-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c25a7-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c25a7-109">SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c25a7-109">SetGCStartupLimitsEx Method</span></span>](igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="c25a7-110">Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c25a7-110">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="c25a7-111">1. nesil ve kesim boyutlarını daha büyük olarak sunar `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="c25a7-111">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c25a7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c25a7-112">Requirements</span></span>  

 <span data-ttu-id="c25a7-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c25a7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c25a7-114">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="c25a7-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="c25a7-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c25a7-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c25a7-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c25a7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c25a7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c25a7-117">See also</span></span>

- [<span data-ttu-id="c25a7-118">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c25a7-118">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="c25a7-119">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c25a7-119">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="c25a7-120">CorRuntimeHost Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="c25a7-120">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
