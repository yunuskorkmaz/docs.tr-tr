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
ms.openlocfilehash: 1f28a4b4acd9d6050d33b9824aa49a9b9041b59b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111244"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="51b16-102">ICLRMetadataLocator::GetMetadata Metodu</span><span class="sxs-lookup"><span data-stu-id="51b16-102">ICLRMetadataLocator::GetMetadata Method</span></span>
<span data-ttu-id="51b16-103">Bir görüntünün meta verilerini almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="51b16-103">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51b16-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51b16-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="51b16-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51b16-105">Parameters</span></span>  
 `imagePath`  
 <span data-ttu-id="51b16-106">'ndaki Görüntü dosyasının yolunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="51b16-106">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="51b16-107">'ndaki Görüntü dosyasının zaman damgası.</span><span class="sxs-lookup"><span data-stu-id="51b16-107">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="51b16-108">'ndaki Resim dosyasının boyutu.</span><span class="sxs-lookup"><span data-stu-id="51b16-108">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="51b16-109">'ndaki Görüntünün genel benzersiz tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="51b16-109">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="51b16-110">'ndaki Meta verilerin göreli sanal adresi (RVA).</span><span class="sxs-lookup"><span data-stu-id="51b16-110">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="51b16-111">Adres, görüntü temel adresiyle ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="51b16-111">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="51b16-112">'ndaki Gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="51b16-112">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="51b16-113">'ndaki Meta verilerin yerleştirileceği arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="51b16-113">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="51b16-114">dışı Meta verilerin yerleştirileceği arabellek.</span><span class="sxs-lookup"><span data-stu-id="51b16-114">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="51b16-115">dışı Döndürülen meta verilerin boyutu.</span><span class="sxs-lookup"><span data-stu-id="51b16-115">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51b16-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51b16-116">Remarks</span></span>  
 <span data-ttu-id="51b16-117">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="51b16-117">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51b16-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51b16-118">Requirements</span></span>  
 <span data-ttu-id="51b16-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51b16-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51b16-120">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="51b16-120">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="51b16-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="51b16-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51b16-122">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51b16-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51b16-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51b16-123">See also</span></span>

- [<span data-ttu-id="51b16-124">ICLRMetadataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51b16-124">ICLRMetadataLocator Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)
