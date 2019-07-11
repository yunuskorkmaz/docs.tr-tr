---
title: ISymUnmanagedScope::GetStartOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d34bcaf1ef00806e3883996804336bd22b9b634f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777850"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="66e49-102">ISymUnmanagedScope::GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66e49-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="66e49-103">Bu kapsam için başlangıç uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="66e49-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66e49-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66e49-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66e49-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66e49-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="66e49-106">[out] Bir işaretçi bir `ULONG32` içeren başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="66e49-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66e49-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="66e49-107">Return Value</span></span>  
 <span data-ttu-id="66e49-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="66e49-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66e49-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66e49-109">Requirements</span></span>  
 <span data-ttu-id="66e49-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="66e49-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e49-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66e49-111">See also</span></span>

- [<span data-ttu-id="66e49-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="66e49-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="66e49-113">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66e49-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
