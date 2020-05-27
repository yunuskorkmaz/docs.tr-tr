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
ms.openlocfilehash: 576f4561ed782f091840ac378831110a1bfef9c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004705"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="5997d-102">IMetaDataEmit::DefineMemberRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5997d-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="5997d-103">Geçerli kapsam dışındaki bir modülün üyesine yönelik bir başvuru tanımlar ve bu başvuru tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="5997d-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5997d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5997d-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (
    [in]  mdToken           tkImport,
    [in]  LPCWSTR           szName,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMemberRef       *pmr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5997d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5997d-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="5997d-106">'ndaki Üye genel değilse hedef üyenin sınıfı veya arabirimi için belirteç; üye geneldir ise, `mdModuleRef` diğer dosyanın belirteci.</span><span class="sxs-lookup"><span data-stu-id="5997d-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="5997d-107">'ndaki Hedef üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="5997d-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="5997d-108">'ndaki Hedef üyenin imzası.</span><span class="sxs-lookup"><span data-stu-id="5997d-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="5997d-109">'ndaki İçindeki bayt sayısı `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="5997d-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="5997d-110">dışı `mdMemberRef`Atanan belirteç.</span><span class="sxs-lookup"><span data-stu-id="5997d-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5997d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5997d-111">Requirements</span></span>  
 <span data-ttu-id="5997d-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5997d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5997d-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5997d-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5997d-114">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5997d-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5997d-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5997d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5997d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5997d-116">See also</span></span>

- [<span data-ttu-id="5997d-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5997d-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="5997d-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5997d-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
