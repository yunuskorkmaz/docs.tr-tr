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
ms.openlocfilehash: 4ed13397748b2668c275b221e38bd75c0dd37f03
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197704"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="9c0d0-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c0d0-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="9c0d0-103">Bir belge belirtilen konumda bir kesme noktası içeren yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="9c0d0-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c0d0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c0d0-104">Syntax</span></span>  
  
```  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c0d0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c0d0-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="9c0d0-106">[in] Belirtilen belge.</span><span class="sxs-lookup"><span data-stu-id="9c0d0-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="9c0d0-107">[in] Belirtilen belge satır.</span><span class="sxs-lookup"><span data-stu-id="9c0d0-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="9c0d0-108">[in] Belirtilen belgeyi içeren sütun.</span><span class="sxs-lookup"><span data-stu-id="9c0d0-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="9c0d0-109">[out] Adresine bir işaretçi bir [Isymunmanagedmethod arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) içerdiği kesme noktası yöntemi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="9c0d0-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c0d0-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9c0d0-110">Return Value</span></span>  
 <span data-ttu-id="9c0d0-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="9c0d0-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c0d0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c0d0-112">Requirements</span></span>  
 <span data-ttu-id="9c0d0-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9c0d0-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c0d0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c0d0-114">See also</span></span>

- [<span data-ttu-id="9c0d0-115">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c0d0-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
