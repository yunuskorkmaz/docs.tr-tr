---
title: IMetaDataEmit::DefineUserString Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type:
- apiref
ms.openlocfilehash: a71d8694ec8c5bd35ecd3e98ed32e05bc7b382fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177612"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="4e251-102">IMetaDataEmit::DefineUserString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e251-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="4e251-103">Belirtilen gerçek dize için bir meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="4e251-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e251-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e251-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (
    [in]  LPCWSTR     szString,
    [in]  ULONG       cchString,
    [out] mdString    *pstk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e251-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e251-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="4e251-106">[içinde] Depolamak için kullanıcı dizesi.</span><span class="sxs-lookup"><span data-stu-id="4e251-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="4e251-107">[içinde] Geniş karakterlerin `szString`sayısı.</span><span class="sxs-lookup"><span data-stu-id="4e251-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="4e251-108">[çıkış] Atanan dize belirteci.</span><span class="sxs-lookup"><span data-stu-id="4e251-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e251-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e251-109">Requirements</span></span>  
 <span data-ttu-id="4e251-110">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e251-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e251-111">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4e251-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4e251-112">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4e251-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e251-113">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e251-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e251-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e251-114">See also</span></span>

- [<span data-ttu-id="4e251-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e251-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4e251-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e251-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
