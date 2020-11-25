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
ms.openlocfilehash: 4436e4528c1dc486eb5c443c5a9467ac69a26c7d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706937"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="c1233-102">ISymUnmanagedConstant::GetSignature Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1233-102">ISymUnmanagedConstant::GetSignature Method</span></span>

<span data-ttu-id="c1233-103">Sabitin imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="c1233-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1233-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c1233-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1233-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1233-105">Parameters</span></span>  

 `cSig`  
 <span data-ttu-id="c1233-106">'ndaki `pcSig` Parametrenin işaret ettiği arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="c1233-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="c1233-107">dışı `ULONG32` İmzayı içermesi için gereken arabelleğin boyutunu, karakter cinsinden alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c1233-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="c1233-108">dışı İmzayı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="c1233-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1233-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c1233-109">Return Value</span></span>  

 <span data-ttu-id="c1233-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c1233-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1233-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1233-111">Requirements</span></span>  

 <span data-ttu-id="c1233-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c1233-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1233-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1233-113">See also</span></span>

- [<span data-ttu-id="c1233-114">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1233-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="c1233-115">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1233-115">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="c1233-116">GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="c1233-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
