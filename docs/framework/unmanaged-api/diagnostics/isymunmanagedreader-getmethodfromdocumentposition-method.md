---
title: ISymUnmanagedReader::GetMethodFromDocumentPosition Metodu
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
ms.openlocfilehash: f756a6e80eee0998398b4955d1d091d97b2ad73f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426165"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="7009f-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Metodu</span><span class="sxs-lookup"><span data-stu-id="7009f-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="7009f-103">Belgede verilen konumunda kesme noktası içerdiğinden yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="7009f-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7009f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7009f-104">Syntax</span></span>  
  
```  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7009f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7009f-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="7009f-106">[in] Belirtilen belge.</span><span class="sxs-lookup"><span data-stu-id="7009f-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="7009f-107">[in] Belirtilen belge satırı.</span><span class="sxs-lookup"><span data-stu-id="7009f-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="7009f-108">[in] Belirtilen belge sütun.</span><span class="sxs-lookup"><span data-stu-id="7009f-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="7009f-109">[out] Adresine bir işaretçi bir [Isymunmanagedmethod arabirimi](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) kesme içeren yöntemi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="7009f-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7009f-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7009f-110">Return Value</span></span>  
 <span data-ttu-id="7009f-111">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="7009f-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7009f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7009f-112">Requirements</span></span>  
 <span data-ttu-id="7009f-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7009f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7009f-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7009f-114">See Also</span></span>  
 [<span data-ttu-id="7009f-115">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7009f-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
