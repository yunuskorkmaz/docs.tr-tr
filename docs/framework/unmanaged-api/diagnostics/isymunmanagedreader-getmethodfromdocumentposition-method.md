---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanagedreader:: GetMethodFromDocumentPosition Yöntemi'
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
ms.openlocfilehash: 1289b02f8ea8440dcd1b308b6c91a46a213cabb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764092"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a><span data-ttu-id="43349-103">ISymUnmanagedReader::GetMethodFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43349-103">ISymUnmanagedReader::GetMethodFromDocumentPosition Method</span></span>

<span data-ttu-id="43349-104">Bir belgede verilen konumdaki kesme noktasını içeren yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="43349-104">Returns the method that contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43349-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43349-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43349-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43349-106">Parameters</span></span>  

 `document`  
 <span data-ttu-id="43349-107">'ndaki Belirtilen belge.</span><span class="sxs-lookup"><span data-stu-id="43349-107">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="43349-108">'ndaki Belirtilen belgenin satırı.</span><span class="sxs-lookup"><span data-stu-id="43349-108">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="43349-109">'ndaki Belirtilen belgenin sütunu.</span><span class="sxs-lookup"><span data-stu-id="43349-109">[in] The column of the specified document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="43349-110">dışı Kesme noktasını içeren yöntemi temsil eden bir [ıdimunmanagedmethod Interface](isymunmanagedmethod-interface.md) nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="43349-110">[out] A pointer to the address of a [ISymUnmanagedMethod Interface](isymunmanagedmethod-interface.md) object that represents the method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43349-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="43349-111">Return Value</span></span>  

 <span data-ttu-id="43349-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="43349-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43349-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43349-113">Requirements</span></span>  

 <span data-ttu-id="43349-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="43349-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43349-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43349-115">See also</span></span>

- [<span data-ttu-id="43349-116">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43349-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
