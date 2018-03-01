---
title: ISymUnmanagedVariable::GetStartOffset Metodu
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
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b3fa0c710eb5de8b9a92970002336de22adb2458
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="8ef5a-102">ISymUnmanagedVariable::GetStartOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="8ef5a-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="8ef5a-103">Bu değişken, üst içinde başlangıç uzaklığını alır.</span><span class="sxs-lookup"><span data-stu-id="8ef5a-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="8ef5a-104">Bu kapsam içinde yerel bir değişken ise, başlangıç uzaklığı kapsam için tanımlanan uzaklıkları içinde döner.</span><span class="sxs-lookup"><span data-stu-id="8ef5a-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef5a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ef5a-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ef5a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ef5a-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="8ef5a-107">[out] Bir işaretçi bir `ULONG32` başlangıç uzaklığı alır.</span><span class="sxs-lookup"><span data-stu-id="8ef5a-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ef5a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8ef5a-108">Return Value</span></span>  
 <span data-ttu-id="8ef5a-109">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="8ef5a-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef5a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ef5a-110">Requirements</span></span>  
 <span data-ttu-id="8ef5a-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8ef5a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef5a-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ef5a-112">See Also</span></span>  
 [<span data-ttu-id="8ef5a-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ef5a-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="8ef5a-114">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ef5a-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)
