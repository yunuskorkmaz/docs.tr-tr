---
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
ms.openlocfilehash: 48c50ac6be6d525676d85578e5a55a27104c180a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615104"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="196fd-102">ISymUnmanagedNamespace::GetNamespaces Metodu</span><span class="sxs-lookup"><span data-stu-id="196fd-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="196fd-103">Bu ad alanının alt öğelerini alır.</span><span class="sxs-lookup"><span data-stu-id="196fd-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="196fd-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="196fd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="196fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="196fd-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="196fd-106">'ndaki `ULONG32`Dizi boyutunu belirten bir `namespaces` .</span><span class="sxs-lookup"><span data-stu-id="196fd-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="196fd-107">dışı `ULONG32`Ad alanlarını içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="196fd-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="196fd-108">dışı Ad alanlarını içeren arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="196fd-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="196fd-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="196fd-109">Return Value</span></span>  
 <span data-ttu-id="196fd-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="196fd-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="196fd-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="196fd-111">Requirements</span></span>  
 <span data-ttu-id="196fd-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="196fd-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="196fd-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="196fd-113">See also</span></span>

- [<span data-ttu-id="196fd-114">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="196fd-114">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)
