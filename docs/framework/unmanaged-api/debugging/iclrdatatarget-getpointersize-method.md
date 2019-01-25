---
title: ICLRDataTarget::GetPointerSize Metodu
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetPointerSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80ed86526c99c36254f2b9c71f00483095e771ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734357"
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="94eae-102">ICLRDataTarget::GetPointerSize Metodu</span><span class="sxs-lookup"><span data-stu-id="94eae-102">ICLRDataTarget::GetPointerSize Method</span></span>
<span data-ttu-id="94eae-103">Hedef işlemin kullandığı işaretçi türünün bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="94eae-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="94eae-104">Bu yöntem, ortak dil çalışma zamanı veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="94eae-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94eae-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94eae-105">Syntax</span></span>  
  
```  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="94eae-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94eae-106">Parameters</span></span>  
 `pointerSize`  
 <span data-ttu-id="94eae-107">[out] Hedef işlem üzerinde bir işaretçi bayt cinsinden boyutunu belirten bir tamsayı değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94eae-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94eae-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94eae-108">Remarks</span></span>  
 <span data-ttu-id="94eae-109">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="94eae-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94eae-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94eae-110">Requirements</span></span>  
 <span data-ttu-id="94eae-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94eae-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94eae-112">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="94eae-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="94eae-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94eae-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94eae-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94eae-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94eae-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94eae-115">See also</span></span>
- [<span data-ttu-id="94eae-116">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94eae-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
