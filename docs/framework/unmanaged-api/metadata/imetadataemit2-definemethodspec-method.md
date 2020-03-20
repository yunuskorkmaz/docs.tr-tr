---
title: IMetaDataEmit2::DefineMethodSpec Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineMethodSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type:
- apiref
ms.openlocfilehash: a5d9342b8bfe650106ccf9daf2a91dfbcd575446
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175546"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="4a038-102">IMetaDataEmit2::DefineMethodSpec Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4a038-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="4a038-103">Yöntemin genel bir örneğini oluşturur ve tanıma bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="4a038-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a038-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a038-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a038-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4a038-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="4a038-106">[içinde] Genel örneği oluşturmak için yöntem için bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="4a038-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="4a038-107">Belirteç türü `mdMethodDef` veya `mdMemberRef`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4a038-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="4a038-108">[içinde] Yöntemin ikili COM+ imzasına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4a038-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="4a038-109">[içinde] Boyutu, bayt, ve. `pvSigBlob`</span><span class="sxs-lookup"><span data-stu-id="4a038-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="4a038-110">[çıkış] Yöntemin meta veri imza tanımına bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="4a038-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a038-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a038-111">Requirements</span></span>  
 <span data-ttu-id="4a038-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a038-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a038-113">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4a038-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4a038-114">**Kütüphane:** MsCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="4a038-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4a038-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a038-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a038-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a038-116">See also</span></span>

- [<span data-ttu-id="4a038-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a038-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="4a038-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a038-118">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
