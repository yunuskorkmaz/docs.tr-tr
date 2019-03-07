---
title: ICorPublishAppDomain::GetName Yöntemi
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
ms.openlocfilehash: 4e44ee4a1a2cdd40d93c487ccb41316f729038a5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469150"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="119f0-102">ICorPublishAppDomain::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="119f0-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="119f0-103">Bu tarafından temsil edilen uygulama etki alanının adını alır [Icorpublishappdomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="119f0-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="119f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="119f0-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="119f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="119f0-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="119f0-106">[in] Boyutu `szName` dizisi.</span><span class="sxs-lookup"><span data-stu-id="119f0-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="119f0-107">[out] Döndürülen null karakter de dahil olmak üzere geniş karakter sayısı için bir işaretçi `szName` dizisi.</span><span class="sxs-lookup"><span data-stu-id="119f0-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="119f0-108">[out] Dizi adı depolanacağı.</span><span class="sxs-lookup"><span data-stu-id="119f0-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="119f0-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="119f0-109">Remarks</span></span>  
 <span data-ttu-id="119f0-110">Varsa `szName` kullanmaktan, `GetName` yöntemi kopyalar kadar `cchName` (null Sonlandırıcı dahil) karakterlerine `szName`.</span><span class="sxs-lookup"><span data-stu-id="119f0-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="119f0-111">Null olmayan bir döndürülürse `pcchName`, (null Sonlandırıcı dahil) adında gerçek sayısını depolanan `szName` dizisi.</span><span class="sxs-lookup"><span data-stu-id="119f0-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="119f0-112">`GetName` Yöntemi karakterlerinin kaçının tutulacağını kopyalanan bağımsız olarak bir S_OK HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="119f0-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="119f0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="119f0-113">Requirements</span></span>  
 <span data-ttu-id="119f0-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="119f0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="119f0-115">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="119f0-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="119f0-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="119f0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="119f0-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="119f0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="119f0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="119f0-118">See also</span></span>
- [<span data-ttu-id="119f0-119">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="119f0-119">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
