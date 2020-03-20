---
title: IMetaDataImport::EnumMemberRefs Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMemberRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type:
- apiref
ms.openlocfilehash: b8a65b0748fec0e474d8b3b5dc03473fbd716108
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177326"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="72d26-102">IMetaDataImport::EnumMemberRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72d26-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="72d26-103">Belirtilen tipteki üyeleri temsil eden ÜyeRef belirteçlerini oyalar.</span><span class="sxs-lookup"><span data-stu-id="72d26-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72d26-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72d26-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,
   [in]   mdToken        tkParent,
   [out]  mdMemberRef    rMemberRefs[],
   [in]   ULONG          cMax,
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72d26-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72d26-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="72d26-106">[içinde, dışarı] Sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="72d26-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="72d26-107">[içinde] Üyeleri numaralandırılacak tür için TypeDef, TypeRef, MethodDef veya ModuleRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="72d26-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="72d26-108">[çıkış] ÜyeRef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="72d26-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="72d26-109">[içinde] `rMemberRefs` Dizinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="72d26-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="72d26-110">[çıkış] ÜyeRef belirteçlerinin gerçek sayısı `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="72d26-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72d26-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="72d26-111">Return Value</span></span>  
  
|<span data-ttu-id="72d26-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72d26-112">HRESULT</span></span>|<span data-ttu-id="72d26-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72d26-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="72d26-114">`EnumMemberRefs`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="72d26-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="72d26-115">Sayısallaştırmak için ÜyeRef belirteçleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="72d26-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="72d26-116">Bu durumda, `pcTokens` sıfıra.</span><span class="sxs-lookup"><span data-stu-id="72d26-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72d26-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72d26-117">Requirements</span></span>  
 <span data-ttu-id="72d26-118">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72d26-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72d26-119">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="72d26-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72d26-120">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="72d26-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72d26-121">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72d26-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72d26-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72d26-122">See also</span></span>

- [<span data-ttu-id="72d26-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72d26-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="72d26-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72d26-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
