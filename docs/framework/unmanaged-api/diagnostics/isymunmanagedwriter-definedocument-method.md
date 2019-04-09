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
ms.openlocfilehash: 726ac0e23f739f451e1a0ab66c4c36aa6edbe569
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132138"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="06fde-102">ISymUnmanagedWriter::DefineDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06fde-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="06fde-103">Kaynak belge tanımlar.</span><span class="sxs-lookup"><span data-stu-id="06fde-103">Defines a source document.</span></span> <span data-ttu-id="06fde-104">GUID'ler, bilinen diller, satıcılar ve belge türü için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="06fde-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06fde-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06fde-105">Syntax</span></span>  
  
```  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06fde-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06fde-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="06fde-107">[in] Bir işaretçi bir `WCHAR` belgenin tanımlar Tekdüzen Kaynak Konum Belirleyicisi (URL) tanımlar.</span><span class="sxs-lookup"><span data-stu-id="06fde-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="06fde-108">[in] Belge dili tanımlayan bir GUID için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="06fde-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="06fde-109">[in] Belge dili satıcısının kimliğini tanımlayan bir GUID için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="06fde-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="06fde-110">[in] Belge türünü tanımlayan bir GUID için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="06fde-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="06fde-111">[out] Döndürülen işaretçi [Isymunmanagedwriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="06fde-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06fde-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="06fde-112">Return Value</span></span>  
 <span data-ttu-id="06fde-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="06fde-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06fde-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06fde-114">Requirements</span></span>  
 <span data-ttu-id="06fde-115">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="06fde-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06fde-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06fde-116">See also</span></span>

- [<span data-ttu-id="06fde-117">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06fde-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
