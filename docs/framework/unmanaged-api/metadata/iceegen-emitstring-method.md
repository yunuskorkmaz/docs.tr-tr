---
title: ICeeGen::EmitString Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3adc29f73a3ab4a43a399b024a6c0187f02b5851
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750618"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="2130d-102">ICeeGen::EmitString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2130d-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="2130d-103">Belirtilen dize kod tabanında yayar.</span><span class="sxs-lookup"><span data-stu-id="2130d-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="2130d-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2130d-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2130d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2130d-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2130d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2130d-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="2130d-107">[in] Yaymak için dize.</span><span class="sxs-lookup"><span data-stu-id="2130d-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="2130d-108">[out] Göreli sanal adres yayılan dize.</span><span class="sxs-lookup"><span data-stu-id="2130d-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2130d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2130d-109">Requirements</span></span>  
 <span data-ttu-id="2130d-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2130d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2130d-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="2130d-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2130d-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="2130d-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2130d-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2130d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2130d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2130d-114">See also</span></span>

- [<span data-ttu-id="2130d-115">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2130d-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
