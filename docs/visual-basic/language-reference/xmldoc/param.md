---
title: <param> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 476b3f4f6b85908897e15f73bc23d2b060e337c3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283653"
---
# <a name="param-visual-basic"></a><span data-ttu-id="34fe6-102">\<param > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34fe6-102">\<param> (Visual Basic)</span></span>
<span data-ttu-id="34fe6-103">Bir parametre adı ve açıklama tanımlar.</span><span class="sxs-lookup"><span data-stu-id="34fe6-103">Defines a parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34fe6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34fe6-104">Syntax</span></span>  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34fe6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34fe6-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="34fe6-106">Bir yöntem parametresi adı.</span><span class="sxs-lookup"><span data-stu-id="34fe6-106">The name of a method parameter.</span></span> <span data-ttu-id="34fe6-107">Adı çift tırnak içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="34fe6-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="34fe6-108">Parametre için bir açıklama.</span><span class="sxs-lookup"><span data-stu-id="34fe6-108">A description for the parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34fe6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="34fe6-109">Remarks</span></span>  
 <span data-ttu-id="34fe6-110">`<param>` Etiket kullanılmalıdır yöntemi bildirimi için açıklama parametrelerden biri yöntemi tanımlamak için.</span><span class="sxs-lookup"><span data-stu-id="34fe6-110">The `<param>` tag should be used in the comment for a method declaration to describe one of the parameters for the method.</span></span>  
  
 <span data-ttu-id="34fe6-111">Metni `<param>` etiketi aşağıdaki konumlarda gösterilir:</span><span class="sxs-lookup"><span data-stu-id="34fe6-111">The text for the `<param>` tag will appear in the following locations:</span></span>  
  
-   <span data-ttu-id="34fe6-112">IntelliSense, parametre bilgisi.</span><span class="sxs-lookup"><span data-stu-id="34fe6-112">Parameter Info of IntelliSense.</span></span> <span data-ttu-id="34fe6-113">Daha fazla bilgi için [IntelliSense kullanarak](/visualstudio/ide/using-intellisense).</span><span class="sxs-lookup"><span data-stu-id="34fe6-113">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>  
  
-   <span data-ttu-id="34fe6-114">Nesne Tarayıcısı.</span><span class="sxs-lookup"><span data-stu-id="34fe6-114">Object Browser.</span></span> <span data-ttu-id="34fe6-115">Daha fazla bilgi için [Structure of Code görüntüleme](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="34fe6-115">For more information, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="34fe6-116">Derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) işlem belgeleri açıklamaları için bir dosya için.</span><span class="sxs-lookup"><span data-stu-id="34fe6-116">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34fe6-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="34fe6-117">Example</span></span>  
 <span data-ttu-id="34fe6-118">Bu örnekte `<param>` açıklamak için etiket `id` parametresi.</span><span class="sxs-lookup"><span data-stu-id="34fe6-118">This example uses the `<param>` tag to describe the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="34fe6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34fe6-119">See also</span></span>
- [<span data-ttu-id="34fe6-120">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="34fe6-120">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
