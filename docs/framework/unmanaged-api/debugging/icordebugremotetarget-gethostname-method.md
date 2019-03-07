---
title: ICorDebugRemoteTarget::GetHostName Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2861a2f0aec66832c618dda7d50dd543920102f4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468616"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="c45ca-102">ICorDebugRemoteTarget::GetHostName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c45ca-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="c45ca-103">Tam etki alanı adı veya uzaktan hata ayıklama hedef makinesinin IPv4 adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c45ca-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="c45ca-104">IPv6 şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="c45ca-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c45ca-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c45ca-105">Syntax</span></span>  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a><span data-ttu-id="c45ca-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c45ca-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="c45ca-107">[in] Karakter cinsinden boyutu, `szHostName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="c45ca-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="c45ca-108">Bu parametre 0 (sıfır) ise `szHostName` null olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c45ca-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="c45ca-109">[out] Konak adı veya IP adresi null sonlandırıcıyı da dahil olmak üzere karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="c45ca-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="c45ca-110">Bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="c45ca-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="c45ca-111">[out] Ana bilgisayar adı veya IP adresini içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="c45ca-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c45ca-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c45ca-112">Return Value</span></span>  
 <span data-ttu-id="c45ca-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="c45ca-113">S_OK</span></span>  
 <span data-ttu-id="c45ca-114">Konak adı veya IP adresi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c45ca-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="c45ca-115">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="c45ca-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c45ca-116">Konak adı veya IP adresini döndürmek yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="c45ca-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c45ca-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c45ca-117">Remarks</span></span>  
 <span data-ttu-id="c45ca-118">Bu yöntem, hata ayıklayıcıyı yazan tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c45ca-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="c45ca-119">Birden fazla arama paradigması izlemelidir: İlk çağrı, çağıran her ikisi de null geçirir `cchHostName` ve `szHostName`, ve `pcchHostName` gerekli arabellek boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c45ca-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer.</span></span> <span data-ttu-id="c45ca-120">İkinci çağrıda, daha önce döndürülen boyutu geçirilen `cchHostName`, ve uygun boyutlandırılmış bir arabellek geçirilen `szHostName`.</span><span class="sxs-lookup"><span data-stu-id="c45ca-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c45ca-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c45ca-121">Requirements</span></span>  
 <span data-ttu-id="c45ca-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c45ca-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c45ca-123">**Üst bilgi:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="c45ca-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c45ca-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c45ca-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c45ca-125">**.NET framework sürümleri:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="c45ca-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c45ca-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c45ca-126">See also</span></span>
- [<span data-ttu-id="c45ca-127">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c45ca-127">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="c45ca-128">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c45ca-128">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
