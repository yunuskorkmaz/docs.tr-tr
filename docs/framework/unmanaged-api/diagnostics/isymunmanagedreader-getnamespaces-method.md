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
ms.openlocfilehash: 5227de340bec85620f8c8d45538ad9a9d7f688fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630963"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="369d4-102">ISymUnmanagedReader::GetNamespaces Metodu</span><span class="sxs-lookup"><span data-stu-id="369d4-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="369d4-103">Bu sembol deposundaki genel kapsamda tanımlanan ad alanları alır.</span><span class="sxs-lookup"><span data-stu-id="369d4-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="369d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="369d4-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="369d4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="369d4-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="369d4-106">[in] Ad alanları dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="369d4-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="369d4-107">[out] Ad alanı listenin uzunluğunu alır bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="369d4-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="369d4-108">[out] Ad alanı listesini alır bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="369d4-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="369d4-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="369d4-109">Return Value</span></span>  
 <span data-ttu-id="369d4-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="369d4-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="369d4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="369d4-111">Requirements</span></span>  
 <span data-ttu-id="369d4-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="369d4-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="369d4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="369d4-113">See also</span></span>
- [<span data-ttu-id="369d4-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="369d4-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
