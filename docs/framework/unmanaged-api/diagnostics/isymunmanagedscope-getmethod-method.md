---
title: ISymUnmanagedScope::GetMethod Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetMethod method [.NET Framework debugging]
ms.assetid: a61866ee-221a-45b9-a1b7-395825b77872
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bb062ad7ab485a1631a9cbe15f904b21226cb502
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedscopegetmethod-method"></a><span data-ttu-id="120b8-102">ISymUnmanagedScope::GetMethod Metodu</span><span class="sxs-lookup"><span data-stu-id="120b8-102">ISymUnmanagedScope::GetMethod Method</span></span>
<span data-ttu-id="120b8-103">Bu kapsam içeren yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="120b8-103">Gets the method that contains this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="120b8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="120b8-104">Syntax</span></span>  
  
```  
HRESULT GetMethod(  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="120b8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="120b8-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="120b8-106">[out] Bir işaretçi döndürülen [Isymunmanagedmethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="120b8-106">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="120b8-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="120b8-107">Return Value</span></span>  
 <span data-ttu-id="120b8-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="120b8-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="120b8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="120b8-109">Requirements</span></span>  
 <span data-ttu-id="120b8-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="120b8-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="120b8-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="120b8-111">See Also</span></span>  
 [<span data-ttu-id="120b8-112">Isymunmanagedscope arabirimi</span><span class="sxs-lookup"><span data-stu-id="120b8-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
