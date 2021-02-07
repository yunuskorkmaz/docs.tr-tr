---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedvariable:: GetSignature Yöntemi'
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
ms.openlocfilehash: 6e8242581cf2d59563b6193ed7c7686292cbf775
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762740"
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="55f0b-103">ISymUnmanagedVariable::GetSignature Metodu</span><span class="sxs-lookup"><span data-stu-id="55f0b-103">ISymUnmanagedVariable::GetSignature Method</span></span>

<span data-ttu-id="55f0b-104">Bu değişkenin imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="55f0b-104">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f0b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55f0b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55f0b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="55f0b-106">Parameters</span></span>  

 `cSig`  
 <span data-ttu-id="55f0b-107">'ndaki Parametre tarafından işaret edilen arabelleğin uzunluğu `sig` .</span><span class="sxs-lookup"><span data-stu-id="55f0b-107">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="55f0b-108">dışı `ULONG32` İmzayı içermesi için gereken arabelleğin boyutunu, karakter cinsinden alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="55f0b-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="55f0b-109">dışı İmzayı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="55f0b-109">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="55f0b-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="55f0b-110">Return Value</span></span>  

 <span data-ttu-id="55f0b-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="55f0b-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55f0b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55f0b-112">Requirements</span></span>  

 <span data-ttu-id="55f0b-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="55f0b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f0b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55f0b-114">See also</span></span>

- [<span data-ttu-id="55f0b-115">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55f0b-115">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
