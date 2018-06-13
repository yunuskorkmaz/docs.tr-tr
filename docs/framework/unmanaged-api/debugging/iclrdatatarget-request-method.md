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
ms.openlocfilehash: dc79277c75118b11766e66137284bd5655eed091
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405378"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="30483-102">ICLRDataTarget::Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30483-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="30483-103">Uygulama tarafından tanımlandığı şekilde, bir işlem istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="30483-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30483-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30483-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="30483-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30483-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="30483-106">[in] Kullanıcı tanımlı.</span><span class="sxs-lookup"><span data-stu-id="30483-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="30483-107">[in] Gelen istek için kullanılan giriş arabelleği boyutu.</span><span class="sxs-lookup"><span data-stu-id="30483-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="30483-108">[in] İsteği içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="30483-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="30483-109">[in] Yanıt için kullanılan çıkış arabelleği boyutu.</span><span class="sxs-lookup"><span data-stu-id="30483-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="30483-110">[out] Yanıtı içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="30483-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30483-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30483-111">Remarks</span></span>  
 <span data-ttu-id="30483-112">`Request` Yöntemi belirtilmeyen özel işlemler eklenmesi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="30483-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="30483-113">Diğer bir deyişle, bu yöntem, arabirim tanımı düzeltilmesi gerek kalmadan genişletilebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="30483-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="30483-114">Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="30483-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30483-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30483-115">Requirements</span></span>  
 <span data-ttu-id="30483-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30483-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30483-117">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="30483-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="30483-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30483-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30483-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30483-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30483-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30483-120">See Also</span></span>  
 [<span data-ttu-id="30483-121">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30483-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
