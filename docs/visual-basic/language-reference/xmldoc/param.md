---
title: '&lt;param&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09c7473cd88a701d8e46251be9b1c268c2dc8805
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltparamgt-visual-basic"></a><span data-ttu-id="57f70-102">&lt;param&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57f70-102">&lt;param&gt; (Visual Basic)</span></span>
<span data-ttu-id="57f70-103">Bir parametre adı ve açıklama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="57f70-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57f70-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57f70-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57f70-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57f70-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="57f70-106">Yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="57f70-106">The name of a method parameter.</span></span> <span data-ttu-id="57f70-107">Ad çift tırnak işaretleri içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="57f70-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="57f70-108">Parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="57f70-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="57f70-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="57f70-109">Remarks</span></span>  
 <span data-ttu-id="57f70-110">`<param>` Etiketi açıklamasında bir yöntem bildirimi için parametrelerden biri yönteminde açıklamak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="57f70-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="57f70-111">Metni `<param>` etiket aşağıdaki konumlarda görünecektir:</span><span class="sxs-lookup"><span data-stu-id="57f70-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="57f70-112">IntelliSense parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="57f70-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="57f70-113">Daha fazla bilgi için bkz: [kullanarak IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="57f70-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="57f70-114">Nesne Tarayıcısı.</span><span class="sxs-lookup"><span data-stu-id="57f70-114">Object Browser.</span></span> <span data-ttu-id="57f70-115">Daha fazla bilgi için bkz: [kodunu yapısı görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="57f70-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="57f70-116">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="57f70-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57f70-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="57f70-117">Example</span></span>  
 <span data-ttu-id="57f70-118">Bu örnekte `<param>` açıklamak için etiket `id` parametresi.</span><span class="sxs-lookup"><span data-stu-id="57f70-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="57f70-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="57f70-119">See Also</span></span>  
 [<span data-ttu-id="57f70-120">XML açıklama etiketleri</span><span class="sxs-lookup"><span data-stu-id="57f70-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
