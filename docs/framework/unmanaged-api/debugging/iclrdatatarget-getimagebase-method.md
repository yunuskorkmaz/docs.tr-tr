---
description: ': ICLRDataTarget:: GetImageBase yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 34e8341b219aaa184b4894c631f854e0a31921d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794877"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="322fb-103">ICLRDataTarget::GetImageBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="322fb-103">ICLRDataTarget::GetImageBase Method</span></span>

<span data-ttu-id="322fb-104">Belirtilen görüntünün taban bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="322fb-104">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="322fb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="322fb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="322fb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="322fb-106">Parameters</span></span>  

 `imagePath`  
 <span data-ttu-id="322fb-107">'ndaki Görüntünün yolu da dahil olmak üzere dosya adı.</span><span class="sxs-lookup"><span data-stu-id="322fb-107">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="322fb-108">dışı Görüntünün temel adresini depolayan CLRDATA_ADDRESS işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="322fb-108">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="322fb-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="322fb-109">Remarks</span></span>  

 <span data-ttu-id="322fb-110">Görüntü dosyası adı bir yola sahip olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="322fb-110">The image file name may or may not have a path.</span></span> <span data-ttu-id="322fb-111">Bir yol belirtilmişse, eşleşme tam yol üzerinde yapılır; Aksi takdirde, eşleştirme yalnızca dosya adı üzerinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="322fb-111">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="322fb-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="322fb-112">Requirements</span></span>  

 <span data-ttu-id="322fb-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="322fb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="322fb-114">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="322fb-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="322fb-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="322fb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="322fb-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="322fb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="322fb-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="322fb-117">See also</span></span>

- [<span data-ttu-id="322fb-118">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="322fb-118">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
