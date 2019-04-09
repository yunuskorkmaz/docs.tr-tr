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
ms.openlocfilehash: e823911280f52e16c745c9c77fe17b49bd35dc0b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129837"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="5e0af-102">ICLRDataTarget::GetImageBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e0af-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="5e0af-103">Belirtilen görüntü temel bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="5e0af-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e0af-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e0af-104">Syntax</span></span>  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e0af-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e0af-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="5e0af-106">[in] Diskteki yolu da dahil olmak üzere resim dosya adı.</span><span class="sxs-lookup"><span data-stu-id="5e0af-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="5e0af-107">[out] Görüntüyü temel adresini depolayan bir CLRDATA_ADDRESS işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5e0af-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e0af-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e0af-108">Remarks</span></span>  
 <span data-ttu-id="5e0af-109">Resim dosyası adına olabilir veya bir yol olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="5e0af-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="5e0af-110">Bir yol belirtilmezse, eşleşen dosyanın tam yolunu üzerinde gerçekleştirilir; Aksi halde, eşleme yalnızca dosya adını gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5e0af-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e0af-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e0af-111">Requirements</span></span>  
 <span data-ttu-id="5e0af-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e0af-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e0af-113">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="5e0af-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5e0af-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e0af-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5e0af-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="5e0af-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5e0af-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e0af-116">See also</span></span>

- [<span data-ttu-id="5e0af-117">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e0af-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
