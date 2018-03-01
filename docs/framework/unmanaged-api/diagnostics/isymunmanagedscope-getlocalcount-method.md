---
title: ISymUnmanagedScope::GetLocalCount Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9db774140ef55b2dfcb54ff701c2b842418a4923
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="d56e4-102">ISymUnmanagedScope::GetLocalCount Metodu</span><span class="sxs-lookup"><span data-stu-id="d56e4-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="d56e4-103">Bu kapsam içinde tanımlanan yerel değişkenler sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="d56e4-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d56e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d56e4-104">Syntax</span></span>  
  
```  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d56e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d56e4-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="d56e4-106">[out] Bir işaretçi bir `ULONG32` yerel değişkenler sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="d56e4-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d56e4-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d56e4-107">Return Value</span></span>  
 <span data-ttu-id="d56e4-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="d56e4-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d56e4-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d56e4-109">Requirements</span></span>  
 <span data-ttu-id="d56e4-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d56e4-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d56e4-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d56e4-111">See Also</span></span>  
 [<span data-ttu-id="d56e4-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d56e4-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
