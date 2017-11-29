---
title: ICLRDataTarget::GetTLSValue Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetTLSValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a820ec7c0a00306266be432a8aceacb3d30d1b4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="484c1-102">ICLRDataTarget::GetTLSValue Metodu</span><span class="sxs-lookup"><span data-stu-id="484c1-102">ICLRDataTarget::GetTLSValue Method</span></span>
<span data-ttu-id="484c1-103">Belirtilen iş parçacığının hedef işlemdeki iş parçacığı yerel depolaması (TLS) bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="484c1-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="484c1-104">Bu yöntem ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="484c1-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="484c1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="484c1-105">Syntax</span></span>  
  
```  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="484c1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="484c1-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="484c1-107">[in] Bir iş parçacığı hedef işlem, işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="484c1-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="484c1-108">[in] Konumun dizini.</span><span class="sxs-lookup"><span data-stu-id="484c1-108">[in] The index of the location.</span></span> <span data-ttu-id="484c1-109">Bu değer, belirtilen iş parçacığı yerel deposunda geçerli bir dizin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="484c1-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="484c1-110">[out] Bir işaretçi bir `CLRDATA_ADDRESS` değeri belirten değeri belirtilen TLS konumdan döndürdü.</span><span class="sxs-lookup"><span data-stu-id="484c1-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="484c1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="484c1-111">Remarks</span></span>  
 <span data-ttu-id="484c1-112">Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="484c1-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="484c1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="484c1-113">Requirements</span></span>  
 <span data-ttu-id="484c1-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="484c1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="484c1-115">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="484c1-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="484c1-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="484c1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="484c1-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="484c1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="484c1-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="484c1-118">See Also</span></span>  
 [<span data-ttu-id="484c1-119">Iclrdatatarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="484c1-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
