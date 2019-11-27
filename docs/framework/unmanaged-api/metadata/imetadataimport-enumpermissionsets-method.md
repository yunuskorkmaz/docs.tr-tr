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
ms.openlocfilehash: 9d0f443b5b7d2d358534e888c3fc84ad3f554119
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450049"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="d3e77-102">IMetaDataImport::EnumPermissionSets Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3e77-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="d3e77-103">Belirtilen meta veri kapsamındaki nesneler için izinleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="d3e77-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3e77-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3e77-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d3e77-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3e77-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="d3e77-106">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d3e77-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="d3e77-107">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3e77-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="d3e77-108">'ndaki Aramanın kapsamını sınırlayan bir meta veri belirteci veya mümkün olan en geniş kapsamı aramak için NULL.</span><span class="sxs-lookup"><span data-stu-id="d3e77-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="d3e77-109">'ndaki Tüm eylemleri döndürmek için `rPermission`veya sıfıra dahil edilecek <xref:System.Security.Permissions.SecurityAction> değerlerini temsil eden bayraklar.</span><span class="sxs-lookup"><span data-stu-id="d3e77-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="d3e77-110">dışı Izin belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="d3e77-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="d3e77-111">'ndaki `rPermission` dizisinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="d3e77-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="d3e77-112">dışı `rPermission`' de döndürülen Izin belirteçleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="d3e77-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3e77-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d3e77-113">Return Value</span></span>  
  
|<span data-ttu-id="d3e77-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d3e77-114">HRESULT</span></span>|<span data-ttu-id="d3e77-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3e77-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d3e77-116">`EnumPermissionSets` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d3e77-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d3e77-117">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="d3e77-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="d3e77-118">Bu durumda `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="d3e77-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3e77-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3e77-119">Requirements</span></span>  
 <span data-ttu-id="d3e77-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3e77-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3e77-121">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d3e77-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3e77-122">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d3e77-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d3e77-123">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3e77-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e77-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3e77-124">See also</span></span>

- [<span data-ttu-id="d3e77-125">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3e77-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d3e77-126">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3e77-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
