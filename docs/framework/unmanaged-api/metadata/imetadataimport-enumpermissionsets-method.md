---
title: IMetaDataImport::EnumPermissionSets Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumPermissionSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 990910b8b30e9794550d71cf9eaf8cd53639f696
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492250"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="e64e0-102">IMetaDataImport::EnumPermissionSets Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e64e0-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="e64e0-103">Belirtilen meta veri kapsamdaki nesneler için izinleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="e64e0-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e64e0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e64e0-104">Syntax</span></span>  
  
```  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,   
   [in]      mdToken       tk,   
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e64e0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e64e0-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="e64e0-106">[out içinde] Numaralandırıcı bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e64e0-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="e64e0-107">Bu, bu yöntemin ilk çağrı için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e64e0-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="e64e0-108">[in] Olası en geniş kapsamı aramak için NULL veya arama kapsamını sınırlayan bir meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="e64e0-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="e64e0-109">[in] Bayrakları temsil eden <xref:System.Security.Permissions.SecurityAction> dahil edilecek değerleri `rPermission`, ya da tüm eylemleri döndürmek için sıfır.</span><span class="sxs-lookup"><span data-stu-id="e64e0-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="e64e0-110">[out] İzni simgeleri depolamak için kullanılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="e64e0-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="e64e0-111">[in] En büyük boyutunu `rPermission` dizisi.</span><span class="sxs-lookup"><span data-stu-id="e64e0-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="e64e0-112">[out] Döndürülen izni belirteçleri sayısı `rPermission`.</span><span class="sxs-lookup"><span data-stu-id="e64e0-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e64e0-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e64e0-113">Return Value</span></span>  
  
|<span data-ttu-id="e64e0-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e64e0-114">HRESULT</span></span>|<span data-ttu-id="e64e0-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e64e0-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="e64e0-116">`EnumPermissionSets` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e64e0-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="e64e0-117">Numaralandırılacak hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="e64e0-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="e64e0-118">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="e64e0-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e64e0-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e64e0-119">Requirements</span></span>  
 <span data-ttu-id="e64e0-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e64e0-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e64e0-121">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="e64e0-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e64e0-122">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e64e0-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e64e0-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e64e0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e64e0-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e64e0-124">See also</span></span>
- [<span data-ttu-id="e64e0-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e64e0-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="e64e0-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e64e0-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
