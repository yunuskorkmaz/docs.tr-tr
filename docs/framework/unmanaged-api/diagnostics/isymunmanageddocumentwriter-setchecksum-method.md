---
description: 'Daha fazla bilgi edinin: ISymUnmanagedDocumentWriter:: SetCheckSum Yöntemi'
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
ms.openlocfilehash: ac2ba9654f3610dca333cf0e06c20696cf31bd1f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710095"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="d3fdc-103">ISymUnmanagedDocumentWriter::SetCheckSum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3fdc-103">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>

<span data-ttu-id="d3fdc-104">Sağlama toplamı bilgilerini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d3fdc-104">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3fdc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3fdc-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3fdc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d3fdc-106">Parameters</span></span>  

 `algorithmId`  
 <span data-ttu-id="d3fdc-107">'ndaki Algoritma tanımlayıcısını temsil eden GUID.</span><span class="sxs-lookup"><span data-stu-id="d3fdc-107">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="d3fdc-108">'ndaki `ULONG32` Bu, arabelleğin bayt cinsinden boyutunu belirten bir `checkSum` .</span><span class="sxs-lookup"><span data-stu-id="d3fdc-108">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="d3fdc-109">'ndaki Sağlama toplamı bilgilerini depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="d3fdc-109">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3fdc-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d3fdc-110">Return Value</span></span>  

 <span data-ttu-id="d3fdc-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="d3fdc-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3fdc-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3fdc-112">Requirements</span></span>  

 <span data-ttu-id="d3fdc-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d3fdc-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3fdc-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3fdc-114">See also</span></span>

- [<span data-ttu-id="d3fdc-115">ISymUnmanagedDocumentWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3fdc-115">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
