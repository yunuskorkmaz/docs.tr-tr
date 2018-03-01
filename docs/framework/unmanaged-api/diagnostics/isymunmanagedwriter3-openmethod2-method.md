---
title: "ISymUnmanagedWriter3::OpenMethod2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8da6de0271ddce5b956e667420a206c09cc291d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="109c9-102">ISymUnmanagedWriter3::OpenMethod2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="109c9-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="109c9-103">Bir yöntem açar ve gerçek bölüm sapması görüntüdeki sağlar.</span><span class="sxs-lookup"><span data-stu-id="109c9-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="109c9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="109c9-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="109c9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="109c9-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="109c9-106">[in] Yöntemin açılması meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="109c9-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="109c9-107">[in] Görüntüde bölüm uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="109c9-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="109c9-108">[in] Görüntüde uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="109c9-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="109c9-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="109c9-109">Return Value</span></span>  
 <span data-ttu-id="109c9-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="109c9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="109c9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="109c9-111">Requirements</span></span>  
 <span data-ttu-id="109c9-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="109c9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="109c9-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="109c9-113">See Also</span></span>  
 [<span data-ttu-id="109c9-114">ISymUnmanagedWriter3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="109c9-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 [<span data-ttu-id="109c9-115">OpenMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="109c9-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
