---
description: ': ICLRMetadataLocator:: GetMetadata Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4a7e8b906b66c4295dd24800d260790526114701
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772633"
---
# <a name="iclrmetadatalocatorgetmetadata-method"></a><span data-ttu-id="845fb-103">ICLRMetadataLocator::GetMetadata Metodu</span><span class="sxs-lookup"><span data-stu-id="845fb-103">ICLRMetadataLocator::GetMetadata Method</span></span>

<span data-ttu-id="845fb-104">Bir görüntünün meta verilerini almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="845fb-104">Called by the common language runtime (CLR) data access services to retrieve the metadata of an image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="845fb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="845fb-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="845fb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="845fb-106">Parameters</span></span>  

 `imagePath`  
 <span data-ttu-id="845fb-107">'ndaki Görüntü dosyasının yolunu belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="845fb-107">[in] A string that specifies the path of the image file.</span></span>  
  
 `imageTimestamp`  
 <span data-ttu-id="845fb-108">'ndaki Görüntü dosyasının zaman damgası.</span><span class="sxs-lookup"><span data-stu-id="845fb-108">[in] The time stamp of the image file.</span></span>  
  
 `imageSize`  
 <span data-ttu-id="845fb-109">'ndaki Resim dosyasının boyutu.</span><span class="sxs-lookup"><span data-stu-id="845fb-109">[in] The size of the image file.</span></span>  
  
 `mvid`  
 <span data-ttu-id="845fb-110">'ndaki Görüntünün genel benzersiz tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="845fb-110">[in] The globally unique identifier of the image.</span></span>  
  
 `mdRva`  
 <span data-ttu-id="845fb-111">'ndaki Meta verilerin göreli sanal adresi (RVA).</span><span class="sxs-lookup"><span data-stu-id="845fb-111">[in] The relative virtual address (RVA) of the metadata.</span></span> <span data-ttu-id="845fb-112">Adres, görüntü temel adresiyle ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="845fb-112">The address is relative to the image base address.</span></span>  
  
 `flags`  
 <span data-ttu-id="845fb-113">'ndaki Gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="845fb-113">[in] Reserved for future use.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="845fb-114">'ndaki Meta verilerin yerleştirileceği arabelleğin boyutu.</span><span class="sxs-lookup"><span data-stu-id="845fb-114">[in] The size of the buffer in which to place the metadata.</span></span>  
  
 `buffer`  
 <span data-ttu-id="845fb-115">dışı Meta verilerin yerleştirileceği arabellek.</span><span class="sxs-lookup"><span data-stu-id="845fb-115">[out] The buffer in which to place the metadata.</span></span>  
  
 `dataSize`  
 <span data-ttu-id="845fb-116">dışı Döndürülen meta verilerin boyutu.</span><span class="sxs-lookup"><span data-stu-id="845fb-116">[out] The size of the metadata that is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="845fb-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="845fb-117">Remarks</span></span>  

 <span data-ttu-id="845fb-118">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="845fb-118">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="845fb-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="845fb-119">Requirements</span></span>  

 <span data-ttu-id="845fb-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="845fb-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="845fb-121">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="845fb-121">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="845fb-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="845fb-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="845fb-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="845fb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="845fb-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="845fb-124">See also</span></span>

- [<span data-ttu-id="845fb-125">ICLRMetadataLocator Arabirimi</span><span class="sxs-lookup"><span data-stu-id="845fb-125">ICLRMetadataLocator Interface</span></span>](iclrmetadatalocator-interface.md)
