---
description: ': ICLRDataTarget:: Settinglsvalue yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 2432cd66f604575e35f171c98a0fb313c5ccd94e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785693"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="605da-103">ICLRDataTarget::SetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="605da-103">ICLRDataTarget::SetTLSValue Method</span></span>

<span data-ttu-id="605da-104">Hedef işlemde belirtilen iş parçacığının iş parçacığı yerel deposunda (TLS) bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="605da-104">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="605da-105">Bu yöntem, ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="605da-105">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="605da-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="605da-106">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="605da-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="605da-107">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="605da-108">'ndaki Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="605da-108">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="605da-109">'ndaki Konumun dizini.</span><span class="sxs-lookup"><span data-stu-id="605da-109">[in] The index of the location.</span></span> <span data-ttu-id="605da-110">Bu değer, belirtilen iş parçacığının yerel deposunda geçerli bir dizin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="605da-110">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="605da-111">'ndaki `CLRDATA_ADDRESS` VERILEN TLS konumuna yerleştirilecek değeri belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="605da-111">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="605da-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="605da-112">Remarks</span></span>  

 <span data-ttu-id="605da-113">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="605da-113">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="605da-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="605da-114">Requirements</span></span>  

 <span data-ttu-id="605da-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="605da-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="605da-116">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="605da-116">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="605da-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="605da-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="605da-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="605da-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="605da-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="605da-119">See also</span></span>

- [<span data-ttu-id="605da-120">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="605da-120">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
