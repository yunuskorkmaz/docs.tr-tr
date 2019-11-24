---
title: ISymUnmanagedVariable::GetAddressKind Yöntemi
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
ms.openlocfilehash: 4d2de38e5e506873a6db262dcec19c7af9d8a0d0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446099"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="10060-102">ISymUnmanagedVariable::GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="10060-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="10060-103">Gets the kind of address of this variable.</span><span class="sxs-lookup"><span data-stu-id="10060-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10060-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="10060-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10060-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="10060-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="10060-106">[out] A pointer to a `ULONG32` that receives the value.</span><span class="sxs-lookup"><span data-stu-id="10060-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="10060-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span><span class="sxs-lookup"><span data-stu-id="10060-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10060-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="10060-108">Return Value</span></span>  
 <span data-ttu-id="10060-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="10060-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10060-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="10060-110">Requirements</span></span>  
 <span data-ttu-id="10060-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="10060-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10060-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10060-112">See also</span></span>

- [<span data-ttu-id="10060-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="10060-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
