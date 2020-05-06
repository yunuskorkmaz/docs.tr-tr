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
ms.openlocfilehash: 71b07e11cd3fec1a0dbebe986d98067c2e6f18e1
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860638"
---
# <a name="iclrdatatargetgetimagebase-method"></a><span data-ttu-id="ea6e2-102">ICLRDataTarget::GetImageBase Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea6e2-102">ICLRDataTarget::GetImageBase Method</span></span>
<span data-ttu-id="ea6e2-103">Belirtilen görüntünün taban bellek adresini alır.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-103">Gets the base memory address of the specified image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea6e2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea6e2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea6e2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea6e2-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="ea6e2-106">'ndaki Görüntünün yolu da dahil olmak üzere dosya adı.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-106">[in] The file name of the image, including its path.</span></span>  
  
 `baseAddress`  
 <span data-ttu-id="ea6e2-107">dışı Görüntünün temel adresini depolayan CLRDATA_ADDRESS işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-107">[out] A pointer to a CLRDATA_ADDRESS that stores the base address of the image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea6e2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ea6e2-108">Remarks</span></span>  
 <span data-ttu-id="ea6e2-109">Görüntü dosyası adı bir yola sahip olabilir veya olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-109">The image file name may or may not have a path.</span></span> <span data-ttu-id="ea6e2-110">Bir yol belirtilmişse, eşleşme tam yol üzerinde yapılır; Aksi takdirde, eşleştirme yalnızca dosya adı üzerinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-110">If a path is specified, matching is done on the whole path; otherwise, matching is done only on the file name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea6e2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea6e2-111">Requirements</span></span>  
 <span data-ttu-id="ea6e2-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea6e2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea6e2-113">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="ea6e2-113">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ea6e2-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ea6e2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea6e2-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea6e2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea6e2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-116">See also</span></span>

- [<span data-ttu-id="ea6e2-117">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea6e2-117">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
