---
title: ISymUnmanagedReader::GetMethodsFromDocumentPosition Metodu
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f55c8986d2efc78b6fcd2840bad588af84228017
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561784"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="6e60a-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Metodu</span><span class="sxs-lookup"><span data-stu-id="6e60a-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>
<span data-ttu-id="6e60a-103">Yöntemler, her biri bir belge belirtilen konumda bir kesme noktası içeren bir dizisini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e60a-103">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e60a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e60a-104">Syntax</span></span>  
  
```  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e60a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e60a-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="6e60a-106">[in] Belirtilen belge.</span><span class="sxs-lookup"><span data-stu-id="6e60a-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="6e60a-107">[in] Belirtilen belge satır.</span><span class="sxs-lookup"><span data-stu-id="6e60a-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="6e60a-108">[in] Belirtilen belgeyi içeren sütun.</span><span class="sxs-lookup"><span data-stu-id="6e60a-108">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="6e60a-109">[in] Boyutu `pRetVal` dizisi.</span><span class="sxs-lookup"><span data-stu-id="6e60a-109">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="6e60a-110">[out] Döndürülen öğe sayısını alır bir değişken işaretçisi `pRetVal` dizisi.</span><span class="sxs-lookup"><span data-stu-id="6e60a-110">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6e60a-111">[out] Bir dizi işaretçileri, her biri için işaret eden bir [Isymunmanagedmethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) kesme noktası içeren bir yöntemi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="6e60a-111">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e60a-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6e60a-112">Return Value</span></span>  
 <span data-ttu-id="6e60a-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6e60a-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e60a-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e60a-114">Requirements</span></span>  
 <span data-ttu-id="6e60a-115">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6e60a-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e60a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e60a-116">See also</span></span>
- [<span data-ttu-id="6e60a-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e60a-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
