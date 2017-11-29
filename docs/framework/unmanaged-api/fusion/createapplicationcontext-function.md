---
title: "CreateApplicationContext İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateApplicationContext
api_location: fusion.dll
api_type: DLLExport
f1_keywords: CreateApplicationContext
helpviewer_keywords: CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c089c32d4bc8474168274186a9303d39976abfca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="7b0cd-102">CreateApplicationContext İşlevi</span><span class="sxs-lookup"><span data-stu-id="7b0cd-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="7b0cd-103">Bu işlev .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="7b0cd-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b0cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b0cd-104">Syntax</span></span>  
  
```  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b0cd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7b0cd-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="7b0cd-106">[in] Bir kolay ad için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7b0cd-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="7b0cd-107">[out] Uygulama bağlamı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7b0cd-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b0cd-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7b0cd-108">Requirements</span></span>  
 <span data-ttu-id="7b0cd-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b0cd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b0cd-110">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="7b0cd-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="7b0cd-111">**Kitaplığı:** bir kaynak olarak Fusion.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7b0cd-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="7b0cd-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b0cd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b0cd-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b0cd-113">See Also</span></span>  
 [<span data-ttu-id="7b0cd-114">Iassemblycache arabirimi</span><span class="sxs-lookup"><span data-stu-id="7b0cd-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="7b0cd-115">Fusion genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="7b0cd-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="7b0cd-116">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="7b0cd-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
