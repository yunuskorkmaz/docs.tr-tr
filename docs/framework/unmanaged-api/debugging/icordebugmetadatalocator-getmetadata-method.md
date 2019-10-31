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
ms.openlocfilehash: 6e4f11de423d1ab6b66aca40e671607a383a4413
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136629"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="d32d2-102">ICorDebugMetaDataLocator::GetMetaData Metodu</span><span class="sxs-lookup"><span data-stu-id="d32d2-102">ICorDebugMetaDataLocator::GetMetaData Method</span></span>
<span data-ttu-id="d32d2-103">Hata ayıklayıcının istenen bir işlemi tamamlaması için gereken meta verileri bir modülün tam yolunu döndürmesini ister.</span><span class="sxs-lookup"><span data-stu-id="d32d2-103">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d32d2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d32d2-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="d32d2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d32d2-105">Parameters</span></span>  
 `wszImagePath`  
 <span data-ttu-id="d32d2-106">'ndaki Dosyanın tam yolunu temsil eden, null ile sonlandırılmış bir dize.</span><span class="sxs-lookup"><span data-stu-id="d32d2-106">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="d32d2-107">Tam yol kullanılamıyorsa dosyanın adı ve uzantısı (*filename*. *Uzantısı*).</span><span class="sxs-lookup"><span data-stu-id="d32d2-107">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="d32d2-108">'ndaki Görüntünün PE dosya üst bilgilerindeki zaman damgası.</span><span class="sxs-lookup"><span data-stu-id="d32d2-108">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="d32d2-109">Bu parametre, bir sembol sunucusu ([symsrv](/windows/desktop/debug/using-symsrv)) araması için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d32d2-109">This parameter can potentially be used for a symbol server ([SymSrv](/windows/desktop/debug/using-symsrv)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="d32d2-110">'ndaki PE dosya başlıklarından görüntü boyutu.</span><span class="sxs-lookup"><span data-stu-id="d32d2-110">[in] The image size from PE file headers.</span></span> <span data-ttu-id="d32d2-111">Bu parametre, bir SymSrv araması için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d32d2-111">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="d32d2-112">'ndaki `wszPathBuffer`karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="d32d2-112">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="d32d2-113">dışı `wszPathBuffer`yazılan `WCHAR`s sayısı.</span><span class="sxs-lookup"><span data-stu-id="d32d2-113">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="d32d2-114">Yöntem E_NOT_SUFFICIENT_BUFFER döndürürse, yolu depolamak için gereken `WCHAR`s sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="d32d2-114">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="d32d2-115">dışı Hata ayıklayıcının istenen meta verileri içeren dosyanın tam yolunu kopyalayabileceği bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d32d2-115">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="d32d2-116">[CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırmasındaki `ofReadOnly` bayrağı, bu dosyadaki meta verilere salt okuma erişimi istemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d32d2-116">The `ofReadOnly` flag from the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d32d2-117">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d32d2-117">Return Value</span></span>  
 <span data-ttu-id="d32d2-118">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="d32d2-118">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="d32d2-119">Diğer tüm Hata HRESULTs 'ler dosyanın alınabilir olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d32d2-119">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="d32d2-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d32d2-120">HRESULT</span></span>|<span data-ttu-id="d32d2-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d32d2-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d32d2-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="d32d2-122">S_OK</span></span>|<span data-ttu-id="d32d2-123">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="d32d2-123">The method completed successfully.</span></span> <span data-ttu-id="d32d2-124">`wszPathBuffer` dosyanın tam yolunu içerir ve null ile sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="d32d2-124">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="d32d2-125">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="d32d2-125">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="d32d2-126">`wszPathBuffer` geçerli boyutu tam yolu tutmak için yeterli değil.</span><span class="sxs-lookup"><span data-stu-id="d32d2-126">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="d32d2-127">Bu durumda `pcchPathBuffer`, Sonlandırıcı null karakteri de dahil olmak üzere gerekli `WCHAR`sayısını içerir ve istenen arabellek boyutuyla `GetMetaData` ikinci bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d32d2-127">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d32d2-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d32d2-128">Remarks</span></span>  
 <span data-ttu-id="d32d2-129">`wszImagePath` bir modülden bir modülün tam yolunu içeriyorsa, dökümün toplandığı bilgisayardan yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d32d2-129">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="d32d2-130">Dosya bu konumda bulunmayabilir veya yolda aynı ada sahip yanlış bir dosya depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="d32d2-130">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d32d2-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d32d2-131">Requirements</span></span>  
 <span data-ttu-id="d32d2-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d32d2-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d32d2-133">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d32d2-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d32d2-134">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d32d2-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d32d2-135">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d32d2-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d32d2-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d32d2-136">See also</span></span>

- [<span data-ttu-id="d32d2-137">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d32d2-137">ICorDebugThread4 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [<span data-ttu-id="d32d2-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d32d2-138">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d32d2-139">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d32d2-139">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
