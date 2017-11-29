---
title: "GetCLRIdentityManager İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCLRIdentityManager
api_location: mscoree.dll
api_type: COM
f1_keywords: GetCLRIdentityManager
helpviewer_keywords: GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ddc0395b6fd659ecd6a26a3132fccc65bbb961fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="d598d-102">GetCLRIdentityManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="d598d-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="d598d-103">Ortak dil çalışma zamanı (CLR) kimlikleri yönetmek için bir arabirimi için bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="d598d-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="d598d-104">Bu işlev kaldırılmamıştır [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d598d-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d598d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d598d-105">Syntax</span></span>  
  
```  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d598d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d598d-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="d598d-107">[in] A `REFIID` (bir arabirim tanımlayıcısı) almak için hangi arabirimi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d598d-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="d598d-108">Bu değer, IID_ICLRAssemblyIdentityManager veya IID_ICLRHostBindingPolicyManager olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d598d-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="d598d-109">[out] Ya da adresini gösteren bir işaretçi bir [Iclrassemblyıdentitymanager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) veya bir [Iclrhostbindingpolicymanager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d598d-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d598d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d598d-110">Remarks</span></span>  
 <span data-ttu-id="d598d-111">Çağrı [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) gösteren bir işaretçi almak için işlevini `GetCLRIdentityManager` işlevi.</span><span class="sxs-lookup"><span data-stu-id="d598d-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d598d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d598d-112">Requirements</span></span>  
 <span data-ttu-id="d598d-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d598d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d598d-114">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d598d-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d598d-115">**Kitaplığı:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="d598d-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="d598d-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d598d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d598d-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d598d-117">See Also</span></span>  
 [<span data-ttu-id="d598d-118">Kullanım dışı CLR barındırma işlevleri</span><span class="sxs-lookup"><span data-stu-id="d598d-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
