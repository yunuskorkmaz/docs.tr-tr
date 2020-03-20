---
title: IMetaDataImport::GetEventProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetEventProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type:
- apiref
ms.openlocfilehash: 306c1748b4997309ee15fb7751bc818b0287aaf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177265"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="a3cc7-102">IMetaDataImport::GetEventProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a3cc7-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="a3cc7-103">Bildirim türü, temsilciler için ekleme ve kaldırma yöntemleri ve herhangi bir bayrak ve diğer ilişkili veriler de dahil olmak üzere, belirtilen olay belirteci tarafından temsil edilen olay için meta veri bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="a3cc7-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3cc7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3cc7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventProps (  
   [in]  mdEvent       ev,  
   [out] mdTypeDef     *pClass,
   [out] LPCWSTR       szEvent,
   [in]  ULONG         cchEvent,
   [out] ULONG         *pchEvent,
   [out] DWORD         *pdwEventFlags,  
   [out] mdToken       *ptkEventType,  
   [out] mdMethodDef   *pmdAddOn,
   [out] mdMethodDef   *pmdRemoveOn,
   [out] mdMethodDef   *pmdFire,
   [out] mdMethodDef   rmdOtherMethod[],
   [in]  ULONG         cMax,  
   [out] ULONG         *pcOtherMethod  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3cc7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a3cc7-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="a3cc7-106">[içinde] Meta veri almak için olayı temsil eden olay meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="a3cc7-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="a3cc7-107">[çıkış] Olayı bildiren sınıfı temsil eden TypeDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a3cc7-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="a3cc7-108">[çıkış] Başvuran olayın `ev`adı.</span><span class="sxs-lookup"><span data-stu-id="a3cc7-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="a3cc7-109">[içinde] Geniş karakterlerde istenen `szEvent`uzunluk.</span><span class="sxs-lookup"><span data-stu-id="a3cc7-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="a3cc7-110">[çıkış] Geniş karakterlerde döndürülen `szEvent`uzunluk.</span><span class="sxs-lookup"><span data-stu-id="a3cc7-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="a3cc7-111">[çıkış] Olayın <xref:System.Delegate> türünü temsil eden bir TypeRef veya TypeDef meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a3cc7-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="a3cc7-112">[çıkış] Olay için işleyicileri ekleyen yöntemi temsil eden meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a3cc7-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="a3cc7-113">[çıkış] Olay için işleyicileri kaldıran yöntemi temsil eden meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a3cc7-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="a3cc7-114">[çıkış] Olayı yükselten yöntemi temsil eden meta veri belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a3cc7-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="a3cc7-115">[çıkış] Olayla ilişkili diğer yöntemlere işaretçi dizisi.</span><span class="sxs-lookup"><span data-stu-id="a3cc7-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a3cc7-116">[içinde] `rmdOtherMethod` Dizinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="a3cc7-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="a3cc7-117">[çıkış] Döndürülen belirteçlerin `rmdOtherMethod`sayısı.</span><span class="sxs-lookup"><span data-stu-id="a3cc7-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3cc7-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3cc7-118">Requirements</span></span>  
 <span data-ttu-id="a3cc7-119">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3cc7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3cc7-120">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a3cc7-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a3cc7-121">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="a3cc7-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a3cc7-122">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3cc7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3cc7-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3cc7-123">See also</span></span>

- [<span data-ttu-id="a3cc7-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3cc7-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a3cc7-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a3cc7-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
