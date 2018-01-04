---
title: ISymUnmanagedVariable::GetAddressKind Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetAddressKind
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c4651641e3c430379b11698acf29eae450b02b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="a22c7-102">ISymUnmanagedVariable::GetAddressKind Metodu</span><span class="sxs-lookup"><span data-stu-id="a22c7-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="a22c7-103">Bu değişkenin adres türünü alır.</span><span class="sxs-lookup"><span data-stu-id="a22c7-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a22c7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a22c7-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a22c7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a22c7-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a22c7-106">[out] Bir işaretçi bir `ULONG32` değerini alır.</span><span class="sxs-lookup"><span data-stu-id="a22c7-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="a22c7-107">Olası değerler tanımlanan [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="a22c7-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a22c7-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a22c7-108">Return Value</span></span>  
 <span data-ttu-id="a22c7-109">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a22c7-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a22c7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a22c7-110">Requirements</span></span>  
 <span data-ttu-id="a22c7-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a22c7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a22c7-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a22c7-112">See Also</span></span>  
 [<span data-ttu-id="a22c7-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a22c7-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
