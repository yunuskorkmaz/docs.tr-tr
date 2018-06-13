---
title: ICorPublishAppDomain::GetName Metodu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 796f8ea42cc5cbe13729f7b92e15bc214d62734d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423864"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="0ba72-102">ICorPublishAppDomain::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="0ba72-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="0ba72-103">Bu tarafından temsil edilen uygulama etki alanı adını alır [Icorpublishappdomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="0ba72-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ba72-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0ba72-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ba72-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0ba72-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="0ba72-106">[in] Boyutunu `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="0ba72-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="0ba72-107">[out] Null döndürdü karakteri de dahil olmak üzere geniş karakter sayısını gösteren bir işaretçi `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="0ba72-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="0ba72-108">[out] Dizi adı depolanacağı.</span><span class="sxs-lookup"><span data-stu-id="0ba72-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ba72-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0ba72-109">Remarks</span></span>  
 <span data-ttu-id="0ba72-110">Varsa `szName` boş olduğundan `GetName` yöntemi kopyalar kadar `cchName` (null Sonlandırıcı dahil) karakterlere `szName`.</span><span class="sxs-lookup"><span data-stu-id="0ba72-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="0ba72-111">Null olmayan bir döndürülürse `pcchName`, gerçek (null Sonlandırıcı dahil) adı karakter sayısı depolanan `szName` dizi.</span><span class="sxs-lookup"><span data-stu-id="0ba72-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="0ba72-112">`GetName` Yöntemi kaç karakterin kopyalanan bakılmaksızın bir S_OK HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="0ba72-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ba72-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0ba72-113">Requirements</span></span>  
 <span data-ttu-id="0ba72-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ba72-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ba72-115">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="0ba72-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="0ba72-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ba72-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ba72-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ba72-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ba72-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0ba72-118">See Also</span></span>  
 [<span data-ttu-id="0ba72-119">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0ba72-119">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
