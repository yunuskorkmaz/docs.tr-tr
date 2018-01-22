---
title: IBindingDisplay::GetCurrentDisplay Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IBindingDisplay.GetCurrentDisplay
api_location: diasymreader.dll
api_type: COM
f1_keywords: IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cce7638bfe6ffe0d4b5f7f9a64aaff0c59c860cb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="d8a89-102">IBindingDisplay::GetCurrentDisplay Metodu</span><span class="sxs-lookup"><span data-stu-id="d8a89-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="d8a89-103">Geçerli bağlama görüntü bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8a89-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8a89-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8a89-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8a89-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8a89-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="d8a89-106">[Çıkış, retval] Bağlama görüntü bilgilerini içeren bir SAFEARRAY'i gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d8a89-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8a89-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8a89-107">Remarks</span></span>  
 <span data-ttu-id="d8a89-108">[Ibindingdisplay::ınitializeforprocess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) yöntemi gerekir daha önce başarılı ve programı bir hata ayıklayıcı tarafından durdurulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8a89-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="d8a89-109">Çağıran döndürülen ayırması `SAFEARRAY` kullanarak bellek [SafeArrayDestroy](http://msdn.microsoft.com/library/fc94f7e7-b903-4c78-905c-54df1f8d13fa).</span><span class="sxs-lookup"><span data-stu-id="d8a89-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](http://msdn.microsoft.com/library/fc94f7e7-b903-4c78-905c-54df1f8d13fa).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8a89-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8a89-110">Requirements</span></span>  
 <span data-ttu-id="d8a89-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8a89-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8a89-112">**Başlık:** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="d8a89-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="d8a89-113">**Kitaplığı:** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="d8a89-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="d8a89-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8a89-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8a89-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8a89-115">See Also</span></span>  
 [<span data-ttu-id="d8a89-116">IBindingDisplay Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8a89-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 [<span data-ttu-id="d8a89-117">InitializeForProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8a89-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
