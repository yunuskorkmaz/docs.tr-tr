---
title: ISymUnmanagedMethod::GetParameters Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetParameters
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetParameters
helpviewer_keywords:
- ISymUnmanagedMethod::GetParameters method [.NET Framework debugging]
- GetParameters method [.NET Framework debugging]
ms.assetid: 3a8074f1-facc-4a3f-bb9b-d6574fc2fc74
topic_type:
- apiref
ms.openlocfilehash: 9e8139a822c877e70731e18ae5a75b83e6b7578e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448960"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="be20d-102">ISymUnmanagedMethod::GetParameters Metodu</span><span class="sxs-lookup"><span data-stu-id="be20d-102">ISymUnmanagedMethod::GetParameters Method</span></span>
<span data-ttu-id="be20d-103">Bu yöntemin parametrelerini alır.</span><span class="sxs-lookup"><span data-stu-id="be20d-103">Gets the parameters for this method.</span></span> <span data-ttu-id="be20d-104">Parametreler, yöntemin imzasında tanımlandıkları sırada döndürülür.</span><span class="sxs-lookup"><span data-stu-id="be20d-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be20d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be20d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be20d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="be20d-106">Parameters</span></span>  
 `cParams`  
 <span data-ttu-id="be20d-107">'ndaki `params` dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="be20d-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="be20d-108">'ndaki Parametreleri içermesi için gereken arabelleğin boyutunu alan bir `ULONG32` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="be20d-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="be20d-109">dışı Parametreleri alan arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="be20d-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be20d-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="be20d-110">Return Value</span></span>  
 <span data-ttu-id="be20d-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="be20d-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be20d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be20d-112">Requirements</span></span>  
 <span data-ttu-id="be20d-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="be20d-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be20d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be20d-114">See also</span></span>

- [<span data-ttu-id="be20d-115">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be20d-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
