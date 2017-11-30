---
title: "ICLRDataTarget::Request Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.Request
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e0ce905ea21267419e6a68e73f918de8fc364f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="526c2-102">ICLRDataTarget::Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="526c2-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="526c2-103">Uygulama tarafından tanımlandığı şekilde, bir işlem istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="526c2-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="526c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="526c2-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="526c2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="526c2-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="526c2-106">[in] Kullanıcı tanımlı.</span><span class="sxs-lookup"><span data-stu-id="526c2-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="526c2-107">[in] Gelen istek için kullanılan giriş arabelleği boyutu.</span><span class="sxs-lookup"><span data-stu-id="526c2-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="526c2-108">[in] İsteği içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="526c2-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="526c2-109">[in] Yanıt için kullanılan çıkış arabelleği boyutu.</span><span class="sxs-lookup"><span data-stu-id="526c2-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="526c2-110">[out] Yanıtı içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="526c2-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="526c2-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="526c2-111">Remarks</span></span>  
 <span data-ttu-id="526c2-112">`Request` Yöntemi belirtilmeyen özel işlemler eklenmesi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="526c2-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="526c2-113">Diğer bir deyişle, bu yöntem, arabirim tanımı düzeltilmesi gerek kalmadan genişletilebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="526c2-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="526c2-114">Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="526c2-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="526c2-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="526c2-115">Requirements</span></span>  
 <span data-ttu-id="526c2-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="526c2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="526c2-117">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="526c2-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="526c2-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="526c2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="526c2-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="526c2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="526c2-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="526c2-120">See Also</span></span>  
 [<span data-ttu-id="526c2-121">Iclrdatatarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="526c2-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
