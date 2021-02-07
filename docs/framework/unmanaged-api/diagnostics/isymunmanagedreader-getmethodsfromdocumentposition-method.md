---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: GetMethodsFromDocumentPosition yöntemi'
title: ISymUnmanagedReader::GetMethodsFromDocumentPosition Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
ms.openlocfilehash: 033bdce2cd70e578ebd3be8a187d983a2c58b99d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764040"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="72ff7-103">ISymUnmanagedReader::GetMethodsFromDocumentPosition Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72ff7-103">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>

<span data-ttu-id="72ff7-104">Her biri bir belgede verilen konumdaki kesme noktasını içeren bir yöntem dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="72ff7-104">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72ff7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72ff7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72ff7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72ff7-106">Parameters</span></span>  

 `document`  
 <span data-ttu-id="72ff7-107">'ndaki Belirtilen belge.</span><span class="sxs-lookup"><span data-stu-id="72ff7-107">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="72ff7-108">'ndaki Belirtilen belgenin satırı.</span><span class="sxs-lookup"><span data-stu-id="72ff7-108">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="72ff7-109">'ndaki Belirtilen belgenin sütunu.</span><span class="sxs-lookup"><span data-stu-id="72ff7-109">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="72ff7-110">'ndaki `pRetVal` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="72ff7-110">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="72ff7-111">dışı Dizide döndürülen öğelerin sayısını alan bir değişken işaretçisi `pRetVal` .</span><span class="sxs-lookup"><span data-stu-id="72ff7-111">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="72ff7-112">dışı Her biri, kesme noktasını içeren bir yöntemi temsil eden bir [ıstreamunmanagedmethod](isymunmanagedmethod-interface.md) nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="72ff7-112">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72ff7-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="72ff7-113">Return Value</span></span>  

 <span data-ttu-id="72ff7-114">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="72ff7-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72ff7-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72ff7-115">Requirements</span></span>  

 <span data-ttu-id="72ff7-116">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="72ff7-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72ff7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72ff7-117">See also</span></span>

- [<span data-ttu-id="72ff7-118">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72ff7-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
