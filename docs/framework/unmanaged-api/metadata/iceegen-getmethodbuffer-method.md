---
title: ICeeGen::GetMethodBuffer Metodu
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d8ccaa1b03ae1afc87eb7b0a66dd517bba8fcf8a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497476"
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="edee9-102">ICeeGen::GetMethodBuffer Metodu</span><span class="sxs-lookup"><span data-stu-id="edee9-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="edee9-103">Uygun boyutta bir arabellek yöntemi için belirtilen göreli sanal adresindeki alır.</span><span class="sxs-lookup"><span data-stu-id="edee9-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="edee9-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="edee9-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edee9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="edee9-105">Syntax</span></span>  
  
```  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edee9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="edee9-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="edee9-107">[in] Yöntemin bir arabellek döndürülecek göreli sanal adres.</span><span class="sxs-lookup"><span data-stu-id="edee9-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="edee9-108">[out] Döndürülen arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="edee9-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edee9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="edee9-109">Requirements</span></span>  
 <span data-ttu-id="edee9-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edee9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edee9-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="edee9-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="edee9-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="edee9-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="edee9-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edee9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edee9-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="edee9-114">See also</span></span>
- [<span data-ttu-id="edee9-115">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="edee9-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
