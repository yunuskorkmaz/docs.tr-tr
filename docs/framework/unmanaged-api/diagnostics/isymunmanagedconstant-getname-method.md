---
title: ISymUnmanagedConstant::GetName Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
ms.openlocfilehash: fca7b11a83b5a695feae82fe5f25218f87afbce2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732898"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="9dcbf-102">ISymUnmanagedConstant::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9dcbf-102">ISymUnmanagedConstant::GetName Method</span></span>

<span data-ttu-id="9dcbf-103">Sabitin adını alır.</span><span class="sxs-lookup"><span data-stu-id="9dcbf-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dcbf-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9dcbf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9dcbf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9dcbf-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="9dcbf-106">'ndaki `szName` Parametrenin işaret ettiği arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="9dcbf-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9dcbf-107">dışı `ULONG32` Null sonlandırma dahil olmak üzere, adı içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9dcbf-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="9dcbf-108">dışı Adı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="9dcbf-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9dcbf-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9dcbf-109">Return Value</span></span>  

 <span data-ttu-id="9dcbf-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="9dcbf-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dcbf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9dcbf-111">Requirements</span></span>  

 <span data-ttu-id="9dcbf-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="9dcbf-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dcbf-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dcbf-113">See also</span></span>

- [<span data-ttu-id="9dcbf-114">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9dcbf-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="9dcbf-115">GetSignature Metodu</span><span class="sxs-lookup"><span data-stu-id="9dcbf-115">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="9dcbf-116">GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="9dcbf-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
