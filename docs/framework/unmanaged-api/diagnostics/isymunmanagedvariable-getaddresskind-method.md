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
ms.openlocfilehash: 6a7824949edc905a3edcd58f60d40f8b1a40c53c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726918"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="2d562-102">ISymUnmanagedVariable::GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d562-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>

<span data-ttu-id="2d562-103">Bu değişkenin adres türünü alır.</span><span class="sxs-lookup"><span data-stu-id="2d562-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d562-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2d562-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d562-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d562-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="2d562-106">dışı Değerini alan bir işaretçisi `ULONG32` .</span><span class="sxs-lookup"><span data-stu-id="2d562-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="2d562-107">Olası değerler [CorSymAddrKind](corsymaddrkind-enumeration.md) numaralandırması içinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2d562-107">The possible values are defined in the [CorSymAddrKind](corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d562-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2d562-108">Return Value</span></span>  

 <span data-ttu-id="2d562-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2d562-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d562-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d562-110">Requirements</span></span>  

 <span data-ttu-id="2d562-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2d562-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d562-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d562-112">See also</span></span>

- [<span data-ttu-id="2d562-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d562-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
