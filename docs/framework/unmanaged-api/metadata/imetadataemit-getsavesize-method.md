---
title: IMetaDataEmit::GetSaveSize Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.GetSaveSize
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7585f6adbca97b252fdad90276b0cd422d32c04a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="6c24d-102">IMetaDataEmit::GetSaveSize Metodu</span><span class="sxs-lookup"><span data-stu-id="6c24d-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="6c24d-103">Derleme ve meta verilerini tahmini ikili boyutunu geçerli kapsamda alır.</span><span class="sxs-lookup"><span data-stu-id="6c24d-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c24d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c24d-104">Syntax</span></span>  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c24d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c24d-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="6c24d-106">[in] Değerini [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) doğru veya yaklaşık boyutu almak belirtir numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="6c24d-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="6c24d-107">Yalnızca üç değerler geçerlidir: cssAccurate, cssQuick ve cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="6c24d-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
-   <span data-ttu-id="6c24d-108">cssAccurate tam boyutu kaydetme verir ancak hesaplamak için daha uzun sürer.</span><span class="sxs-lookup"><span data-stu-id="6c24d-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
-   <span data-ttu-id="6c24d-109">cssQuick güvenliğiniz için doldurulan bir boyutu döndüren ancak hesaplamak için daha az zaman alır.</span><span class="sxs-lookup"><span data-stu-id="6c24d-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
-   <span data-ttu-id="6c24d-110">cssDiscardTransientCAs söyler `GetSaveSize` discardable özel öznitelikler hemen atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c24d-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="6c24d-111">[out] Dosyayı kaydetmek için gereken boyutu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6c24d-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c24d-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c24d-112">Remarks</span></span>  
 <span data-ttu-id="6c24d-113">`GetSaveSize`, derleme ve tüm meta veriler geçerli kapsamda kaydetmek için bayt cinsinden gerekli alanı hesaplar.</span><span class="sxs-lookup"><span data-stu-id="6c24d-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="6c24d-114">(Çağrı [Imetadataemit::savetostream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) yöntemi bu bayt sayısını yayması.)</span><span class="sxs-lookup"><span data-stu-id="6c24d-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="6c24d-115">Arayan uyguluyorsa [Imaptoken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) arabirimi (aracılığıyla [Imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) veya [Imetadataemit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` iki geçişleri gerçekleştirecek en iyi duruma getirme ve onu sıkıştırmak için meta veriler üzerinde.</span><span class="sxs-lookup"><span data-stu-id="6c24d-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="6c24d-116">Aksi takdirde, herhangi bir iyileştirme gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="6c24d-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="6c24d-117">En iyi duruma getirme gerçekleştirilirse, ilk geçişi yalnızca alma zamanı aramaları performansı ayarlamak için meta veri yapılarını sıralar.</span><span class="sxs-lookup"><span data-stu-id="6c24d-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="6c24d-118">Bu adım genellikle ileride kullanılmak üzere aracı tarafından korunduğunu belirteçleri geçersiz kılınır yan etkisi, geçici kayıtlarıyla taşıma sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="6c24d-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="6c24d-119">Meta veriler bu belirteci değişinceye kadar arayan ikinci geçişinden sonra ancak bildirin değil.</span><span class="sxs-lookup"><span data-stu-id="6c24d-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="6c24d-120">İkinci geçişinde koyma (erken bağlama) en iyi duruma getirme gibi meta veriler, toplam boyutunu azaltmak için yönelik çeşitli iyileştirmeler gerçekleştirilen `mdTypeRef` ve `mdMemberRef` belirteçler: başvuru türü veya içinde bildirilen üyesi olduğunda geçerli meta veri kapsamı.</span><span class="sxs-lookup"><span data-stu-id="6c24d-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="6c24d-121">Bu geçişte belirteci eşleme başka bir gidiş oluşur.</span><span class="sxs-lookup"><span data-stu-id="6c24d-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="6c24d-122">Bu aşamadan sonra meta veri altyapısı aracılığıyla arayan bildirir, `IMapToken` herhangi arabirimi simge değerlerini değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="6c24d-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c24d-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c24d-123">Requirements</span></span>  
 <span data-ttu-id="6c24d-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c24d-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c24d-125">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6c24d-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6c24d-126">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6c24d-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c24d-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c24d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c24d-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c24d-128">See Also</span></span>  
 [<span data-ttu-id="6c24d-129">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c24d-129">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="6c24d-130">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c24d-130">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
