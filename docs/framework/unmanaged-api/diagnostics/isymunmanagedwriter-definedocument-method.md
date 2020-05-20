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
ms.openlocfilehash: fdcfb0c4f9c21eb516f4196d0c8f682669468219
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615234"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="859d8-102">ISymUnmanagedWriter::DefineDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="859d8-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="859d8-103">Bir kaynak belge tanımlar.</span><span class="sxs-lookup"><span data-stu-id="859d8-103">Defines a source document.</span></span> <span data-ttu-id="859d8-104">GUID 'Ler, bilinen diller, satıcılar ve belge türleri için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="859d8-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="859d8-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="859d8-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="859d8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="859d8-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="859d8-107">'ndaki `WCHAR`Belgeyi tanımlayan Tekdüzen Kaynak Konumlandırıcı 'sını (URL) tanımlayan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="859d8-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="859d8-108">'ndaki Belge dilini tanımlayan bir GUID işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="859d8-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="859d8-109">'ndaki Belge dili için satıcının kimliğini tanımlayan bir GUID işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="859d8-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="859d8-110">'ndaki Belge türünü tanımlayan GUID için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="859d8-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="859d8-111">dışı Döndürülen [ıdimunmanagedwriter](isymunmanagedwriter-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="859d8-111">[out] A pointer to the returned [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="859d8-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="859d8-112">Return Value</span></span>  
 <span data-ttu-id="859d8-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="859d8-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="859d8-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="859d8-114">Requirements</span></span>  
 <span data-ttu-id="859d8-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="859d8-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="859d8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="859d8-116">See also</span></span>

- [<span data-ttu-id="859d8-117">ISymUnmanagedWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="859d8-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
