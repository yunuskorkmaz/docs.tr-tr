---
title: ISymUnmanagedReader::GetMethodFromDocumentPosition Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1935b831902e975616557f512789c339baf49c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776980"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="24814-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24814-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="24814-103">Bir belge belirtilen konumda bir kesme noktası içeren yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="24814-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24814-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24814-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24814-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24814-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="24814-106">[in] Belirtilen belge.</span><span class="sxs-lookup"><span data-stu-id="24814-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="24814-107">[in] Belirtilen belge satır.</span><span class="sxs-lookup"><span data-stu-id="24814-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="24814-108">[in] Belirtilen belgeyi içeren sütun.</span><span class="sxs-lookup"><span data-stu-id="24814-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="24814-109">[out] Adresine bir işaretçi bir [Isymunmanagedmethod arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) içerdiği kesme noktası yöntemi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="24814-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24814-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="24814-110">Return Value</span></span>  
 <span data-ttu-id="24814-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="24814-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24814-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24814-112">Requirements</span></span>  
 <span data-ttu-id="24814-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="24814-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24814-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24814-114">See also</span></span>

- [<span data-ttu-id="24814-115">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="24814-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
