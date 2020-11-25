---
title: ISymUnmanagedVariable::GetSignature Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type:
- apiref
ms.openlocfilehash: 791b92c30fc2bf3d506113620b59ba20015e077e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725826"
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="131d5-102">ISymUnmanagedVariable::GetSignature Metodu</span><span class="sxs-lookup"><span data-stu-id="131d5-102">ISymUnmanagedVariable::GetSignature Method</span></span>

<span data-ttu-id="131d5-103">Bu değişkenin imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="131d5-103">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="131d5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="131d5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="131d5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="131d5-105">Parameters</span></span>  

 `cSig`  
 <span data-ttu-id="131d5-106">'ndaki Parametre tarafından işaret edilen arabelleğin uzunluğu `sig` .</span><span class="sxs-lookup"><span data-stu-id="131d5-106">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="131d5-107">dışı `ULONG32` İmzayı içermesi için gereken arabelleğin boyutunu, karakter cinsinden alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="131d5-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="131d5-108">dışı İmzayı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="131d5-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="131d5-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="131d5-109">Return Value</span></span>  

 <span data-ttu-id="131d5-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="131d5-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="131d5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="131d5-111">Requirements</span></span>  

 <span data-ttu-id="131d5-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="131d5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="131d5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="131d5-113">See also</span></span>

- [<span data-ttu-id="131d5-114">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="131d5-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
