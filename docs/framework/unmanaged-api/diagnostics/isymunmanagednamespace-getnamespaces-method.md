---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagednamespace:: GetNamespaces Yöntemi'
title: ISymUnmanagedNamespace::GetNamespaces Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type:
- apiref
ms.openlocfilehash: f17b16e2a3a7001d16c86dd6dc95241c1b0785e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709912"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="290d3-103">ISymUnmanagedNamespace::GetNamespaces Metodu</span><span class="sxs-lookup"><span data-stu-id="290d3-103">ISymUnmanagedNamespace::GetNamespaces Method</span></span>

<span data-ttu-id="290d3-104">Bu ad alanının alt öğelerini alır.</span><span class="sxs-lookup"><span data-stu-id="290d3-104">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="290d3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="290d3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="290d3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="290d3-106">Parameters</span></span>  

 `cNameSpaces`  
 <span data-ttu-id="290d3-107">'ndaki `ULONG32` Dizi boyutunu belirten bir `namespaces` .</span><span class="sxs-lookup"><span data-stu-id="290d3-107">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="290d3-108">dışı `ULONG32` Ad alanlarını içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="290d3-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="290d3-109">dışı Ad alanlarını içeren arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="290d3-109">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="290d3-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="290d3-110">Return Value</span></span>  

 <span data-ttu-id="290d3-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="290d3-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="290d3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="290d3-112">Requirements</span></span>  

 <span data-ttu-id="290d3-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="290d3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="290d3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="290d3-114">See also</span></span>

- [<span data-ttu-id="290d3-115">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="290d3-115">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
