---
description: 'Daha fazla bilgi edinin: CreateApplicationContext Işlevi'
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
ms.openlocfilehash: f192e1ccc371cb6d50e4a41a286c412825ee4181
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761190"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="9f72e-103">CreateApplicationContext İşlevi</span><span class="sxs-lookup"><span data-stu-id="9f72e-103">CreateApplicationContext Function</span></span>

<span data-ttu-id="9f72e-104">Bu işlev .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="9f72e-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f72e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f72e-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f72e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f72e-106">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="9f72e-107">'ndaki Kolay bir ad işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9f72e-107">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="9f72e-108">dışı Uygulama bağlamına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9f72e-108">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f72e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f72e-109">Requirements</span></span>  

 <span data-ttu-id="9f72e-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f72e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f72e-111">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="9f72e-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="9f72e-112">**Kitaplık:** Fusion.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9f72e-112">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="9f72e-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f72e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f72e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f72e-114">See also</span></span>

- [<span data-ttu-id="9f72e-115">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f72e-115">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="9f72e-116">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9f72e-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="9f72e-117">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="9f72e-117">Global Assembly Cache</span></span>](../../app-domains/gac.md)
