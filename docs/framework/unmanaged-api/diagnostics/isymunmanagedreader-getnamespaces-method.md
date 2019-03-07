---
title: ISymUnmanagedReader::GetNamespaces Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2048062267131f6b6cc6672d74c7f9d76b4b59f9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484751"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="c65c0-102">ISymUnmanagedReader::GetNamespaces Metodu</span><span class="sxs-lookup"><span data-stu-id="c65c0-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="c65c0-103">Bu sembol deposundaki genel kapsamda tanımlanan ad alanları alır.</span><span class="sxs-lookup"><span data-stu-id="c65c0-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c65c0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c65c0-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c65c0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c65c0-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="c65c0-106">[in] Ad alanları dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="c65c0-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="c65c0-107">[out] Ad alanı listenin uzunluğunu alır bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c65c0-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="c65c0-108">[out] Ad alanı listesini alır bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c65c0-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c65c0-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c65c0-109">Return Value</span></span>  
 <span data-ttu-id="c65c0-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c65c0-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c65c0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c65c0-111">Requirements</span></span>  
 <span data-ttu-id="c65c0-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c65c0-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c65c0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c65c0-113">See also</span></span>
- [<span data-ttu-id="c65c0-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c65c0-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
