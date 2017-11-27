---
title: ISymUnmanagedConstant::GetValue Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedConstant.GetValue
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: df55345b34340349c4c20213f75591e9586153cc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="23de6-102">ISymUnmanagedConstant::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="23de6-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="23de6-103">Sabit değerini alır.</span><span class="sxs-lookup"><span data-stu-id="23de6-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23de6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23de6-104">Syntax</span></span>  
  
```  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="23de6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="23de6-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="23de6-106">[out] Bir işaretçi bir değişkene değer alır.</span><span class="sxs-lookup"><span data-stu-id="23de6-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23de6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="23de6-107">Return Value</span></span>  
 <span data-ttu-id="23de6-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="23de6-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23de6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23de6-109">Requirements</span></span>  
 <span data-ttu-id="23de6-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="23de6-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23de6-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23de6-111">See Also</span></span>  
 [<span data-ttu-id="23de6-112">Isymunmanagedconstant arabirimi</span><span class="sxs-lookup"><span data-stu-id="23de6-112">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="23de6-113">GetName yöntemi</span><span class="sxs-lookup"><span data-stu-id="23de6-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)  
 [<span data-ttu-id="23de6-114">GetSignature yöntemi</span><span class="sxs-lookup"><span data-stu-id="23de6-114">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
