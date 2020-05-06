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
ms.openlocfilehash: 6c98fc93fd659ccfc0ccd42eec7d95382cf342f8
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860518"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="7ca08-102">ICLRDataTarget::SetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ca08-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="7ca08-103">Hedef işlemde belirtilen iş parçacığının iş parçacığı yerel deposunda (TLS) bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7ca08-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="7ca08-104">Bu yöntem, ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7ca08-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ca08-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ca08-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ca08-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7ca08-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="7ca08-107">'ndaki Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="7ca08-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="7ca08-108">'ndaki Konumun dizini.</span><span class="sxs-lookup"><span data-stu-id="7ca08-108">[in] The index of the location.</span></span> <span data-ttu-id="7ca08-109">Bu değer, belirtilen iş parçacığının yerel deposunda geçerli bir dizin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ca08-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="7ca08-110">'ndaki Verilen `CLRDATA_ADDRESS` TLS konumuna yerleştirilecek değeri belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="7ca08-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ca08-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ca08-111">Remarks</span></span>  
 <span data-ttu-id="7ca08-112">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7ca08-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ca08-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ca08-113">Requirements</span></span>  
 <span data-ttu-id="7ca08-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ca08-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ca08-115">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="7ca08-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7ca08-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7ca08-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ca08-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ca08-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca08-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ca08-118">See also</span></span>

- [<span data-ttu-id="7ca08-119">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ca08-119">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
