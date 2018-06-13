---
title: '&lt;param&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: c992c96303eb1441eaf667693b7aefb5361b196c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602927"
---
# <a name="ltparamgt-visual-basic"></a><span data-ttu-id="943b1-102">&lt;param&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="943b1-102">&lt;param&gt; (Visual Basic)</span></span>
<span data-ttu-id="943b1-103">Bir parametre adı ve açıklama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="943b1-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="943b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="943b1-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="943b1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="943b1-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="943b1-106">Yöntem parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="943b1-106">The name of a method parameter.</span></span> <span data-ttu-id="943b1-107">Ad çift tırnak işaretleri içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="943b1-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="943b1-108">Parametresi için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="943b1-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="943b1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="943b1-109">Remarks</span></span>  
 <span data-ttu-id="943b1-110">`<param>` Etiketi açıklamasında bir yöntem bildirimi için parametrelerden biri yönteminde açıklamak için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="943b1-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="943b1-111">Metni `<param>` etiket aşağıdaki konumlarda görünecektir:</span><span class="sxs-lookup"><span data-stu-id="943b1-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="943b1-112">IntelliSense parametre bilgileri.</span><span class="sxs-lookup"><span data-stu-id="943b1-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="943b1-113">Daha fazla bilgi için bkz: [kullanarak IntelliSense](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="943b1-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="943b1-114">Nesne Tarayıcısı.</span><span class="sxs-lookup"><span data-stu-id="943b1-114">Object Browser.</span></span> <span data-ttu-id="943b1-115">Daha fazla bilgi için bkz: [kodunu yapısı görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="943b1-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="943b1-116">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="943b1-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="943b1-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="943b1-117">Example</span></span>  
 <span data-ttu-id="943b1-118">Bu örnekte `<param>` açıklamak için etiket `id` parametresi.</span><span class="sxs-lookup"><span data-stu-id="943b1-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="943b1-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="943b1-119">See Also</span></span>  
 [<span data-ttu-id="943b1-120">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="943b1-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
