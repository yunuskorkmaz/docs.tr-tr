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
ms.openlocfilehash: 57f771d933e896677dfc0bd5d9dac58da2af22c8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617262"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="24760-102">GetCLRIdentityManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="24760-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="24760-103">Ortak dil çalışma zamanının (CLR) kimlikleri yönetmesine izin veren bir arabirime yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="24760-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="24760-104">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="24760-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24760-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="24760-105">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24760-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24760-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="24760-107">'ndaki `REFIID`Hangi arabirimin alınacağını belirten bir (bir arabirim tanımlayıcısı).</span><span class="sxs-lookup"><span data-stu-id="24760-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="24760-108">Bu değer IID_ICLRAssemblyIdentityManager ya da IID_ICLRHostBindingPolicyManager olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="24760-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="24760-109">dışı Bir [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) veya [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="24760-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24760-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24760-110">Remarks</span></span>  
 <span data-ttu-id="24760-111">İşleve bir işaretçi almak için [GetRealProcAddress](getrealprocaddress-function.md) işlevini çağırın `GetCLRIdentityManager` .</span><span class="sxs-lookup"><span data-stu-id="24760-111">Call the [GetRealProcAddress](getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24760-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24760-112">Requirements</span></span>  
 <span data-ttu-id="24760-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24760-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24760-114">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="24760-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="24760-115">**Kitaplık:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="24760-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="24760-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24760-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24760-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24760-117">See also</span></span>

- [<span data-ttu-id="24760-118">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="24760-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
