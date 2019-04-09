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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33213aced635549dd439cf679d89367a71baa7c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168811"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="9ce6d-102">ISymUnmanagedDocument Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ce6d-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="9ce6d-103">Bir sembol deposu tarafından başvurulan bir belgeyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9ce6d-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="9ce6d-104">Bir belge, bir Tekdüzen Kaynak Konum Belirleyicisi (URL) ve bir belge türü GUID ile tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9ce6d-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="9ce6d-105">URL'yi kullanarak nasıl depolanacağını bağımsız olarak belgeyi bulun ve belge türü GUID.</span><span class="sxs-lookup"><span data-stu-id="9ce6d-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="9ce6d-106">Belge kaynak sembolü deposuna ve bu arabirimi üzerinden alın.</span><span class="sxs-lookup"><span data-stu-id="9ce6d-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ce6d-107">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9ce6d-107">Methods</span></span>  
  
|<span data-ttu-id="9ce6d-108">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9ce6d-108">Method</span></span>|<span data-ttu-id="9ce6d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ce6d-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ce6d-110">FindClosestLine Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ce6d-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="9ce6d-111">Bir dizi noktası olmayabilir veya bu belgeyi bir satır verilen bir dizi noktası en yakın satır döndürür.</span><span class="sxs-lookup"><span data-stu-id="9ce6d-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="9ce6d-112">GetCheckSum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ce6d-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="9ce6d-113">Sağlama toplamı alır.</span><span class="sxs-lookup"><span data-stu-id="9ce6d-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="9ce6d-114">GetCheckSumAlgorithmId Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ce6d-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="9ce6d-115">Sağlama algoritması tanımlayıcısını alır veya hiç sağlama toplamı sıfırlardan GUİD'sini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9ce6d-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="9ce6d-116">GetDocumentType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ce6d-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="9ce6d-117">Bu belgenin belge türünü alır.</span><span class="sxs-lookup"><span data-stu-id="9ce6d-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="9ce6d-118">GetLanguage Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ce6d-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="9ce6d-119">Bu belgenin dil tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="9ce6d-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="9ce6d-120">GetLanguageVendor Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ce6d-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="9ce6d-121">Bu belgenin dil satıcı alır.</span><span class="sxs-lookup"><span data-stu-id="9ce6d-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="9ce6d-122">GetSourceLength Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ce6d-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="9ce6d-123">Katıştırılmış kaynak bayt cinsinden uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="9ce6d-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="9ce6d-124">GetSourceRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ce6d-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="9ce6d-125">Katıştırılmış kaynak Belirtilen aralıktaki belirli arabelleğe döndürür.</span><span class="sxs-lookup"><span data-stu-id="9ce6d-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="9ce6d-126">GetURL Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ce6d-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="9ce6d-127">Bu belge için URL'yi döndürür.</span><span class="sxs-lookup"><span data-stu-id="9ce6d-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="9ce6d-128">HasEmbeddedSource Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ce6d-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="9ce6d-129">Döndürür `true` hata ayıklama sembolleri; katıştırılmış kaynak belge varsa, aksi halde döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="9ce6d-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ce6d-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ce6d-130">See also</span></span>

- [<span data-ttu-id="9ce6d-131">Tanılama Sembol Deposu Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9ce6d-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
