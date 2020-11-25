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
ms.openlocfilehash: d8b02e85efc2cd7364690dd42104a313ba6ec272
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711461"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="101bf-102">IMetaDataImport::EnumMemberRefs Yöntemi</span><span class="sxs-lookup"><span data-stu-id="101bf-102">IMetaDataImport::EnumMemberRefs Method</span></span>

<span data-ttu-id="101bf-103">Belirtilen türdeki üyeleri temsil eden MemberRef belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="101bf-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="101bf-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="101bf-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,
   [in]   mdToken        tkParent,
   [out]  mdMemberRef    rMemberRefs[],
   [in]   ULONG          cMax,
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="101bf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="101bf-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="101bf-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="101bf-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="101bf-107">'ndaki Üyeleri numaralandırılmış olan tür için bir TypeDef, TypeRef, MethodDef veya ModuleRef belirteci.</span><span class="sxs-lookup"><span data-stu-id="101bf-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="101bf-108">dışı MemberRef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="101bf-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="101bf-109">'ndaki Dizinin en büyük boyutu `rMemberRefs` .</span><span class="sxs-lookup"><span data-stu-id="101bf-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="101bf-110">dışı İçinde döndürülen MemberRef belirteçleri gerçek sayısı `rMemberRefs` .</span><span class="sxs-lookup"><span data-stu-id="101bf-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="101bf-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="101bf-111">Return Value</span></span>  
  
|<span data-ttu-id="101bf-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="101bf-112">HRESULT</span></span>|<span data-ttu-id="101bf-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="101bf-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="101bf-114">`EnumMemberRefs` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="101bf-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="101bf-115">Numaralandırılacak bir MemberRef belirteci yok.</span><span class="sxs-lookup"><span data-stu-id="101bf-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="101bf-116">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="101bf-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="101bf-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="101bf-117">Requirements</span></span>  

 <span data-ttu-id="101bf-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="101bf-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="101bf-119">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="101bf-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="101bf-120">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="101bf-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="101bf-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="101bf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="101bf-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="101bf-122">See also</span></span>

- [<span data-ttu-id="101bf-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="101bf-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="101bf-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="101bf-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
