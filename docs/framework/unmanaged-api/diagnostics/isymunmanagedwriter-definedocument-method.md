---
title: ISymUnmanagedWriter::DefineDocument Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 532f69afd949971fbb4f56a8fdbcc6eab159446f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427713"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="97d89-102">ISymUnmanagedWriter::DefineDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="97d89-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="97d89-103">Kaynak belge tanımlar.</span><span class="sxs-lookup"><span data-stu-id="97d89-103">Defines a source document.</span></span> <span data-ttu-id="97d89-104">GUID, bilinen diller, satıcılar ve belge türleri için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="97d89-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d89-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="97d89-105">Syntax</span></span>  
  
```  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97d89-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="97d89-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="97d89-107">[in] Bir işaretçi bir `WCHAR` belge tanımlayan Tekdüzen Kaynak Konum Belirleyicisi (URL) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="97d89-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="97d89-108">[in] Bir işaretçi belge dili tanımlayan bir GUID.</span><span class="sxs-lookup"><span data-stu-id="97d89-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="97d89-109">[in] Bir işaretçi belge dili satıcısının kimliğini tanımlayan bir GUID.</span><span class="sxs-lookup"><span data-stu-id="97d89-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="97d89-110">[in] Bir işaretçi belge türünü tanımlayan bir GUID.</span><span class="sxs-lookup"><span data-stu-id="97d89-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="97d89-111">[out] Bir işaretçi döndürülen [Isymunmanagedwriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="97d89-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97d89-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="97d89-112">Return Value</span></span>  
 <span data-ttu-id="97d89-113">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="97d89-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97d89-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97d89-114">Requirements</span></span>  
 <span data-ttu-id="97d89-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="97d89-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d89-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97d89-116">See Also</span></span>  
 [<span data-ttu-id="97d89-117">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="97d89-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
