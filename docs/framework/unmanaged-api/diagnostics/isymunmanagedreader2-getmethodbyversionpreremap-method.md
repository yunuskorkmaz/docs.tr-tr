---
title: ISymUnmanagedReader2::GetMethodByVersionPreRemap Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e84d912a96752a893230393b59496377b783956
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494918"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="ae7ca-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Metodu</span><span class="sxs-lookup"><span data-stu-id="ae7ca-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="ae7ca-103">Bir sembol okuyucu yöntemi verilen token metody ve bir Düzenle ve devam et sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="ae7ca-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="ae7ca-104">Sürüm numaraları 1'den başlar ve yöntemi Düzenle ve devam et bir işlemin sonucunda her değiştirildiğinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="ae7ca-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae7ca-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae7ca-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae7ca-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae7ca-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="ae7ca-107">[in] Yöntem meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="ae7ca-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="ae7ca-108">[in] Yöntemi sürümü.</span><span class="sxs-lookup"><span data-stu-id="ae7ca-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ae7ca-109">[out] Döndürülen işaretçi [Isymunmanagedmethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ae7ca-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae7ca-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ae7ca-110">Return Value</span></span>  
 <span data-ttu-id="ae7ca-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ae7ca-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae7ca-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae7ca-112">Requirements</span></span>  
 <span data-ttu-id="ae7ca-113">**Üst bilgi:** CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="ae7ca-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="ae7ca-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ae7ca-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae7ca-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae7ca-115">See also</span></span>
- [<span data-ttu-id="ae7ca-116">ISymUnmanagedReader2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae7ca-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
