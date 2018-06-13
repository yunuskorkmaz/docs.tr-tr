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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d88e9279f70c36fd8a9c626972e33305cded5fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424397"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="b70af-102">ISymUnmanagedMethod::GetOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="b70af-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="b70af-103">Bir belge içinde belirli bir konuma karşılık gelen bu yöntem içinde uzaklığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="b70af-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b70af-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b70af-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b70af-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b70af-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="b70af-106">[in] Uzaklık istenen belge için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b70af-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="b70af-107">[in] Uzaklık istenen belge satırı.</span><span class="sxs-lookup"><span data-stu-id="b70af-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="b70af-108">[in] Uzaklık istenen belge sütun.</span><span class="sxs-lookup"><span data-stu-id="b70af-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="b70af-109">[out] Bir işaretçi bir `ULONG32` uzaklıkları alır.</span><span class="sxs-lookup"><span data-stu-id="b70af-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b70af-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b70af-110">Return Value</span></span>  
 <span data-ttu-id="b70af-111">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b70af-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b70af-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b70af-112">Requirements</span></span>  
 <span data-ttu-id="b70af-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b70af-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b70af-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b70af-114">See Also</span></span>  
 [<span data-ttu-id="b70af-115">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b70af-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
