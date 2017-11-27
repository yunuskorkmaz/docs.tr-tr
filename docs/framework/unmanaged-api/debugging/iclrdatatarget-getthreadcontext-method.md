---
title: ICLRDataTarget::GetThreadContext Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 480b65b279dbc0359b078f3f1d543f63a0bfd0f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="c5ee7-102">ICLRDataTarget::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="c5ee7-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="c5ee7-103">Hedef işlemdeki verilen iş parçacığı için geçerli yürütme bağlamı alır.</span><span class="sxs-lookup"><span data-stu-id="c5ee7-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="c5ee7-104">Bu yöntem ortak dil çalışma zamanı veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c5ee7-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5ee7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5ee7-105">Syntax</span></span>  
  
```  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5ee7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5ee7-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c5ee7-107">[in] Bir iş parçacığı hedef işlem, işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="c5ee7-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="c5ee7-108">[in] Döndürülecek bağlam hangi kısımlarının belirtin bayraklar.</span><span class="sxs-lookup"><span data-stu-id="c5ee7-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="c5ee7-109">Uygulama bağlamı en az bu bölümlerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="c5ee7-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="c5ee7-110">[in] İçerik boyutu.</span><span class="sxs-lookup"><span data-stu-id="c5ee7-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="c5ee7-111">[out] Bağlam yerleştirileceği bir arabellek işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c5ee7-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="c5ee7-112">Verileri `context` arabellek Win32 biçiminde olmalıdır `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="c5ee7-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="c5ee7-113">Bağlam işlemciye özgü kayıt verilerini, bu nedenle belirtir Win32 tanımını `CONTEXT` yapısı işlemci mimarisine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5ee7-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="c5ee7-114">Win32 tanımını WinNT.h üstbilgi dosyasına `CONTEXT` yapısı.</span><span class="sxs-lookup"><span data-stu-id="c5ee7-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5ee7-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5ee7-115">Remarks</span></span>  
 <span data-ttu-id="c5ee7-116">Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c5ee7-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5ee7-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5ee7-117">Requirements</span></span>  
 <span data-ttu-id="c5ee7-118">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5ee7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5ee7-119">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c5ee7-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c5ee7-120">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5ee7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5ee7-121">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5ee7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5ee7-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5ee7-122">See Also</span></span>  
 [<span data-ttu-id="c5ee7-123">Iclrdatatarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5ee7-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
