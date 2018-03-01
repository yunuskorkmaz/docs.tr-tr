---
title: ICLRDataTarget::GetTLSValue Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDataTarget.GetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ab3d978e9500a17f5b8ae011322ad05aedddf98b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="28b54-102">ICLRDataTarget::GetTLSValue Metodu</span><span class="sxs-lookup"><span data-stu-id="28b54-102">ICLRDataTarget::GetTLSValue Method</span></span>
<span data-ttu-id="28b54-103">Belirtilen iş parçacığının hedef işlemdeki iş parçacığı yerel depolaması (TLS) bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="28b54-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="28b54-104">Bu yöntem ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="28b54-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28b54-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28b54-105">Syntax</span></span>  
  
```  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="28b54-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28b54-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="28b54-107">[in] Bir iş parçacığı hedef işlem, işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="28b54-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="28b54-108">[in] Konumun dizini.</span><span class="sxs-lookup"><span data-stu-id="28b54-108">[in] The index of the location.</span></span> <span data-ttu-id="28b54-109">Bu değer, belirtilen iş parçacığı yerel deposunda geçerli bir dizin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="28b54-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="28b54-110">[out] Bir işaretçi bir `CLRDATA_ADDRESS` değeri belirten değeri belirtilen TLS konumdan döndürdü.</span><span class="sxs-lookup"><span data-stu-id="28b54-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28b54-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="28b54-111">Remarks</span></span>  
 <span data-ttu-id="28b54-112">Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="28b54-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28b54-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28b54-113">Requirements</span></span>  
 <span data-ttu-id="28b54-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28b54-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28b54-115">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="28b54-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="28b54-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28b54-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28b54-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28b54-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28b54-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28b54-118">See Also</span></span>  
 [<span data-ttu-id="28b54-119">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28b54-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
