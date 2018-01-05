---
title: ICeeGen::GetString Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7365cb96021438d9c7e287463782e1cb112a66a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="cd61f-102">ICeeGen::GetString Metodu</span><span class="sxs-lookup"><span data-stu-id="cd61f-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="cd61f-103">Belirtilen göreli sanal adresinde depolanan dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="cd61f-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="cd61f-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="cd61f-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd61f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cd61f-105">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd61f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cd61f-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="cd61f-107">[in] Döndürülecek dizesinin göreli sanal adres.</span><span class="sxs-lookup"><span data-stu-id="cd61f-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="cd61f-108">[out] Döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="cd61f-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd61f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd61f-109">Requirements</span></span>  
 <span data-ttu-id="cd61f-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd61f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd61f-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cd61f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd61f-112">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="cd61f-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd61f-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd61f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd61f-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cd61f-114">See Also</span></span>  
 [<span data-ttu-id="cd61f-115">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd61f-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
