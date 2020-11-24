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
ms.openlocfilehash: 417644e5d0c7af802d5266bd1825efa83c181597
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689608"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="ac7f4-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac7f4-102">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>

<span data-ttu-id="ac7f4-103">Bir belgede verilen konumdaki kesme noktasını içeren yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ac7f4-103">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac7f4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ac7f4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac7f4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac7f4-105">Parameters</span></span>  

 `document`  
 <span data-ttu-id="ac7f4-106">'ndaki Belirtilen belge.</span><span class="sxs-lookup"><span data-stu-id="ac7f4-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="ac7f4-107">'ndaki Belirtilen belgenin satırı.</span><span class="sxs-lookup"><span data-stu-id="ac7f4-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="ac7f4-108">'ndaki Belirtilen belgenin sütunu.</span><span class="sxs-lookup"><span data-stu-id="ac7f4-108">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ac7f4-109">dışı Kesme noktasını içeren yöntemi temsil eden bir [ıdimunmanagedmethod Interface](isymunmanagedmethod-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ac7f4-109">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac7f4-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ac7f4-110">Return Value</span></span>  

 <span data-ttu-id="ac7f4-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ac7f4-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac7f4-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac7f4-112">Requirements</span></span>  

 <span data-ttu-id="ac7f4-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ac7f4-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac7f4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac7f4-114">See also</span></span>

- [<span data-ttu-id="ac7f4-115">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac7f4-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
