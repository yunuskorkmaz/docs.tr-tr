---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanageddocument:: GetSourceRange yöntemi'
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
ms.openlocfilehash: 98718298d7bf2f44d418a40f17ad19cdee0b6771
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790171"
---
# <a name="isymunmanageddocumentgetsourcerange-method"></a><span data-ttu-id="f7c5f-103">ISymUnmanagedDocument::GetSourceRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f7c5f-103">ISymUnmanagedDocument::GetSourceRange Method</span></span>

<span data-ttu-id="f7c5f-104">Eklenmiş kaynağın belirtilen aralığını verilen arabelleğe döndürür.</span><span class="sxs-lookup"><span data-stu-id="f7c5f-104">Returns the specified range of the embedded source into the given buffer.</span></span> <span data-ttu-id="f7c5f-105">Arabellek, kaynağı tutabilecek kadar büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7c5f-105">The buffer must be large enough to hold the source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7c5f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7c5f-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="f7c5f-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f7c5f-107">Parameters</span></span>  

 `startLine`  
 <span data-ttu-id="f7c5f-108">'ndaki Geçerli belgedeki başlangıç satırı.</span><span class="sxs-lookup"><span data-stu-id="f7c5f-108">[in] The starting line in the current document.</span></span>  
  
 `startColumn`  
 <span data-ttu-id="f7c5f-109">'ndaki Geçerli belgedeki başlangıç sütunu.</span><span class="sxs-lookup"><span data-stu-id="f7c5f-109">[in] The starting column in the current document.</span></span>  
  
 `endLine`  
 <span data-ttu-id="f7c5f-110">'ndaki Geçerli belgedeki son satır.</span><span class="sxs-lookup"><span data-stu-id="f7c5f-110">[in] The final line in the current document.</span></span>  
  
 `endColumn`  
 <span data-ttu-id="f7c5f-111">'ndaki Geçerli belgedeki son sütun.</span><span class="sxs-lookup"><span data-stu-id="f7c5f-111">[in] The final column in the current document.</span></span>  
  
 `cSourceBytes`  
 <span data-ttu-id="f7c5f-112">'ndaki Kaynağın bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="f7c5f-112">[in] The size of the source, in bytes.</span></span>  
  
 `pcSourceBytes`  
 <span data-ttu-id="f7c5f-113">dışı Kaynak boyutunu alan değişken için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f7c5f-113">[out] A pointer to a variable that receives the source size.</span></span>  
  
 `source`  
 <span data-ttu-id="f7c5f-114">dışı Kaynak belge için bayt cinsinden belirtilen aralığın boyutu ve uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="f7c5f-114">[out] The size and length of the specified range of the source document, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7c5f-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f7c5f-115">Return Value</span></span>  

 <span data-ttu-id="f7c5f-116">Yöntem başarılı olursa S_OK.</span><span class="sxs-lookup"><span data-stu-id="f7c5f-116">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c5f-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7c5f-117">See also</span></span>

- [<span data-ttu-id="f7c5f-118">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7c5f-118">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
