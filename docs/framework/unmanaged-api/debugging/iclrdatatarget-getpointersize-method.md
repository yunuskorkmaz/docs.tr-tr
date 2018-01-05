---
title: ICLRDataTarget::GetPointerSize Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetPointerSize
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetPointerSize
helpviewer_keywords:
- GetPointerSize method [.NET Framework debugging]
- ICLRDataTarget::GetPointerSize method [.NET Framework debugging]
ms.assetid: 51d9f4a4-81a7-4527-8537-5212bdb05c70
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ca35246b82ed4adc982b6e7b157398d230dabe4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetpointersize-method"></a><span data-ttu-id="45d66-102">ICLRDataTarget::GetPointerSize Metodu</span><span class="sxs-lookup"><span data-stu-id="45d66-102">ICLRDataTarget::GetPointerSize Method</span></span>
<span data-ttu-id="45d66-103">Hedef işlemin kullanan işaretçi türü bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="45d66-103">Gets the size, in bytes, of the pointer type that the target process uses.</span></span> <span data-ttu-id="45d66-104">Bu yöntem ortak dil çalışma zamanı veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="45d66-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45d66-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45d66-105">Syntax</span></span>  
  
```  
HRESULT GetPointerSize (  
    [out] ULONG32     *pointerSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45d66-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="45d66-106">Parameters</span></span>  
 `pointerSize`  
 <span data-ttu-id="45d66-107">[out] Bir işaretçinin hedef işleme bayt cinsinden boyutu belirten bir tamsayı değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="45d66-107">[out] A pointer to an integer value that specifies the size, in bytes, of a pointer on the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45d66-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45d66-108">Remarks</span></span>  
 <span data-ttu-id="45d66-109">Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="45d66-109">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45d66-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45d66-110">Requirements</span></span>  
 <span data-ttu-id="45d66-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45d66-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45d66-112">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="45d66-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="45d66-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45d66-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45d66-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45d66-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45d66-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45d66-115">See Also</span></span>  
 [<span data-ttu-id="45d66-116">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45d66-116">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
