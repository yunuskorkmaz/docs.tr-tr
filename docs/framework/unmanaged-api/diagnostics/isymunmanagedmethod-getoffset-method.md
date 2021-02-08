---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedmethod:: GetOffset Yöntemi'
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
ms.openlocfilehash: 3bc7154a47a38fd2cbadc62921f6e57f7901087e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790132"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="5ae9f-103">ISymUnmanagedMethod::GetOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="5ae9f-103">ISymUnmanagedMethod::GetOffset Method</span></span>

<span data-ttu-id="5ae9f-104">Bu yöntemin içindeki, bir belge içinde verilen konuma karşılık gelen sapmayı döndürür.</span><span class="sxs-lookup"><span data-stu-id="5ae9f-104">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ae9f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ae9f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ae9f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ae9f-106">Parameters</span></span>  

 `document`  
 <span data-ttu-id="5ae9f-107">'ndaki Kaydırın istendiği belge için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5ae9f-107">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="5ae9f-108">'ndaki Kaydırın istendiği belge satırı.</span><span class="sxs-lookup"><span data-stu-id="5ae9f-108">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="5ae9f-109">'ndaki Kaydırın istendiği belge sütunu.</span><span class="sxs-lookup"><span data-stu-id="5ae9f-109">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="5ae9f-110">dışı `ULONG32` Uzaklıkları alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5ae9f-110">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5ae9f-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5ae9f-111">Return Value</span></span>  

 <span data-ttu-id="5ae9f-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5ae9f-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ae9f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ae9f-113">Requirements</span></span>  

 <span data-ttu-id="5ae9f-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5ae9f-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ae9f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ae9f-115">See also</span></span>

- [<span data-ttu-id="5ae9f-116">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ae9f-116">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
