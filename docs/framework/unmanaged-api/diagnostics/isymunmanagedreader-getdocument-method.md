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
ms.openlocfilehash: f20f7aabc05bb9e15b040d968c08d10444efd8fc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485818"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="e4b17-102">ISymUnmanagedReader::GetDocument Metodu</span><span class="sxs-lookup"><span data-stu-id="e4b17-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="e4b17-103">Bir belgeyi bulur.</span><span class="sxs-lookup"><span data-stu-id="e4b17-103">Finds a document.</span></span> <span data-ttu-id="e4b17-104">Belge dili, satıcı ve tür isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e4b17-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4b17-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e4b17-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4b17-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e4b17-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="e4b17-107">[in] Belge tanımlayan URL.</span><span class="sxs-lookup"><span data-stu-id="e4b17-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="e4b17-108">[in] Belge dili.</span><span class="sxs-lookup"><span data-stu-id="e4b17-108">[in] The document language.</span></span> <span data-ttu-id="e4b17-109">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e4b17-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="e4b17-110">[in] Belge dili için satıcı kimliği.</span><span class="sxs-lookup"><span data-stu-id="e4b17-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="e4b17-111">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e4b17-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="e4b17-112">[in] Belge türü.</span><span class="sxs-lookup"><span data-stu-id="e4b17-112">[in] The type of the document.</span></span> <span data-ttu-id="e4b17-113">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e4b17-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e4b17-114">[out] Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e4b17-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e4b17-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e4b17-115">Return Value</span></span>  
 <span data-ttu-id="e4b17-116">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e4b17-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4b17-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e4b17-117">Requirements</span></span>  
 <span data-ttu-id="e4b17-118">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e4b17-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4b17-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4b17-119">See also</span></span>
- [<span data-ttu-id="e4b17-120">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e4b17-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
