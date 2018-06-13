---
title: ISymUnmanagedReader::GetDocuments Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocuments
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bcb0efab3b61f55bd5fdd3405799c7ac78ee521
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424657"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="08c95-102">ISymUnmanagedReader::GetDocuments Metodu</span><span class="sxs-lookup"><span data-stu-id="08c95-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="08c95-103">Sembol deposunda tanımlanan tüm belgeleri bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="08c95-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08c95-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08c95-104">Syntax</span></span>  
  
```  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08c95-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08c95-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="08c95-106">[in] Boyutunu `pDocs` dizi.</span><span class="sxs-lookup"><span data-stu-id="08c95-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="08c95-107">[out] Bir işaretçi bir değişkene dizi uzunluğu alır.</span><span class="sxs-lookup"><span data-stu-id="08c95-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="08c95-108">[out] Bir işaretçi bir değişkene belge dizisi alır.</span><span class="sxs-lookup"><span data-stu-id="08c95-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08c95-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="08c95-109">Return Value</span></span>  
 <span data-ttu-id="08c95-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="08c95-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08c95-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08c95-111">Requirements</span></span>  
 <span data-ttu-id="08c95-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="08c95-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c95-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08c95-113">See Also</span></span>  
 [<span data-ttu-id="08c95-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08c95-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
