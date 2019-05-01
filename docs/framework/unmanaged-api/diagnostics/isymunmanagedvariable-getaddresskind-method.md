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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eae5b21af3bcdca911ec13067a61bb957d4ae6ab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797585"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="bebb9-102">ISymUnmanagedVariable::GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bebb9-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="bebb9-103">Bu değişkenin adresi türünü alır.</span><span class="sxs-lookup"><span data-stu-id="bebb9-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bebb9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bebb9-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bebb9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bebb9-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="bebb9-106">[out] Bir işaretçi bir `ULONG32` , değerini alır.</span><span class="sxs-lookup"><span data-stu-id="bebb9-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="bebb9-107">Olası değerler tanımlanan [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="bebb9-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bebb9-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bebb9-108">Return Value</span></span>  
 <span data-ttu-id="bebb9-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="bebb9-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bebb9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bebb9-110">Requirements</span></span>  
 <span data-ttu-id="bebb9-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bebb9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bebb9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bebb9-112">See also</span></span>

- [<span data-ttu-id="bebb9-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bebb9-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
