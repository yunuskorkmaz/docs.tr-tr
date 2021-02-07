---
description: 'Daha fazla bilgi edinin: ISymUnmanagedReader2:: GetMethodByVersionPreRemap Yöntemi'
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
ms.openlocfilehash: b827821f529b9917c6bbb3452f0c3fe3283f1ee9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763728"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="1ed6c-103">ISymUnmanagedReader2::GetMethodByVersionPreRemap Metodu</span><span class="sxs-lookup"><span data-stu-id="1ed6c-103">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>

<span data-ttu-id="1ed6c-104">Bir yöntem belirteci ve bir Düzenle ve devam et sürüm numarası verilen bir sembol okuyucu yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-104">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="1ed6c-105">Sürüm numaraları 1 ' den başlar ve bir düzenleme ve devam etme işleminin sonucu olarak yöntemin her değiştirildiği her seferinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-105">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ed6c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1ed6c-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ed6c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ed6c-107">Parameters</span></span>  

 `token`  
 <span data-ttu-id="1ed6c-108">'ndaki Yöntem meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-108">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="1ed6c-109">'ndaki Yöntem sürümü.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-109">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1ed6c-110">dışı Döndürülen [ıdimunmanagedmethod](isymunmanagedmethod-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-110">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ed6c-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1ed6c-111">Return Value</span></span>  

 <span data-ttu-id="1ed6c-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ed6c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ed6c-113">Requirements</span></span>  

 <span data-ttu-id="1ed6c-114">**Üst bilgi:** Corsya. IDL.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-114">**Header:** CorSym.idl.</span></span> <span data-ttu-id="1ed6c-115">CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1ed6c-115">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ed6c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ed6c-116">See also</span></span>

- [<span data-ttu-id="1ed6c-117">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ed6c-117">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
