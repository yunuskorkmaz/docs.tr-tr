---
title: ICorPublishAppDomain::GetName Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishAppDomain.GetName
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9807f914c767cc212bf97d83042e76d42a3d9440
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="82f02-102">ICorPublishAppDomain::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="82f02-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="82f02-103">Bu tarafından temsil edilen uygulama etki alanı adını alır [Icorpublishappdomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="82f02-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82f02-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82f02-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82f02-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82f02-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="82f02-106">[in] Boyutunu `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="82f02-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="82f02-107">[out] Null döndürdü karakteri de dahil olmak üzere geniş karakter sayısını gösteren bir işaretçi `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="82f02-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="82f02-108">[out] Dizi adı depolanacağı.</span><span class="sxs-lookup"><span data-stu-id="82f02-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82f02-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="82f02-109">Remarks</span></span>  
 <span data-ttu-id="82f02-110">Varsa `szName` boş olduğundan `GetName` yöntemi kopyalar kadar `cchName` (null Sonlandırıcı dahil) karakterlere `szName`.</span><span class="sxs-lookup"><span data-stu-id="82f02-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="82f02-111">Null olmayan bir döndürülürse `pcchName`, gerçek (null Sonlandırıcı dahil) adı karakter sayısı depolanan `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="82f02-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="82f02-112">`GetName` Yöntemi kaç karakterin kopyalanan bakılmaksızın bir S_OK HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="82f02-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82f02-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82f02-113">Requirements</span></span>  
 <span data-ttu-id="82f02-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82f02-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82f02-115">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="82f02-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="82f02-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82f02-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82f02-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82f02-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f02-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="82f02-118">See Also</span></span>  
 [<span data-ttu-id="82f02-119">Icorpublishappdomain arabirimi</span><span class="sxs-lookup"><span data-stu-id="82f02-119">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
