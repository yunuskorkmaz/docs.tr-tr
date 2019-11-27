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
ms.openlocfilehash: 696389b51328e167212fb2292a873c34b9263811
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431826"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="8d45c-102">IMetaDataEmit::DefineMemberRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d45c-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="8d45c-103">Geçerli kapsam dışındaki bir modülün üyesine yönelik bir başvuru tanımlar ve bu başvuru tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="8d45c-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d45c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d45c-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (   
    [in]  mdToken           tkImport,   
    [in]  LPCWSTR           szName,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [out] mdMemberRef       *pmr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d45c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8d45c-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="8d45c-106">'ndaki Üye genel değilse hedef üyenin sınıfı veya arabirimi için belirteç; üye geneldir ise, bu dosya için `mdModuleRef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="8d45c-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="8d45c-107">'ndaki Hedef üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="8d45c-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8d45c-108">'ndaki Hedef üyenin imzası.</span><span class="sxs-lookup"><span data-stu-id="8d45c-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8d45c-109">'ndaki `pvSigBlob`bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="8d45c-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="8d45c-110">dışı `mdMemberRef` belirteci atandı.</span><span class="sxs-lookup"><span data-stu-id="8d45c-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d45c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d45c-111">Requirements</span></span>  
 <span data-ttu-id="8d45c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d45c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d45c-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8d45c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8d45c-114">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="8d45c-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d45c-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d45c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d45c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d45c-116">See also</span></span>

- [<span data-ttu-id="8d45c-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d45c-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="8d45c-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d45c-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
