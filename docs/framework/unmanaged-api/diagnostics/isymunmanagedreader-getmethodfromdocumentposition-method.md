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
ms.openlocfilehash: 8015056b110fe8a5b5122b1bc81143980b780047
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614987"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="ac772-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac772-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>
<span data-ttu-id="ac772-103">Bir belgede verilen konumdaki kesme noktasını içeren yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac772-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac772-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ac772-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac772-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac772-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="ac772-106">'ndaki Belirtilen belge.</span><span class="sxs-lookup"><span data-stu-id="ac772-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="ac772-107">'ndaki Belirtilen belgenin satırı.</span><span class="sxs-lookup"><span data-stu-id="ac772-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="ac772-108">'ndaki Belirtilen belgenin sütunu.</span><span class="sxs-lookup"><span data-stu-id="ac772-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ac772-109">dışı Kesme noktasını içeren yöntemi temsil eden bir [ıdimunmanagedmethod Interface](isymunmanagedmethod-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ac772-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac772-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ac772-110">Return Value</span></span>  
 <span data-ttu-id="ac772-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ac772-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac772-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac772-112">Requirements</span></span>  
 <span data-ttu-id="ac772-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ac772-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac772-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac772-114">See also</span></span>

- [<span data-ttu-id="ac772-115">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac772-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
