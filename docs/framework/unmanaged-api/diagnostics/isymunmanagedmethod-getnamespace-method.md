---
title: ISymUnmanagedMethod::GetNamespace Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 544fffd1b230469227d6ddbe3afcba54b6a7d5c1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484595"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="51dc9-102">ISymUnmanagedMethod::GetNamespace Metodu</span><span class="sxs-lookup"><span data-stu-id="51dc9-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="51dc9-103">Bu yöntem içinde tanımlandığı ad alanını alır.</span><span class="sxs-lookup"><span data-stu-id="51dc9-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51dc9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51dc9-104">Syntax</span></span>  
  
```  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51dc9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51dc9-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="51dc9-106">[out] Ayarlanmış bir işaretçi ve döndürülen [Isymunmanagednamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="51dc9-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="51dc9-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="51dc9-107">Return Value</span></span>  
 <span data-ttu-id="51dc9-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="51dc9-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51dc9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51dc9-109">Requirements</span></span>  
 <span data-ttu-id="51dc9-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="51dc9-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51dc9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51dc9-111">See also</span></span>
- [<span data-ttu-id="51dc9-112">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51dc9-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
