---
title: ISymUnmanagedReader::GetDocument Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a173c23ea33532f05e30d072677715e15d04018
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093691"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="343ff-102">ISymUnmanagedReader::GetDocument Metodu</span><span class="sxs-lookup"><span data-stu-id="343ff-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="343ff-103">Bir belgeyi bulur.</span><span class="sxs-lookup"><span data-stu-id="343ff-103">Finds a document.</span></span> <span data-ttu-id="343ff-104">Belge dili, satıcı ve tür isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="343ff-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="343ff-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="343ff-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="343ff-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="343ff-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="343ff-107">[in] Belge tanımlayan URL.</span><span class="sxs-lookup"><span data-stu-id="343ff-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="343ff-108">[in] Belge dili.</span><span class="sxs-lookup"><span data-stu-id="343ff-108">[in] The document language.</span></span> <span data-ttu-id="343ff-109">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="343ff-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="343ff-110">[in] Belge dili için satıcı kimliği.</span><span class="sxs-lookup"><span data-stu-id="343ff-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="343ff-111">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="343ff-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="343ff-112">[in] Belge türü.</span><span class="sxs-lookup"><span data-stu-id="343ff-112">[in] The type of the document.</span></span> <span data-ttu-id="343ff-113">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="343ff-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="343ff-114">[out] Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="343ff-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="343ff-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="343ff-115">Return Value</span></span>  
 <span data-ttu-id="343ff-116">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="343ff-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="343ff-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="343ff-117">Requirements</span></span>  
 <span data-ttu-id="343ff-118">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="343ff-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="343ff-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="343ff-119">See also</span></span>

- [<span data-ttu-id="343ff-120">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="343ff-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
