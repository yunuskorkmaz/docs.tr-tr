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
ms.openlocfilehash: 3677b38854ada67c4f2d30043bf80a83d9268971
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655006"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="9e5da-102">ICorDebugMetaDataLocator::GetMetaData Metodu</span><span class="sxs-lookup"><span data-stu-id="9e5da-102">ICorDebugMetaDataLocator::GetMetaData Method</span></span>
<span data-ttu-id="9e5da-103">Tam yolu, meta veri hata ayıklayıcı istenen bir işlemi tamamlamak için gereken bir birime geri dönmek için hata ayıklayıcı ister.</span><span class="sxs-lookup"><span data-stu-id="9e5da-103">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e5da-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9e5da-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="9e5da-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9e5da-105">Parameters</span></span>  
 `wszImagePath`  
 <span data-ttu-id="9e5da-106">[in] Dosyaya tam yolunu temsil ettiği bir null ile sonlandırılmış bir dize.</span><span class="sxs-lookup"><span data-stu-id="9e5da-106">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="9e5da-107">Tam yol mevcut değilse adı ve dosya uzantısını (*filename*. *Uzantı*).</span><span class="sxs-lookup"><span data-stu-id="9e5da-107">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="9e5da-108">[in] Görüntünün PE dosyası başlıklarından zaman damgası.</span><span class="sxs-lookup"><span data-stu-id="9e5da-108">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="9e5da-109">Bu parametre için bir sembol sunucusu potansiyel olarak kullanılabilir ([SymSrv](/windows/desktop/debug/using-symsrv)) araması.</span><span class="sxs-lookup"><span data-stu-id="9e5da-109">This parameter can potentially be used for a symbol server ([SymSrv](/windows/desktop/debug/using-symsrv)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="9e5da-110">[in] PE dosyası başlıklarından resim boyutu.</span><span class="sxs-lookup"><span data-stu-id="9e5da-110">[in] The image size from PE file headers.</span></span> <span data-ttu-id="9e5da-111">Bu parametre, büyük olasılıkla SymSrv arama için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9e5da-111">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="9e5da-112">[in] Karakter sayısında `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="9e5da-112">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="9e5da-113">[out] Sayısı `WCHAR`yazılan s `wszPathBuffer`.</span><span class="sxs-lookup"><span data-stu-id="9e5da-113">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="9e5da-114">Yöntem E_NOT_SUFFICIENT_BUFFER döndürürse, sayısı içeren `WCHAR`s gereken yolu depolamak.</span><span class="sxs-lookup"><span data-stu-id="9e5da-114">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="9e5da-115">[out] İçine istenen meta verilerini içeren dosyanın tam yolunu hata ayıklayıcı kopyalayacak bir arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9e5da-115">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="9e5da-116">`ofReadOnly` Gelen bayrak [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırma meta verileri bu dosyada salt okunur erişim istemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9e5da-116">The `ofReadOnly` flag from the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e5da-117">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9e5da-117">Return Value</span></span>  
 <span data-ttu-id="9e5da-118">Bu yöntem aşağıdaki özel HRESULT'ları yanı sıra HRESULT döndürür yöntemi hatayı gösteren hatalar.</span><span class="sxs-lookup"><span data-stu-id="9e5da-118">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="9e5da-119">Diğer tüm başarısız HRESULTs dosya alınabilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e5da-119">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="9e5da-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e5da-120">HRESULT</span></span>|<span data-ttu-id="9e5da-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9e5da-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e5da-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e5da-122">S_OK</span></span>|<span data-ttu-id="9e5da-123">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9e5da-123">The method completed successfully.</span></span> <span data-ttu-id="9e5da-124">`wszPathBuffer` dosyanın tam yolunu içerir ve null sonlandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="9e5da-124">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="9e5da-125">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="9e5da-125">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="9e5da-126">Geçerli boyutunu `wszPathBuffer` tam yolunu tutmak yeterli değil.</span><span class="sxs-lookup"><span data-stu-id="9e5da-126">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="9e5da-127">Bu durumda, `pcchPathBuffer` gerekli sayısı içeren `WCHAR`s, sonlandırıcı null karakter de dahil olmak üzere ve `GetMetaData` istenen arabellek boyutu ile ikinci kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9e5da-127">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e5da-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9e5da-128">Remarks</span></span>  
 <span data-ttu-id="9e5da-129">Varsa `wszImagePath` tam yolu içeren isteğe bağlı olarak bir modülden için bir döküm, döküm burada toplanmıştır bilgisayardan yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9e5da-129">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="9e5da-130">Dosyanın bu konumda mevcut değil veya yanlış bir dosya aynı ada sahip yol üzerinde depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="9e5da-130">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e5da-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9e5da-131">Requirements</span></span>  
 <span data-ttu-id="9e5da-132">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e5da-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e5da-133">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e5da-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e5da-134">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e5da-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e5da-135">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e5da-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e5da-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e5da-136">See also</span></span>
- [<span data-ttu-id="9e5da-137">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9e5da-137">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="9e5da-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9e5da-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9e5da-139">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9e5da-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
