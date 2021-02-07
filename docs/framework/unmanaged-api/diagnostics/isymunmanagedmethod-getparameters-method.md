---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedmethod:: GetParameters Yöntemi'
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
ms.openlocfilehash: c8860a4d42019aaacef01879b175fd45ea837f2b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721378"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="e6673-103">ISymUnmanagedMethod::GetParameters Metodu</span><span class="sxs-lookup"><span data-stu-id="e6673-103">ISymUnmanagedMethod::GetParameters Method</span></span>

<span data-ttu-id="e6673-104">Bu yöntemin parametrelerini alır.</span><span class="sxs-lookup"><span data-stu-id="e6673-104">Gets the parameters for this method.</span></span> <span data-ttu-id="e6673-105">Parametreler, yöntemin imzasında tanımlandıkları sırada döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e6673-105">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6673-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e6673-106">Syntax</span></span>  
  
```cpp  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6673-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e6673-107">Parameters</span></span>  

 `cParams`  
 <span data-ttu-id="e6673-108">'ndaki `params` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="e6673-108">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="e6673-109">'ndaki `ULONG32` Parametreleri içermesi için gereken arabelleğin boyutunu alan öğesine bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e6673-109">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="e6673-110">dışı Parametreleri alan arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e6673-110">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6673-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e6673-111">Return Value</span></span>  

 <span data-ttu-id="e6673-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e6673-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6673-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e6673-113">Requirements</span></span>  

 <span data-ttu-id="e6673-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e6673-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6673-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6673-115">See also</span></span>

- [<span data-ttu-id="e6673-116">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e6673-116">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
