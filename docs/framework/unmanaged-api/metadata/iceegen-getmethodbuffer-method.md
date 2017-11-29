---
title: ICeeGen::GetMethodBuffer Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.GetMethodBuffer
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be6b74de649a9b13092e6a5dcd2d2f80a215a16d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iceegengetmethodbuffer-method"></a><span data-ttu-id="80dc0-102">ICeeGen::GetMethodBuffer Metodu</span><span class="sxs-lookup"><span data-stu-id="80dc0-102">ICeeGen::GetMethodBuffer Method</span></span>
<span data-ttu-id="80dc0-103">Uygun boyutta bir arabellek yöntemi belirtilen göreli sanal adresinde alır.</span><span class="sxs-lookup"><span data-stu-id="80dc0-103">Gets a buffer of the appropriate size for the method at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="80dc0-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="80dc0-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80dc0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80dc0-105">Syntax</span></span>  
  
```  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80dc0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80dc0-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="80dc0-107">[in] Arabellek döndürülecek yöntemi göreli sanal adresi.</span><span class="sxs-lookup"><span data-stu-id="80dc0-107">[in] The relative virtual address of the method for which to return a buffer.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="80dc0-108">[out] Döndürülen arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="80dc0-108">[out] A pointer to the returned buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80dc0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80dc0-109">Requirements</span></span>  
 <span data-ttu-id="80dc0-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80dc0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80dc0-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="80dc0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="80dc0-112">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="80dc0-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="80dc0-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80dc0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80dc0-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80dc0-114">See Also</span></span>  
 [<span data-ttu-id="80dc0-115">Iceegen arabirimi</span><span class="sxs-lookup"><span data-stu-id="80dc0-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
