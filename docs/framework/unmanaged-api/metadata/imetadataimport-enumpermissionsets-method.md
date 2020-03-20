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
ms.openlocfilehash: e628cf5dab8006b0df0ab6c60dc995cd0c6bb29d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175453"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="5d329-102">IMetaDataImport::EnumPermissionSets Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d329-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="5d329-103">Belirli bir meta veri kapsamındaki nesnelerin izinlerini oyalar.</span><span class="sxs-lookup"><span data-stu-id="5d329-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d329-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d329-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,
   [in]      mdToken       tk,
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d329-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d329-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="5d329-106">[içinde, dışarı] Sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5d329-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="5d329-107">Bu yöntemin ilk araması için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5d329-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="5d329-108">[içinde] Aramanın kapsamını sınırlayan bir meta veri belirteci veya mümkün olan en geniş kapsamı aramak için NULL.</span><span class="sxs-lookup"><span data-stu-id="5d329-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="5d329-109">[içinde] Tüm eylemleri <xref:System.Security.Permissions.SecurityAction> döndürmek için `rPermission`dahil olacak değerleri veya sıfırı temsil eden bayraklar.</span><span class="sxs-lookup"><span data-stu-id="5d329-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="5d329-110">[çıkış] İzin belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="5d329-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="5d329-111">[içinde] `rPermission` Dizinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="5d329-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="5d329-112">[çıkış] Döndürülen İzin belirteçlerinin `rPermission`sayısı.</span><span class="sxs-lookup"><span data-stu-id="5d329-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d329-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5d329-113">Return Value</span></span>  
  
|<span data-ttu-id="5d329-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5d329-114">HRESULT</span></span>|<span data-ttu-id="5d329-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d329-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5d329-116">`EnumPermissionSets`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5d329-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5d329-117">Sayısala rendelemek için hiçbir belirteçleri vardır.</span><span class="sxs-lookup"><span data-stu-id="5d329-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="5d329-118">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="5d329-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5d329-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d329-119">Requirements</span></span>  
 <span data-ttu-id="5d329-120">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d329-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d329-121">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5d329-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5d329-122">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="5d329-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5d329-123">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d329-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d329-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d329-124">See also</span></span>

- [<span data-ttu-id="5d329-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d329-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5d329-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d329-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
