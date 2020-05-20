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
ms.openlocfilehash: f4f925282d65cd9cbc8eb1c8825f358602de68ed
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441701"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="8484e-102">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8484e-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="8484e-103">Yönetilmeyen kod için bir sembol cildi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8484e-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8484e-104">Güvenilmeyen bir kaynaktan program veritabanı (PDB) dosyasını açmak için bir güvenlik riskidir.</span><span class="sxs-lookup"><span data-stu-id="8484e-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8484e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8484e-105">Methods</span></span>  
  
|<span data-ttu-id="8484e-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8484e-106">Method</span></span>|<span data-ttu-id="8484e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8484e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8484e-108">GetReaderForFile Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8484e-108">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="8484e-109">Meta veri arabirimi ve bir dosya adı verildiğinde, modülle ilişkili hata ayıklama sembollerini okuyacak doğru [ıdimunmanagedreader](isymunmanagedreader-interface.md) yapısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="8484e-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="8484e-110">GetReaderFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8484e-110">GetReaderFromStream Method</span></span>](isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="8484e-111">Meta veri arabirimi ve sembol deposunu içeren bir akış verildiğinde, verilen sembol deposundan hata ayıklama sembollerini okuyan doğru [ıstreamunmanagedreader](isymunmanagedreader-interface.md) yapısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="8484e-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8484e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8484e-112">Requirements</span></span>  
 <span data-ttu-id="8484e-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8484e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8484e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8484e-114">See also</span></span>

- [<span data-ttu-id="8484e-115">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8484e-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="8484e-116">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8484e-116">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="8484e-117">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8484e-117">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
