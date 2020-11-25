---
title: IMetaDataEmit::DefineMemberRef Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
ms.openlocfilehash: 597ba1884351ee6d8b7eb7e0f3f01ce3ad733304
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716661"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="c1ade-102">IMetaDataEmit::DefineMemberRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1ade-102">IMetaDataEmit::DefineMemberRef Method</span></span>

<span data-ttu-id="c1ade-103">Geçerli kapsam dışındaki bir modülün üyesine yönelik bir başvuru tanımlar ve bu başvuru tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="c1ade-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1ade-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c1ade-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (
    [in]  mdToken           tkImport,
    [in]  LPCWSTR           szName,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMemberRef       *pmr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1ade-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1ade-105">Parameters</span></span>  

 `tkImport`  
 <span data-ttu-id="c1ade-106">'ndaki Üye genel değilse hedef üyenin sınıfı veya arabirimi için belirteç; üye geneldir ise, `mdModuleRef` diğer dosyanın belirteci.</span><span class="sxs-lookup"><span data-stu-id="c1ade-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="c1ade-107">'ndaki Hedef üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="c1ade-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="c1ade-108">'ndaki Hedef üyenin imzası.</span><span class="sxs-lookup"><span data-stu-id="c1ade-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="c1ade-109">'ndaki İçindeki bayt sayısı `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="c1ade-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="c1ade-110">dışı `mdMemberRef` Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="c1ade-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1ade-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1ade-111">Requirements</span></span>  

 <span data-ttu-id="c1ade-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1ade-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1ade-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c1ade-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1ade-114">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c1ade-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1ade-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1ade-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ade-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1ade-116">See also</span></span>

- [<span data-ttu-id="c1ade-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1ade-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c1ade-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1ade-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
