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
ms.openlocfilehash: 417ce67d807fddd3b99ceff4b05f1524db3044e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430534"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="ae335-102">ISymUnmanagedMethod::GetRootScope Metodu</span><span class="sxs-lookup"><span data-stu-id="ae335-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="ae335-103">Bu yöntem için kök sözcük kapsamda alır.</span><span class="sxs-lookup"><span data-stu-id="ae335-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="ae335-104">Bu kapsam tüm yöntemi barındırır.</span><span class="sxs-lookup"><span data-stu-id="ae335-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae335-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae335-105">Syntax</span></span>  
  
```  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae335-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae335-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ae335-107">[out] Ayarlanmış bir işaretçi döndürülen için [Isymunmanagedscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ae335-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae335-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ae335-108">Return Value</span></span>  
 <span data-ttu-id="ae335-109">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ae335-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae335-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae335-110">Requirements</span></span>  
 <span data-ttu-id="ae335-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ae335-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae335-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ae335-112">See Also</span></span>  
 [<span data-ttu-id="ae335-113">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae335-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
