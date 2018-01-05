---
title: ICorDebugMetaDataLocator::GetMetaData Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMetaDataLocator.GetMetaData
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4883ee56c7dd027f053dd072d7c8613f606ff2be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="8024a-102">ICorDebugMetaDataLocator::GetMetaData Metodu</span><span class="sxs-lookup"><span data-stu-id="8024a-102">ICorDebugMetaDataLocator::GetMetaData Method</span></span>
<span data-ttu-id="8024a-103">Tam yolu, meta veri hata ayıklayıcı istenen işlemi tamamlamak için gereken bir birime geri dönmek için hata ayıklayıcı sorar.</span><span class="sxs-lookup"><span data-stu-id="8024a-103">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8024a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8024a-104">Syntax</span></span>  
  
```  
HRESULT GetMetaData(  
      [in] LPCWSTR wszImagePath,  
      [in] DWORD   dwImageTimeStamp,  
      [in] DWORD   dwImageSize,  
      [in] ULONG32 cchPathBuffer,  
      [out] ULONG32 * pcchPathBuffer,  
      [out, size_is(cchPathBuffer), length_is(*pcchPathBuffer)]  
               WCHAR wszPathBuffer[]  
      );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8024a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8024a-105">Parameters</span></span>  
 `wszImagePath`  
 <span data-ttu-id="8024a-106">[in] Dosyaya tam yolunu gösteren bir null ile sonlandırılmış bir dize.</span><span class="sxs-lookup"><span data-stu-id="8024a-106">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="8024a-107">Tam yol kullanılabilir değilse adı ve dosya uzantısını (*filename*. *Uzantı*).</span><span class="sxs-lookup"><span data-stu-id="8024a-107">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="8024a-108">[in] Resmin PE dosya başlıklarından zaman damgası.</span><span class="sxs-lookup"><span data-stu-id="8024a-108">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="8024a-109">Bu parametre için bir simge sunucusu potansiyel olarak kullanılabilir ([SymSrv](http://msdn.microsoft.com/library/cc266470.aspx)) arama.</span><span class="sxs-lookup"><span data-stu-id="8024a-109">This parameter can potentially be used for a symbol server ([SymSrv](http://msdn.microsoft.com/library/cc266470.aspx)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="8024a-110">[in] Görüntü boyutu PE dosya başlıklarından.</span><span class="sxs-lookup"><span data-stu-id="8024a-110">[in] The image size from PE file headers.</span></span> <span data-ttu-id="8024a-111">Bu parametre için bir SymSrv arama potansiyel olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8024a-111">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="8024a-112">[in] Karakter sayısı `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="8024a-112">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="8024a-113">[out] Sayısı `WCHAR`yazılan s `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="8024a-113">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="8024a-114">Yöntem E_NOT_SUFFICIENT_BUFFER döndürüyorsa sayısını içeren `WCHAR`s gerekli yolun depolamak.</span><span class="sxs-lookup"><span data-stu-id="8024a-114">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="8024a-115">[out] İşaretçi arabellek için istenen meta verilerini içeren dosyanın tam yolunu içine hata ayıklayıcı kopyalayacak.</span><span class="sxs-lookup"><span data-stu-id="8024a-115">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="8024a-116">`ofReadOnly` Gelen bayrak [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırması bu dosyadaki meta veriler salt okunur erişim istemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8024a-116">The `ofReadOnly` flag from the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8024a-117">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8024a-117">Return Value</span></span>  
 <span data-ttu-id="8024a-118">Bu yöntem aşağıdaki belirli HRESULTs yanı sıra HRESULT yöntem hatası olduğunu gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="8024a-118">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="8024a-119">Diğer tüm hata HRESULTs dosyası alınabilir olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8024a-119">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="8024a-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8024a-120">HRESULT</span></span>|<span data-ttu-id="8024a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8024a-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8024a-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="8024a-122">S_OK</span></span>|<span data-ttu-id="8024a-123">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="8024a-123">The method completed successfully.</span></span> <span data-ttu-id="8024a-124">`wszPathBuffer`sonlandırılmış ve dosyanın tam yolunu içerir.</span><span class="sxs-lookup"><span data-stu-id="8024a-124">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="8024a-125">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="8024a-125">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="8024a-126">Geçerli boyutunu `wszPathBuffer` tam yolunu tutmak yeterli değil.</span><span class="sxs-lookup"><span data-stu-id="8024a-126">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="8024a-127">Bu durumda, `pcchPathBuffer` gerekli sayısını içeren `WCHAR`sonlandırma null karakteri de dahil olmak üzere s ve `GetMetaData` istenen arabellek boyutuna sahip ikinci bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8024a-127">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8024a-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8024a-128">Remarks</span></span>  
 <span data-ttu-id="8024a-129">Varsa `wszImagePath` tam bir yol içeriyor isteğe bağlı olarak bir modülden için bir döküm, burada döküm toplandı bilgisayardan yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8024a-129">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="8024a-130">Dosyanın bu konumda var olmayabilir veya aynı ada sahip yanlış bir dosya yolunda depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="8024a-130">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8024a-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8024a-131">Requirements</span></span>  
 <span data-ttu-id="8024a-132">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8024a-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8024a-133">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8024a-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8024a-134">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8024a-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8024a-135">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8024a-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8024a-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8024a-136">See Also</span></span>  
 [<span data-ttu-id="8024a-137">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8024a-137">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [<span data-ttu-id="8024a-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8024a-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8024a-139">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8024a-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
