---
title: ISymUnmanagedDocument::GetSourceRange Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetSourceRange
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetSourceRange
helpviewer_keywords:
- ISymUnmanagedDocument::GetSourceRange method [.NET Framework debugging]
- GetSourceRange method [.NET Framework debugging]
ms.assetid: 20fefee7-1040-41ba-93dc-bd42f68b90c2
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dcddebbca74bb94bd2411038a02b900b2f64f2d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="382bf-102">ISymUnmanagedDocument::GetSourceRange Metodu</span><span class="sxs-lookup"><span data-stu-id="382bf-102">ISymUnmanagedDocument::GetSourceRange Method</span></span>
<span data-ttu-id="382bf-103">Katıştırılmış kaynak belirtilen aralığını verilen arabelleğe döndürür.</span><span class="sxs-lookup"><span data-stu-id="382bf-103">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="382bf-104">Arabellek kaynak tutabilecek kadar büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="382bf-104">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="382bf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="382bf-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="382bf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="382bf-106">Parameters</span></span>  
 `startLine`  
 <span data-ttu-id="382bf-107">[in] Geçerli belgede başlangıç satırı.</span><span class="sxs-lookup"><span data-stu-id="382bf-107">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="382bf-108">[in] Geçerli belgede başlangıç sütunu.</span><span class="sxs-lookup"><span data-stu-id="382bf-108">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="382bf-109">[in] Geçerli belgede son satır.</span><span class="sxs-lookup"><span data-stu-id="382bf-109">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="382bf-110">[in] Geçerli belgede son sütun.</span><span class="sxs-lookup"><span data-stu-id="382bf-110">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="382bf-111">[in] Kaynak bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="382bf-111">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="382bf-112">[out] Bir işaretçi bir değişkene kaynak boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="382bf-112">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="382bf-113">[out] Boyutu ve belirtilen aralık kaynak belgenin bayt cinsinden uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="382bf-113">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="382bf-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="382bf-114">Return Value</span></span>  
 <span data-ttu-id="382bf-115">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="382bf-115">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="382bf-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="382bf-116">See Also</span></span>  
 [<span data-ttu-id="382bf-117">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="382bf-117">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
