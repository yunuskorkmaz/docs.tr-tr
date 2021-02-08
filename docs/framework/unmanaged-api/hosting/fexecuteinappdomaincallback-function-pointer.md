---
description: 'Daha fazla bilgi edinin: FExecuteInAppDomainCallback Işlev Işaretçisi'
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
ms.openlocfilehash: 97c7fe14a3eafd6f4626d8729be3b45ad5502f1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785403"
---
# <a name="fexecuteinappdomaincallback-function-pointer"></a><span data-ttu-id="cc7d5-103">FExecuteInAppDomainCallback İşlev İşaretçisi</span><span class="sxs-lookup"><span data-stu-id="cc7d5-103">FExecuteInAppDomainCallback Function Pointer</span></span>

<span data-ttu-id="cc7d5-104">Yönetilen kodu yürütmek için ortak dil çalışma zamanı (CLR) tarafından çağrılan bir işleve işaret eder.</span><span class="sxs-lookup"><span data-stu-id="cc7d5-104">Points to a function that is called by the common language runtime (CLR) to execute managed code.</span></span>  
  
 <span data-ttu-id="cc7d5-105">Bu işlev işaretçisi .NET Framework 4 ' te kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="cc7d5-105">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc7d5-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc7d5-106">Syntax</span></span>  
  
```cpp  
typedef HRESULT (__stdcall *FExecuteInAppDomainCallback) (  
    [in] void  *cookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc7d5-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cc7d5-107">Parameters</span></span>  

 `cookie`  
 <span data-ttu-id="cc7d5-108">'ndaki Yürütülebilecek yönetilen kodu içeren, bir veya daha fazla arayana ayrılan belleğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cc7d5-108">[in] A pointer to opaque caller-allocated memory that contains the managed code to be executed.</span></span>  
  
 <span data-ttu-id="cc7d5-109">Bu belleğin ayrılması ve ömrü, çağıran tarafından denetlenir (yani, CLR).</span><span class="sxs-lookup"><span data-stu-id="cc7d5-109">The allocation and lifetime of this memory are controlled by the caller (that is, the CLR).</span></span> <span data-ttu-id="cc7d5-110">Bu, CLR tarafından yönetilen yığın belleği değildir.</span><span class="sxs-lookup"><span data-stu-id="cc7d5-110">This is not CLR managed-heap memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc7d5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc7d5-111">Requirements</span></span>  

 <span data-ttu-id="cc7d5-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc7d5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc7d5-113">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cc7d5-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc7d5-114">**Kitaplık:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="cc7d5-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="cc7d5-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc7d5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc7d5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc7d5-116">See also</span></span>

- [<span data-ttu-id="cc7d5-117">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="cc7d5-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
