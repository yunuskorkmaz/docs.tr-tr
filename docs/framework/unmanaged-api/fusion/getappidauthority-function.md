---
description: 'Daha fazla bilgi edinin: Getappidaduthority Işlevi'
title: GetAppIdAuthority İşlevi
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
ms.openlocfilehash: a0c2a7b754c2b014b189f96fd3c27347571cc0d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761076"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="1bb7b-103">GetAppIdAuthority İşlevi</span><span class="sxs-lookup"><span data-stu-id="1bb7b-103">GetAppIdAuthority Function</span></span>

<span data-ttu-id="1bb7b-104">Uygulama kimlikleri ve başvuruları için anahtarları yöneten bir [ıappidaduthority](iappidauthority-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="1bb7b-104">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bb7b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1bb7b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bb7b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1bb7b-106">Parameters</span></span>  

 `ppIAppIdAuthority`  
 <span data-ttu-id="1bb7b-107">dışı Döndürülen `IAppIdAuthority` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1bb7b-107">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bb7b-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1bb7b-108">Requirements</span></span>  

 <span data-ttu-id="1bb7b-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bb7b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bb7b-110">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="1bb7b-110">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="1bb7b-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bb7b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bb7b-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bb7b-112">See also</span></span>

- [<span data-ttu-id="1bb7b-113">IAppIdAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1bb7b-113">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)
- [<span data-ttu-id="1bb7b-114">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1bb7b-114">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
