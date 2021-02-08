---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedreader:: GetMethodByVersion yöntemi'
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
ms.openlocfilehash: 6b2fa3ff3af91d59bb79029d039e5656610bebff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772074"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="5bfd7-103">ISymUnmanagedReader::GetMethodByVersion Metodu</span><span class="sxs-lookup"><span data-stu-id="5bfd7-103">ISymUnmanagedReader::GetMethodByVersion Method</span></span>

<span data-ttu-id="5bfd7-104">Yöntem belirteci ve bir düzenleme ve kopyalama sürümü numarası verilen bir sembol okuyucu yöntemi alır.</span><span class="sxs-lookup"><span data-stu-id="5bfd7-104">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="5bfd7-105">Sürüm numaraları 1 ' den başlar ve bir düzenleme ve kopyalama işleminin sonucu olarak yöntemin her değiştirildiği her seferinde artırılır.</span><span class="sxs-lookup"><span data-stu-id="5bfd7-105">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bfd7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bfd7-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bfd7-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5bfd7-107">Parameters</span></span>  

 `token`  
 <span data-ttu-id="5bfd7-108">'ndaki Yöntem belirteci.</span><span class="sxs-lookup"><span data-stu-id="5bfd7-108">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="5bfd7-109">'ndaki Yöntem sürümü.</span><span class="sxs-lookup"><span data-stu-id="5bfd7-109">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="5bfd7-110">dışı Döndürülen arabirime yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5bfd7-110">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bfd7-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5bfd7-111">Return Value</span></span>  

 <span data-ttu-id="5bfd7-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5bfd7-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bfd7-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5bfd7-113">Requirements</span></span>  

 <span data-ttu-id="5bfd7-114">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5bfd7-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bfd7-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bfd7-115">See also</span></span>

- [<span data-ttu-id="5bfd7-116">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5bfd7-116">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
