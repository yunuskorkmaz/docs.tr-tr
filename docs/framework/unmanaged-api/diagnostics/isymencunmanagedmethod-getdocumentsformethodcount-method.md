---
description: 'Şu konuda daha fazla bilgi edinin: ISymENCUnmanagedMethod:: GetDocumentsForMethodCount yöntemi'
title: ISymENCUnmanagedMethod::GetDocumentsForMethodCount Metodu
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethodCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount
helpviewer_keywords:
- GetDocumentsForMethodCount method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount method [.NET Framework debugging]
ms.assetid: cc1a823a-3ff3-4a33-b641-96edc93d2b17
topic_type:
- apiref
ms.openlocfilehash: 0594771c544ad1de32531e92f30fe96f245b5699
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738019"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="52eec-103">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Metodu</span><span class="sxs-lookup"><span data-stu-id="52eec-103">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>

<span data-ttu-id="52eec-104">Bu yöntemin içinde satır bulunan belge sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="52eec-104">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52eec-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52eec-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52eec-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52eec-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="52eec-107">dışı `ULONG32` Belgeleri içermesi için gereken arabelleğin boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="52eec-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52eec-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="52eec-108">Return Value</span></span>  

 <span data-ttu-id="52eec-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="52eec-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52eec-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52eec-110">Requirements</span></span>  

 <span data-ttu-id="52eec-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="52eec-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52eec-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52eec-112">See also</span></span>

- [<span data-ttu-id="52eec-113">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52eec-113">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
