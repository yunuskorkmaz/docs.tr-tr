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
ms.openlocfilehash: dbf876a514ce106c566a168f688eb3a22d3a1ea2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449050"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="2ce08-102">ISymUnmanagedDocumentWriter::SetCheckSum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ce08-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>
<span data-ttu-id="2ce08-103">Sağlama toplamı bilgilerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2ce08-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ce08-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ce08-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ce08-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ce08-105">Parameters</span></span>  
 `algorithmId`  
 <span data-ttu-id="2ce08-106">'ndaki Algoritma tanımlayıcısını temsil eden GUID.</span><span class="sxs-lookup"><span data-stu-id="2ce08-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="2ce08-107">'ndaki `checkSum` arabelleğinin boyutunu bayt cinsinden belirten bir `ULONG32`.</span><span class="sxs-lookup"><span data-stu-id="2ce08-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="2ce08-108">'ndaki Sağlama toplamı bilgilerini depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="2ce08-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ce08-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2ce08-109">Return Value</span></span>  
 <span data-ttu-id="2ce08-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2ce08-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ce08-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ce08-111">Requirements</span></span>  
 <span data-ttu-id="2ce08-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2ce08-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ce08-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ce08-113">See also</span></span>

- [<span data-ttu-id="2ce08-114">ISymUnmanagedDocumentWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ce08-114">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
