---
title: CreateApplicationContext İşlevi
ms.date: 03/30/2017
api_name:
- CreateApplicationContext
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateApplicationContext
helpviewer_keywords:
- CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9853f974230ee755a33bc46ca6ba3e086051b236
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778472"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="e074e-102">CreateApplicationContext İşlevi</span><span class="sxs-lookup"><span data-stu-id="e074e-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="e074e-103">Bu işlev .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="e074e-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e074e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e074e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="e074e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e074e-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="e074e-106">[in] Bir kolay ad için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e074e-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="e074e-107">[out] Uygulama bağlamı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e074e-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e074e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e074e-108">Requirements</span></span>  
 <span data-ttu-id="e074e-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e074e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e074e-110">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e074e-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e074e-111">**Kitaplığı:** Bir kaynak olarak Fusion.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e074e-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="e074e-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e074e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e074e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e074e-113">See also</span></span>

- [<span data-ttu-id="e074e-114">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e074e-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
- [<span data-ttu-id="e074e-115">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="e074e-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
- [<span data-ttu-id="e074e-116">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="e074e-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
