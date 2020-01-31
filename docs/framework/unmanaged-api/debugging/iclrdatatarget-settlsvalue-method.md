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
ms.openlocfilehash: 6e6e157c7176a0f4f1ad3c585977e2cfb31c33d8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793685"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="5f560-102">ICLRDataTarget::SetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5f560-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="5f560-103">Hedef işlemde belirtilen iş parçacığının iş parçacığı yerel deposunda (TLS) bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5f560-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="5f560-104">Bu yöntem, ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5f560-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f560-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5f560-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f560-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5f560-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="5f560-107">'ndaki Hedef işlemdeki bir iş parçacığının işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="5f560-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="5f560-108">'ndaki Konumun dizini.</span><span class="sxs-lookup"><span data-stu-id="5f560-108">[in] The index of the location.</span></span> <span data-ttu-id="5f560-109">Bu değer, belirtilen iş parçacığının yerel deposunda geçerli bir dizin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5f560-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="5f560-110">'ndaki Verilen TLS konumuna yerleştirilecek değeri belirten `CLRDATA_ADDRESS` değeri.</span><span class="sxs-lookup"><span data-stu-id="5f560-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f560-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5f560-111">Remarks</span></span>  
 <span data-ttu-id="5f560-112">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5f560-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f560-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5f560-113">Requirements</span></span>  
 <span data-ttu-id="5f560-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f560-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f560-115">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="5f560-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5f560-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5f560-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f560-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f560-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f560-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5f560-118">See also</span></span>

- [<span data-ttu-id="5f560-119">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5f560-119">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
