---
title: "Hatalı kayıt uzunluğu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 747d62cb41ef841b4486e0c7108c37a86929683e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-record-length"></a><span data-ttu-id="63740-102">Hatalı kayıt uzunluğu</span><span class="sxs-lookup"><span data-stu-id="63740-102">Bad record length</span></span>
<span data-ttu-id="63740-103">Bu hatanın olası nedenleri arasında şunlardır:</span><span class="sxs-lookup"><span data-stu-id="63740-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="63740-104">Belirtilen bir kayıt değişkeni uzunluğu bir `FileGet`, `FileGetObject`, `FilePut` veya `FilePutObject` deyimi farklı ilgili belirtilen uzunluk olarak `FileOpen` deyimi.</span><span class="sxs-lookup"><span data-stu-id="63740-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
-   <span data-ttu-id="63740-105">Değişken bir `FilePut` veya `FilePutObject` deyimi olduğu veya değişken uzunlukta bir dize içerir.</span><span class="sxs-lookup"><span data-stu-id="63740-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
-   <span data-ttu-id="63740-106">Değişken bir `FilePut` veya `FilePutObject` ya da içeren bir `Variant` türü.</span><span class="sxs-lookup"><span data-stu-id="63740-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="63740-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="63740-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="63740-108">Kayıt değişkenin türü tanımlama kullanıcı tanımlı türünde sabit uzunluklu değişkenlerin boyutlarının toplamıdır aynı değeri de belirtildiği gibi emin olun `FileOpen` deyiminin `Len` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="63740-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2.  <span data-ttu-id="63740-109">Varsa değişkenin bir `FilePut` veya `FilePutObject` deyimi olduğu veya değişken uzunlukta bir dize içeriyorsa, değişken uzunlukta bir dize en az 2 karakter belirtilen kayıt uzunluğundan daha kısa olduğundan emin olun `Len` yan tümcesi `FileOpen` deyimi.</span><span class="sxs-lookup"><span data-stu-id="63740-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3.  <span data-ttu-id="63740-110">Varsa değişken bir `FilePut` veya `FilePutObject` ya da içeren bir `Variant` değişken uzunlukta bir dize en az 4 bayt belirtilen kayıt uzunluğundan daha kısa olduğundan emin olun `Len` yan tümcesi `FileOpen` deyimi.</span><span class="sxs-lookup"><span data-stu-id="63740-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63740-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63740-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
