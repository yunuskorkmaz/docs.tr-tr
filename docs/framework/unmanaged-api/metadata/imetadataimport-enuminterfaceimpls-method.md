---
title: IMetaDataImport::EnumInterfaceImpls Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
ms.openlocfilehash: b535fdd5027a26cc4dd0eafec9883f0186773dd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175505"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="933a5-102">IMetaDataImport::EnumInterfaceImpls Yöntemi</span><span class="sxs-lookup"><span data-stu-id="933a5-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="933a5-103">Belirtilen `TypeDef`tarafından uygulanan tüm arabirimleri oyalar.</span><span class="sxs-lookup"><span data-stu-id="933a5-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="933a5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="933a5-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="933a5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="933a5-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="933a5-106">[içinde, dışarı] Sayıya işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="933a5-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="933a5-107">[içinde] Arabirim uygulamalarını temsil eden MethodDef belirteçleri numaralandırılacak Olan TypeDef belirteci.</span><span class="sxs-lookup"><span data-stu-id="933a5-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="933a5-108">[çıkış] MethodDef belirteçlerini depolamak için kullanılan dizi.</span><span class="sxs-lookup"><span data-stu-id="933a5-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="933a5-109">[içinde] `rImpls` Dizinin maksimum uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="933a5-109">[in] The maximum length of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="933a5-110">[çıkış] Döndürülen belirteçlerin gerçek `rImpls`sayısı.</span><span class="sxs-lookup"><span data-stu-id="933a5-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="933a5-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="933a5-111">Return Value</span></span>  
  
|<span data-ttu-id="933a5-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="933a5-112">HRESULT</span></span>|<span data-ttu-id="933a5-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="933a5-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="933a5-114">`EnumInterfaceImpls`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="933a5-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="933a5-115">Sayısala çıkarmak için MethodDef belirteçleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="933a5-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="933a5-116">Bu durumda, `pcImpls` sıfıra ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="933a5-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="933a5-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="933a5-117">Remarks</span></span>

<span data-ttu-id="933a5-118">Numaralandırma, belirtilen ler tarafından `mdInterfaceImpl` uygulanan her arabirim için bir `TypeDef`belirteç ler koleksiyonunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="933a5-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="933a5-119">Arabirim belirteçleri, arabirimlerin belirtildiği sırayla `DefineTypeDef` `SetTypeDefProps`döndürülür (üzerinden veya).</span><span class="sxs-lookup"><span data-stu-id="933a5-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="933a5-120">Döndürülen `mdInterfaceImpl` belirteçlerin özellikleri [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)kullanılarak sorgulanabilir.</span><span class="sxs-lookup"><span data-stu-id="933a5-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="933a5-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="933a5-121">Requirements</span></span>  
 <span data-ttu-id="933a5-122">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="933a5-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="933a5-123">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="933a5-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="933a5-124">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="933a5-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="933a5-125">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="933a5-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="933a5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="933a5-126">See also</span></span>

- [<span data-ttu-id="933a5-127">IMetaDataImport Arabirimi</span><span class="sxs-lookup"><span data-stu-id="933a5-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="933a5-128">IMetaDataImport2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="933a5-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
