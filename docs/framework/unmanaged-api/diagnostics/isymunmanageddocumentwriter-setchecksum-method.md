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
ms.openlocfilehash: 3b9b77b94e466a4aab4a575501ac6922293b3410
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424150"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="a9a46-102">ISymUnmanagedDocumentWriter::SetCheckSum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9a46-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="a9a46-103">Sağlama bilgilerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a9a46-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9a46-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9a46-104">Syntax</span></span>  
  
```  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9a46-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9a46-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="a9a46-106">[in] Algoritma tanımlayıcısı temsil eden GUID.</span><span class="sxs-lookup"><span data-stu-id="a9a46-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="a9a46-107">[in] A `ULONG32` bayt cinsinden boyutu belirten `checkSum` arabellek.</span><span class="sxs-lookup"><span data-stu-id="a9a46-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="a9a46-108">[in] Sağlama bilgilerini depolayan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="a9a46-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9a46-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a9a46-109">Return Value</span></span>  
 <span data-ttu-id="a9a46-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a9a46-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9a46-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9a46-111">Requirements</span></span>  
 <span data-ttu-id="a9a46-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a9a46-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9a46-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a9a46-113">See Also</span></span>  
 [<span data-ttu-id="a9a46-114">ISymUnmanagedDocumentWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9a46-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
