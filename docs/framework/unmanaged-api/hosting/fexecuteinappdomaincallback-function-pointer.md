---
title: FExecuteInAppDomainCallback İşlev İşaretçisi
ms.date: 03/30/2017
api_name:
- FExecuteInAppDomainCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FExecuteInAppDomainCallback
helpviewer_keywords:
- FExecuteInAppDomainCallback function pointer [.NET Framework hosting]
ms.assetid: 2709f18f-3eee-497f-bc33-3ab7a485599b
topic_type:
- apiref
ms.openlocfilehash: 970468bc2f50144c62c6e3cbcf9c00c2027f7663
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138175"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="d72c4-102">FExecuteInAppDomainCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="d72c4-102">FExecuteInAppDomainCallback Function Pointer</span></span>
<span data-ttu-id="d72c4-103">Yönetilen kodu yürütmek için ortak dil çalışma zamanı (CLR) tarafından çağrılan bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="d72c4-103">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="d72c4-104">Bu işlev işaretçisi .NET Framework 4 ' te kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="d72c4-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d72c4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d72c4-105">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d72c4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d72c4-106">Parameters</span></span>  
 `cookie`  
 <span data-ttu-id="d72c4-107">'ndaki Yürütülebilecek yönetilen kodu içeren, bir veya daha fazla arayana ayrılan belleğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d72c4-107">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="d72c4-108">Bu belleğin ayrılması ve ömrü, çağıran tarafından denetlenir (yani, CLR).</span><span class="sxs-lookup"><span data-stu-id="d72c4-108">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="d72c4-109">Bu, CLR tarafından yönetilen yığın belleği değildir.</span><span class="sxs-lookup"><span data-stu-id="d72c4-109">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d72c4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d72c4-110">Requirements</span></span>  
 <span data-ttu-id="d72c4-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d72c4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d72c4-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d72c4-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d72c4-113">**Kitaplık:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="d72c4-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="d72c4-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d72c4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d72c4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d72c4-115">See also</span></span>

- [<span data-ttu-id="d72c4-116">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d72c4-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
