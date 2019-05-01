---
title: ISymUnmanagedMethod::GetRootScope Yöntemi
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
ms.openlocfilehash: 7c77be0dde950693d3943e41c392dcdcd9bc995e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939613"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="582c4-102">ISymUnmanagedMethod::GetRootScope Yöntemi</span><span class="sxs-lookup"><span data-stu-id="582c4-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="582c4-103">Bu yöntem kök sözlü kapsamda alır.</span><span class="sxs-lookup"><span data-stu-id="582c4-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="582c4-104">Bu kapsam tüm yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="582c4-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="582c4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="582c4-105">Syntax</span></span>  
  
```  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="582c4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="582c4-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="582c4-107">[out] Ayarlanmış bir işaretçi ve döndürülen [Isymunmanagedscope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="582c4-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="582c4-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="582c4-108">Return Value</span></span>  
 <span data-ttu-id="582c4-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="582c4-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="582c4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="582c4-110">Requirements</span></span>  
 <span data-ttu-id="582c4-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="582c4-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="582c4-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="582c4-112">See also</span></span>

- [<span data-ttu-id="582c4-113">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="582c4-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
