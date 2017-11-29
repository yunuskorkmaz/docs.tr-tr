---
title: ISymUnmanagedReader::GetDocuments Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetDocuments
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetDocuments
helpviewer_keywords:
- GetDocuments method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocuments method [.NET Framework debugging]
ms.assetid: e3b73a3f-d089-4101-a9a9-5e0765d05b61
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 27268b7f32f2c9aa667790c6d4516f1b8e015f96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetdocuments-method"></a><span data-ttu-id="2cbca-102">ISymUnmanagedReader::GetDocuments Metodu</span><span class="sxs-lookup"><span data-stu-id="2cbca-102">ISymUnmanagedReader::GetDocuments Method</span></span>
<span data-ttu-id="2cbca-103">Sembol deposunda tanımlanan tüm belgeleri bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="2cbca-103">Returns an array of all the documents defined in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cbca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2cbca-104">Syntax</span></span>  
  
```  
HRESULT GetDocuments (  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,  
    [out, size_is (cDocs),  
        length_is (*pcDocs)] ISymUnmanagedDocument *pDocs[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2cbca-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2cbca-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="2cbca-106">[in] Boyutunu `pDocs` dizi.</span><span class="sxs-lookup"><span data-stu-id="2cbca-106">[in] The size of the `pDocs` array.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="2cbca-107">[out] Bir işaretçi bir değişkene dizi uzunluğu alır.</span><span class="sxs-lookup"><span data-stu-id="2cbca-107">[out] A pointer to a variable that receives the array length.</span></span>  
  
 `pDocs`  
 <span data-ttu-id="2cbca-108">[out] Bir işaretçi bir değişkene belge dizisi alır.</span><span class="sxs-lookup"><span data-stu-id="2cbca-108">[out] A pointer to a variable that receives the document array.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cbca-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2cbca-109">Return Value</span></span>  
 <span data-ttu-id="2cbca-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2cbca-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cbca-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2cbca-111">Requirements</span></span>  
 <span data-ttu-id="2cbca-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2cbca-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cbca-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2cbca-113">See Also</span></span>  
 [<span data-ttu-id="2cbca-114">Isymunmanagedreader arabirimi</span><span class="sxs-lookup"><span data-stu-id="2cbca-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
