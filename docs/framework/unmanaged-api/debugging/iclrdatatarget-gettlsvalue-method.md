---
description: ': ICLRDataTarget:: GetTLSValue yöntemi hakkında daha fazla bilgi edinin'
title: ICLRDataTarget::GetTLSValue Yöntemi
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
ms.openlocfilehash: 5c0c4a462d89c2eceada4180ea532f36fc9e48b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99718050"
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="b5a8d-103">ICLRDataTarget::GetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b5a8d-103">ICLRDataTarget::GetTLSValue Method</span></span>

<span data-ttu-id="b5a8d-104">Hedef işlemde belirtilen iş parçacığının iş parçacığı yerel depolama alanından (TLS) bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="b5a8d-104">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="b5a8d-105">Bu yöntem, ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b5a8d-105">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5a8d-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b5a8d-106">Syntax</span></span>  
  
```cpp  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5a8d-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b5a8d-107">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="b5a8d-108">'ndaki Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="b5a8d-108">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="b5a8d-109">'ndaki Konumun dizini.</span><span class="sxs-lookup"><span data-stu-id="b5a8d-109">[in] The index of the location.</span></span> <span data-ttu-id="b5a8d-110">Bu değer, belirtilen iş parçacığının yerel deposunda geçerli bir dizin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b5a8d-110">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="b5a8d-111">dışı `CLRDATA_ADDRESS` VERILEN TLS konumundan döndürülen değeri belirten bir değer işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b5a8d-111">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5a8d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5a8d-112">Remarks</span></span>  

 <span data-ttu-id="b5a8d-113">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b5a8d-113">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5a8d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b5a8d-114">Requirements</span></span>  

 <span data-ttu-id="b5a8d-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5a8d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5a8d-116">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="b5a8d-116">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b5a8d-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b5a8d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5a8d-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5a8d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5a8d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5a8d-119">See also</span></span>

- [<span data-ttu-id="b5a8d-120">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b5a8d-120">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
