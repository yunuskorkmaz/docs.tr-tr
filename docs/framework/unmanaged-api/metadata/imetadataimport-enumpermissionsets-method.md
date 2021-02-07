---
description: 'Şu konuda daha fazla bilgi edinin: IMetaDataImport:: Trmpermissionsets yöntemi'
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
ms.openlocfilehash: 7138cb2a89ecbea1afbf3e9fccfcac26e7e0fd7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688760"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="632db-103">IMetaDataImport::EnumPermissionSets Yöntemi</span><span class="sxs-lookup"><span data-stu-id="632db-103">IMetaDataImport::EnumPermissionSets Method</span></span>

<span data-ttu-id="632db-104">Belirtilen meta veri kapsamındaki nesneler için izinleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="632db-104">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="632db-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="632db-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="632db-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="632db-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="632db-107">[in, out] Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="632db-107">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="632db-108">Bu yöntemin ilk çağrısı için bu NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="632db-108">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="632db-109">'ndaki Aramanın kapsamını sınırlayan bir meta veri belirteci veya mümkün olan en geniş kapsamı aramak için NULL.</span><span class="sxs-lookup"><span data-stu-id="632db-109">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="632db-110">'ndaki <xref:System.Security.Permissions.SecurityAction> `rPermission` Tüm eylemleri döndürmek için, veya sıfıra eklenecek değerleri temsil eden bayraklar.</span><span class="sxs-lookup"><span data-stu-id="632db-110">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="632db-111">dışı Izin belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="632db-111">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="632db-112">'ndaki Dizinin en büyük boyutu `rPermission` .</span><span class="sxs-lookup"><span data-stu-id="632db-112">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="632db-113">dışı İçinde döndürülen Izin belirteçleri sayısı `rPermission` .</span><span class="sxs-lookup"><span data-stu-id="632db-113">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="632db-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="632db-114">Return Value</span></span>  
  
|<span data-ttu-id="632db-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="632db-115">HRESULT</span></span>|<span data-ttu-id="632db-116">Description</span><span class="sxs-lookup"><span data-stu-id="632db-116">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="632db-117">`EnumPermissionSets` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="632db-117">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="632db-118">Numaralandırılacak belirteç yok.</span><span class="sxs-lookup"><span data-stu-id="632db-118">There are no tokens to enumerate.</span></span> <span data-ttu-id="632db-119">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="632db-119">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="632db-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="632db-120">Requirements</span></span>  

 <span data-ttu-id="632db-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="632db-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="632db-122">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="632db-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="632db-123">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="632db-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="632db-124">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="632db-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="632db-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="632db-125">See also</span></span>

- [<span data-ttu-id="632db-126">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="632db-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="632db-127">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="632db-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
