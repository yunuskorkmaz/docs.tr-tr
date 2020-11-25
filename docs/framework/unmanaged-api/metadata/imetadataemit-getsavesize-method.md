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
ms.openlocfilehash: 5cb202f5284c1c18545ec750b2fa0f04d4b0d2e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722069"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="e7c1a-102">IMetaDataEmit::GetSaveSize Metodu</span><span class="sxs-lookup"><span data-stu-id="e7c1a-102">IMetaDataEmit::GetSaveSize Method</span></span>

<span data-ttu-id="e7c1a-103">Derlemenin tahmini ikili boyutunu ve geçerli kapsamdaki meta verilerini alır.</span><span class="sxs-lookup"><span data-stu-id="e7c1a-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7c1a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e7c1a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7c1a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7c1a-105">Parameters</span></span>  

 `fSave`  
 <span data-ttu-id="e7c1a-106">'ndaki Doğru veya yaklaşık bir boyut almak isteyip istemediğinizi belirten [CorSaveSize](corsavesize-enumeration.md) numaralandırması değeri.</span><span class="sxs-lookup"><span data-stu-id="e7c1a-106">[in] A value of the [CorSaveSize](corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="e7c1a-107">Yalnızca üç değer geçerlidir: cssAccurate, cssQuick ve cssDiscardTransientCAs:</span><span class="sxs-lookup"><span data-stu-id="e7c1a-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="e7c1a-108">cssAccurate, tam kaydetme boyutunu döndürür ancak daha uzun süre içinde hesaplama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e7c1a-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="e7c1a-109">cssQuick, güvenlik için doldurulmuş bir boyut döndürür, ancak hesaplanması daha az zaman alır.</span><span class="sxs-lookup"><span data-stu-id="e7c1a-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="e7c1a-110">cssDiscardTransientCAs `GetSaveSize` , discardable özel öznitelikleri oluşturabildiğini söyler.</span><span class="sxs-lookup"><span data-stu-id="e7c1a-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="e7c1a-111">dışı Dosyanın kaydedilmesi için gereken boyuta yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e7c1a-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7c1a-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7c1a-112">Remarks</span></span>  

 <span data-ttu-id="e7c1a-113">`GetSaveSize` derlemeyi ve geçerli kapsamdaki tüm meta verilerini kaydetmek için gereken alanı bayt cinsinden hesaplar.</span><span class="sxs-lookup"><span data-stu-id="e7c1a-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="e7c1a-114">( [Imetadatayayma:: SaveToStream](imetadataemit-savetostream-method.md) metoduna yapılan bir çağrı, bu sayıda bayt yaymalıdır.)</span><span class="sxs-lookup"><span data-stu-id="e7c1a-114">(A call to the [IMetaDataEmit::SaveToStream](imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="e7c1a-115">Arayan, [IMapToken](imaptoken-interface.md) arabirimini ( [ımetadatayayma:: SetHandler](imetadataemit-sethandler-method.md) veya [ımetadatayayma:: Merge](imetadataemit-merge-method.md)) uygularsa, `GetSaveSize` en uygun hale getirmek ve sıkıştırmak için meta veriler üzerinde iki geçiş gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="e7c1a-115">If the caller implements the [IMapToken](imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="e7c1a-116">Aksi takdirde, iyileştirmeler yapılmaz.</span><span class="sxs-lookup"><span data-stu-id="e7c1a-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="e7c1a-117">İyileştirme gerçekleştirilirse, ilk geçiş yalnızca meta veri yapılarını sıralar ve içeri aktarma zamanı aramalarının performansını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e7c1a-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="e7c1a-118">Bu adım genellikle, sonraki başvuru için araç tarafından tutulan belirteçlerin geçersiz kılınmasıyla birlikte kayıtları taşımaya neden olur.</span><span class="sxs-lookup"><span data-stu-id="e7c1a-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="e7c1a-119">Ancak meta veriler, ikinci pass öğesine kadar bu belirteç değişikliklerini çağırana bildirir.</span><span class="sxs-lookup"><span data-stu-id="e7c1a-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="e7c1a-120">İkinci geçişte, başvurunun en iyi duruma getirilmesi (erken bağlama) `mdTypeRef` ve `mdMemberRef` belirteçlerin geçerli meta veri kapsamında bildirildiği bir türe veya üyeye olması gibi, meta verilerin genel boyutunu azaltmaya yönelik çeşitli iyileştirmeler yapılır.</span><span class="sxs-lookup"><span data-stu-id="e7c1a-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="e7c1a-121">Bu geçişte, belirteç eşlemesinin başka bir turu oluşur.</span><span class="sxs-lookup"><span data-stu-id="e7c1a-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="e7c1a-122">Bu geçiş işleminden sonra, meta veri altyapısı, `IMapToken` değiştirilen herhangi bir belirteç değerinin arabiriminden, bu çağrıyı yapana bildirir.</span><span class="sxs-lookup"><span data-stu-id="e7c1a-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7c1a-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7c1a-123">Requirements</span></span>  

 <span data-ttu-id="e7c1a-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7c1a-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7c1a-125">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e7c1a-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e7c1a-126">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e7c1a-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7c1a-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7c1a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7c1a-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7c1a-128">See also</span></span>

- [<span data-ttu-id="e7c1a-129">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7c1a-129">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e7c1a-130">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7c1a-130">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
