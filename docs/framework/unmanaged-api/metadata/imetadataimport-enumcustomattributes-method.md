---
title: IMetaDataImport::EnumCustomAttributes Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: a43c1883038e41cac1b58c78bc26f20d436ebbd1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440245"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="966f4-102">IMetaDataImport::EnumCustomAttributes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="966f4-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="966f4-103">Belirtilen tür veya üyeyle ilişkili özel öznitelik tanımı belirteçlerini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="966f4-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="966f4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="966f4-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (   
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,   
   [in]  mdToken            tkType,   
   [out] mdCustomAttribute  rCustomAttributes[],   
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="966f4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="966f4-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="966f4-106">[in, out] Döndürülen Numaralandırıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="966f4-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="966f4-107">'ndaki Numaralandırma kapsamı için bir belirteç veya tüm özel öznitelikler için sıfır.</span><span class="sxs-lookup"><span data-stu-id="966f4-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="966f4-108">'ndaki Numaralandırılacak özniteliklerin türü oluşturucusuna yönelik belirteç veya tüm türler için `null`.</span><span class="sxs-lookup"><span data-stu-id="966f4-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="966f4-109">dışı Özel öznitelik belirteçlerinin dizisi.</span><span class="sxs-lookup"><span data-stu-id="966f4-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="966f4-110">'ndaki `rCustomAttributes` dizisinin en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="966f4-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="966f4-111">[Out, isteğe bağlı] `rCustomAttributes`' de döndürülen belirteç değerlerinin gerçek sayısı.</span><span class="sxs-lookup"><span data-stu-id="966f4-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="966f4-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="966f4-112">Return Value</span></span>  
  
|<span data-ttu-id="966f4-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="966f4-113">HRESULT</span></span>|<span data-ttu-id="966f4-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="966f4-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="966f4-115">`EnumCustomAttributes` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="966f4-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="966f4-116">Numaralandırılacak özel öznitelik yok.</span><span class="sxs-lookup"><span data-stu-id="966f4-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="966f4-117">Bu durumda `pcCustomAttributes` sıfırdır.</span><span class="sxs-lookup"><span data-stu-id="966f4-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="966f4-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="966f4-118">Requirements</span></span>  
 <span data-ttu-id="966f4-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="966f4-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="966f4-120">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="966f4-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="966f4-121">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="966f4-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="966f4-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="966f4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="966f4-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="966f4-123">See also</span></span>

- [<span data-ttu-id="966f4-124">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="966f4-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="966f4-125">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="966f4-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
