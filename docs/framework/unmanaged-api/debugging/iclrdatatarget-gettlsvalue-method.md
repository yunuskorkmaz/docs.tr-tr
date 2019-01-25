---
title: ICLRDataTarget::GetTLSValue Metodu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 676f3fe9aa9ad7de1499bb42ff23d446b1cb73d8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535495"
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="ad74d-102">ICLRDataTarget::GetTLSValue Metodu</span><span class="sxs-lookup"><span data-stu-id="ad74d-102">ICLRDataTarget::GetTLSValue Method</span></span>
<span data-ttu-id="ad74d-103">Hedef işlemde belirtilen iş parçacığının, iş parçacığı yerel depolaması (TLS) bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="ad74d-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="ad74d-104">Bu yöntem, ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ad74d-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad74d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ad74d-105">Syntax</span></span>  
  
```  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad74d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad74d-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="ad74d-107">[in] Bir iş parçacığı hedef işlem, işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ad74d-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="ad74d-108">[in] Konumun dizini.</span><span class="sxs-lookup"><span data-stu-id="ad74d-108">[in] The index of the location.</span></span> <span data-ttu-id="ad74d-109">Bu değer, belirtilen iş parçacığı yerel deposuna geçerli bir dizin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ad74d-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="ad74d-110">[out] Bir işaretçi bir `CLRDATA_ADDRESS` değeri belirten bir değeri belirli TLS konumdan döndürdü.</span><span class="sxs-lookup"><span data-stu-id="ad74d-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad74d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ad74d-111">Remarks</span></span>  
 <span data-ttu-id="ad74d-112">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ad74d-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad74d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad74d-113">Requirements</span></span>  
 <span data-ttu-id="ad74d-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad74d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad74d-115">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="ad74d-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ad74d-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad74d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad74d-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad74d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad74d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad74d-118">See also</span></span>
- [<span data-ttu-id="ad74d-119">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad74d-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
