---
title: ISymUnmanagedScope::GetStartOffset Metodu
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
ms.openlocfilehash: 19d116825efc4eb2ec1de22f232f46f8fb0fdf18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425917"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="59e61-102">ISymUnmanagedScope::GetStartOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="59e61-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="59e61-103">Bu kapsam için başlangıç uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="59e61-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59e61-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59e61-104">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59e61-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="59e61-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="59e61-106">[out] Bir işaretçi bir `ULONG32` başlangıç uzaklığı içerir.</span><span class="sxs-lookup"><span data-stu-id="59e61-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59e61-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="59e61-107">Return Value</span></span>  
 <span data-ttu-id="59e61-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="59e61-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59e61-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59e61-109">Requirements</span></span>  
 <span data-ttu-id="59e61-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="59e61-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59e61-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59e61-111">See Also</span></span>  
 [<span data-ttu-id="59e61-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="59e61-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="59e61-113">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="59e61-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
