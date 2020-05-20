---
title: ISymUnmanagedReader::GetNamespaces Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type:
- apiref
ms.openlocfilehash: 44f9284f0a89f0941940cf379c48b2b138149122
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614948"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="7e769-102">ISymUnmanagedReader::GetNamespaces Metodu</span><span class="sxs-lookup"><span data-stu-id="7e769-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="7e769-103">Bu sembol deposu içindeki genel kapsamda tanımlanan ad alanlarını alır.</span><span class="sxs-lookup"><span data-stu-id="7e769-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e769-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7e769-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e769-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7e769-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="7e769-106">'ndaki Ad alanları dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="7e769-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="7e769-107">dışı Ad alanı listesinin uzunluğunu alan bir değişken işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="7e769-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="7e769-108">dışı Ad alanı listesini alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7e769-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7e769-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7e769-109">Return Value</span></span>  
 <span data-ttu-id="7e769-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="7e769-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e769-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e769-111">Requirements</span></span>  
 <span data-ttu-id="7e769-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7e769-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e769-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e769-113">See also</span></span>

- [<span data-ttu-id="7e769-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e769-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
