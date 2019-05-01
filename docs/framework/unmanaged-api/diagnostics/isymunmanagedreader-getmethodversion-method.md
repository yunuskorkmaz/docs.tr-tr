---
title: ISymUnmanagedReader::GetMethodVersion Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5d4145e6c76cf95f2468a3f5ad59edcd310423e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993323"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="c3f64-102">ISymUnmanagedReader::GetMethodVersion Metodu</span><span class="sxs-lookup"><span data-stu-id="c3f64-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>
<span data-ttu-id="c3f64-103">Yöntem sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="c3f64-103">Gets the method version.</span></span> <span data-ttu-id="c3f64-104">Yöntemi sürüm 1 ile başlayan ve yöntem yeniden derlenen her zaman artırılır.</span><span class="sxs-lookup"><span data-stu-id="c3f64-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="c3f64-105">Yeniden derleme değişikliğe gerek kalmadan yönteme oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="c3f64-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3f64-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3f64-106">Syntax</span></span>  
  
```  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3f64-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3f64-107">Parameters</span></span>  
 `pMethod`  
 <span data-ttu-id="c3f64-108">[in] Hangi sürümü almak yöntem.</span><span class="sxs-lookup"><span data-stu-id="c3f64-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="c3f64-109">[out] Bir işaretçi bir değişkene yöntemi sürümünü alır.</span><span class="sxs-lookup"><span data-stu-id="c3f64-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3f64-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c3f64-110">Return Value</span></span>  
 <span data-ttu-id="c3f64-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c3f64-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3f64-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3f64-112">Requirements</span></span>  
 <span data-ttu-id="c3f64-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c3f64-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3f64-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3f64-114">See also</span></span>

- [<span data-ttu-id="c3f64-115">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3f64-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
