---
title: ISymUnmanagedScope::GetNamespaces Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type:
- apiref
ms.openlocfilehash: 6f11a69671864ba4627c2bb8c86e0c9beb27eeb1
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83611126"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="ad491-102">ISymUnmanagedScope::GetNamespaces Metodu</span><span class="sxs-lookup"><span data-stu-id="ad491-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="ad491-103">Bu kapsam içinde kullanılmakta olan ad alanlarını alır.</span><span class="sxs-lookup"><span data-stu-id="ad491-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad491-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ad491-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad491-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ad491-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="ad491-106">'ndaki `namespaces`Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="ad491-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="ad491-107">dışı `ULONG32`Ad alanlarını içermesi için gereken arabellek boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ad491-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="ad491-108">dışı Ad alanlarını alan dizi.</span><span class="sxs-lookup"><span data-stu-id="ad491-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad491-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ad491-109">Return Value</span></span>  
 <span data-ttu-id="ad491-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ad491-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad491-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ad491-111">Requirements</span></span>  
 <span data-ttu-id="ad491-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ad491-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad491-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad491-113">See also</span></span>

- [<span data-ttu-id="ad491-114">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ad491-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
