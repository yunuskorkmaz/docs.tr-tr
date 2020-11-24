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
ms.openlocfilehash: 9418be85f5b72bac8eed7f5ea4af4fc42439b01f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683242"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="09b81-102">CreateApplicationContext İşlevi</span><span class="sxs-lookup"><span data-stu-id="09b81-102">CreateApplicationContext Function</span></span>

<span data-ttu-id="09b81-103">Bu işlev .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="09b81-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09b81-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="09b81-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="09b81-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="09b81-105">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="09b81-106">'ndaki Kolay bir ad işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="09b81-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="09b81-107">dışı Uygulama bağlamına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="09b81-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09b81-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09b81-108">Requirements</span></span>  

 <span data-ttu-id="09b81-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09b81-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09b81-110">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="09b81-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="09b81-111">**Kitaplık:** Fusion.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="09b81-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="09b81-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09b81-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b81-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09b81-113">See also</span></span>

- [<span data-ttu-id="09b81-114">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09b81-114">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="09b81-115">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="09b81-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="09b81-116">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="09b81-116">Global Assembly Cache</span></span>](../../app-domains/gac.md)
