---
title: ICorDebugMetaDataLocator::GetMetaData Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator.GetMetaData
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c787a93ac98a086dfb6218d1b4891de87e0e107d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487009"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="b646d-102">ICorDebugMetaDataLocator::GetMetaData Metodu</span><span class="sxs-lookup"><span data-stu-id="b646d-102">ICorDebugMetaDataLocator::GetMetaData Method</span></span>
<span data-ttu-id="b646d-103">Tam yolu, meta veri hata ayıklayıcı istenen bir işlemi tamamlamak için gereken bir birime geri dönmek için hata ayıklayıcı ister.</span><span class="sxs-lookup"><span data-stu-id="b646d-103">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b646d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b646d-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b646d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b646d-105">Parameters</span></span>  
 `wszImagePath`  
 <span data-ttu-id="b646d-106">[in] Dosyaya tam yolunu temsil ettiği bir null ile sonlandırılmış bir dize.</span><span class="sxs-lookup"><span data-stu-id="b646d-106">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="b646d-107">Tam yol mevcut değilse adı ve dosya uzantısını (*filename*. *Uzantı*).</span><span class="sxs-lookup"><span data-stu-id="b646d-107">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="b646d-108">[in] Görüntünün PE dosyası başlıklarından zaman damgası.</span><span class="sxs-lookup"><span data-stu-id="b646d-108">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="b646d-109">Bu parametre için bir sembol sunucusu potansiyel olarak kullanılabilir ([SymSrv](/windows/desktop/debug/using-symsrv)) araması.</span><span class="sxs-lookup"><span data-stu-id="b646d-109">This parameter can potentially be used for a symbol server ([SymSrv](/windows/desktop/debug/using-symsrv)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="b646d-110">[in] PE dosyası başlıklarından resim boyutu.</span><span class="sxs-lookup"><span data-stu-id="b646d-110">[in] The image size from PE file headers.</span></span> <span data-ttu-id="b646d-111">Bu parametre, büyük olasılıkla SymSrv arama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b646d-111">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="b646d-112">[in] Karakter sayısında `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="b646d-112">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="b646d-113">[out] Sayısı `WCHAR`yazılan s `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="b646d-113">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="b646d-114">Yöntem E_NOT_SUFFICIENT_BUFFER döndürürse, sayısı içeren `WCHAR`s gereken yolu depolamak.</span><span class="sxs-lookup"><span data-stu-id="b646d-114">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="b646d-115">[out] İçine istenen meta verilerini içeren dosyanın tam yolunu hata ayıklayıcı kopyalayacak bir arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b646d-115">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="b646d-116">`ofReadOnly` Gelen bayrak [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırma meta verileri bu dosyada salt okunur erişim istemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b646d-116">The `ofReadOnly` flag from the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b646d-117">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b646d-117">Return Value</span></span>  
 <span data-ttu-id="b646d-118">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="b646d-118">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="b646d-119">Diğer tüm başarısız HRESULTs dosya alınabilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b646d-119">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="b646d-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b646d-120">HRESULT</span></span>|<span data-ttu-id="b646d-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b646d-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b646d-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="b646d-122">S_OK</span></span>|<span data-ttu-id="b646d-123">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="b646d-123">The method completed successfully.</span></span> <span data-ttu-id="b646d-124">`wszPathBuffer` dosyanın tam yolunu içerir ve null sonlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b646d-124">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="b646d-125">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="b646d-125">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="b646d-126">Geçerli boyutunu `wszPathBuffer` tam yolunu tutmak yeterli değil.</span><span class="sxs-lookup"><span data-stu-id="b646d-126">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="b646d-127">Bu durumda, `pcchPathBuffer` gerekli sayısı içeren `WCHAR`s, sonlandırıcı null karakter de dahil olmak üzere ve `GetMetaData` istenen arabellek boyutu ile ikinci kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b646d-127">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b646d-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b646d-128">Remarks</span></span>  
 <span data-ttu-id="b646d-129">Varsa `wszImagePath` tam yolu içeren isteğe bağlı olarak bir modülden için bir döküm, döküm burada toplanmıştır bilgisayardan yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b646d-129">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="b646d-130">Dosyanın bu konumda mevcut değil veya yanlış bir dosya aynı ada sahip yol üzerinde depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="b646d-130">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b646d-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b646d-131">Requirements</span></span>  
 <span data-ttu-id="b646d-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b646d-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b646d-133">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b646d-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b646d-134">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b646d-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b646d-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b646d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b646d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b646d-136">See also</span></span>
- [<span data-ttu-id="b646d-137">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b646d-137">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="b646d-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b646d-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b646d-139">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b646d-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
