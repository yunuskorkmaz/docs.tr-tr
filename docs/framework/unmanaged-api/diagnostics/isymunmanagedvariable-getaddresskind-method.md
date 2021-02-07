---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedvariable:: GetAddressKind yöntemi'
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
ms.openlocfilehash: 4b090560335432ad39157fee987ce15728fece63
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762857"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="27e2b-103">ISymUnmanagedVariable::GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="27e2b-103">ISymUnmanagedVariable::GetAddressKind Method</span></span>

<span data-ttu-id="27e2b-104">Bu değişkenin adres türünü alır.</span><span class="sxs-lookup"><span data-stu-id="27e2b-104">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27e2b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27e2b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27e2b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27e2b-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="27e2b-107">dışı Değerini alan bir işaretçisi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="27e2b-107">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="27e2b-108">Olası değerler [CorSymAddrKind](corsymaddrkind-enumeration.md) numaralandırması içinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="27e2b-108">The possible values are defined in the [CorSymAddrKind](corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27e2b-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="27e2b-109">Return Value</span></span>  

 <span data-ttu-id="27e2b-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="27e2b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27e2b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27e2b-111">Requirements</span></span>  

 <span data-ttu-id="27e2b-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="27e2b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27e2b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27e2b-113">See also</span></span>

- [<span data-ttu-id="27e2b-114">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27e2b-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
