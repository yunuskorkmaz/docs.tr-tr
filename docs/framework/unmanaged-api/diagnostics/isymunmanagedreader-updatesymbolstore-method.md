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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e5ae097314a935bc06272c0e8febfbaad620f13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667641"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="82d73-102">ISymUnmanagedReader::UpdateSymbolStore Yöntemi</span><span class="sxs-lookup"><span data-stu-id="82d73-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="82d73-103">Mevcut simge deposu delta sembol deposu ile güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="82d73-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="82d73-104">Bu yöntem, özgün taşınabilir yürütülebilir (PE) dosya için deltaları eşleştirmek için Sembol deposundaki güncelleştirmek için Düzenle ve devam et senaryolarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="82d73-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82d73-105">Yalnızca birini belirtmeniz gerekir `filename` veya `pIStream` parametreleri, her ikisini birden değil.</span><span class="sxs-lookup"><span data-stu-id="82d73-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="82d73-106">Varsa `filename` belirtilirse, bu dosyada simgelerle sembol deposundaki güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="82d73-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="82d73-107">Varsa `pIStream` belirtilirse, depolama, verilerle güncelleştirilir <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="82d73-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82d73-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="82d73-108">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82d73-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="82d73-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="82d73-110">[in] Sembol deposu içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="82d73-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="82d73-111">[in] Alternatif olarak kullanılan dosya akışı `filename` parametresi.</span><span class="sxs-lookup"><span data-stu-id="82d73-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82d73-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="82d73-112">Return Value</span></span>  
 <span data-ttu-id="82d73-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="82d73-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82d73-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="82d73-114">Requirements</span></span>  
 <span data-ttu-id="82d73-115">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="82d73-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d73-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82d73-116">See also</span></span>
- [<span data-ttu-id="82d73-117">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="82d73-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
