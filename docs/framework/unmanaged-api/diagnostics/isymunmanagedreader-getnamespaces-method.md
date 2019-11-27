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
ms.openlocfilehash: 458faedea418e626a6494ca2afcdbf0e034472e8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447738"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="b4f51-102">ISymUnmanagedReader::GetNamespaces Metodu</span><span class="sxs-lookup"><span data-stu-id="b4f51-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="b4f51-103">Bu sembol deposu içindeki genel kapsamda tanımlanan ad alanlarını alır.</span><span class="sxs-lookup"><span data-stu-id="b4f51-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4f51-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4f51-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4f51-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b4f51-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="b4f51-106">'ndaki Ad alanları dizisinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="b4f51-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="b4f51-107">dışı Ad alanı listesinin uzunluğunu alan bir değişken işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b4f51-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="b4f51-108">dışı Ad alanı listesini alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b4f51-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4f51-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b4f51-109">Return Value</span></span>  
 <span data-ttu-id="b4f51-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b4f51-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4f51-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4f51-111">Requirements</span></span>  
 <span data-ttu-id="b4f51-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b4f51-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f51-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4f51-113">See also</span></span>

- [<span data-ttu-id="b4f51-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4f51-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
