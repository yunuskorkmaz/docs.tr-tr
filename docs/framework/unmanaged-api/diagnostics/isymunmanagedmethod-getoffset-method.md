---
title: ISymUnmanagedMethod::GetOffset Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f75236ae954b4ff3df9dd1c322cef45dfaf7fb2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="c3e73-102">ISymUnmanagedMethod::GetOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="c3e73-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="c3e73-103">Bir belge içinde belirli bir konuma karşılık gelen bu yöntem içinde uzaklığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3e73-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3e73-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3e73-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3e73-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3e73-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="c3e73-106">[in] Uzaklık istenen belge için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c3e73-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="c3e73-107">[in] Uzaklık istenen belge satırı.</span><span class="sxs-lookup"><span data-stu-id="c3e73-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="c3e73-108">[in] Uzaklık istenen belge sütun.</span><span class="sxs-lookup"><span data-stu-id="c3e73-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="c3e73-109">[out] Bir işaretçi bir `ULONG32` uzaklıkları alır.</span><span class="sxs-lookup"><span data-stu-id="c3e73-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3e73-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c3e73-110">Return Value</span></span>  
 <span data-ttu-id="c3e73-111">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c3e73-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3e73-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3e73-112">Requirements</span></span>  
 <span data-ttu-id="c3e73-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c3e73-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3e73-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c3e73-114">See Also</span></span>  
 [<span data-ttu-id="c3e73-115">Isymunmanagedmethod arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3e73-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
