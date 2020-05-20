---
title: ISymUnmanagedBinder3 Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
ms.openlocfilehash: 5a26de2a8f5439b7c81560927c991d449e57b76c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441597"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="7dec6-102">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7dec6-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="7dec6-103">Sembol bağlayıcı arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="7dec6-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="7dec6-104">Bu arabirimi `QueryInterface` arabirimini uygulayan bir nesne çağırarak edinin `ISymUnmanagedBinder` .</span><span class="sxs-lookup"><span data-stu-id="7dec6-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7dec6-105">Güvenilmeyen bir kaynaktan program veritabanı (PDB) dosyasını açmak için bir güvenlik riskidir.</span><span class="sxs-lookup"><span data-stu-id="7dec6-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7dec6-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7dec6-106">Methods</span></span>  
  
|<span data-ttu-id="7dec6-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7dec6-107">Method</span></span>|<span data-ttu-id="7dec6-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7dec6-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7dec6-109">GetReaderFromCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7dec6-109">GetReaderFromCallback Method</span></span>](isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="7dec6-110">Kullanıcının `IID_IDiaReadExeAtRVACallback` `IID_IDiaReadExeAtOffsetCallback` bellekten hata ayıklama dizini bilgilerini elde etmek için bir veya geri çağırma yoluyla veya sağlaması sağlar</span><span class="sxs-lookup"><span data-stu-id="7dec6-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7dec6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7dec6-111">Requirements</span></span>  
 <span data-ttu-id="7dec6-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7dec6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dec6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7dec6-113">See also</span></span>

- [<span data-ttu-id="7dec6-114">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7dec6-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="7dec6-115">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7dec6-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="7dec6-116">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7dec6-116">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
