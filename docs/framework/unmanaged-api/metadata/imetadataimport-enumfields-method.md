---
title: IMetaDataImport::EnumFields Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumFields
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumFields
helpviewer_keywords:
- EnumFields method [.NET Framework metadata]
- IMetaDataImport::EnumFields method [.NET Framework metadata]
ms.assetid: 1d23247e-c58c-45db-afd8-83aa89cde18e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd8a2d373b801bd8238d50eecb388ef511bc34bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33446208"
---
# <a name="imetadataimportenumfields-method"></a><span data-ttu-id="f93b2-102">IMetaDataImport::EnumFields Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f93b2-102">IMetaDataImport::EnumFields Method</span></span>
<span data-ttu-id="f93b2-103">Belirtilen TypeDef belirteç tarafından başvurulan türü için fieldDef simgesi belirteçleri numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="f93b2-103">Enumerates FieldDef tokens for the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f93b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f93b2-104">Syntax</span></span>  
  
```  
HRESULT EnumFields (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   cl,   
   [out]     mdFieldDef  rFields[],   
   [in]      ULONG       cMax,   
   [out]     ULONG       *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f93b2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f93b2-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="f93b2-106">[içinde out] Numaralayıcı gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f93b2-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="f93b2-107">[in] Numaralandırılacak alanları olan sınıfın TypeDef simgesi.</span><span class="sxs-lookup"><span data-stu-id="f93b2-107">[in] The TypeDef token of the class whose fields are to be enumerated.</span></span>  
  
 `rFields`  
 <span data-ttu-id="f93b2-108">[out] FieldDef simgesi belirteçleri listesi.</span><span class="sxs-lookup"><span data-stu-id="f93b2-108">[out] The list of FieldDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="f93b2-109">[in] En büyük boyutunu `rFields` dizi.</span><span class="sxs-lookup"><span data-stu-id="f93b2-109">[in] The maximum size of the `rFields` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="f93b2-110">[out] Döndürülen fieldDef simgesi belirteçleri gerçek sayısını `rFields`.</span><span class="sxs-lookup"><span data-stu-id="f93b2-110">[out] The actual number of FieldDef tokens returned in `rFields`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f93b2-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f93b2-111">Return Value</span></span>  
  
|<span data-ttu-id="f93b2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f93b2-112">HRESULT</span></span>|<span data-ttu-id="f93b2-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f93b2-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="f93b2-114">`EnumFields` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f93b2-114">`EnumFields` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="f93b2-115">Numaralandırılacak alan yok.</span><span class="sxs-lookup"><span data-stu-id="f93b2-115">There are no fields to enumerate.</span></span> <span data-ttu-id="f93b2-116">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="f93b2-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f93b2-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f93b2-117">Requirements</span></span>  
 <span data-ttu-id="f93b2-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f93b2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f93b2-119">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f93b2-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f93b2-120">**Kitaplığı:** bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f93b2-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f93b2-121">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f93b2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f93b2-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f93b2-122">See Also</span></span>  
 [<span data-ttu-id="f93b2-123">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f93b2-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="f93b2-124">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f93b2-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
