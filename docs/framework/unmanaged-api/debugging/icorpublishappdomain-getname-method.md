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
ms.openlocfilehash: 4325d61d12a66b17f88e5e368cbbc7806d0a3ec5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790717"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="85e81-102">ICorPublishAppDomain::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85e81-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="85e81-103">Bu [ICorPublishAppDomain](icorpublishappdomain-interface.md)tarafından temsil edilen uygulama etki alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="85e81-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85e81-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85e81-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85e81-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="85e81-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="85e81-106">'ndaki `szName` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="85e81-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="85e81-107">dışı `szName` dizisinde döndürülen, null karakter dahil olmak üzere geniş karakter sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="85e81-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="85e81-108">dışı Adın kaydedileceği bir dizi.</span><span class="sxs-lookup"><span data-stu-id="85e81-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85e81-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="85e81-109">Remarks</span></span>  
 <span data-ttu-id="85e81-110">`szName` null değilse `GetName` yöntemi, `szName``cchName` karaktere (null Sonlandırıcı dahil) kopyalar.</span><span class="sxs-lookup"><span data-stu-id="85e81-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="85e81-111">`pcchName`null olmayan bir değer döndürülürse, ad içindeki gerçek karakter sayısı (null Sonlandırıcı dahil) `szName` dizisinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="85e81-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="85e81-112">`GetName` yöntemi, kaç karakter kopyalandığına bakılmaksızın HRESULT S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="85e81-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85e81-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85e81-113">Requirements</span></span>  
 <span data-ttu-id="85e81-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85e81-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85e81-115">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="85e81-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="85e81-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="85e81-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85e81-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85e81-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85e81-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85e81-118">See also</span></span>

- [<span data-ttu-id="85e81-119">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85e81-119">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
