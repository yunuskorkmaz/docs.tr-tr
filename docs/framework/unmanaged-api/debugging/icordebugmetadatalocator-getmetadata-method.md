---
description: ': ICorDebugMetaDataLocator:: GetMetaData Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 419a03e42a54057ab70e31a368e918612f3a85f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691698"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a><span data-ttu-id="3134e-103">ICorDebugMetaDataLocator::GetMetaData Metodu</span><span class="sxs-lookup"><span data-stu-id="3134e-103">ICorDebugMetaDataLocator::GetMetaData Method</span></span>

<span data-ttu-id="3134e-104">Hata ayıklayıcının istenen bir işlemi tamamlaması için gereken meta verileri bir modülün tam yolunu döndürmesini ister.</span><span class="sxs-lookup"><span data-stu-id="3134e-104">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3134e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3134e-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="3134e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3134e-106">Parameters</span></span>  

 `wszImagePath`  
 <span data-ttu-id="3134e-107">'ndaki Dosyanın tam yolunu temsil eden, null ile sonlandırılmış bir dize.</span><span class="sxs-lookup"><span data-stu-id="3134e-107">[in] A null-terminated string that represents the full path to the file.</span></span> <span data-ttu-id="3134e-108">Tam yol kullanılamıyorsa dosyanın adı ve uzantısı (*filename*.*Uzantısı*).</span><span class="sxs-lookup"><span data-stu-id="3134e-108">If the full path is not available, the name and extension of the file (*filename*.*extension*).</span></span>  
  
 `dwImageTimeStamp`  
 <span data-ttu-id="3134e-109">'ndaki Görüntünün PE dosya üst bilgilerindeki zaman damgası.</span><span class="sxs-lookup"><span data-stu-id="3134e-109">[in] The time stamp from the image's PE file headers.</span></span> <span data-ttu-id="3134e-110">Bu parametre, bir sembol sunucusu ([symsrv](/windows/desktop/debug/using-symsrv)) araması için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3134e-110">This parameter can potentially be used for a symbol server ([SymSrv](/windows/desktop/debug/using-symsrv)) lookup.</span></span>  
  
 `dwImageSize`  
 <span data-ttu-id="3134e-111">'ndaki PE dosya başlıklarından görüntü boyutu.</span><span class="sxs-lookup"><span data-stu-id="3134e-111">[in] The image size from PE file headers.</span></span> <span data-ttu-id="3134e-112">Bu parametre, bir SymSrv araması için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3134e-112">This parameter can potentially be used for a SymSrv lookup.</span></span>  
  
 `cchPathBuffer`  
 <span data-ttu-id="3134e-113">'ndaki İçindeki karakter sayısı `wszPathBuffer` .</span><span class="sxs-lookup"><span data-stu-id="3134e-113">[in] The character count in `wszPathBuffer`.</span></span>  
  
 `pcchPathBuffer`  
 <span data-ttu-id="3134e-114">dışı `WCHAR`Üzerine yazılan s sayısı `wszPathBuffer` .</span><span class="sxs-lookup"><span data-stu-id="3134e-114">[out] The count of `WCHAR`s written to `wszPathBuffer`.</span></span>  
  
 <span data-ttu-id="3134e-115">Yöntem E_NOT_SUFFICIENT_BUFFER döndürürse, `WCHAR` yolu depolamak için gereken s sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="3134e-115">If the method returns E_NOT_SUFFICIENT_BUFFER, contains the count of `WCHAR`s needed to store the path.</span></span>  
  
 `wszPathBuffer`  
 <span data-ttu-id="3134e-116">dışı Hata ayıklayıcının istenen meta verileri içeren dosyanın tam yolunu kopyalayabileceği bir arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3134e-116">[out] Pointer to a buffer into which the debugger will copy the full path of the file that contains the requested metadata.</span></span>  
  
 <span data-ttu-id="3134e-117">`ofReadOnly` [CorOpenFlags](../metadata/coropenflags-enumeration.md) numaralandırmasındaki bayrak, bu dosyadaki meta verilere salt okuma erişimi istemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3134e-117">The `ofReadOnly` flag from the [CorOpenFlags](../metadata/coropenflags-enumeration.md) enumeration is used to request read-only access to the metadata in this file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3134e-118">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3134e-118">Return Value</span></span>  

 <span data-ttu-id="3134e-119">Bu yöntem, aşağıdaki belirli Hsonuçların yanı sıra Yöntem hatasını belirten HRESULT hataları döndürür.</span><span class="sxs-lookup"><span data-stu-id="3134e-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span> <span data-ttu-id="3134e-120">Diğer tüm Hata HRESULTs 'ler dosyanın alınabilir olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3134e-120">All other failure HRESULTs indicate that the file is not retrievable.</span></span>  
  
|<span data-ttu-id="3134e-121">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3134e-121">HRESULT</span></span>|<span data-ttu-id="3134e-122">Description</span><span class="sxs-lookup"><span data-stu-id="3134e-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3134e-123">S_OK</span><span class="sxs-lookup"><span data-stu-id="3134e-123">S_OK</span></span>|<span data-ttu-id="3134e-124">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="3134e-124">The method completed successfully.</span></span> <span data-ttu-id="3134e-125">`wszPathBuffer` dosyanın tam yolunu içerir ve null ile sonlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3134e-125">`wszPathBuffer` contains the full path to the file and is null-terminated.</span></span>|  
|<span data-ttu-id="3134e-126">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="3134e-126">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="3134e-127">Geçerli boyutu `wszPathBuffer` tam yolu tutmak için yeterli değil.</span><span class="sxs-lookup"><span data-stu-id="3134e-127">The current size of `wszPathBuffer` is not sufficient to hold the full path.</span></span> <span data-ttu-id="3134e-128">Bu durumda, `pcchPathBuffer` `WCHAR` Sonlandırıcı null karakteri dahil olmak üzere gerekli sayısını içerir ve `GetMetaData` İstenen arabellek boyutuyla ikinci bir kez çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3134e-128">In this case, `pcchPathBuffer` contains the needed count of `WCHAR`s, including the terminating null character, and `GetMetaData` is called a second time with the requested buffer size.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3134e-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3134e-129">Remarks</span></span>  

 <span data-ttu-id="3134e-130">Bir `wszImagePath` Modül için bir dökümden tam yol içeriyorsa, dökümün toplandığı bilgisayardan yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="3134e-130">If `wszImagePath` contains a full path for a module from a dump, it specifies the path from the computer where the dump was collected.</span></span> <span data-ttu-id="3134e-131">Dosya bu konumda bulunmayabilir veya yolda aynı ada sahip yanlış bir dosya depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="3134e-131">The file may not exist at this location, or an incorrect file with the same name may be stored on the path.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3134e-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3134e-132">Requirements</span></span>  

 <span data-ttu-id="3134e-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3134e-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3134e-134">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3134e-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3134e-135">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3134e-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3134e-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3134e-136">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3134e-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3134e-137">See also</span></span>

- [<span data-ttu-id="3134e-138">ICorDebugThread4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3134e-138">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="3134e-139">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3134e-139">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3134e-140">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="3134e-140">Debugging</span></span>](index.md)
