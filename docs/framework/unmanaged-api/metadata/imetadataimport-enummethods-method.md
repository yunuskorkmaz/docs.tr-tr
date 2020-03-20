---
title: IMetaDataImport::EnumMethods Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
ms.openlocfilehash: 218b65b5899692774c434ae136a3976ecb97ea2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177302"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="13461-102">IMetaDataImport::EnumMethods Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13461-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="13461-103">Belirtilen tipteki yöntemleri temsil eden MethodDef belirteçlerini oyalar.</span><span class="sxs-lookup"><span data-stu-id="13461-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13461-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13461-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,
   [in]  mdTypeDef      cl,
   [out] mdMethodDef    rMethods[],
   [in]  ULONG          cMax,
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13461-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13461-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="13461-106">[içinde, dışarı] Sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="13461-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="13461-107">Bu yöntemin ilk araması için NULL olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="13461-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="13461-108">[içinde] Türü temsil eden ve sayısallama yöntemlerini temsil eden bir TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="13461-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="13461-109">[çıkış] MethodDef belirteçlerini depolamak için dizi.</span><span class="sxs-lookup"><span data-stu-id="13461-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="13461-110">[içinde] MethodDef `rMethods` dizisinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="13461-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="13461-111">[çıkış] MethodDef belirteçlerinin sayısı `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="13461-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13461-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13461-112">Return Value</span></span>  
  
|<span data-ttu-id="13461-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13461-113">HRESULT</span></span>|<span data-ttu-id="13461-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13461-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="13461-115">`EnumMethods`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="13461-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="13461-116">Sayısala çıkarmak için MethodDef belirteçleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="13461-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="13461-117">Bu durumda, `pcTokens` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="13461-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13461-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13461-118">Requirements</span></span>  
 <span data-ttu-id="13461-119">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13461-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13461-120">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="13461-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13461-121">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="13461-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="13461-122">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13461-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13461-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13461-123">See also</span></span>

- [<span data-ttu-id="13461-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13461-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="13461-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13461-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
