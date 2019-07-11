---
title: ICLRDataTarget::Request Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5f6926d66a438cfc4fd97d7120e359b737212dde
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738623"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="99604-102">ICLRDataTarget::Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99604-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="99604-103">Uygulama tarafından tanımlanan bir işlemi istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="99604-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99604-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99604-104">Syntax</span></span>  
  
```cpp  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]   
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]   
        BYTE                *outBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99604-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99604-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="99604-106">[in] Kullanıcı tanımlı.</span><span class="sxs-lookup"><span data-stu-id="99604-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="99604-107">[in] Gelen istek için kullanılan giriş arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="99604-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="99604-108">[in] İstek içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="99604-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="99604-109">[in] Yanıt için kullanılan çıkış arabelleği boyutu.</span><span class="sxs-lookup"><span data-stu-id="99604-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="99604-110">[out] Yanıtı içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="99604-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="99604-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99604-111">Remarks</span></span>  
 <span data-ttu-id="99604-112">`Request` Yöntemi belirtilmeyen özel işlemler eklenmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="99604-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="99604-113">Diğer bir deyişle, bu yöntem, arabirim tanımı gözden geçirilmesini gerek kalmadan genişletilebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="99604-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="99604-114">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="99604-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99604-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99604-115">Requirements</span></span>  
 <span data-ttu-id="99604-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99604-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99604-117">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="99604-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="99604-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99604-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99604-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99604-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99604-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99604-120">See also</span></span>

- [<span data-ttu-id="99604-121">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99604-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
