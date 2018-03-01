---
title: "XML açıklama özel olmalıdır bir &#39; cref &#39; özniteliği"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0c22c9cd9415faf17d027c3751d166662a92b50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a><span data-ttu-id="4fab5-102">XML açıklama özel olmalıdır bir &#39; cref &#39; özniteliği</span><span class="sxs-lookup"><span data-stu-id="4fab5-102">XML comment exception must have a &#39;cref&#39; attribute</span></span>
<span data-ttu-id="4fab5-103">\<Özel durum > etiketi yöntemi tarafından oluşturulan özel durumları belge için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="4fab5-103">The \<exception> tag provides a way to document the exceptions that may be thrown by a method.</span></span> <span data-ttu-id="4fab5-104">Gerekli `cref` özniteliği belgelerine Oluşturucu tarafından denetlenir bir üyenin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4fab5-104">The required `cref` attribute designates the name of a member, which is checked by the documentation generator.</span></span> <span data-ttu-id="4fab5-105">Üye varsa, belge dosyasındaki kurallı öğe adı için çevrilir.</span><span class="sxs-lookup"><span data-stu-id="4fab5-105">If the member exists, it is translated to the canonical element name in the documentation file.</span></span>  
  
 <span data-ttu-id="4fab5-106">**Hata Kimliği:** BC42319</span><span class="sxs-lookup"><span data-stu-id="4fab5-106">**Error ID:** BC42319</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4fab5-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4fab5-107">To correct this error</span></span>  
  
-   <span data-ttu-id="4fab5-108">Ekleme `cref` özniteliğini aşağıdaki gibi özel durumu:</span><span class="sxs-lookup"><span data-stu-id="4fab5-108">Add the `cref` attribute to the exception as follows:</span></span>  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4fab5-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4fab5-109">See Also</span></span>  
 [<span data-ttu-id="4fab5-110">\<Özel Durum ></span><span class="sxs-lookup"><span data-stu-id="4fab5-110">\<exception></span></span>](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [<span data-ttu-id="4fab5-111">Nasıl yapılır: XML belgesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="4fab5-111">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="4fab5-112">XML açıklama etiketleri</span><span class="sxs-lookup"><span data-stu-id="4fab5-112">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
