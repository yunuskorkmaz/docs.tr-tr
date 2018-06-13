---
title: ICLRDataTarget::GetImageBase Metodu
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
ms.openlocfilehash: 9a79133b117f3a718dd84af6c2144a6098bc79f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407253"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="4b388-102">ICLRDataTarget::GetImageBase Metodu</span><span class="sxs-lookup"><span data-stu-id="4b388-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="4b388-103">Belirtilen görüntü temel bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="4b388-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b388-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4b388-104">Syntax</span></span>  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b388-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4b388-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="4b388-106">[in] Görüntünün yolunu da içeren dosya adı.</span><span class="sxs-lookup"><span data-stu-id="4b388-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="4b388-107">[out] Temel adres görüntünün depolayan bir CLRDATA_ADDRESS gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4b388-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b388-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b388-108">Remarks</span></span>  
 <span data-ttu-id="4b388-109">Resim dosyası adı olabilir veya bir yol olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="4b388-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="4b388-110">Bir yol belirtilmezse, eşleşen dosyanın tam yolunu üzerinde gerçekleştirilir; Aksi takdirde, eşleşen yalnızca dosya adını yapılır.</span><span class="sxs-lookup"><span data-stu-id="4b388-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b388-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b388-111">Requirements</span></span>  
 <span data-ttu-id="4b388-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b388-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b388-113">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="4b388-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4b388-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b388-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b388-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b388-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b388-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b388-116">See Also</span></span>  
 [<span data-ttu-id="4b388-117">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b388-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
