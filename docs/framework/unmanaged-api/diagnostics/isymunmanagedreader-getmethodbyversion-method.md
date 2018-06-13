---
title: ISymUnmanagedReader::GetMethodByVersion Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef5888c33e9532e5fc132fe571d59699d6f80c49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425185"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="788f2-102">ISymUnmanagedReader::GetMethodByVersion Metodu</span><span class="sxs-lookup"><span data-stu-id="788f2-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="788f2-103">Bir simge okuyucu yöntemi, verilen bir yöntem belirteci ve düzenleme ve kopyalama sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="788f2-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="788f2-104">Sürüm numaraları 1'den başlar ve bir düzenleme ve kopyalama işlemi sonucunda yöntemi her değiştirildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="788f2-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="788f2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="788f2-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="788f2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="788f2-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="788f2-107">[in] Yöntem simgesi.</span><span class="sxs-lookup"><span data-stu-id="788f2-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="788f2-108">[in] Yöntem sürümü.</span><span class="sxs-lookup"><span data-stu-id="788f2-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="788f2-109">[out] Döndürülen arabirimi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="788f2-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="788f2-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="788f2-110">Return Value</span></span>  
 <span data-ttu-id="788f2-111">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="788f2-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="788f2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="788f2-112">Requirements</span></span>  
 <span data-ttu-id="788f2-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="788f2-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="788f2-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="788f2-114">See Also</span></span>  
 [<span data-ttu-id="788f2-115">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="788f2-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
