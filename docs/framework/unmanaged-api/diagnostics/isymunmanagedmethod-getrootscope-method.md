---
title: ISymUnmanagedMethod::GetRootScope Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRootScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 458f6ab4a6848ce6921542ca62fe6d5c7cf4719f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704647"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="738bc-102">ISymUnmanagedMethod::GetRootScope Metodu</span><span class="sxs-lookup"><span data-stu-id="738bc-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="738bc-103">Bu yöntem kök sözlü kapsamda alır.</span><span class="sxs-lookup"><span data-stu-id="738bc-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="738bc-104">Bu kapsam tüm yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="738bc-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="738bc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="738bc-105">Syntax</span></span>  
  
```  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="738bc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="738bc-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="738bc-107">[out] Ayarlanmış bir işaretçi ve döndürülen [Isymunmanagedscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="738bc-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="738bc-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="738bc-108">Return Value</span></span>  
 <span data-ttu-id="738bc-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="738bc-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="738bc-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="738bc-110">Requirements</span></span>  
 <span data-ttu-id="738bc-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="738bc-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="738bc-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="738bc-112">See also</span></span>
- [<span data-ttu-id="738bc-113">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="738bc-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
