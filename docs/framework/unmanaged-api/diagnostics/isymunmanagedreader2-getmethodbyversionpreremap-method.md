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
ms.openlocfilehash: 5484242562deaf463b7435ad4e54735a7abee45e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730493"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="bf75a-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Metodu</span><span class="sxs-lookup"><span data-stu-id="bf75a-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>

<span data-ttu-id="bf75a-103">Bir yöntem belirteci ve bir Düzenle ve devam et sürüm numarası verilen bir sembol okuyucu yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="bf75a-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="bf75a-104">Sürüm numaraları 1 ' den başlar ve bir düzenleme ve devam etme işleminin sonucu olarak yöntemin her değiştirildiği her seferinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="bf75a-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf75a-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bf75a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf75a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bf75a-106">Parameters</span></span>  

 `token`  
 <span data-ttu-id="bf75a-107">'ndaki Yöntem meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="bf75a-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="bf75a-108">'ndaki Yöntem sürümü.</span><span class="sxs-lookup"><span data-stu-id="bf75a-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="bf75a-109">dışı Döndürülen [ıdimunmanagedmethod](isymunmanagedmethod-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bf75a-109">[out] A pointer to the returned [ISymUnmanagedMethod](isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf75a-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bf75a-110">Return Value</span></span>  

 <span data-ttu-id="bf75a-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="bf75a-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf75a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf75a-112">Requirements</span></span>  

 <span data-ttu-id="bf75a-113">**Üst bilgi:** Corsya. IDL.</span><span class="sxs-lookup"><span data-stu-id="bf75a-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="bf75a-114">CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bf75a-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf75a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf75a-115">See also</span></span>

- [<span data-ttu-id="bf75a-116">ISymUnmanagedReader2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf75a-116">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
