---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: GetMethod yöntemi'
title: ISymUnmanagedReader::GetMethod Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedReader interface [.NET Framework debugging]
- ISymUnmanagedReader::GetMethod method [.NET Framework debugging]
ms.assetid: ae6cfb29-bc2c-4606-af86-1d32ebd31020
topic_type:
- apiref
ms.openlocfilehash: 7c0bb65840a3bc1c9450ad29fa8438cdb0377a16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689501"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="2bb15-103">ISymUnmanagedReader::GetMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2bb15-103">ISymUnmanagedReader::GetMethod Method</span></span>

<span data-ttu-id="2bb15-104">Yöntem belirteci verilen bir sembol okuyucu yöntemini alır.</span><span class="sxs-lookup"><span data-stu-id="2bb15-104">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bb15-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2bb15-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2bb15-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2bb15-106">Parameters</span></span>  

 `token`  
 <span data-ttu-id="2bb15-107">'ndaki Yöntem belirteci.</span><span class="sxs-lookup"><span data-stu-id="2bb15-107">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="2bb15-108">dışı Döndürülen arabirime yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2bb15-108">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2bb15-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2bb15-109">Return Value</span></span>  

 <span data-ttu-id="2bb15-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2bb15-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bb15-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2bb15-111">Requirements</span></span>  

 <span data-ttu-id="2bb15-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2bb15-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bb15-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bb15-113">See also</span></span>

- [<span data-ttu-id="2bb15-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2bb15-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
