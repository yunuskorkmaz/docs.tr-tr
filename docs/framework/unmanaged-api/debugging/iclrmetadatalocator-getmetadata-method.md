---
title: ICLRMetadataLocator::GetMetadata Metodu
ms.date: 03/30/2017
api_name:
- ICLRMetadataLocator.GetMetadata
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRMetadataLocator::GetMetadata
helpviewer_keywords:
- GetMetadata method, ICLRMetadataLocator interface [.NET Framework debugging]
- ICLRMetadataLocator::GetMetadata method [.NET Framework debugging]
ms.assetid: 704a8893-ac56-43b4-90ea-715f38ccb40e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4338619414c9c9ac8c5fe85479562410d1678698
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403864"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="55f99-102">ICLRMetadataLocator::GetMetadata Metodu</span><span class="sxs-lookup"><span data-stu-id="55f99-102">ICLRMetadataLocator::GetMetadata Method</span></span>
<span data-ttu-id="55f99-103">Görüntü meta verilerini almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="55f99-103">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f99-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55f99-104">Syntax</span></span>  
  
```  
HRESULT GetMetadata(  
    [in]  LPCWSTR         imagePath,  
    [in]  ULONG32         imageTimestamp,  
    [in]  ULONG32         imageSize,  
    [in]  GUID*           mvid,  
    [in]  ULONG32         mdRva,  
    [in]  ULONG32         flags,  
    [in]  ULONG32         bufferSize,  
    [out, size_is(bufferSize), length_is(*dataSize)]  
          BYTE*           buffer,  
    [out] ULONG32*        dataSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55f99-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="55f99-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="55f99-106">[in] Görüntü dosyasının yolunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="55f99-106">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="55f99-107">[in] Görüntü dosyasının zaman damgası.</span><span class="sxs-lookup"><span data-stu-id="55f99-107">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="55f99-108">[in] Görüntü dosyasının boyutu.</span><span class="sxs-lookup"><span data-stu-id="55f99-108">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="55f99-109">[in] Görüntü genel benzersiz tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="55f99-109">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="55f99-110">[in] Meta veri göreli sanal adres (RAV).</span><span class="sxs-lookup"><span data-stu-id="55f99-110">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="55f99-111">Görüntü taban adresi göre adresidir.</span><span class="sxs-lookup"><span data-stu-id="55f99-111">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="55f99-112">[in] Gelecekte kullanılmak üzere ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="55f99-112">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="55f99-113">[in] Meta veriler yerleştirileceği arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="55f99-113">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="55f99-114">[out] Meta veriler yerleştirileceği arabelleği.</span><span class="sxs-lookup"><span data-stu-id="55f99-114">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="55f99-115">[out] Döndürülen meta veri boyutu.</span><span class="sxs-lookup"><span data-stu-id="55f99-115">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55f99-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55f99-116">Remarks</span></span>  
 <span data-ttu-id="55f99-117">Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="55f99-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55f99-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55f99-118">Requirements</span></span>  
 <span data-ttu-id="55f99-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55f99-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55f99-120">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="55f99-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="55f99-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55f99-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55f99-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55f99-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f99-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="55f99-123">See Also</span></span>  
 [<span data-ttu-id="55f99-124">ICLRMetadataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55f99-124">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
