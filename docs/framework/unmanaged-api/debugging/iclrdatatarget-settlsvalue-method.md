---
title: ICLRDataTarget::SetTLSValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c0be35772b10d89f90da5b33f47aa781034b13a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59152938"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="cfecb-102">ICLRDataTarget::SetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfecb-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="cfecb-103">Hedef işlemde belirtilen iş parçacığının iş parçacığı yerel depolama (TLS) bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="cfecb-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="cfecb-104">Bu yöntem, ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cfecb-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfecb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfecb-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfecb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cfecb-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="cfecb-107">[in] Bir iş parçacığı hedef işlem, işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="cfecb-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="cfecb-108">[in] Konumun dizini.</span><span class="sxs-lookup"><span data-stu-id="cfecb-108">[in] The index of the location.</span></span> <span data-ttu-id="cfecb-109">Bu değer, belirtilen iş parçacığı yerel deposuna geçerli bir dizin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cfecb-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="cfecb-110">[in] A `CLRDATA_ADDRESS` değeri belirli TLS konuma yerleştirmek için belirten değer.</span><span class="sxs-lookup"><span data-stu-id="cfecb-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfecb-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cfecb-111">Remarks</span></span>  
 <span data-ttu-id="cfecb-112">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="cfecb-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfecb-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfecb-113">Requirements</span></span>  
 <span data-ttu-id="cfecb-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfecb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfecb-115">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="cfecb-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cfecb-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfecb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfecb-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfecb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfecb-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfecb-118">See also</span></span>

- [<span data-ttu-id="cfecb-119">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfecb-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
