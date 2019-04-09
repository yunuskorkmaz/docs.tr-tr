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
ms.openlocfilehash: e9005dd8fde0d7258bd1dd48b561e4925e87733b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102703"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="c592f-102">ICLRDataTarget::Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c592f-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="c592f-103">Uygulama tarafından tanımlanan bir işlemi istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c592f-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c592f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c592f-104">Syntax</span></span>  
  
```  
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
  
## <a name="parameters"></a><span data-ttu-id="c592f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c592f-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="c592f-106">[in] Kullanıcı tanımlı.</span><span class="sxs-lookup"><span data-stu-id="c592f-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="c592f-107">[in] Gelen istek için kullanılan giriş arabellek boyutu.</span><span class="sxs-lookup"><span data-stu-id="c592f-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="c592f-108">[in] İstek içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="c592f-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="c592f-109">[in] Yanıt için kullanılan çıkış arabelleği boyutu.</span><span class="sxs-lookup"><span data-stu-id="c592f-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="c592f-110">[out] Yanıtı içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="c592f-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c592f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c592f-111">Remarks</span></span>  
 <span data-ttu-id="c592f-112">`Request` Yöntemi belirtilmeyen özel işlemler eklenmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="c592f-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="c592f-113">Diğer bir deyişle, bu yöntem, arabirim tanımı gözden geçirilmesini gerek kalmadan genişletilebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="c592f-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="c592f-114">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c592f-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c592f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c592f-115">Requirements</span></span>  
 <span data-ttu-id="c592f-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c592f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c592f-117">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c592f-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c592f-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c592f-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c592f-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c592f-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c592f-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c592f-120">See also</span></span>

- [<span data-ttu-id="c592f-121">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c592f-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
