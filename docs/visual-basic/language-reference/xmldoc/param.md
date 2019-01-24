---
title: '&lt;param&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: cc9ceccef8123d49d6267276e9dcb7be84f78a01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670686"
---
# <a name="ltparamgt-visual-basic"></a><span data-ttu-id="de4cb-102">&lt;param&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de4cb-102">&lt;param&gt; (Visual Basic)</span></span>
<span data-ttu-id="de4cb-103">Bir parametre adı ve açıklama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="de4cb-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de4cb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de4cb-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de4cb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="de4cb-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="de4cb-106">Bir yöntem parametresi adı.</span><span class="sxs-lookup"><span data-stu-id="de4cb-106">The name of a method parameter.</span></span> <span data-ttu-id="de4cb-107">Adı çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="de4cb-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="de4cb-108">Parametre için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="de4cb-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de4cb-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de4cb-109">Remarks</span></span>  
 <span data-ttu-id="de4cb-110">`<param>` Etiket kullanılmalıdır yöntemi bildirimi için açıklama parametrelerden biri yöntemi tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="de4cb-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="de4cb-111">Metni `<param>` etiketi aşağıdaki konumlarda gösterilir:</span><span class="sxs-lookup"><span data-stu-id="de4cb-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="de4cb-112">IntelliSense, parametre bilgisi.</span><span class="sxs-lookup"><span data-stu-id="de4cb-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="de4cb-113">Daha fazla bilgi için [IntelliSense kullanarak](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="de4cb-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="de4cb-114">Nesne Tarayıcısı.</span><span class="sxs-lookup"><span data-stu-id="de4cb-114">Object Browser.</span></span> <span data-ttu-id="de4cb-115">Daha fazla bilgi için [Structure of Code görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="de4cb-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="de4cb-116">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="de4cb-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de4cb-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="de4cb-117">Example</span></span>  
 <span data-ttu-id="de4cb-118">Bu örnekte `<param>` açıklamak için etiket `id` parametresi.</span><span class="sxs-lookup"><span data-stu-id="de4cb-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="de4cb-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de4cb-119">See also</span></span>
- [<span data-ttu-id="de4cb-120">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="de4cb-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
