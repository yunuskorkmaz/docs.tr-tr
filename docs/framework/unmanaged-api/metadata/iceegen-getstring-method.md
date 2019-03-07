---
title: ICeeGen::GetString Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf3f781e23d0787d01a1ef04b41b2c38eaaa9e0d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479343"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="1e18c-102">ICeeGen::GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e18c-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="1e18c-103">Belirtilen göreli sanal adresindeki depolanan dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="1e18c-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="1e18c-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="1e18c-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e18c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e18c-105">Syntax</span></span>  
  
```  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e18c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e18c-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="1e18c-107">[in] Göreli sanal adres döndürmek için dize.</span><span class="sxs-lookup"><span data-stu-id="1e18c-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="1e18c-108">[out] Döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="1e18c-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e18c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e18c-109">Requirements</span></span>  
 <span data-ttu-id="1e18c-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e18c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e18c-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1e18c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1e18c-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="1e18c-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1e18c-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e18c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e18c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e18c-114">See also</span></span>
- [<span data-ttu-id="1e18c-115">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e18c-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
