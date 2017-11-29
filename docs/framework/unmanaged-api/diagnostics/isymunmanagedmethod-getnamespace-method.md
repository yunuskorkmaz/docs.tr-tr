---
title: ISymUnmanagedMethod::GetNamespace Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5aff1bcd98e67f381340ed81a187db591c0986be
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="5b1b9-102">ISymUnmanagedMethod::GetNamespace Metodu</span><span class="sxs-lookup"><span data-stu-id="5b1b9-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="5b1b9-103">Bu yöntem tanımlandığı ad alır.</span><span class="sxs-lookup"><span data-stu-id="5b1b9-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b1b9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b1b9-104">Syntax</span></span>  
  
```  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b1b9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5b1b9-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="5b1b9-106">[out] Ayarlanmış bir işaretçi döndürülen için [Isymunmanagednamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5b1b9-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b1b9-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5b1b9-107">Return Value</span></span>  
 <span data-ttu-id="5b1b9-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5b1b9-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b1b9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b1b9-109">Requirements</span></span>  
 <span data-ttu-id="5b1b9-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5b1b9-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b1b9-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5b1b9-111">See Also</span></span>  
 [<span data-ttu-id="5b1b9-112">Isymunmanagedmethod arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b1b9-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
