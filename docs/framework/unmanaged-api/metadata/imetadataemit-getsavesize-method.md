---
title: IMetaDataEmit::GetSaveSize Metodu
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 164cdc5c04a55e9c33dda51e10dfb37f38ec1b6d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746550"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="3f24a-102">IMetaDataEmit::GetSaveSize Metodu</span><span class="sxs-lookup"><span data-stu-id="3f24a-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="3f24a-103">Derleme meta verilerini ve ikili tahmini boyutu geçerli kapsamda alır.</span><span class="sxs-lookup"><span data-stu-id="3f24a-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f24a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f24a-104">Syntax</span></span>  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f24a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f24a-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="3f24a-106">[in] Değerini [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) bir doğru ya da yaklaşık boyutunu almak belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="3f24a-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="3f24a-107">Yalnızca üç değerler geçerlidir: cssAccurate, cssQuick ve cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="3f24a-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
-   <span data-ttu-id="3f24a-108">cssAccurate tam boyutu kaydetme döndürür ancak hesaplamak için uzun sürer.</span><span class="sxs-lookup"><span data-stu-id="3f24a-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
-   <span data-ttu-id="3f24a-109">cssQuick güvenliği için doldurulan bir boyutunu döndürür ancak hesaplamak için daha kısa sürer.</span><span class="sxs-lookup"><span data-stu-id="3f24a-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
-   <span data-ttu-id="3f24a-110">cssDiscardTransientCAs söyler `GetSaveSize` discardable özel öznitelikler yerine atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f24a-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="3f24a-111">[out] Dosyayı kaydetmek için gereken boyut için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3f24a-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f24a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f24a-112">Remarks</span></span>  
 <span data-ttu-id="3f24a-113">`GetSaveSize` , derleme ve tüm meta veriler geçerli kapsamda kaydetmek için bayt cinsinden gereken alanı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="3f24a-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="3f24a-114">(Bir çağrı [Imetadataemit::savetostream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) yöntemi bu bayt sayısını yayması.)</span><span class="sxs-lookup"><span data-stu-id="3f24a-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="3f24a-115">Çağıranın uyguluyorsa [Imaptoken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) arabirimi (aracılığıyla [Imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) veya [Imetadataemit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` iki geçiş yapar en iyi duruma getirmek ve bunu sıkıştırmak için meta verileri.</span><span class="sxs-lookup"><span data-stu-id="3f24a-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="3f24a-116">Aksi takdirde, hiçbir iyileştirmeleri gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3f24a-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="3f24a-117">İlk geçişinde, yalnızca en iyi duruma getirme gerçekleştirilirse, alma zamanı Arama performansını ayarlamak için meta veri yapıları sıralar.</span><span class="sxs-lookup"><span data-stu-id="3f24a-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="3f24a-118">Bu adım, genellikle etrafında, kayıtları ileride kullanılmak üzere aracı tarafından korunan belirteçleri geçersiz kılınır yan etkisi olan taşıma sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="3f24a-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="3f24a-119">Meta veri belirteci değişikliklerin kadar çağıran ikinci aşamadan sonra ancak bildirin değil.</span><span class="sxs-lookup"><span data-stu-id="3f24a-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="3f24a-120">İkinci geçişinde çeşitli en iyi duruma getirme koyma (erken bağlama) en iyi duruma getirme gibi meta veriler, toplam boyutunu azaltmak için hedeflenen gerçekleştirilir `mdTypeRef` ve `mdMemberRef` belirteçler başvuru sağlayan bir tür veya içinde bildirilen üye olduğunda geçerli meta veri kapsamı.</span><span class="sxs-lookup"><span data-stu-id="3f24a-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="3f24a-121">Bu geçişte belirteci eşleme başka bir gidiş gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="3f24a-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="3f24a-122">Bu aşamadan sonra meta veri altyapısı aracılığıyla arayan bildirir, `IMapToken` belirteci değerleri herhangi bir arabirim değişti.</span><span class="sxs-lookup"><span data-stu-id="3f24a-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f24a-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3f24a-123">Requirements</span></span>  
 <span data-ttu-id="3f24a-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f24a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f24a-125">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="3f24a-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f24a-126">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="3f24a-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3f24a-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f24a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f24a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f24a-128">See also</span></span>
- [<span data-ttu-id="3f24a-129">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f24a-129">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="3f24a-130">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3f24a-130">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
