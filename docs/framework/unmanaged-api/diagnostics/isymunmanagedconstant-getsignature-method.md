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
ms.openlocfilehash: 332d60418c744a9391c7c0afc20248c2239b090c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441626"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="572f9-102">ISymUnmanagedConstant::GetSignature Yöntemi</span><span class="sxs-lookup"><span data-stu-id="572f9-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="572f9-103">Sabitin imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="572f9-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="572f9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="572f9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="572f9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="572f9-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="572f9-106">'ndaki `pcSig`Parametrenin işaret ettiği arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="572f9-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="572f9-107">dışı `ULONG32`İmzayı içermesi için gereken arabelleğin boyutunu, karakter cinsinden alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="572f9-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="572f9-108">dışı İmzayı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="572f9-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="572f9-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="572f9-109">Return Value</span></span>  
 <span data-ttu-id="572f9-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="572f9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="572f9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="572f9-111">Requirements</span></span>  
 <span data-ttu-id="572f9-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="572f9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="572f9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="572f9-113">See also</span></span>

- [<span data-ttu-id="572f9-114">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="572f9-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="572f9-115">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="572f9-115">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="572f9-116">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="572f9-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
