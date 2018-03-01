---
title: ISymUnmanagedConstant::GetValue Metodu
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
- ISymUnmanagedConstant.GetValue
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 15ae3e9f2e680c7e85d3b8daa0d6010773797258
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="6ef22-102">ISymUnmanagedConstant::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="6ef22-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="6ef22-103">Sabit değerini alır.</span><span class="sxs-lookup"><span data-stu-id="6ef22-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ef22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ef22-104">Syntax</span></span>  
  
```  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ef22-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ef22-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="6ef22-106">[out] Bir işaretçi bir değişkene değer alır.</span><span class="sxs-lookup"><span data-stu-id="6ef22-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ef22-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6ef22-107">Return Value</span></span>  
 <span data-ttu-id="6ef22-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6ef22-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ef22-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ef22-109">Requirements</span></span>  
 <span data-ttu-id="6ef22-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6ef22-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ef22-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6ef22-111">See Also</span></span>  
 [<span data-ttu-id="6ef22-112">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ef22-112">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="6ef22-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ef22-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)  
 [<span data-ttu-id="6ef22-114">GetSignature Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ef22-114">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
