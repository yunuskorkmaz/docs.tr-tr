---
title: ISymUnmanagedDocument::GetSourceRange Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 00baed93bd9ab48c92de83dac76931c3149afc2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424644"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="dd24e-102">ISymUnmanagedDocument::GetSourceRange Metodu</span><span class="sxs-lookup"><span data-stu-id="dd24e-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="dd24e-103">Katıştırılmış kaynak belirtilen aralığını verilen arabelleğe döndürür.</span><span class="sxs-lookup"><span data-stu-id="dd24e-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="dd24e-104">Arabellek kaynak tutabilecek kadar büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dd24e-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd24e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd24e-105">Syntax</span></span>  
  
```  
HRESULT GetSourceRange(  
    [in]  ULONG32  startLine,  
    [in]  ULONG32  startColumn,  
    [in]  ULONG32  endLine,  
    [in]  ULONG32  endColumn,  
    [in]  ULONG32  cSourceBytes,  
    [out] ULONG32  *pcSourceBytes,  
    [out, size_is(cSourceBytes),  
        length_is(*pcSourceBytes)] BYTE source[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd24e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dd24e-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="dd24e-107">[in] Geçerli belgede başlangıç satırı.</span><span class="sxs-lookup"><span data-stu-id="dd24e-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="dd24e-108">[in] Geçerli belgede başlangıç sütunu.</span><span class="sxs-lookup"><span data-stu-id="dd24e-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="dd24e-109">[in] Geçerli belgede son satır.</span><span class="sxs-lookup"><span data-stu-id="dd24e-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="dd24e-110">[in] Geçerli belgede son sütun.</span><span class="sxs-lookup"><span data-stu-id="dd24e-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="dd24e-111">[in] Kaynak bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="dd24e-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="dd24e-112">[out] Bir işaretçi bir değişkene kaynak boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="dd24e-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="dd24e-113">[out] Boyutu ve belirtilen aralık kaynak belgenin bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="dd24e-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd24e-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dd24e-114">Return Value</span></span>  
 <span data-ttu-id="dd24e-115">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="dd24e-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd24e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dd24e-116">See Also</span></span>  
 [<span data-ttu-id="dd24e-117">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dd24e-117">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
