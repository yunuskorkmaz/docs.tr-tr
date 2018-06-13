---
title: ISymUnmanagedScope::GetLocalCount Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2f8dde609f83a0bbf040ce0e8a4f164259e8584a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427933"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="dda70-102">ISymUnmanagedScope::GetLocalCount Metodu</span><span class="sxs-lookup"><span data-stu-id="dda70-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="dda70-103">Bu kapsam içinde tanımlanan yerel değişkenler sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="dda70-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dda70-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dda70-104">Syntax</span></span>  
  
```  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dda70-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dda70-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="dda70-106">[out] Bir işaretçi bir `ULONG32` yerel değişkenler sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="dda70-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dda70-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dda70-107">Return Value</span></span>  
 <span data-ttu-id="dda70-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="dda70-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dda70-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dda70-109">Requirements</span></span>  
 <span data-ttu-id="dda70-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dda70-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda70-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dda70-111">See Also</span></span>  
 [<span data-ttu-id="dda70-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dda70-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
