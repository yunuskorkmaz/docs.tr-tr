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
ms.openlocfilehash: 2f91891164f1f80617cab10347eb4a7a08762c10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140346"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="517a4-102">ICorPublishAppDomain::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="517a4-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="517a4-103">Bu [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)tarafından temsil edilen uygulama etki alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="517a4-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="517a4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="517a4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="517a4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="517a4-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="517a4-106">'ndaki `szName` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="517a4-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="517a4-107">dışı `szName` dizisinde döndürülen, null karakter dahil olmak üzere geniş karakter sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="517a4-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="517a4-108">dışı Adın kaydedileceği bir dizi.</span><span class="sxs-lookup"><span data-stu-id="517a4-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="517a4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="517a4-109">Remarks</span></span>  
 <span data-ttu-id="517a4-110">`szName` null değilse `GetName` yöntemi, `szName``cchName` karaktere (null Sonlandırıcı dahil) kopyalar.</span><span class="sxs-lookup"><span data-stu-id="517a4-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="517a4-111">`pcchName`null olmayan bir değer döndürülürse, ad içindeki gerçek karakter sayısı (null Sonlandırıcı dahil) `szName` dizisinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="517a4-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="517a4-112">`GetName` yöntemi, kaç karakter kopyalandığına bakmaksızın S_OK HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="517a4-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="517a4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="517a4-113">Requirements</span></span>  
 <span data-ttu-id="517a4-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="517a4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="517a4-115">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="517a4-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="517a4-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="517a4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="517a4-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="517a4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="517a4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="517a4-118">See also</span></span>

- [<span data-ttu-id="517a4-119">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="517a4-119">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
