---
description: ': ICLRDataTarget:: Request yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 75c400a51a2fdaf0044d85b5f483d783fae4628b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712174"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="3e47d-103">ICLRDataTarget::Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3e47d-103">ICLRDataTarget::Request Method</span></span>

<span data-ttu-id="3e47d-104">Uygulama tarafından tanımlanan bir işlem istemek için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3e47d-104">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e47d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3e47d-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3e47d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3e47d-106">Parameters</span></span>  

 `reqCode`  
 <span data-ttu-id="3e47d-107">'ndaki Kullanıcı tanımlı.</span><span class="sxs-lookup"><span data-stu-id="3e47d-107">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="3e47d-108">'ndaki Gelen istek için kullanılan giriş arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="3e47d-108">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="3e47d-109">'ndaki İsteği içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="3e47d-109">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="3e47d-110">'ndaki Yanıt için kullanılan çıkış arabelleğinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="3e47d-110">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="3e47d-111">dışı Yanıtı içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="3e47d-111">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e47d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3e47d-112">Remarks</span></span>  

 <span data-ttu-id="3e47d-113">`Request`Yöntemi, belirtilmeyen özel işlemlerin eklenmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3e47d-113">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="3e47d-114">Diğer bir deyişle, bu yöntem, arabirim tanımının düzeltilmesi gerekmeden genişletilebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e47d-114">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="3e47d-115">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3e47d-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e47d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3e47d-116">Requirements</span></span>  

 <span data-ttu-id="3e47d-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e47d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e47d-118">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="3e47d-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="3e47d-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3e47d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e47d-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e47d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e47d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e47d-121">See also</span></span>

- [<span data-ttu-id="3e47d-122">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3e47d-122">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
