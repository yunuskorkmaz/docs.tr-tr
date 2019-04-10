---
title: ISymUnmanagedDocument::GetSourceRange Yöntemi
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
ms.openlocfilehash: 59420cfd29c3228aece9fc5ae02b950db6099ea0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218478"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="34924-102">ISymUnmanagedDocument::GetSourceRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="34924-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="34924-103">Katıştırılmış kaynak Belirtilen aralıktaki belirli arabelleğe döndürür.</span><span class="sxs-lookup"><span data-stu-id="34924-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="34924-104">Arabellek kaynağını tutabilecek kadar büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="34924-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34924-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34924-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="34924-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34924-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="34924-107">[in] Geçerli belgedeki başlangıç satırı.</span><span class="sxs-lookup"><span data-stu-id="34924-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="34924-108">[in] Geçerli belgedeki başlangıç sütunu.</span><span class="sxs-lookup"><span data-stu-id="34924-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="34924-109">[in] Geçerli belgedeki son satır.</span><span class="sxs-lookup"><span data-stu-id="34924-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="34924-110">[in] Son sütun geçerli belge.</span><span class="sxs-lookup"><span data-stu-id="34924-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="34924-111">[in] Kaynak, bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="34924-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="34924-112">[out] Kaynak boyutu alan bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="34924-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="34924-113">[out] Boyutu ve belirtilen kaynak belgesinde bayt aralığı uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="34924-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="34924-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="34924-114">Return Value</span></span>  
 <span data-ttu-id="34924-115">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="34924-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34924-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34924-116">See also</span></span>

- [<span data-ttu-id="34924-117">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="34924-117">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
