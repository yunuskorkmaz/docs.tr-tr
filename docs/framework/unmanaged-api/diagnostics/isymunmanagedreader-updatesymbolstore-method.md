---
title: ISymUnmanagedReader::UpdateSymbolStore Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.UpdateSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type:
- apiref
ms.openlocfilehash: ccc787aa1c820a486d9a513055c9c9834b90bd1a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615442"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="5bed4-102">ISymUnmanagedReader::UpdateSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5bed4-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="5bed4-103">Var olan sembol deposunu bir Delta sembol deposu ile güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="5bed4-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="5bed4-104">Bu yöntem, sembol deposunu değişimleri ile orijinal taşınabilir yürütülebilir (PE) dosyası eşleşecek şekilde güncelleştirmek için Düzenle ve devam et senaryolarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5bed4-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5bed4-105">Ya da parametrelerinden yalnızca birini belirtmeniz gerekir `filename` `pIStream` .</span><span class="sxs-lookup"><span data-stu-id="5bed4-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="5bed4-106">`filename`Belirtilmişse, sembol deposu bu dosyadaki simgelerle güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5bed4-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="5bed4-107">`pIStream`Belirtilmişse, mağaza içindeki verilerle güncelleştirilir <xref:System.Runtime.InteropServices.ComTypes.IStream> .</span><span class="sxs-lookup"><span data-stu-id="5bed4-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bed4-108">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5bed4-108">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bed4-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5bed4-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="5bed4-110">'ndaki Sembol deposunu içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="5bed4-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="5bed4-111">'ndaki Parametresi için alternatif olarak kullanılan dosya akışı `filename` .</span><span class="sxs-lookup"><span data-stu-id="5bed4-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bed4-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5bed4-112">Return Value</span></span>  
 <span data-ttu-id="5bed4-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5bed4-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bed4-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5bed4-114">Requirements</span></span>  
 <span data-ttu-id="5bed4-115">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5bed4-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bed4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bed4-116">See also</span></span>

- [<span data-ttu-id="5bed4-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5bed4-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
