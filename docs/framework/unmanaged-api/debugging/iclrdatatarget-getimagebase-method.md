---
title: ICLRDataTarget::GetImageBase Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetImageBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91d893c0df13fbcb44c66df7f268cffdffb5fff6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488438"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="97fa4-102">ICLRDataTarget::GetImageBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97fa4-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="97fa4-103">Belirtilen görüntü temel bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="97fa4-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97fa4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97fa4-104">Syntax</span></span>  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97fa4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97fa4-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="97fa4-106">[in] Diskteki yolu da dahil olmak üzere resim dosya adı.</span><span class="sxs-lookup"><span data-stu-id="97fa4-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="97fa4-107">[out] Görüntüyü temel adresini depolayan bir CLRDATA_ADDRESS işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="97fa4-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97fa4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="97fa4-108">Remarks</span></span>  
 <span data-ttu-id="97fa4-109">Resim dosyası adına olabilir veya bir yol olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="97fa4-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="97fa4-110">Bir yol belirtilmezse, eşleşen dosyanın tam yolunu üzerinde gerçekleştirilir; Aksi halde, eşleme yalnızca dosya adını gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="97fa4-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97fa4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97fa4-111">Requirements</span></span>  
 <span data-ttu-id="97fa4-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97fa4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97fa4-113">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="97fa4-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="97fa4-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97fa4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97fa4-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97fa4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97fa4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97fa4-116">See also</span></span>
- [<span data-ttu-id="97fa4-117">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97fa4-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
