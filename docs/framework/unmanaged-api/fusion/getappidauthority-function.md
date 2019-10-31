---
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
ms.openlocfilehash: 22a6af61251942f068676daaee2bdfa868e32a97
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134551"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="10927-102">GetAppIdAuthority İşlevi</span><span class="sxs-lookup"><span data-stu-id="10927-102">GetAppIdAuthority Function</span></span>
<span data-ttu-id="10927-103">Uygulama kimlikleri ve başvuruları için anahtarları yöneten bir [ıappidaduthority](iappidauthority-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="10927-103">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10927-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10927-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="10927-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="10927-105">Parameters</span></span>  
 `ppIAppIdAuthority`  
 <span data-ttu-id="10927-106">dışı Döndürülen `IAppIdAuthority` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="10927-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10927-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10927-107">Requirements</span></span>  
 <span data-ttu-id="10927-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10927-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10927-109">**Üst bilgi:** Yalıtım. h</span><span class="sxs-lookup"><span data-stu-id="10927-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="10927-110">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10927-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10927-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10927-111">See also</span></span>

- [<span data-ttu-id="10927-112">IAppIdAuthority Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10927-112">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)
- [<span data-ttu-id="10927-113">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="10927-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
