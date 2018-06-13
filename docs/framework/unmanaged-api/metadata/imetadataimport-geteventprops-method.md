---
title: IMetaDataImport::GetEventProps Metodu
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6ac1ecb73257782888c963082953ed243177a86b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448810"
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="b0325-102">IMetaDataImport::GetEventProps Metodu</span><span class="sxs-lookup"><span data-stu-id="b0325-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="b0325-103">Belirtilen olay belirteci bildiri türü, Ekle ve temsilciler remove yöntemlerini ve herhangi bir bayrağı ve diğer ilişkili veriler de dahil olmak üzere tarafından temsil edilen olay için meta veri bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="b0325-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0325-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0325-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="b0325-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0325-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="b0325-106">[in] Meta verilerini almak için olay temsil eden olay meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="b0325-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="b0325-107">[out] Olay bildirir sınıfı temsil eden TypeDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b0325-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="b0325-108">[out] Tarafından başvurulan olayın adı `ev`.</span><span class="sxs-lookup"><span data-stu-id="b0325-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="b0325-109">[in] Geniş karakter cinsinden istenen uzunluğu `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="b0325-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="b0325-110">[out] Geniş karakter cinsinden döndürülen uzunluğu `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="b0325-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="b0325-111">[out] Bir TypeRef veya TypeDef meta verileri belirteci gösteren bir işaretçi <xref:System.Delegate> olay türü.</span><span class="sxs-lookup"><span data-stu-id="b0325-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="b0325-112">[out] Olay işleyicileri ekler yöntemi temsil eden meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b0325-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="b0325-113">[out] Olay işleyicileri kaldırır yöntemi temsil eden meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b0325-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="b0325-114">[out] Olayı oluşturan yöntemi temsil eden meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b0325-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="b0325-115">[out] Olayla ilişkili diğer yöntemleri için belirteç işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="b0325-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b0325-116">[in] En büyük boyutunu `rmdOtherMethod` dizi.</span><span class="sxs-lookup"><span data-stu-id="b0325-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="b0325-117">[out] Döndürülen belirteçleri sayısı `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="b0325-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0325-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0325-118">Requirements</span></span>  
 <span data-ttu-id="b0325-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0325-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0325-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b0325-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b0325-121">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b0325-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b0325-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0325-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0325-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b0325-123">See Also</span></span>  
 [<span data-ttu-id="b0325-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0325-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b0325-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0325-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
