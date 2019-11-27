---
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
ms.openlocfilehash: 401dfbea0da309db24f3052f462daa66e8bbef4a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449272"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="0b856-102">ISymUnmanagedConstant::GetSignature Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b856-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="0b856-103">Sabitin imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="0b856-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b856-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b856-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b856-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b856-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="0b856-106">'ndaki `pcSig` parametresinin işaret ettiği arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="0b856-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="0b856-107">dışı İmzayı içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir `ULONG32` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0b856-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="0b856-108">dışı İmzayı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="0b856-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b856-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0b856-109">Return Value</span></span>  
 <span data-ttu-id="0b856-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="0b856-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b856-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b856-111">Requirements</span></span>  
 <span data-ttu-id="0b856-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0b856-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b856-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b856-113">See also</span></span>

- [<span data-ttu-id="0b856-114">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b856-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="0b856-115">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b856-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="0b856-116">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b856-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
