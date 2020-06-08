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
ms.openlocfilehash: 8e067dc4943e6847177c13a683703e3a649a49e4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503828"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="eb87a-102">IMetaDataEmit2::DefineMethodSpec Yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb87a-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="eb87a-103">Bir yönteminin genel bir örneğini oluşturur ve tanımına bir belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="eb87a-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb87a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="eb87a-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb87a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb87a-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="eb87a-106">'ndaki Genel örneğin oluşturulacağı yöntemi için bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="eb87a-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="eb87a-107">Belirtecin veya türünde olması gerekir `mdMethodDef` `mdMemberRef` .</span><span class="sxs-lookup"><span data-stu-id="eb87a-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="eb87a-108">'ndaki Metodun ikili COM+ imzasına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eb87a-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="eb87a-109">'ndaki Bayt cinsinden boyutu `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="eb87a-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="eb87a-110">dışı Metodun meta veri imza tanımına belirteç.</span><span class="sxs-lookup"><span data-stu-id="eb87a-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb87a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb87a-111">Requirements</span></span>  
 <span data-ttu-id="eb87a-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb87a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb87a-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="eb87a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eb87a-114">**Kitaplık:** MsCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="eb87a-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eb87a-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb87a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb87a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb87a-116">See also</span></span>

- [<span data-ttu-id="eb87a-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb87a-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="eb87a-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb87a-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
