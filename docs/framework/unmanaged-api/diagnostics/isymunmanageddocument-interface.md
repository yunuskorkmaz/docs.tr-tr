---
description: 'Daha fazla bilgi edinin: ı, Unmanageddocument arabirimi'
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
ms.openlocfilehash: cd1907e570dd15ebcac3ee12aa09c626c9bb7787
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710146"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="4c398-103">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4c398-103">ISymUnmanagedDocument Interface</span></span>

<span data-ttu-id="4c398-104">Bir sembol deposu tarafından başvurulan bir belgeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="4c398-104">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="4c398-105">Belge, Tekdüzen Kaynak Bulucu (URL) ve belge türü GUID 'SI tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4c398-105">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="4c398-106">Belgeyi, URL ve belge türü GUID kullanılarak nasıl depolandığına bakılmaksızın bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c398-106">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="4c398-107">Belge kaynağını sembol deposunda depolayıp bu arabirim aracılığıyla alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c398-107">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c398-108">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4c398-108">Methods</span></span>  
  
|<span data-ttu-id="4c398-109">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4c398-109">Method</span></span>|<span data-ttu-id="4c398-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4c398-110">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c398-111">FindClosestLine Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c398-111">FindClosestLine Method</span></span>](isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="4c398-112">Bu belgede bir sıra noktası olabilecek veya olmayan bir satır verildiğinde, bir dizi noktası olan en yakın çizgiyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="4c398-112">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="4c398-113">GetCheckSum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c398-113">GetCheckSum Method</span></span>](isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="4c398-114">Sağlama toplamını alır.</span><span class="sxs-lookup"><span data-stu-id="4c398-114">Gets the checksum.</span></span>|  
|[<span data-ttu-id="4c398-115">GetCheckSumAlgorithmId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c398-115">GetCheckSumAlgorithmId Method</span></span>](isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="4c398-116">Sağlama toplamı algoritması tanımlayıcısını alır veya hiçbir sağlama toplamı yoksa tüm sıfırları GUID 'leri döndürür.</span><span class="sxs-lookup"><span data-stu-id="4c398-116">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="4c398-117">GetDocumentType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c398-117">GetDocumentType Method</span></span>](isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="4c398-118">Bu belgenin belge türünü alır.</span><span class="sxs-lookup"><span data-stu-id="4c398-118">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="4c398-119">GetLanguage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c398-119">GetLanguage Method</span></span>](isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="4c398-120">Bu belgenin dil tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="4c398-120">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="4c398-121">GetLanguageVendor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c398-121">GetLanguageVendor Method</span></span>](isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="4c398-122">Bu belgenin dil satıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="4c398-122">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="4c398-123">GetSourceLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c398-123">GetSourceLength Method</span></span>](isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="4c398-124">Gömülü kaynağın uzunluğunu bayt olarak alır.</span><span class="sxs-lookup"><span data-stu-id="4c398-124">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="4c398-125">GetSourceRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c398-125">GetSourceRange Method</span></span>](isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="4c398-126">Eklenmiş kaynağın belirtilen aralığını verilen arabelleğe döndürür.</span><span class="sxs-lookup"><span data-stu-id="4c398-126">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="4c398-127">GetURL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c398-127">GetURL Method</span></span>](isymunmanageddocument-geturl-method.md)|<span data-ttu-id="4c398-128">Bu belgenin URL 'sini döndürür.</span><span class="sxs-lookup"><span data-stu-id="4c398-128">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="4c398-129">HasEmbeddedSource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4c398-129">HasEmbeddedSource Method</span></span>](isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="4c398-130">`true`Belgenin hata ayıklama sembollerine katıştırılmış kaynak olup olmadığını döndürür; Aksi takdirde, döndürür `false` .</span><span class="sxs-lookup"><span data-stu-id="4c398-130">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c398-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c398-131">See also</span></span>

- [<span data-ttu-id="4c398-132">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4c398-132">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
