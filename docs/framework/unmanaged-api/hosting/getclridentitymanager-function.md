---
description: ': GetCLRIdentityManager Işlevi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 483cf0499fa162da4c89e350198a5609f9f1bab6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785373"
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="e880d-103">GetCLRIdentityManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="e880d-103">GetCLRIdentityManager Function</span></span>

<span data-ttu-id="e880d-104">Ortak dil çalışma zamanının (CLR) kimlikleri yönetmesine izin veren bir arabirime yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="e880d-104">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="e880d-105">Bu işlev .NET Framework 4 ' te kullanım dışıdır.</span><span class="sxs-lookup"><span data-stu-id="e880d-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e880d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e880d-106">Syntax</span></span>  
  
```cpp  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e880d-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e880d-107">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="e880d-108">'ndaki `REFIID` Hangi arabirimin alınacağını belirten bir (bir arabirim tanımlayıcısı).</span><span class="sxs-lookup"><span data-stu-id="e880d-108">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="e880d-109">Bu değer IID_ICLRAssemblyIdentityManager ya da IID_ICLRHostBindingPolicyManager olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e880d-109">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="e880d-110">dışı Bir [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) veya [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e880d-110">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e880d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e880d-111">Remarks</span></span>  

 <span data-ttu-id="e880d-112">İşleve bir işaretçi almak için [GetRealProcAddress](getrealprocaddress-function.md) işlevini çağırın `GetCLRIdentityManager` .</span><span class="sxs-lookup"><span data-stu-id="e880d-112">Call the [GetRealProcAddress](getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e880d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e880d-113">Requirements</span></span>  

 <span data-ttu-id="e880d-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e880d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e880d-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e880d-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e880d-116">**Kitaplık:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="e880d-116">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="e880d-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e880d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e880d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e880d-118">See also</span></span>

- [<span data-ttu-id="e880d-119">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e880d-119">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
