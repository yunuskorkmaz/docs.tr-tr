---
title: ISymUnmanagedMethod::GetRootScope Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetRootScope
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 82b03e6db75d69d1d36f0137922448bad165e6ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="7088d-102">ISymUnmanagedMethod::GetRootScope Metodu</span><span class="sxs-lookup"><span data-stu-id="7088d-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="7088d-103">Bu yöntem için kök sözcük kapsamda alır.</span><span class="sxs-lookup"><span data-stu-id="7088d-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="7088d-104">Bu kapsam tüm yöntemi barındırır.</span><span class="sxs-lookup"><span data-stu-id="7088d-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7088d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7088d-105">Syntax</span></span>  
  
```  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7088d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7088d-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="7088d-107">[out] Ayarlanmış bir işaretçi döndürülen için [Isymunmanagedscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7088d-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7088d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7088d-108">Return Value</span></span>  
 <span data-ttu-id="7088d-109">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="7088d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7088d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7088d-110">Requirements</span></span>  
 <span data-ttu-id="7088d-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7088d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7088d-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7088d-112">See Also</span></span>  
 [<span data-ttu-id="7088d-113">Isymunmanagedmethod arabirimi</span><span class="sxs-lookup"><span data-stu-id="7088d-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
