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
ms.openlocfilehash: 1425d48bb18d4161a1c96239b76b8315ae258705
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73112774"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="ecc12-102">ICLRDataTarget::SetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ecc12-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="ecc12-103">Hedef işlemde belirtilen iş parçacığının iş parçacığı yerel deposunda (TLS) bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ecc12-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="ecc12-104">Bu yöntem, ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ecc12-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc12-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ecc12-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecc12-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ecc12-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="ecc12-107">'ndaki Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ecc12-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="ecc12-108">'ndaki Konumun dizini.</span><span class="sxs-lookup"><span data-stu-id="ecc12-108">[in] The index of the location.</span></span> <span data-ttu-id="ecc12-109">Bu değer, belirtilen iş parçacığının yerel deposunda geçerli bir dizin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ecc12-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="ecc12-110">'ndaki Verilen TLS konumuna yerleştirilecek değeri belirten `CLRDATA_ADDRESS` değeri.</span><span class="sxs-lookup"><span data-stu-id="ecc12-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecc12-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ecc12-111">Remarks</span></span>  
 <span data-ttu-id="ecc12-112">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ecc12-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecc12-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ecc12-113">Requirements</span></span>  
 <span data-ttu-id="ecc12-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecc12-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecc12-115">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="ecc12-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ecc12-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ecc12-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecc12-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecc12-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc12-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ecc12-118">See also</span></span>

- [<span data-ttu-id="ecc12-119">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ecc12-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
