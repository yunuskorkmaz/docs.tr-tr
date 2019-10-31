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
ms.openlocfilehash: fed643ae52f50b1b8cd134880c644c8941da6f56
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122868"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="84983-102">ICLRDataTarget::GetImageBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84983-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="84983-103">Belirtilen görüntünün taban bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="84983-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84983-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84983-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84983-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84983-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="84983-106">'ndaki Görüntünün yolu da dahil olmak üzere dosya adı.</span><span class="sxs-lookup"><span data-stu-id="84983-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="84983-107">dışı Görüntünün temel adresini depolayan bir CLRDATA_ADDRESS işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="84983-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84983-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84983-108">Remarks</span></span>  
 <span data-ttu-id="84983-109">Görüntü dosyası adı bir yola sahip olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="84983-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="84983-110">Bir yol belirtilmişse, eşleşme tam yol üzerinde yapılır; Aksi takdirde, eşleştirme yalnızca dosya adı üzerinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="84983-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84983-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84983-111">Requirements</span></span>  
 <span data-ttu-id="84983-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84983-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84983-113">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="84983-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="84983-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="84983-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84983-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84983-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84983-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84983-116">See also</span></span>

- [<span data-ttu-id="84983-117">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84983-117">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
