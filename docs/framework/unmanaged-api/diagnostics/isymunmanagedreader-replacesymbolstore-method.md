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
ms.openlocfilehash: db2137146ded5200e05bbf88e23ae599f3eb7dec
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615455"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="57fa6-102">ISymUnmanagedReader::ReplaceSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57fa6-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="57fa6-103">Var olan sembol deposunu bir Delta sembol deposu ile değiştirir.</span><span class="sxs-lookup"><span data-stu-id="57fa6-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="57fa6-104">Bu yöntem [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) yöntemine benzerdir, ancak verilen Delta bir güncelleştirme yerine tam bir değişiklik olarak hareket eder.</span><span class="sxs-lookup"><span data-stu-id="57fa6-104">This method is similar to the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57fa6-105">Ya da parametrelerinden yalnızca birini belirtmeniz gerekir `filename` `pIStream` .</span><span class="sxs-lookup"><span data-stu-id="57fa6-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="57fa6-106">`filename`Belirtilmişse, sembol deposu bu dosyadaki simgelerle güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="57fa6-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="57fa6-107">`pIStream`Belirtilmişse, mağaza içindeki verilerle güncelleştirilir <xref:System.Runtime.InteropServices.ComTypes.IStream> .</span><span class="sxs-lookup"><span data-stu-id="57fa6-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57fa6-108">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="57fa6-108">Syntax</span></span>  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57fa6-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57fa6-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="57fa6-110">'ndaki Sembol deposunu içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="57fa6-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="57fa6-111">'ndaki Parametresi için alternatif olarak kullanılan dosya akışı `filename` .</span><span class="sxs-lookup"><span data-stu-id="57fa6-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57fa6-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="57fa6-112">Return Value</span></span>  
 <span data-ttu-id="57fa6-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="57fa6-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57fa6-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57fa6-114">Requirements</span></span>  
 <span data-ttu-id="57fa6-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="57fa6-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57fa6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57fa6-116">See also</span></span>

- [<span data-ttu-id="57fa6-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57fa6-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
