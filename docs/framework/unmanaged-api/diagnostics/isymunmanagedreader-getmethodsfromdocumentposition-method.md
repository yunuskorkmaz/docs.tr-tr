---
title: ISymUnmanagedReader::GetMethodsFromDocumentPosition Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cdf3762c40e5ec4da84a27ed7abcb15981b81379
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a><span data-ttu-id="c0b30-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Metodu</span><span class="sxs-lookup"><span data-stu-id="c0b30-102">ISymUnmanagedReader::GetMethodsFromDocumentPosition Method</span></span>
<span data-ttu-id="c0b30-103">Her biri bir belgede verilen konumunda kesme noktası içeren bir dizi yöntemleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0b30-103">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0b30-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0b30-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="c0b30-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0b30-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="c0b30-106">[in] Belirtilen belge.</span><span class="sxs-lookup"><span data-stu-id="c0b30-106">[in] The specified document.</span></span>  
  
 `line`  
 <span data-ttu-id="c0b30-107">[in] Belirtilen belge satırı.</span><span class="sxs-lookup"><span data-stu-id="c0b30-107">[in] The line of the specified document.</span></span>  
  
 `column`  
 <span data-ttu-id="c0b30-108">[in] Belirtilen belge sütun.</span><span class="sxs-lookup"><span data-stu-id="c0b30-108">[in] The column of the specified document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="c0b30-109">[in] Boyutunu `pRetVal` dizi.</span><span class="sxs-lookup"><span data-stu-id="c0b30-109">[in] The size of the `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="c0b30-110">[out] Döndürülen öğe sayısını alır bir değişken için bir işaretçi `pRetVal` dizi.</span><span class="sxs-lookup"><span data-stu-id="c0b30-110">[out] A pointer to a variable that receives the number of elements returned in the `pRetVal` array.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="c0b30-111">[out] Her biri işaret işaretçileri, bir dizi bir [Isymunmanagedmethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) kesme noktası içeren bir yöntemi temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="c0b30-111">[out] An array of pointers, each of which points to an [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) object that represents a method containing the breakpoint.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0b30-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c0b30-112">Return Value</span></span>  
 <span data-ttu-id="c0b30-113">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c0b30-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0b30-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0b30-114">Requirements</span></span>  
 <span data-ttu-id="c0b30-115">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c0b30-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0b30-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c0b30-116">See Also</span></span>  
 [<span data-ttu-id="c0b30-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0b30-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
