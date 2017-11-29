---
title: '&lt;typeparam&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b654fe6fc93642693730256b523fee999aa55937
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="lttypeparamgt-visual-basic"></a><span data-ttu-id="d8ed3-102">&lt;typeparam&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8ed3-102">&lt;typeparam&gt; (Visual Basic)</span></span>
<span data-ttu-id="d8ed3-103">Bir parametre adı ve açıklama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d8ed3-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8ed3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8ed3-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8ed3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8ed3-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="d8ed3-106">Tür parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="d8ed3-106">The name of the type parameter.</span></span> <span data-ttu-id="d8ed3-107">Ad çift tırnak işaretleri içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="d8ed3-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="d8ed3-108">Tür parametresi açıklaması.</span><span class="sxs-lookup"><span data-stu-id="d8ed3-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8ed3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8ed3-109">Remarks</span></span>  
 <span data-ttu-id="d8ed3-110">Kullanım `<typeparam>` genel türü ya da Genel üye bildirimi türü parametrelerden biri açıklamak açıklama etiketinde.</span><span class="sxs-lookup"><span data-stu-id="d8ed3-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="d8ed3-111">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="d8ed3-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8ed3-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8ed3-112">Example</span></span>  
 <span data-ttu-id="d8ed3-113">Bu örnekte `<typeparam>` açıklamak için etiket `id` parametresi.</span><span class="sxs-lookup"><span data-stu-id="d8ed3-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d8ed3-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8ed3-114">See Also</span></span>  
 [<span data-ttu-id="d8ed3-115">XML açıklama etiketleri</span><span class="sxs-lookup"><span data-stu-id="d8ed3-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
