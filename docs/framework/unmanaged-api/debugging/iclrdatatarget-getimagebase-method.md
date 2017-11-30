---
title: ICLRDataTarget::GetImageBase Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetImageBase
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1d397995266d6063164510a4b563ba94f7f54950
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="9f3e4-102">ICLRDataTarget::GetImageBase Metodu</span><span class="sxs-lookup"><span data-stu-id="9f3e4-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="9f3e4-103">Belirtilen görüntü temel bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="9f3e4-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f3e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f3e4-104">Syntax</span></span>  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9f3e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f3e4-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="9f3e4-106">[in] Görüntünün yolunu da içeren dosya adı.</span><span class="sxs-lookup"><span data-stu-id="9f3e4-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="9f3e4-107">[out] Temel adres görüntünün depolayan bir CLRDATA_ADDRESS gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9f3e4-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f3e4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9f3e4-108">Remarks</span></span>  
 <span data-ttu-id="9f3e4-109">Resim dosyası adı olabilir veya bir yol olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="9f3e4-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="9f3e4-110">Bir yol belirtilmezse, eşleşen dosyanın tam yolunu üzerinde gerçekleştirilir; Aksi takdirde, eşleşen yalnızca dosya adını yapılır.</span><span class="sxs-lookup"><span data-stu-id="9f3e4-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f3e4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f3e4-111">Requirements</span></span>  
 <span data-ttu-id="9f3e4-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f3e4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f3e4-113">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="9f3e4-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9f3e4-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9f3e4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9f3e4-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f3e4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f3e4-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9f3e4-116">See Also</span></span>  
 [<span data-ttu-id="9f3e4-117">Iclrdatatarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f3e4-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
