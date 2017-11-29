---
title: "ISymUnmanagedWriter::DefineDocument Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.DefineDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 638759cb52eb28cc79217da81a867f2593e1ae97
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="0144a-102">ISymUnmanagedWriter::DefineDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0144a-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="0144a-103">Kaynak belge tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0144a-103">Defines a source document.</span></span> <span data-ttu-id="0144a-104">GUID, bilinen diller, satıcılar ve belge türleri için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0144a-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0144a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0144a-105">Syntax</span></span>  
  
```  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0144a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0144a-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="0144a-107">[in] Bir işaretçi bir `WCHAR` belge tanımlayan Tekdüzen Kaynak Konum Belirleyicisi (URL) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0144a-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="0144a-108">[in] Bir işaretçi belge dili tanımlayan bir GUID.</span><span class="sxs-lookup"><span data-stu-id="0144a-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="0144a-109">[in] Bir işaretçi belge dili satıcısının kimliğini tanımlayan bir GUID.</span><span class="sxs-lookup"><span data-stu-id="0144a-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="0144a-110">[in] Bir işaretçi belge türünü tanımlayan bir GUID.</span><span class="sxs-lookup"><span data-stu-id="0144a-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="0144a-111">[out] Bir işaretçi döndürülen [Isymunmanagedwriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="0144a-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0144a-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0144a-112">Return Value</span></span>  
 <span data-ttu-id="0144a-113">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="0144a-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0144a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0144a-114">Requirements</span></span>  
 <span data-ttu-id="0144a-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0144a-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0144a-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0144a-116">See Also</span></span>  
 [<span data-ttu-id="0144a-117">Isymunmanagedwriter arabirimi</span><span class="sxs-lookup"><span data-stu-id="0144a-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
