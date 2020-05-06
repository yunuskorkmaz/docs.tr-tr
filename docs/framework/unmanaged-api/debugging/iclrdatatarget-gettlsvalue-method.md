---
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
ms.openlocfilehash: 141dc8632812ab4a2ce82864cde56337025baa28
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860575"
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="c4055-102">ICLRDataTarget::GetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4055-102">ICLRDataTarget::GetTLSValue Method</span></span>
<span data-ttu-id="c4055-103">Hedef işlemde belirtilen iş parçacığının iş parçacığı yerel depolama alanından (TLS) bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="c4055-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="c4055-104">Bu yöntem, ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c4055-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4055-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4055-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4055-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4055-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c4055-107">'ndaki Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c4055-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="c4055-108">'ndaki Konumun dizini.</span><span class="sxs-lookup"><span data-stu-id="c4055-108">[in] The index of the location.</span></span> <span data-ttu-id="c4055-109">Bu değer, belirtilen iş parçacığının yerel deposunda geçerli bir dizin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c4055-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="c4055-110">dışı Verilen TLS konumundan döndürülen `CLRDATA_ADDRESS` değeri belirten bir değer işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c4055-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4055-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4055-111">Remarks</span></span>  
 <span data-ttu-id="c4055-112">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c4055-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4055-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4055-113">Requirements</span></span>  
 <span data-ttu-id="c4055-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4055-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4055-115">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="c4055-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c4055-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c4055-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4055-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4055-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4055-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4055-118">See also</span></span>

- [<span data-ttu-id="c4055-119">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4055-119">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
