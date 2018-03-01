---
title: ICorPublishAppDomain::GetName Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9808d99406f2b83a6ee4e4a634210bf9c894bfd7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="082d4-102">ICorPublishAppDomain::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="082d4-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="082d4-103">Bu tarafından temsil edilen uygulama etki alanı adını alır [Icorpublishappdomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="082d4-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="082d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="082d4-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="082d4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="082d4-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="082d4-106">[in] Boyutunu `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="082d4-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="082d4-107">[out] Null döndürdü karakteri de dahil olmak üzere geniş karakter sayısını gösteren bir işaretçi `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="082d4-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="082d4-108">[out] Dizi adı depolanacağı.</span><span class="sxs-lookup"><span data-stu-id="082d4-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="082d4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="082d4-109">Remarks</span></span>  
 <span data-ttu-id="082d4-110">Varsa `szName` boş olduğundan `GetName` yöntemi kopyalar kadar `cchName` (null Sonlandırıcı dahil) karakterlere `szName`.</span><span class="sxs-lookup"><span data-stu-id="082d4-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="082d4-111">Null olmayan bir döndürülürse `pcchName`, gerçek (null Sonlandırıcı dahil) adı karakter sayısı depolanan `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="082d4-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="082d4-112">`GetName` Yöntemi kaç karakterin kopyalanan bakılmaksızın bir S_OK HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="082d4-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="082d4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="082d4-113">Requirements</span></span>  
 <span data-ttu-id="082d4-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="082d4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="082d4-115">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="082d4-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="082d4-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="082d4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="082d4-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="082d4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="082d4-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="082d4-118">See Also</span></span>  
 [<span data-ttu-id="082d4-119">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="082d4-119">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
