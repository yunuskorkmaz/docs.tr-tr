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
ms.openlocfilehash: f1b9f55a383f1deb867c6b3e2fa385a82158d1e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703583"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="d2c3d-102">ICLRDataTarget::GetImageBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2c3d-102">ICLRDataTarget::GetImageBase Method</span></span>

<span data-ttu-id="d2c3d-103">Belirtilen görüntünün taban bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="d2c3d-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2c3d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d2c3d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2c3d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d2c3d-105">Parameters</span></span>  

 `imagePath`  
 <span data-ttu-id="d2c3d-106">'ndaki Görüntünün yolu da dahil olmak üzere dosya adı.</span><span class="sxs-lookup"><span data-stu-id="d2c3d-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="d2c3d-107">dışı Görüntünün temel adresini depolayan CLRDATA_ADDRESS işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d2c3d-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2c3d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2c3d-108">Remarks</span></span>  

 <span data-ttu-id="d2c3d-109">Görüntü dosyası adı bir yola sahip olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d2c3d-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="d2c3d-110">Bir yol belirtilmişse, eşleşme tam yol üzerinde yapılır; Aksi takdirde, eşleştirme yalnızca dosya adı üzerinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="d2c3d-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2c3d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2c3d-111">Requirements</span></span>  

 <span data-ttu-id="d2c3d-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2c3d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2c3d-113">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="d2c3d-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="d2c3d-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d2c3d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2c3d-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2c3d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c3d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2c3d-116">See also</span></span>

- [<span data-ttu-id="d2c3d-117">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2c3d-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
