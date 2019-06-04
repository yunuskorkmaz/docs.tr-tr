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
ms.openlocfilehash: e18172ecf2d4300ae42cc42ecdb1783744cac105
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490423"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="bf9d7-102">GetCLRIdentityManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="bf9d7-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="bf9d7-103">Ortak dil çalışma zamanı (CLR) kimliklerini yönetmek için bir arabirimi için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="bf9d7-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="bf9d7-104">Bu işlev .NET Framework 4'te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="bf9d7-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf9d7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf9d7-105">Syntax</span></span>  
  
```  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf9d7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bf9d7-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="bf9d7-107">[in] A `REFIID` (bir arabirim tanımlayıcısı) almak için hangi arabirimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="bf9d7-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="bf9d7-108">Bu değer, IID_ICLRAssemblyIdentityManager ya da IID_ICLRHostBindingPolicyManager olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bf9d7-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="bf9d7-109">[out] Bir işaretçi ya da adresine bir [Iclrassemblyıdentitymanager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) veya [Iclrhostbindingpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="bf9d7-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf9d7-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf9d7-110">Remarks</span></span>  
 <span data-ttu-id="bf9d7-111">Çağrı [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) işaretçisi almak için işlevi `GetCLRIdentityManager` işlevi.</span><span class="sxs-lookup"><span data-stu-id="bf9d7-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf9d7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf9d7-112">Requirements</span></span>  
 <span data-ttu-id="bf9d7-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf9d7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf9d7-114">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bf9d7-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bf9d7-115">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="bf9d7-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="bf9d7-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf9d7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf9d7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf9d7-117">See also</span></span>

- [<span data-ttu-id="bf9d7-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="bf9d7-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
