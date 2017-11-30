---
title: ICorDebugRemoteTarget::GetHostName Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemoteTarget.GetHostName
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2af5d75145b9fdd2d370b76f798c5e350d8bec50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="20a1d-102">ICorDebugRemoteTarget::GetHostName Metodu</span><span class="sxs-lookup"><span data-stu-id="20a1d-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="20a1d-103">Tam etki alanı adı veya uzaktan hata ayıklama hedef makine IPv4 adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="20a1d-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="20a1d-104">IPv6, şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="20a1d-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20a1d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20a1d-105">Syntax</span></span>  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="20a1d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="20a1d-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="20a1d-107">[in] Karakter, boyutu, `szHostName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="20a1d-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="20a1d-108">Bu parametre 0 (sıfır) ise `szHostName` null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="20a1d-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="20a1d-109">[out] Ana bilgisayar adı veya IP adresi null Sonlandırıcı dahil karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="20a1d-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="20a1d-110">Bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="20a1d-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="20a1d-111">[out] Ana bilgisayar adı veya IP adresini içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="20a1d-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20a1d-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="20a1d-112">Return Value</span></span>  
 <span data-ttu-id="20a1d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="20a1d-113">S_OK</span></span>  
 <span data-ttu-id="20a1d-114">Ana bilgisayar adı veya IP adresi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="20a1d-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="20a1d-115">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="20a1d-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="20a1d-116">Ana bilgisayar adı veya IP adresi iade edilemiyor.</span><span class="sxs-lookup"><span data-stu-id="20a1d-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20a1d-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20a1d-117">Remarks</span></span>  
 <span data-ttu-id="20a1d-118">Bu yöntem, hata ayıklayıcı yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="20a1d-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="20a1d-119">Birden fazla çağrı standardı izlemelidir: ilk çağrıda çağıran her ikisi de null değerini iletir `cchHostName` ve `szHostName`, ve `pcchHostName` gerekli arabellek boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="20a1d-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer .</span></span> <span data-ttu-id="20a1d-120">İkinci çağrıda önceden döndürüldü boyutu geçirilen `cchHostName`, ve uygun şekilde boyutlu bir arabellek geçirilen `szHostName`.</span><span class="sxs-lookup"><span data-stu-id="20a1d-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20a1d-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20a1d-121">Requirements</span></span>  
 <span data-ttu-id="20a1d-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20a1d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20a1d-123">**Başlık:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="20a1d-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="20a1d-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="20a1d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="20a1d-125">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="20a1d-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a1d-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20a1d-126">See Also</span></span>  
 [<span data-ttu-id="20a1d-127">Icordebugremotetarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="20a1d-127">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="20a1d-128">Icordebug arabirimi</span><span class="sxs-lookup"><span data-stu-id="20a1d-128">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
