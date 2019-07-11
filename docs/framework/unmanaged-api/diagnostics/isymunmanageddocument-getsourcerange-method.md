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
ms.openlocfilehash: 981048c10be27900f011afeab55d1c5eb523f734
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776673"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="adff7-102">ISymUnmanagedDocument::GetSourceRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="adff7-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="adff7-103">Katıştırılmış kaynak Belirtilen aralıktaki belirli arabelleğe döndürür.</span><span class="sxs-lookup"><span data-stu-id="adff7-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="adff7-104">Arabellek kaynağını tutabilecek kadar büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="adff7-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adff7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="adff7-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="adff7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="adff7-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="adff7-107">[in] Geçerli belgedeki başlangıç satırı.</span><span class="sxs-lookup"><span data-stu-id="adff7-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="adff7-108">[in] Geçerli belgedeki başlangıç sütunu.</span><span class="sxs-lookup"><span data-stu-id="adff7-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="adff7-109">[in] Geçerli belgedeki son satır.</span><span class="sxs-lookup"><span data-stu-id="adff7-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="adff7-110">[in] Son sütun geçerli belge.</span><span class="sxs-lookup"><span data-stu-id="adff7-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="adff7-111">[in] Kaynak, bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="adff7-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="adff7-112">[out] Kaynak boyutu alan bir değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="adff7-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="adff7-113">[out] Boyutu ve belirtilen kaynak belgesinde bayt aralığı uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="adff7-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="adff7-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="adff7-114">Return Value</span></span>  
 <span data-ttu-id="adff7-115">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="adff7-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adff7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adff7-116">See also</span></span>

- [<span data-ttu-id="adff7-117">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="adff7-117">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
