---
title: ISymUnmanagedDocument Arabirimi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
ms.openlocfilehash: 3fa7b6b19d81e374cdb09b07ec181a7f4249a5eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449099"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="6bc09-102">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6bc09-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="6bc09-103">Bir sembol deposu tarafından başvurulan bir belgeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6bc09-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="6bc09-104">Belge, Tekdüzen Kaynak Bulucu (URL) ve belge türü GUID 'SI tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="6bc09-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="6bc09-105">Belgeyi, URL ve belge türü GUID kullanılarak nasıl depolandığına bakılmaksızın bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bc09-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="6bc09-106">Belge kaynağını sembol deposunda depolayıp bu arabirim aracılığıyla alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6bc09-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6bc09-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6bc09-107">Methods</span></span>  
  
|<span data-ttu-id="6bc09-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6bc09-108">Method</span></span>|<span data-ttu-id="6bc09-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6bc09-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6bc09-110">FindClosestLine Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bc09-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="6bc09-111">Bu belgede bir sıra noktası olabilecek veya olmayan bir satır verildiğinde, bir dizi noktası olan en yakın çizgiyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="6bc09-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="6bc09-112">GetCheckSum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bc09-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="6bc09-113">Sağlama toplamını alır.</span><span class="sxs-lookup"><span data-stu-id="6bc09-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="6bc09-114">GetCheckSumAlgorithmId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bc09-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="6bc09-115">Sağlama toplamı algoritması tanımlayıcısını alır veya hiçbir sağlama toplamı yoksa tüm sıfırları GUID 'leri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6bc09-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="6bc09-116">GetDocumentType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bc09-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="6bc09-117">Bu belgenin belge türünü alır.</span><span class="sxs-lookup"><span data-stu-id="6bc09-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="6bc09-118">GetLanguage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bc09-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="6bc09-119">Bu belgenin dil tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="6bc09-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="6bc09-120">GetLanguageVendor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bc09-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="6bc09-121">Bu belgenin dil satıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="6bc09-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="6bc09-122">GetSourceLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bc09-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="6bc09-123">Gömülü kaynağın uzunluğunu bayt olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6bc09-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="6bc09-124">GetSourceRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bc09-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="6bc09-125">Eklenmiş kaynağın belirtilen aralığını verilen arabelleğe döndürür.</span><span class="sxs-lookup"><span data-stu-id="6bc09-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="6bc09-126">GetURL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bc09-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="6bc09-127">Bu belgenin URL 'sini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6bc09-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="6bc09-128">HasEmbeddedSource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bc09-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="6bc09-129">Belge hata ayıklama sembollerine katıştırılmış kaynak içeriyorsa `true` döndürür; Aksi takdirde, `false`döndürür.</span><span class="sxs-lookup"><span data-stu-id="6bc09-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6bc09-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bc09-130">See also</span></span>

- [<span data-ttu-id="6bc09-131">Tanılama Simge Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6bc09-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
