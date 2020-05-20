---
title: ISymUnmanagedMethod::GetOffset Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
ms.openlocfilehash: 358f3d3d7c231a2baa9d2c467935ba3a5867e36b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614480"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="db91a-102">ISymUnmanagedMethod::GetOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="db91a-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="db91a-103">Bu yöntemin içindeki, bir belge içinde verilen konuma karşılık gelen sapmayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="db91a-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db91a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="db91a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db91a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db91a-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="db91a-106">'ndaki Kaydırın istendiği belge için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="db91a-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="db91a-107">'ndaki Kaydırın istendiği belge satırı.</span><span class="sxs-lookup"><span data-stu-id="db91a-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="db91a-108">'ndaki Kaydırın istendiği belge sütunu.</span><span class="sxs-lookup"><span data-stu-id="db91a-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="db91a-109">dışı `ULONG32`Uzaklıkları alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="db91a-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db91a-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="db91a-110">Return Value</span></span>  
 <span data-ttu-id="db91a-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="db91a-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db91a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db91a-112">Requirements</span></span>  
 <span data-ttu-id="db91a-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="db91a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db91a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db91a-114">See also</span></span>

- [<span data-ttu-id="db91a-115">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="db91a-115">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
