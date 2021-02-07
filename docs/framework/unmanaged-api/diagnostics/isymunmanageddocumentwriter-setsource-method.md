---
description: 'Daha fazla bilgi edinin: ISymUnmanagedDocumentWriter:: SetSource yöntemi'
title: ISymUnmanagedDocumentWriter::SetSource Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type:
- apiref
ms.openlocfilehash: e24e34a297a9931babf3df4f2bae1b5e8f60db1b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721482"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="192e5-103">ISymUnmanagedDocumentWriter::SetSource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="192e5-103">ISymUnmanagedDocumentWriter::SetSource Method</span></span>

<span data-ttu-id="192e5-104">Yazılmakta olan bir belge için gömülü kaynağı ayarlar.</span><span class="sxs-lookup"><span data-stu-id="192e5-104">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="192e5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="192e5-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="192e5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="192e5-106">Parameters</span></span>  

 `sourceSize`  
 <span data-ttu-id="192e5-107">'ndaki `ULONG32` Arabellek boyutunu içeren bir `source` .</span><span class="sxs-lookup"><span data-stu-id="192e5-107">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="192e5-108">'ndaki Gömülü kaynağı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="192e5-108">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="192e5-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="192e5-109">Return Value</span></span>  

 <span data-ttu-id="192e5-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="192e5-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="192e5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="192e5-111">Requirements</span></span>  

 <span data-ttu-id="192e5-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="192e5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="192e5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="192e5-113">See also</span></span>

- [<span data-ttu-id="192e5-114">ISymUnmanagedDocumentWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="192e5-114">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
