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
ms.openlocfilehash: d6b05333b9e02c4202c0fd9bdee9b5c055aa4da3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694366"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="5c3f5-102">ICorPublishAppDomain::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c3f5-102">ICorPublishAppDomain::GetName Method</span></span>

<span data-ttu-id="5c3f5-103">Bu [ICorPublishAppDomain](icorpublishappdomain-interface.md)tarafından temsil edilen uygulama etki alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="5c3f5-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c3f5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5c3f5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c3f5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c3f5-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="5c3f5-106">'ndaki `szName` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="5c3f5-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5c3f5-107">dışı Dizide döndürülen, null karakter dahil olmak üzere geniş karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="5c3f5-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="5c3f5-108">dışı Adın kaydedileceği bir dizi.</span><span class="sxs-lookup"><span data-stu-id="5c3f5-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c3f5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c3f5-109">Remarks</span></span>  

 <span data-ttu-id="5c3f5-110">`szName`Null değilse, `GetName` yöntemi `cchName` içine (null Sonlandırıcı dahil) kadar karakter kopyalar `szName` .</span><span class="sxs-lookup"><span data-stu-id="5c3f5-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="5c3f5-111">İçinde null olmayan bir değer döndürülürse `pcchName` , ad içindeki gerçek karakter sayısı (null Sonlandırıcı dahil) `szName` dizide depolanır.</span><span class="sxs-lookup"><span data-stu-id="5c3f5-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="5c3f5-112">`GetName`Yöntemi, kaç karakterin kopyalandığına BAKıLMAKSıZıN HRESULT s_ok döndürür.</span><span class="sxs-lookup"><span data-stu-id="5c3f5-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c3f5-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c3f5-113">Requirements</span></span>  

 <span data-ttu-id="5c3f5-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c3f5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c3f5-115">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="5c3f5-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="5c3f5-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5c3f5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c3f5-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c3f5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c3f5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c3f5-118">See also</span></span>

- [<span data-ttu-id="5c3f5-119">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c3f5-119">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
