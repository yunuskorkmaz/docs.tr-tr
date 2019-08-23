---
title: ISymUnmanagedReader::ReplaceSymbolStore Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8721f7c30061fbfd4a761bed090b761762c3c13c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939036"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="397df-102">ISymUnmanagedReader::ReplaceSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="397df-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="397df-103">Var olan sembol deposunu bir Delta sembol deposu ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="397df-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="397df-104">Bu yöntem [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) yöntemine benzerdir, ancak verilen Delta bir güncelleştirme yerine tam bir değişiklik olarak hareket eder.</span><span class="sxs-lookup"><span data-stu-id="397df-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="397df-105">`filename` Ya`pIStream` da parametrelerinden yalnızca birini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="397df-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="397df-106">`filename` Belirtilmişse, sembol deposu bu dosyadaki simgelerle güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="397df-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="397df-107">Belirtilmişse, mağaza <xref:System.Runtime.InteropServices.ComTypes.IStream>içindeki verilerle güncelleştirilir. `pIStream`</span><span class="sxs-lookup"><span data-stu-id="397df-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="397df-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="397df-108">Syntax</span></span>  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="397df-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="397df-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="397df-110">'ndaki Sembol deposunu içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="397df-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="397df-111">'ndaki `filename` Parametresi için alternatif olarak kullanılan dosya akışı.</span><span class="sxs-lookup"><span data-stu-id="397df-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="397df-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="397df-112">Return Value</span></span>  
 <span data-ttu-id="397df-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAıL veya diğer bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="397df-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="397df-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="397df-114">Requirements</span></span>  
 <span data-ttu-id="397df-115">**Üst bilgi** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="397df-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="397df-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="397df-116">See also</span></span>

- [<span data-ttu-id="397df-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="397df-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
