---
title: ISymUnmanagedVariable::GetAddressKind Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressKind
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 18e83582a73ba3b2eb2538bcdf60984c46131768
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426961"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="48a58-102">ISymUnmanagedVariable::GetAddressKind Metodu</span><span class="sxs-lookup"><span data-stu-id="48a58-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="48a58-103">Bu değişkenin adres türünü alır.</span><span class="sxs-lookup"><span data-stu-id="48a58-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48a58-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48a58-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48a58-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48a58-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="48a58-106">[out] Bir işaretçi bir `ULONG32` değerini alır.</span><span class="sxs-lookup"><span data-stu-id="48a58-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="48a58-107">Olası değerler tanımlanan [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="48a58-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48a58-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="48a58-108">Return Value</span></span>  
 <span data-ttu-id="48a58-109">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="48a58-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48a58-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48a58-110">Requirements</span></span>  
 <span data-ttu-id="48a58-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="48a58-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a58-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48a58-112">See Also</span></span>  
 [<span data-ttu-id="48a58-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48a58-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
