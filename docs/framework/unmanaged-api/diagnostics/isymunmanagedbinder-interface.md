---
title: ISymUnmanagedBinder Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder
helpviewer_keywords:
- ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type:
- apiref
ms.openlocfilehash: 554e59484f00626726f7f024c69e93a5e6647130
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727386"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="b45f3-102">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b45f3-102">ISymUnmanagedBinder Interface</span></span>

<span data-ttu-id="b45f3-103">Yönetilmeyen kod için bir sembol cildi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b45f3-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b45f3-104">Güvenilmeyen bir kaynaktan program veritabanı (PDB) dosyasını açmak için bir güvenlik riskidir.</span><span class="sxs-lookup"><span data-stu-id="b45f3-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b45f3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b45f3-105">Methods</span></span>  
  
|<span data-ttu-id="b45f3-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="b45f3-106">Method</span></span>|<span data-ttu-id="b45f3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b45f3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b45f3-108">GetReaderForFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b45f3-108">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="b45f3-109">Meta veri arabirimi ve bir dosya adı verildiğinde, modülle ilişkili hata ayıklama sembollerini okuyacak doğru [ıdimunmanagedreader](isymunmanagedreader-interface.md) yapısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="b45f3-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="b45f3-110">GetReaderFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b45f3-110">GetReaderFromStream Method</span></span>](isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="b45f3-111">Meta veri arabirimi ve sembol deposunu içeren bir akış verildiğinde, verilen sembol deposundan hata ayıklama sembollerini okuyan doğru [ıstreamunmanagedreader](isymunmanagedreader-interface.md) yapısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="b45f3-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b45f3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b45f3-112">Requirements</span></span>  

 <span data-ttu-id="b45f3-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="b45f3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b45f3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b45f3-114">See also</span></span>

- [<span data-ttu-id="b45f3-115">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b45f3-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="b45f3-116">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b45f3-116">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="b45f3-117">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b45f3-117">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
