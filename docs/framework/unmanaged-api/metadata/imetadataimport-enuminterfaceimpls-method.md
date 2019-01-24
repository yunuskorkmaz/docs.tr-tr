---
title: IMetaDataImport::EnumInterfaceImpls Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c94960478e6b2eb4e7b8f1e9592b0831af3ec686
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603774"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="e4afe-102">IMetaDataImport::EnumInterfaceImpls Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e4afe-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="e4afe-103">Arabirim uygulamalarına temsil eden MethodDef belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="e4afe-103">Enumerates MethodDef tokens representing interface implementations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4afe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4afe-104">Syntax</span></span>  
  
```  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4afe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4afe-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e4afe-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e4afe-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="e4afe-107">[in] Arabirim uygulamaları gösteren, MethodDef sıralanması belirteçleridir TypeDef belirteç.</span><span class="sxs-lookup"><span data-stu-id="e4afe-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="e4afe-108">[out] Dizi MethodDef simgeleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e4afe-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e4afe-109">[in] En büyük boyutunu `rImpls` dizisi.</span><span class="sxs-lookup"><span data-stu-id="e4afe-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="e4afe-110">[out] Döndürülen belirteç gerçek sayısını `rImpls`.</span><span class="sxs-lookup"><span data-stu-id="e4afe-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4afe-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e4afe-111">Return Value</span></span>  
  
|<span data-ttu-id="e4afe-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e4afe-112">HRESULT</span></span>|<span data-ttu-id="e4afe-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e4afe-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e4afe-114">`EnumInterfaceImpls` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e4afe-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e4afe-115">Numaralandırılacak hiçbir MethodDef belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="e4afe-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="e4afe-116">Bu durumda, `pcImpls` sıfır olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e4afe-116">In that case, `pcImpls` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4afe-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4afe-117">Requirements</span></span>  
 <span data-ttu-id="e4afe-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4afe-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4afe-119">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="e4afe-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e4afe-120">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e4afe-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e4afe-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4afe-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4afe-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4afe-122">See also</span></span>
- [<span data-ttu-id="e4afe-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4afe-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e4afe-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4afe-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
