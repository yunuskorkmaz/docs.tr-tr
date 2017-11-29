---
title: ISymUnmanagedVariable::GetAddressField2 Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressField2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressField2
helpviewer_keywords:
- GetAddressField2 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField2 method [.NET Framework debugging]
ms.assetid: 1f25b294-72b6-4882-a49b-6c9d364b6008
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d3e9124cb800416c44596d7b6f21a21c416e0e94
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="a40d4-102">ISymUnmanagedVariable::GetAddressField2 Metodu</span><span class="sxs-lookup"><span data-stu-id="a40d4-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="a40d4-103">İkinci adres alanı için bu değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="a40d4-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="a40d4-104">Bunun anlamı adres türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a40d4-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a40d4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a40d4-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a40d4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a40d4-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a40d4-107">[out] Bir işaretçi bir `ULONG32` ikinci adres alanı alır.</span><span class="sxs-lookup"><span data-stu-id="a40d4-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a40d4-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a40d4-108">Return Value</span></span>  
 <span data-ttu-id="a40d4-109">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a40d4-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a40d4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a40d4-110">Requirements</span></span>  
 <span data-ttu-id="a40d4-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a40d4-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a40d4-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a40d4-112">See Also</span></span>  
 [<span data-ttu-id="a40d4-113">Isymunmanagedvariable arabirimi</span><span class="sxs-lookup"><span data-stu-id="a40d4-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="a40d4-114">GetAddressField1 yöntemi</span><span class="sxs-lookup"><span data-stu-id="a40d4-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)  
 [<span data-ttu-id="a40d4-115">GetAddressField3 yöntemi</span><span class="sxs-lookup"><span data-stu-id="a40d4-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)  
 [<span data-ttu-id="a40d4-116">GetAddressKind yöntemi</span><span class="sxs-lookup"><span data-stu-id="a40d4-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
