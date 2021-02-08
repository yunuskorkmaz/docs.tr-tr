---
description: ': ICorDebugRemoteTarget:: GetHostName yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: a24f34dd638c7031211c2185cd761af0aa24105e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803532"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="c25f9-103">ICorDebugRemoteTarget::GetHostName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c25f9-103">ICorDebugRemoteTarget::GetHostName Method</span></span>

<span data-ttu-id="c25f9-104">Uzaktan hata ayıklama hedef makinesinin tam etki alanı adını veya IPv4 adresini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c25f9-104">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="c25f9-105">IPV6 Şu anda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="c25f9-105">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c25f9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c25f9-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a><span data-ttu-id="c25f9-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c25f9-107">Parameters</span></span>  

 `cchHostName`  
 <span data-ttu-id="c25f9-108">'ndaki Arabelleğin karakter cinsinden boyutu `szHostName` .</span><span class="sxs-lookup"><span data-stu-id="c25f9-108">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="c25f9-109">Bu parametre 0 (sıfır) ise null olmalıdır `szHostName` .</span><span class="sxs-lookup"><span data-stu-id="c25f9-109">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="c25f9-110">dışı Ana bilgisayar adı veya IP adresi içinde null Sonlandırıcı dahil olmak üzere karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="c25f9-110">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="c25f9-111">Bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="c25f9-111">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="c25f9-112">dışı Ana bilgisayar adını veya IP adresini içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="c25f9-112">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c25f9-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c25f9-113">Return Value</span></span>  

 <span data-ttu-id="c25f9-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="c25f9-114">S_OK</span></span>  
 <span data-ttu-id="c25f9-115">Ana bilgisayar adı veya IP adresi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c25f9-115">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="c25f9-116">E_FAIL (veya diğer E_ dönüş kodları)</span><span class="sxs-lookup"><span data-stu-id="c25f9-116">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c25f9-117">Ana bilgisayar adı veya IP adresi döndürülemiyor.</span><span class="sxs-lookup"><span data-stu-id="c25f9-117">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c25f9-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c25f9-118">Remarks</span></span>  

 <span data-ttu-id="c25f9-119">Bu yöntem, hata ayıklayıcı yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c25f9-119">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="c25f9-120">Birden çok çağrı paradigmasını izlemelidir: ilk çağrıda, çağıran her ikisine de null değeri geçirir `cchHostName` `szHostName` ve `pcchHostName` gereken arabelleğin boyutunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="c25f9-120">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer.</span></span> <span data-ttu-id="c25f9-121">İkinci çağrıda, daha önce döndürülen boyut geçirilir `cchHostName` ve uygun boyutta bir arabellek geçirilir `szHostName` .</span><span class="sxs-lookup"><span data-stu-id="c25f9-121">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c25f9-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c25f9-122">Requirements</span></span>  

 <span data-ttu-id="c25f9-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c25f9-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c25f9-124">**Üst bilgi:** CorDebug. IDL</span><span class="sxs-lookup"><span data-stu-id="c25f9-124">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="c25f9-125">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c25f9-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c25f9-126">**.NET Framework sürümleri:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="c25f9-126">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c25f9-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c25f9-127">See also</span></span>

- [<span data-ttu-id="c25f9-128">ICorDebugRemoteTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c25f9-128">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="c25f9-129">ICorDebug Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c25f9-129">ICorDebug Interface</span></span>](icordebug-interface.md)
