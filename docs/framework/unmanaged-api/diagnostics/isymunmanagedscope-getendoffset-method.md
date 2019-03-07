---
title: ISymUnmanagedScope::GetEndOffset Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 47db4313354b00514084ec1110710cbd174a3788
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492627"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="0edb9-102">ISymUnmanagedScope::GetEndOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="0edb9-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="0edb9-103">Bu kapsam için bitiş uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="0edb9-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0edb9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0edb9-104">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0edb9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0edb9-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="0edb9-106">[out] Bir işaretçi bir `ULONG32` , bitiş uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="0edb9-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0edb9-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0edb9-107">Return Value</span></span>  
 <span data-ttu-id="0edb9-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="0edb9-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0edb9-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0edb9-109">Requirements</span></span>  
 <span data-ttu-id="0edb9-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0edb9-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0edb9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0edb9-111">See also</span></span>
- [<span data-ttu-id="0edb9-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0edb9-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="0edb9-113">GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0edb9-113">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)
