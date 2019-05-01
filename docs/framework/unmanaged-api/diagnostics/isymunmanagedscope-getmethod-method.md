---
title: ISymUnmanagedScope::GetMethod Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 954b1d91f33fe9a7e4df1ef51ee3666047836a17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986134"
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="5bd0f-102">ISymUnmanagedScope::GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5bd0f-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="5bd0f-103">Bu kapsam içeren yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="5bd0f-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bd0f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bd0f-104">Syntax</span></span>  
  
```  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bd0f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5bd0f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="5bd0f-106">[out] Döndürülen işaretçi [Isymunmanagedmethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="5bd0f-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bd0f-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5bd0f-107">Return Value</span></span>  
 <span data-ttu-id="5bd0f-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5bd0f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bd0f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5bd0f-109">Requirements</span></span>  
 <span data-ttu-id="5bd0f-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5bd0f-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bd0f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bd0f-111">See also</span></span>

- [<span data-ttu-id="5bd0f-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5bd0f-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
