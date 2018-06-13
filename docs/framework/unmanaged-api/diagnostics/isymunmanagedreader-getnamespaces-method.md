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
ms.openlocfilehash: f50a5cb1f16be44b03cd94b69fdf32efa9e9007b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425148"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="e4cde-102">ISymUnmanagedReader::GetNamespaces Metodu</span><span class="sxs-lookup"><span data-stu-id="e4cde-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="e4cde-103">Bu simge deposundaki genel kapsamda tanımlanan ad alanları alır.</span><span class="sxs-lookup"><span data-stu-id="e4cde-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4cde-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4cde-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e4cde-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4cde-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="e4cde-106">[in] Ad alanları dizi büyüklüğü.</span><span class="sxs-lookup"><span data-stu-id="e4cde-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="e4cde-107">[out] Bir işaretçi bir değişkene ad listesi uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="e4cde-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="e4cde-108">[out] Bir işaretçi bir değişkene ad listesini alır.</span><span class="sxs-lookup"><span data-stu-id="e4cde-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4cde-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e4cde-109">Return Value</span></span>  
 <span data-ttu-id="e4cde-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e4cde-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4cde-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4cde-111">Requirements</span></span>  
 <span data-ttu-id="e4cde-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e4cde-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4cde-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e4cde-113">See Also</span></span>  
 [<span data-ttu-id="e4cde-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4cde-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
