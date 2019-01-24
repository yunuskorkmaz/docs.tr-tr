---
title: GetCLRIdentityManager İşlevi
ms.date: 03/30/2017
api_name:
- GetCLRIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetCLRIdentityManager
helpviewer_keywords:
- GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f40100be3ab05c0c8e8a55d48494569424e88371
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637274"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="80833-102">GetCLRIdentityManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="80833-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="80833-103">Ortak dil çalışma zamanı (CLR) kimliklerini yönetmek için bir arabirimi için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="80833-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="80833-104">Bu işlev içinde kullanımdan kalkmış [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="80833-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80833-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80833-105">Syntax</span></span>  
  
```  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80833-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80833-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="80833-107">[in] A `REFIID` (bir arabirim tanımlayıcısı) almak için hangi arabirimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="80833-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="80833-108">Bu değer, IID_ICLRAssemblyIdentityManager ya da IID_ICLRHostBindingPolicyManager olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="80833-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="80833-109">[out] Bir işaretçi ya da adresine bir [Iclrassemblyıdentitymanager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) veya [Iclrhostbindingpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="80833-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80833-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80833-110">Remarks</span></span>  
 <span data-ttu-id="80833-111">Çağrı [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) işaretçisi almak için işlevi `GetCLRIdentityManager` işlevi.</span><span class="sxs-lookup"><span data-stu-id="80833-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80833-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80833-112">Requirements</span></span>  
 <span data-ttu-id="80833-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80833-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80833-114">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="80833-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80833-115">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="80833-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="80833-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80833-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80833-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80833-117">See also</span></span>
- [<span data-ttu-id="80833-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="80833-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
