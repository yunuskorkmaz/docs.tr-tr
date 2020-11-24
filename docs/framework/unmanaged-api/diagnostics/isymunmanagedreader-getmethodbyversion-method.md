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
ms.openlocfilehash: 64e6b9a1942e9a69e43de3d2f09564814328ec08
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689621"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="1ac17-102">ISymUnmanagedReader::GetMethodByVersion Metodu</span><span class="sxs-lookup"><span data-stu-id="1ac17-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>

<span data-ttu-id="1ac17-103">Yöntem belirteci ve bir düzenleme ve kopyalama sürümü numarası verilen bir sembol okuyucu yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="1ac17-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="1ac17-104">Sürüm numaraları 1 ' den başlar ve bir düzenleme ve kopyalama işleminin sonucu olarak yöntemin her değiştirildiği her seferinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="1ac17-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ac17-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1ac17-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ac17-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1ac17-106">Parameters</span></span>  

 `token`  
 <span data-ttu-id="1ac17-107">'ndaki Yöntem belirteci.</span><span class="sxs-lookup"><span data-stu-id="1ac17-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="1ac17-108">'ndaki Yöntem sürümü.</span><span class="sxs-lookup"><span data-stu-id="1ac17-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1ac17-109">dışı Döndürülen arabirime yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1ac17-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1ac17-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1ac17-110">Return Value</span></span>  

 <span data-ttu-id="1ac17-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1ac17-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ac17-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ac17-112">Requirements</span></span>  

 <span data-ttu-id="1ac17-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1ac17-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ac17-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ac17-114">See also</span></span>

- [<span data-ttu-id="1ac17-115">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ac17-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
