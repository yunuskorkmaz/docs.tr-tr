---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanageddocument:: GetCheckSum yöntemi'
title: ISymUnmanagedDocument::GetCheckSum Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
ms.openlocfilehash: 9f9a42e58b22661a2233fcb457b9b42b0d6a3d1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737694"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="2d7df-103">ISymUnmanagedDocument::GetCheckSum Metodu</span><span class="sxs-lookup"><span data-stu-id="2d7df-103">ISymUnmanagedDocument::GetCheckSum Method</span></span>

<span data-ttu-id="2d7df-104">Sağlama toplamını alır.</span><span class="sxs-lookup"><span data-stu-id="2d7df-104">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d7df-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d7df-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d7df-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d7df-106">Parameters</span></span>  

 `cData`  
 <span data-ttu-id="2d7df-107">'ndaki Parametre tarafından belirtilen arabelleğin uzunluğu `data`</span><span class="sxs-lookup"><span data-stu-id="2d7df-107">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="2d7df-108">dışı Sağlama toplamı için bayt cinsinden boyut ve uzunluk.</span><span class="sxs-lookup"><span data-stu-id="2d7df-108">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="2d7df-109">dışı Sağlama toplamını alan arabellek.</span><span class="sxs-lookup"><span data-stu-id="2d7df-109">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d7df-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2d7df-110">Return Value</span></span>  

 <span data-ttu-id="2d7df-111">Yöntem başarılı olursa S_OK; Aksi takdirde, bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2d7df-111">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d7df-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d7df-112">See also</span></span>

- [<span data-ttu-id="2d7df-113">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d7df-113">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
