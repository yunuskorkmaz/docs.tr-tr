---
title: '&lt;verir&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6130a6fabe450900fe19ef4d361654508f907ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltreturnsgt-visual-basic"></a><span data-ttu-id="2ee70-102">&lt;verir&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ee70-102">&lt;returns&gt; (Visual Basic)</span></span>
<span data-ttu-id="2ee70-103">Özellik veya işlev dönüş değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="2ee70-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ee70-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2ee70-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2ee70-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ee70-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="2ee70-106">Dönüş değeri açıklaması.</span><span class="sxs-lookup"><span data-stu-id="2ee70-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ee70-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ee70-107">Remarks</span></span>  
 <span data-ttu-id="2ee70-108">Kullanım `<returns>` dönüş değeri tanımlamak bir yöntem bildirimi açıklamasını etiketinde.</span><span class="sxs-lookup"><span data-stu-id="2ee70-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="2ee70-109">İle derleme [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) bir dosyaya işlem belgesi açıklamaları için.</span><span class="sxs-lookup"><span data-stu-id="2ee70-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ee70-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="2ee70-110">Example</span></span>  
 <span data-ttu-id="2ee70-111">Bu örnekte `<returns>` ne açıklamak için etiket `DoesRecordExist` işlev döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ee70-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2ee70-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ee70-112">See Also</span></span>  
 [<span data-ttu-id="2ee70-113">XML açıklama etiketleri</span><span class="sxs-lookup"><span data-stu-id="2ee70-113">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
