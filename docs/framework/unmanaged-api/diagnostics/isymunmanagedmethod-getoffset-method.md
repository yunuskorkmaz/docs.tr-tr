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
ms.openlocfilehash: a42dc624d4de9cddebad287f6d90590f96b30272
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939665"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="ddb3c-102">ISymUnmanagedMethod::GetOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="ddb3c-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="ddb3c-103">Bir belge içindeki belirli bir konuma karşılık gelen bu yöntem içinde uzaklığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="ddb3c-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddb3c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ddb3c-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddb3c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ddb3c-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="ddb3c-106">[in] Uzaklık istendiği belge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ddb3c-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="ddb3c-107">[in] Uzaklık istendiği belge satır.</span><span class="sxs-lookup"><span data-stu-id="ddb3c-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="ddb3c-108">[in] Uzaklık istendiği belge sütun.</span><span class="sxs-lookup"><span data-stu-id="ddb3c-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ddb3c-109">[out] Bir işaretçi bir `ULONG32` , uzaklıkları alır.</span><span class="sxs-lookup"><span data-stu-id="ddb3c-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddb3c-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ddb3c-110">Return Value</span></span>  
 <span data-ttu-id="ddb3c-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ddb3c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddb3c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ddb3c-112">Requirements</span></span>  
 <span data-ttu-id="ddb3c-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ddb3c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddb3c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddb3c-114">See also</span></span>

- [<span data-ttu-id="ddb3c-115">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ddb3c-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
