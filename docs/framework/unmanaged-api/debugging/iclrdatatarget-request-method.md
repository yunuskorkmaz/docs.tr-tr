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
ms.openlocfilehash: 336ba38bc80fcb2649a12c78691e52c5e4d70bfe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179107"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="616b0-102">ICLRDataTarget::Request Yöntemi</span><span class="sxs-lookup"><span data-stu-id="616b0-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="616b0-103">Uygulama tarafından tanımlandığı gibi bir işlem istemek için ortak dil çalışma zamanı (CLR) veri erişim hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="616b0-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="616b0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="616b0-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="616b0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="616b0-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="616b0-106">[içinde] Kullanıcı tanımlı.</span><span class="sxs-lookup"><span data-stu-id="616b0-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="616b0-107">[içinde] Gelen istek için kullanılan giriş arabelleği boyutu.</span><span class="sxs-lookup"><span data-stu-id="616b0-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="616b0-108">[içinde] İsteği içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="616b0-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="616b0-109">[içinde] Yanıt için kullanılan çıktı arabelleği boyutu.</span><span class="sxs-lookup"><span data-stu-id="616b0-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="616b0-110">[çıkış] Yanıtı içeren bir Arabellek.</span><span class="sxs-lookup"><span data-stu-id="616b0-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="616b0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="616b0-111">Remarks</span></span>  
 <span data-ttu-id="616b0-112">Yöntem, `Request` belirtilmeyen özel işlemlerin eklenmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="616b0-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="616b0-113">Diğer bir zamanda, bu yöntem arabirim tanımının gözden geçirilmesini gerektirmeden genişletilebilirlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="616b0-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="616b0-114">Bu yöntem hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="616b0-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="616b0-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="616b0-115">Requirements</span></span>  
 <span data-ttu-id="616b0-116">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="616b0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="616b0-117">**Üstbilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="616b0-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="616b0-118">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="616b0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="616b0-119">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="616b0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="616b0-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="616b0-120">See also</span></span>

- [<span data-ttu-id="616b0-121">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="616b0-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
