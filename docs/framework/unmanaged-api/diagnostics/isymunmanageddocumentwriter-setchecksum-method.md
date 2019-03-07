---
title: ISymUnmanagedDocumentWriter::SetCheckSum Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59ec4d9f39362f563312a9ed75bb1ab5cede799d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484036"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="9b95e-102">ISymUnmanagedDocumentWriter::SetCheckSum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b95e-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="9b95e-103">Sağlama bilgilerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9b95e-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b95e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b95e-104">Syntax</span></span>  
  
```  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b95e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b95e-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="9b95e-106">[in] Algoritma tanımlayıcısını temsil eden GUID.</span><span class="sxs-lookup"><span data-stu-id="9b95e-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="9b95e-107">[in] A `ULONG32` bayt cinsinden boyutunu belirten `checkSum` arabellek.</span><span class="sxs-lookup"><span data-stu-id="9b95e-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="9b95e-108">[in] Sağlama toplamı bilgileri depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="9b95e-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b95e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9b95e-109">Return Value</span></span>  
 <span data-ttu-id="9b95e-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="9b95e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b95e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b95e-111">Requirements</span></span>  
 <span data-ttu-id="9b95e-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9b95e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b95e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b95e-113">See also</span></span>
- [<span data-ttu-id="9b95e-114">ISymUnmanagedDocumentWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b95e-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
