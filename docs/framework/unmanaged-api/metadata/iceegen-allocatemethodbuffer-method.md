---
title: "ICeeGen::AllocateMethodBuffer Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICeeGen.AllocateMethodBuffer
api_location: mscoree.dll
api_type: COM
f1_keywords: ICeeGen::AllocateMethodBuffer
helpviewer_keywords:
- AllocateMethodBuffer method [.NET Framework metadata]
- ICeeGen::AllocateMethodBuffer method [.NET Framework metadata]
ms.assetid: 845ab77e-9639-47f5-99fb-f3b619e3e779
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be288bedf12649b4356c68135868b9415840c4d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iceegenallocatemethodbuffer-method"></a><span data-ttu-id="6a5f7-102">ICeeGen::AllocateMethodBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a5f7-102">ICeeGen::AllocateMethodBuffer Method</span></span>
<span data-ttu-id="6a5f7-103">Bir yöntem için belirtilen boyutta bir arabellek oluşturur ve göreli sanal adres yönteminin alır.</span><span class="sxs-lookup"><span data-stu-id="6a5f7-103">Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.</span></span>  
  
 <span data-ttu-id="6a5f7-104">Bu yöntem artık kullanılmıyor ve kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6a5f7-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a5f7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6a5f7-105">Syntax</span></span>  
  
```  
HRESULT AllocateMethodBuffer (   
    [in]  ULONG    cchBuffer,   
    [out] UCHAR    **lpBuffer,  
    [out] ULONG    *RVA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6a5f7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6a5f7-106">Parameters</span></span>  
 `cchBuffer`  
 <span data-ttu-id="6a5f7-107">[in] Oluşturmak için arabellek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="6a5f7-107">[in] The length of the buffer to create.</span></span>  
  
 `lpBuffer`  
 <span data-ttu-id="6a5f7-108">[out] Döndürülen arabellek.</span><span class="sxs-lookup"><span data-stu-id="6a5f7-108">[out] The returned buffer.</span></span>  
  
 `RVA`  
 <span data-ttu-id="6a5f7-109">[out] Yönteminin göreli sanal adres.</span><span class="sxs-lookup"><span data-stu-id="6a5f7-109">[out] The relative virtual address of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a5f7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a5f7-110">Requirements</span></span>  
 <span data-ttu-id="6a5f7-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a5f7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a5f7-112">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6a5f7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6a5f7-113">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6a5f7-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6a5f7-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a5f7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a5f7-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6a5f7-115">See Also</span></span>  
 [<span data-ttu-id="6a5f7-116">Iceegen arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a5f7-116">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
