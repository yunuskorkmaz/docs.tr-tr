---
title: ISymUnmanagedReader::GetDocuments Yöntemi
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
ms.openlocfilehash: efcf5b6673fbdc37fad99d082f91ab3077abbea9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130604"
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="80db8-102">ISymUnmanagedReader::GetDocuments Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80db8-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="80db8-103">Sembol deposu içerisinde tanımlanan tüm belgelerin dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="80db8-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80db8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80db8-104">Syntax</span></span>  
  
```  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80db8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80db8-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="80db8-106">[in] Boyutu `pDocs` dizisi.</span><span class="sxs-lookup"><span data-stu-id="80db8-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="80db8-107">[out] Dizi uzunluğu alır bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="80db8-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="80db8-108">[out] Belge dizi alan bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="80db8-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80db8-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="80db8-109">Return Value</span></span>  
 <span data-ttu-id="80db8-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="80db8-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80db8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80db8-111">Requirements</span></span>  
 <span data-ttu-id="80db8-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="80db8-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80db8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80db8-113">See also</span></span>

- [<span data-ttu-id="80db8-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80db8-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
