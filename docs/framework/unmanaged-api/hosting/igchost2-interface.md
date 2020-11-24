---
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
ms.openlocfilehash: 7529ecd215d74eb0eedbec8b90eba367ed20d56f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687749"
---
# <a name="igchost2-interface"></a><span data-ttu-id="2c3b7-102">IGCHost2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c3b7-102">IGCHost2 Interface</span></span>

<span data-ttu-id="2c3b7-103">Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c3b7-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c3b7-104">Yeni geliştirme için, bunun yerine [ICLRGCManager2](iclrgcmanager2-interface.md) arabirimini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="2c3b7-104">For new development, we recommend that you use the [ICLRGCManager2](iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c3b7-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2c3b7-105">Methods</span></span>  
  
|<span data-ttu-id="2c3b7-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2c3b7-106">Method</span></span>|<span data-ttu-id="2c3b7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c3b7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c3b7-108">SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c3b7-108">SetGCStartupLimitsEx Method</span></span>](igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="2c3b7-109">Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2c3b7-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="2c3b7-110">1. nesil ve kesim boyutlarını daha büyük olarak sunar `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="2c3b7-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c3b7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c3b7-111">Requirements</span></span>  

 <span data-ttu-id="2c3b7-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c3b7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c3b7-113">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="2c3b7-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="2c3b7-114">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2c3b7-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c3b7-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c3b7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3b7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c3b7-116">See also</span></span>

- [<span data-ttu-id="2c3b7-117">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2c3b7-117">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="2c3b7-118">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2c3b7-118">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="2c3b7-119">CorRuntimeHost Ortak Sınıfı</span><span class="sxs-lookup"><span data-stu-id="2c3b7-119">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
