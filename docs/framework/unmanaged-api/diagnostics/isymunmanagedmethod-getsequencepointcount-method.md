---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedmethod:: GetSequencePointCount Yöntemi'
title: ISymUnmanagedMethod::GetSequencePointCount Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePointCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePointCount
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePointCount method [.NET Framework debugging]
- GetSequencePointCount method [.NET Framework debugging]
ms.assetid: 836133e8-6108-4b9b-b0a9-bce4e08dccda
topic_type:
- apiref
ms.openlocfilehash: 6e0341ddc151454de8764a47a92556ab1925bfa1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710015"
---
# <a name="isymunmanagedmethodgetsequencepointcount-method"></a><span data-ttu-id="ef12f-103">ISymUnmanagedMethod::GetSequencePointCount Metodu</span><span class="sxs-lookup"><span data-stu-id="ef12f-103">ISymUnmanagedMethod::GetSequencePointCount Method</span></span>

<span data-ttu-id="ef12f-104">Bu yöntemin içindeki sıra noktalarının sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="ef12f-104">Gets the count of sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef12f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef12f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePointCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef12f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ef12f-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="ef12f-107">dışı `ULONG32` Dizi noktalarını içermesi için gereken arabelleğin boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ef12f-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the sequence points.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef12f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ef12f-108">Return Value</span></span>  

 <span data-ttu-id="ef12f-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ef12f-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef12f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef12f-110">Requirements</span></span>  

 <span data-ttu-id="ef12f-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ef12f-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef12f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef12f-112">See also</span></span>

- [<span data-ttu-id="ef12f-113">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef12f-113">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
