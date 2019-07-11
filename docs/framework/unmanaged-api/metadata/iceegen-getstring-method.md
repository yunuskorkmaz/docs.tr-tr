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
ms.openlocfilehash: ce015713ca7ed26c97348aa39f8170a85c8aa93c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745925"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="0ca0d-102">ICeeGen::GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0ca0d-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="0ca0d-103">Belirtilen göreli sanal adresindeki depolanan dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="0ca0d-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="0ca0d-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0ca0d-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ca0d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ca0d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ca0d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ca0d-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="0ca0d-107">[in] Göreli sanal adres döndürmek için dize.</span><span class="sxs-lookup"><span data-stu-id="0ca0d-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="0ca0d-108">[out] Döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="0ca0d-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ca0d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ca0d-109">Requirements</span></span>  
 <span data-ttu-id="0ca0d-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ca0d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ca0d-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="0ca0d-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0ca0d-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="0ca0d-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0ca0d-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ca0d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ca0d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0ca0d-114">See also</span></span>

- [<span data-ttu-id="0ca0d-115">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ca0d-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
