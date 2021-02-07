---
description: ': ICorPublishAppDomain:: GetName metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 05b1b14f7e0db371b29059ec3d44333ac40428e9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721807"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="05490-103">ICorPublishAppDomain::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05490-103">ICorPublishAppDomain::GetName Method</span></span>

<span data-ttu-id="05490-104">Bu [ICorPublishAppDomain](icorpublishappdomain-interface.md)tarafından temsil edilen uygulama etki alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="05490-104">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05490-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05490-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05490-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05490-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="05490-107">'ndaki `szName` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="05490-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="05490-108">dışı Dizide döndürülen, null karakter dahil olmak üzere geniş karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="05490-108">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="05490-109">dışı Adın kaydedileceği bir dizi.</span><span class="sxs-lookup"><span data-stu-id="05490-109">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05490-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05490-110">Remarks</span></span>  

 <span data-ttu-id="05490-111">`szName`Null değilse, `GetName` yöntemi `cchName` içine (null Sonlandırıcı dahil) kadar karakter kopyalar `szName` .</span><span class="sxs-lookup"><span data-stu-id="05490-111">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="05490-112">İçinde null olmayan bir değer döndürülürse `pcchName` , ad içindeki gerçek karakter sayısı (null Sonlandırıcı dahil) `szName` dizide depolanır.</span><span class="sxs-lookup"><span data-stu-id="05490-112">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="05490-113">`GetName`Yöntemi, kaç karakterin kopyalandığına BAKıLMAKSıZıN HRESULT s_ok döndürür.</span><span class="sxs-lookup"><span data-stu-id="05490-113">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05490-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05490-114">Requirements</span></span>  

 <span data-ttu-id="05490-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05490-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05490-116">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="05490-116">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="05490-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="05490-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05490-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05490-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05490-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05490-119">See also</span></span>

- [<span data-ttu-id="05490-120">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05490-120">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
