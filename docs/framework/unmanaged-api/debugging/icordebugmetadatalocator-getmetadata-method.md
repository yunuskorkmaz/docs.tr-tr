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
ms.openlocfilehash: 43f3c1dd866b98bff51b375a11e28727e41d3ead
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793047"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="5413e-102">ICorDebugMetaDataLocator::GetMetaData Metodu</span><span class="sxs-lookup"><span data-stu-id="5413e-102">ICorDebugMetaDataLocator::GetMetaData Method</span></span>
<span data-ttu-id="5413e-103">Hata ayıklayıcının istenen bir işlemi tamamlaması için gereken meta verileri bir modülün tam yolunu döndürmesini ister.</span><span class="sxs-lookup"><span data-stu-id="5413e-103">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5413e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5413e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="5413e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5413e-105">Parameters</span></span>  
 `wszImagePath`  
 <span data-ttu-id="5413e-106">'ndaki Dosyanın tam yolunu temsil eden, null ile sonlandırılmış bir dize.</span><span class="sxs-lookup"><span data-stu-id="5413e-106">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="5413e-107">Tam yol kullanılamıyorsa dosyanın adı ve uzantısı (*filename*. *Uzantısı*).</span><span class="sxs-lookup"><span data-stu-id="5413e-107">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="5413e-108">'ndaki Görüntünün PE dosya üst bilgilerindeki zaman damgası.</span><span class="sxs-lookup"><span data-stu-id="5413e-108">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="5413e-109">Bu parametre, bir sembol sunucusu ([symsrv](/windows/desktop/debug/using-symsrv)) araması için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5413e-109">This parameter can potentially be used for a symbol server ([SymSrv](/windows/desktop/debug/using-symsrv)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="5413e-110">'ndaki PE dosya başlıklarından görüntü boyutu.</span><span class="sxs-lookup"><span data-stu-id="5413e-110">[in] The image size from PE file headers.</span></span> <span data-ttu-id="5413e-111">Bu parametre, bir SymSrv araması için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5413e-111">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="5413e-112">'ndaki `wszPathBuffer`karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="5413e-112">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="5413e-113">dışı `wszPathBuffer`yazılan `WCHAR`s sayısı.</span><span class="sxs-lookup"><span data-stu-id="5413e-113">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="5413e-114">Yöntem E_NOT_SUFFICIENT_BUFFER döndürürse, yolu depolamak için gereken `WCHAR`s sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="5413e-114">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="5413e-115">dışı Hata ayıklayıcının istenen meta verileri içeren dosyanın tam yolunu kopyalayabileceği bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5413e-115">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="5413e-116">[CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) numaralandırmasındaki `ofReadOnly` bayrağı, bu dosyadaki meta verilere salt okuma erişimi istemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5413e-116">The `ofReadOnly` flag from the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5413e-117">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5413e-117">Return Value</span></span>  
 <span data-ttu-id="5413e-118">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="5413e-118">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="5413e-119">Diğer tüm Hata HRESULTs 'ler dosyanın alınabilir olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5413e-119">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="5413e-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5413e-120">HRESULT</span></span>|<span data-ttu-id="5413e-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5413e-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5413e-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="5413e-122">S_OK</span></span>|<span data-ttu-id="5413e-123">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="5413e-123">The method completed successfully.</span></span> <span data-ttu-id="5413e-124">`wszPathBuffer` dosyanın tam yolunu içerir ve null ile sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="5413e-124">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="5413e-125">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="5413e-125">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="5413e-126">`wszPathBuffer` geçerli boyutu tam yolu tutmak için yeterli değil.</span><span class="sxs-lookup"><span data-stu-id="5413e-126">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="5413e-127">Bu durumda `pcchPathBuffer`, Sonlandırıcı null karakteri de dahil olmak üzere gerekli `WCHAR`sayısını içerir ve istenen arabellek boyutuyla `GetMetaData` ikinci bir kez çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5413e-127">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5413e-128">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5413e-128">Remarks</span></span>  
 <span data-ttu-id="5413e-129">`wszImagePath` bir modülden bir modülün tam yolunu içeriyorsa, dökümün toplandığı bilgisayardan yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5413e-129">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="5413e-130">Dosya bu konumda bulunmayabilir veya yolda aynı ada sahip yanlış bir dosya depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="5413e-130">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5413e-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5413e-131">Requirements</span></span>  
 <span data-ttu-id="5413e-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5413e-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5413e-133">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5413e-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5413e-134">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5413e-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5413e-135">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5413e-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5413e-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5413e-136">See also</span></span>

- [<span data-ttu-id="5413e-137">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5413e-137">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="5413e-138">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5413e-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5413e-139">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="5413e-139">Debugging</span></span>](index.md)
