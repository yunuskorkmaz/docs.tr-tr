---
description: 'Şu konuda daha fazla bilgi edinin: ISymUnmanagedReader2:: GetMethodsInDocument yöntemi'
title: ISymUnmanagedReader2::GetMethodsInDocument Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodsInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument
helpviewer_keywords:
- ISymUnmanagedReader2::GetMethodsInDocument method [.NET Framework debugging]
- GetMethodsInDocument method [.NET Framework debugging]
ms.assetid: c7ae84d6-81e8-4cb7-a1f9-d48b6cde5d79
topic_type:
- apiref
ms.openlocfilehash: 1f75594a479edbf2e0160c9d3543384c0cbf68a0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763689"
---
# <a name="isymunmanagedreader2getmethodsindocument-method"></a><span data-ttu-id="67b20-103">ISymUnmanagedReader2::GetMethodsInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="67b20-103">ISymUnmanagedReader2::GetMethodsInDocument Method</span></span>

<span data-ttu-id="67b20-104">Belirtilen belgede satır bilgilerine sahip her yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="67b20-104">Gets every method that has line information in the provided document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67b20-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="67b20-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodsInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is(cMethod),  
        length_is(*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67b20-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="67b20-106">Parameters</span></span>  

 `document`  
 <span data-ttu-id="67b20-107">'ndaki Belgeye yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="67b20-107">[in] A pointer to the document.</span></span>  
  
 `cMethod`  
 <span data-ttu-id="67b20-108">'ndaki `ULONG32` Dizi boyutunu belirten bir  `pRetVal` .</span><span class="sxs-lookup"><span data-stu-id="67b20-108">[in] A `ULONG32` that indicates the size of the  `pRetVal` array.</span></span>  
  
 `pcMethod`  
 <span data-ttu-id="67b20-109">dışı `ULONG32` Yöntemlerini içermesi için gereken arabelleğin boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="67b20-109">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the methods.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="67b20-110">dışı Yöntemleri alan arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="67b20-110">[out] A pointer to the buffer that receives the methods.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67b20-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="67b20-111">Return Value</span></span>  

 <span data-ttu-id="67b20-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="67b20-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67b20-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="67b20-113">Requirements</span></span>  

 <span data-ttu-id="67b20-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="67b20-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67b20-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67b20-115">See also</span></span>

- [<span data-ttu-id="67b20-116">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="67b20-116">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
