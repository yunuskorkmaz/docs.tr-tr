---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedscope:: GetNamespaces Yöntemi'
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
ms.openlocfilehash: 39b6507845e911cafc9b9ab38f7b67cdf1fdf2c5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763351"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="544b0-103">ISymUnmanagedScope::GetNamespaces Metodu</span><span class="sxs-lookup"><span data-stu-id="544b0-103">ISymUnmanagedScope::GetNamespaces Method</span></span>

<span data-ttu-id="544b0-104">Bu kapsam içinde kullanılmakta olan ad alanlarını alır.</span><span class="sxs-lookup"><span data-stu-id="544b0-104">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="544b0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="544b0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="544b0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="544b0-106">Parameters</span></span>  

 `cNameSpaces`  
 <span data-ttu-id="544b0-107">'ndaki `namespaces` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="544b0-107">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="544b0-108">dışı `ULONG32` Ad alanlarını içermesi için gereken arabellek boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="544b0-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="544b0-109">dışı Ad alanlarını alan dizi.</span><span class="sxs-lookup"><span data-stu-id="544b0-109">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="544b0-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="544b0-110">Return Value</span></span>  

 <span data-ttu-id="544b0-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="544b0-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="544b0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="544b0-112">Requirements</span></span>  

 <span data-ttu-id="544b0-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="544b0-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="544b0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="544b0-114">See also</span></span>

- [<span data-ttu-id="544b0-115">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="544b0-115">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
