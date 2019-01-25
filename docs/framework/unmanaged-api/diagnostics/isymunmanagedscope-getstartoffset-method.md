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
ms.openlocfilehash: 2b81ac93c67d59c294f22eb825527fa9982d9124
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721103"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="d9677-102">ISymUnmanagedScope::GetStartOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="d9677-102">ISymUnmanagedScope::GetStartOffset Method</span></span>
<span data-ttu-id="d9677-103">Bu kapsam için başlangıç uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="d9677-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9677-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9677-104">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9677-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9677-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="d9677-106">[out] Bir işaretçi bir `ULONG32` içeren başlangıç uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="d9677-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9677-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d9677-107">Return Value</span></span>  
 <span data-ttu-id="d9677-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="d9677-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9677-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9677-109">Requirements</span></span>  
 <span data-ttu-id="d9677-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d9677-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9677-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9677-111">See also</span></span>
- [<span data-ttu-id="d9677-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9677-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="d9677-113">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9677-113">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)
