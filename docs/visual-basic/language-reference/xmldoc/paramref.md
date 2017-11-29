---
title: '&lt;paramref&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3bf3d4f04997a03f442cf7fd2a1586604198d3fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltparamrefgt-visual-basic"></a><span data-ttu-id="3f873-102">&lt;paramref&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f873-102">&lt;paramref&gt; (Visual Basic)</span></span>
<span data-ttu-id="3f873-103">Bir word parametre olarak biçimlendirir.</span><span class="sxs-lookup"><span data-stu-id="3f873-103">Formats a word as a parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f873-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f873-104">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f873-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3f873-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="3f873-106">Başvurmak için parametresinin adı.</span><span class="sxs-lookup"><span data-stu-id="3f873-106">The name of the parameter to refer to.</span></span> <span data-ttu-id="3f873-107">Ad çift tırnak işaretleri içine alın ("").</span><span class="sxs-lookup"><span data-stu-id="3f873-107">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f873-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3f873-108">Remarks</span></span>  
 <span data-ttu-id="3f873-109">`<paramref>` Etiketi bir sözcük bir parametre olduğunu belirtmek için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="3f873-109">The `<paramref>` tag gives you a way to indicate that a word is a parameter.</span></span> <span data-ttu-id="3f873-110">XML dosyası, bu parametre farklı bir biçimde biçimlendirmek için işlenebilir.</span><span class="sxs-lookup"><span data-stu-id="3f873-110">The XML file can be processed to format this parameter in some distinct way.</span></span>  
  
 <span data-ttu-id="3f873-111">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="3f873-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f873-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="3f873-112">Example</span></span>  
 <span data-ttu-id="3f873-113">Bu örnekte `<paramref>` başvurmak için etiket `id` parametresi.</span><span class="sxs-lookup"><span data-stu-id="3f873-113">This example uses the `<paramref>` tag to refer to the `id` parameter.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="3f873-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f873-114">See Also</span></span>  
 [<span data-ttu-id="3f873-115">XML açıklama etiketleri</span><span class="sxs-lookup"><span data-stu-id="3f873-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
