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
ms.openlocfilehash: e5d7a6b9826a734363d6beeb2e3fab8422964558
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113347"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="7e436-102">ICLRDataTarget::Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e436-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="7e436-103">Uygulama tarafından tanımlanan bir işlem istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="7e436-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e436-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e436-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7e436-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e436-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="7e436-106">'ndaki Kullanıcı tanımlı.</span><span class="sxs-lookup"><span data-stu-id="7e436-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="7e436-107">'ndaki Gelen istek için kullanılan giriş arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="7e436-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="7e436-108">'ndaki İsteği içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="7e436-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="7e436-109">'ndaki Yanıt için kullanılan çıkış arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="7e436-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="7e436-110">dışı Yanıtı içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="7e436-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e436-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e436-111">Remarks</span></span>  
 <span data-ttu-id="7e436-112">`Request` yöntemi, belirtilmeyen özel işlemlerin eklenmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="7e436-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="7e436-113">Diğer bir deyişle, bu yöntem, arabirim tanımının düzeltilmesi gerekmeden genişletilebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="7e436-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="7e436-114">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="7e436-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e436-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e436-115">Requirements</span></span>  
 <span data-ttu-id="7e436-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e436-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e436-117">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="7e436-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7e436-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7e436-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e436-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e436-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e436-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e436-120">See also</span></span>

- [<span data-ttu-id="7e436-121">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e436-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
