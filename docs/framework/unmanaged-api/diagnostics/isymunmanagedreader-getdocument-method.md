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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939483"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="2e04d-102">ISymUnmanagedReader::GetDocument Metodu</span><span class="sxs-lookup"><span data-stu-id="2e04d-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="2e04d-103">Bir belgeyi bulur.</span><span class="sxs-lookup"><span data-stu-id="2e04d-103">Finds a document.</span></span> <span data-ttu-id="2e04d-104">Belge dili, satıcı ve tür isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2e04d-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e04d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e04d-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e04d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2e04d-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="2e04d-107">[in] Belge tanımlayan URL.</span><span class="sxs-lookup"><span data-stu-id="2e04d-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="2e04d-108">[in] Belge dili.</span><span class="sxs-lookup"><span data-stu-id="2e04d-108">[in] The document language.</span></span> <span data-ttu-id="2e04d-109">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2e04d-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="2e04d-110">[in] Belge dili için satıcı kimliği.</span><span class="sxs-lookup"><span data-stu-id="2e04d-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="2e04d-111">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2e04d-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="2e04d-112">[in] Belge türü.</span><span class="sxs-lookup"><span data-stu-id="2e04d-112">[in] The type of the document.</span></span> <span data-ttu-id="2e04d-113">Bu parametre isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2e04d-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="2e04d-114">[out] Döndürülen arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2e04d-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e04d-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2e04d-115">Return Value</span></span>  
 <span data-ttu-id="2e04d-116">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2e04d-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e04d-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e04d-117">Requirements</span></span>  
 <span data-ttu-id="2e04d-118">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2e04d-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e04d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e04d-119">See also</span></span>

- [<span data-ttu-id="2e04d-120">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e04d-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
