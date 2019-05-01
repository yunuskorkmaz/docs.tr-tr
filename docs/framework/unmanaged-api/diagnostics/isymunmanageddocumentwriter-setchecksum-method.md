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
ms.openlocfilehash: ac3daccfade4f5ae10fe2ebbf83a7a11af34b89b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939769"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="da9f1-102">ISymUnmanagedDocumentWriter::SetCheckSum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da9f1-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="da9f1-103">Sağlama bilgilerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="da9f1-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da9f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da9f1-104">Syntax</span></span>  
  
```  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da9f1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="da9f1-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="da9f1-106">[in] Algoritma tanımlayıcısını temsil eden GUID.</span><span class="sxs-lookup"><span data-stu-id="da9f1-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="da9f1-107">[in] A `ULONG32` bayt cinsinden boyutunu belirten `checkSum` arabellek.</span><span class="sxs-lookup"><span data-stu-id="da9f1-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="da9f1-108">[in] Sağlama toplamı bilgileri depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="da9f1-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da9f1-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="da9f1-109">Return Value</span></span>  
 <span data-ttu-id="da9f1-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="da9f1-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da9f1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="da9f1-111">Requirements</span></span>  
 <span data-ttu-id="da9f1-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="da9f1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da9f1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da9f1-113">See also</span></span>

- [<span data-ttu-id="da9f1-114">ISymUnmanagedDocumentWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="da9f1-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
