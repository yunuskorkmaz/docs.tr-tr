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
ms.openlocfilehash: 762c637696fdf79ccab6702918b5bf962ea55903
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178414"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="db746-102">ICorPublishAppDomain::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="db746-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="db746-103">Bu [iCorPublishAppDomain](icorpublishappdomain-interface.md)tarafından temsil edilen uygulama etki alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="db746-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db746-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db746-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db746-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db746-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="db746-106">[içinde] `szName` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="db746-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="db746-107">[çıkış] Null karakteri de dahil olmak üzere geniş karakter sayısına `szName` işaretçi, dizide döndürülür.</span><span class="sxs-lookup"><span data-stu-id="db746-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="db746-108">[çıkış] Adın depolandığı bir dizi.</span><span class="sxs-lookup"><span data-stu-id="db746-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db746-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db746-109">Remarks</span></span>  
 <span data-ttu-id="db746-110">Null `szName` olmayan ise, `GetName` yöntem karakterlere `cchName` kadar kopyalar (null terminator `szName`dahil) içine .</span><span class="sxs-lookup"><span data-stu-id="db746-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="db746-111">Null olmayan bir döndürülürse, `pcchName`addaki gerçek karakter sayısı (null sonlandırıcı dahil) `szName` dizide depolanır.</span><span class="sxs-lookup"><span data-stu-id="db746-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="db746-112">Yöntem, `GetName` kaç karakter kopyalandığından bağımsız olarak bir S_OK HRESULT döndürür.</span><span class="sxs-lookup"><span data-stu-id="db746-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db746-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db746-113">Requirements</span></span>  
 <span data-ttu-id="db746-114">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db746-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db746-115">**Üstbilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="db746-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="db746-116">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db746-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db746-117">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db746-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db746-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db746-118">See also</span></span>

- [<span data-ttu-id="db746-119">ICorPublishAppDomain Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db746-119">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
