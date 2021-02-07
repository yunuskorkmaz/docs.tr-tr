---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanagedconstant:: GetSignature Yöntemi'
title: ISymUnmanagedConstant::GetSignature Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
ms.openlocfilehash: d28051c9d0e2675e980926fe63ffa7c4d13ef13a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689800"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="bfc88-103">ISymUnmanagedConstant::GetSignature Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfc88-103">ISymUnmanagedConstant::GetSignature Method</span></span>

<span data-ttu-id="bfc88-104">Sabitin imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="bfc88-104">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfc88-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bfc88-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfc88-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bfc88-106">Parameters</span></span>  

 `cSig`  
 <span data-ttu-id="bfc88-107">'ndaki `pcSig` Parametrenin işaret ettiği arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="bfc88-107">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="bfc88-108">dışı `ULONG32` İmzayı içermesi için gereken arabelleğin boyutunu, karakter cinsinden alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="bfc88-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="bfc88-109">dışı İmzayı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="bfc88-109">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bfc88-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bfc88-110">Return Value</span></span>  

 <span data-ttu-id="bfc88-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="bfc88-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfc88-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bfc88-112">Requirements</span></span>  

 <span data-ttu-id="bfc88-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bfc88-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfc88-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bfc88-114">See also</span></span>

- [<span data-ttu-id="bfc88-115">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bfc88-115">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="bfc88-116">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfc88-116">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="bfc88-117">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bfc88-117">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
