---
title: IMetaDataImport::GetEventProps Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetEventProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetEventProps
helpviewer_keywords:
- IMetaDataImport::GetEventProps method [.NET Framework metadata]
- GetEventProps method [.NET Framework metadata]
ms.assetid: 5eaf3b4a-92b7-4d5b-97e0-1e83721e0052
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73f257c46fd21355eeaabbe9e1b5d2841d2c3911
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgeteventprops-method"></a><span data-ttu-id="fa71f-102">IMetaDataImport::GetEventProps Metodu</span><span class="sxs-lookup"><span data-stu-id="fa71f-102">IMetaDataImport::GetEventProps Method</span></span>
<span data-ttu-id="fa71f-103">Belirtilen olay belirteci bildiri türü, Ekle ve temsilciler remove yöntemlerini ve herhangi bir bayrağı ve diğer ilişkili veriler de dahil olmak üzere tarafından temsil edilen olay için meta veri bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="fa71f-103">Gets metadata information for the event represented by the specified event token, including the declaring type, the add and remove methods for delegates, and any flags and other associated data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa71f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa71f-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="fa71f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa71f-105">Parameters</span></span>  
 `ev`  
 <span data-ttu-id="fa71f-106">[in] Meta verilerini almak için olay temsil eden olay meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="fa71f-106">[in] The event metadata token representing the event to get metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="fa71f-107">[out] Olay bildirir sınıfı temsil eden TypeDef belirteci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fa71f-107">[out] A pointer to the TypeDef token representing the class that declares the event.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="fa71f-108">[out] Tarafından başvurulan olayın adı `ev`.</span><span class="sxs-lookup"><span data-stu-id="fa71f-108">[out] The name of the event referenced by `ev`.</span></span>  
  
 `pchEvent`  
 <span data-ttu-id="fa71f-109">[in] Geniş karakter cinsinden istenen uzunluğu `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="fa71f-109">[in] The requested length in wide characters of `szEvent`.</span></span>  
  
 `pdwEventFlags`  
 <span data-ttu-id="fa71f-110">[out] Geniş karakter cinsinden döndürülen uzunluğu `szEvent`.</span><span class="sxs-lookup"><span data-stu-id="fa71f-110">[out] The returned length in wide characters of `szEvent`.</span></span>  
  
 `ptkEventType`  
 <span data-ttu-id="fa71f-111">[out] Bir TypeRef veya TypeDef meta verileri belirteci gösteren bir işaretçi <xref:System.Delegate> olay türü.</span><span class="sxs-lookup"><span data-stu-id="fa71f-111">[out] A pointer to a TypeRef or TypeDef metadata token representing the <xref:System.Delegate> type of the event.</span></span>  
  
 `pmdAddOn`  
 <span data-ttu-id="fa71f-112">[out] Olay işleyicileri ekler yöntemi temsil eden meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fa71f-112">[out] A pointer to the metadata token representing the method that adds handlers for the event.</span></span>  
  
 `pmdRemoveOn`  
 <span data-ttu-id="fa71f-113">[out] Olay işleyicileri kaldırır yöntemi temsil eden meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fa71f-113">[out] A pointer to the metadata token representing the method that removes handlers for the event.</span></span>  
  
 `pmdFire`  
 <span data-ttu-id="fa71f-114">[out] Olayı oluşturan yöntemi temsil eden meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fa71f-114">[out] A pointer to the metadata token representing the method that raises the event.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="fa71f-115">[out] Olayla ilişkili diğer yöntemleri için belirteç işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="fa71f-115">[out] An array of token pointers to other methods associated with the event.</span></span>  
  
 `cMax`  
 <span data-ttu-id="fa71f-116">[in] En büyük boyutunu `rmdOtherMethod` dizi.</span><span class="sxs-lookup"><span data-stu-id="fa71f-116">[in] The maximum size of the `rmdOtherMethod` array.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="fa71f-117">[out] Döndürülen belirteçleri sayısı `rmdOtherMethod`.</span><span class="sxs-lookup"><span data-stu-id="fa71f-117">[out] The number of tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa71f-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa71f-118">Requirements</span></span>  
 <span data-ttu-id="fa71f-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa71f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa71f-120">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fa71f-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fa71f-121">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fa71f-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fa71f-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa71f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa71f-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa71f-123">See Also</span></span>  
 [<span data-ttu-id="fa71f-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa71f-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="fa71f-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa71f-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
