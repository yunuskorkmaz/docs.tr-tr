---
title: ISymUnmanagedVariable::GetEndOffset Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetEndOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b7a2dac8425cd852c6c17ee1674710f6798d3b1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="6cdee-102">ISymUnmanagedVariable::GetEndOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="6cdee-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="6cdee-103">Bu değişken, üst içinde son uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="6cdee-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="6cdee-104">Bu kapsam içinde yerel bir değişken ise bitiş uzaklığı kapsam için tanımlanan uzaklıkları içinde döner.</span><span class="sxs-lookup"><span data-stu-id="6cdee-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cdee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6cdee-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6cdee-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6cdee-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="6cdee-107">[out] Bir işaretçi bir `ULONG32` bitiş uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="6cdee-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cdee-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6cdee-108">Return Value</span></span>  
 <span data-ttu-id="6cdee-109">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6cdee-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cdee-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6cdee-110">Requirements</span></span>  
 <span data-ttu-id="6cdee-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6cdee-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cdee-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6cdee-112">See Also</span></span>  
 [<span data-ttu-id="6cdee-113">Isymunmanagedvariable arabirimi</span><span class="sxs-lookup"><span data-stu-id="6cdee-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="6cdee-114">GetStartOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="6cdee-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)
