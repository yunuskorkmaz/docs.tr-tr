---
description: 'Daha fazla bilgi edinin: ISymUnmanagedBinder3 Interface'
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
ms.openlocfilehash: 6d2172fb119076cea6d0f912fb3f403d36856599
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689839"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="a4175-103">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4175-103">ISymUnmanagedBinder3 Interface</span></span>

<span data-ttu-id="a4175-104">Sembol bağlayıcı arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="a4175-104">Extends the symbol binder interface.</span></span> <span data-ttu-id="a4175-105">Bu arabirimi `QueryInterface` arabirimini uygulayan bir nesne çağırarak edinin `ISymUnmanagedBinder` .</span><span class="sxs-lookup"><span data-stu-id="a4175-105">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a4175-106">Güvenilmeyen bir kaynaktan program veritabanı (PDB) dosyasını açmak için bir güvenlik riskidir.</span><span class="sxs-lookup"><span data-stu-id="a4175-106">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a4175-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a4175-107">Methods</span></span>  
  
|<span data-ttu-id="a4175-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a4175-108">Method</span></span>|<span data-ttu-id="a4175-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a4175-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a4175-110">GetReaderFromCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a4175-110">GetReaderFromCallback Method</span></span>](isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="a4175-111">Kullanıcının `IID_IDiaReadExeAtRVACallback` `IID_IDiaReadExeAtOffsetCallback` bellekten hata ayıklama dizini bilgilerini elde etmek için bir veya geri çağırma yoluyla veya sağlaması sağlar</span><span class="sxs-lookup"><span data-stu-id="a4175-111">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a4175-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a4175-112">Requirements</span></span>  

 <span data-ttu-id="a4175-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a4175-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4175-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4175-114">See also</span></span>

- [<span data-ttu-id="a4175-115">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a4175-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="a4175-116">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4175-116">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="a4175-117">ISymUnmanagedBinder2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a4175-117">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
