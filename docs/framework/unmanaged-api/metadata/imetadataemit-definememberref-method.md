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
ms.openlocfilehash: e371330336002c673f2c54d882e70dbed41b743c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175843"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="c4f19-102">IMetaDataEmit::DefineMemberRef Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4f19-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="c4f19-103">Geçerli kapsam dışında bir modülün üyesine başvuru tanımlar ve bu başvuru tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="c4f19-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4f19-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4f19-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (
    [in]  mdToken           tkImport,
    [in]  LPCWSTR           szName,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMemberRef       *pmr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4f19-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4f19-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="c4f19-106">[içinde] Üye genel değilse, hedef üyenin sınıfı veya arabirimi için belirteç; üye genel ise, `mdModuleRef` diğer dosyaiçin belirteç.</span><span class="sxs-lookup"><span data-stu-id="c4f19-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="c4f19-107">[içinde] Hedef üyenin adı.</span><span class="sxs-lookup"><span data-stu-id="c4f19-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="c4f19-108">[içinde] Hedef üyenin imzası.</span><span class="sxs-lookup"><span data-stu-id="c4f19-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="c4f19-109">[içinde] Bayt `pvSigBlob`sayısı.</span><span class="sxs-lookup"><span data-stu-id="c4f19-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="c4f19-110">[çıkış] Atanan `mdMemberRef` belirteç.</span><span class="sxs-lookup"><span data-stu-id="c4f19-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4f19-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4f19-111">Requirements</span></span>  
 <span data-ttu-id="c4f19-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4f19-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4f19-113">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c4f19-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c4f19-114">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="c4f19-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4f19-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4f19-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4f19-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4f19-116">See also</span></span>

- [<span data-ttu-id="c4f19-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4f19-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c4f19-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4f19-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
