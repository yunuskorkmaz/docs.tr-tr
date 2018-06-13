---
title: Hatalı kayıt uzunluğu
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: b4b311e2eb504c485772091ed126b3beb71729cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585976"
---
# <a name="bad-record-length"></a><span data-ttu-id="27325-102">Hatalı kayıt uzunluğu</span><span class="sxs-lookup"><span data-stu-id="27325-102">Bad record length</span></span>
<span data-ttu-id="27325-103">Bu hatanın olası nedenleri arasında şunlardır:</span><span class="sxs-lookup"><span data-stu-id="27325-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="27325-104">Belirtilen bir kayıt değişkeni uzunluğu bir `FileGet`, `FileGetObject`, `FilePut` veya `FilePutObject` deyimi farklı ilgili belirtilen uzunluk olarak `FileOpen` deyimi.</span><span class="sxs-lookup"><span data-stu-id="27325-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
-   <span data-ttu-id="27325-105">Değişken bir `FilePut` veya `FilePutObject` deyimi olduğu veya değişken uzunlukta bir dize içerir.</span><span class="sxs-lookup"><span data-stu-id="27325-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
-   <span data-ttu-id="27325-106">Değişken bir `FilePut` veya `FilePutObject` ya da içeren bir `Variant` türü.</span><span class="sxs-lookup"><span data-stu-id="27325-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="27325-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="27325-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="27325-108">Kayıt değişkenin türü tanımlama kullanıcı tanımlı türünde sabit uzunluklu değişkenlerin boyutlarının toplamıdır aynı değeri de belirtildiği gibi emin olun `FileOpen` deyiminin `Len` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="27325-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2.  <span data-ttu-id="27325-109">Varsa değişkenin bir `FilePut` veya `FilePutObject` deyimi olduğu veya değişken uzunlukta bir dize içeriyorsa, değişken uzunlukta bir dize en az 2 karakter belirtilen kayıt uzunluğundan daha kısa olduğundan emin olun `Len` yan tümcesi `FileOpen` deyimi.</span><span class="sxs-lookup"><span data-stu-id="27325-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3.  <span data-ttu-id="27325-110">Varsa değişken bir `FilePut` veya `FilePutObject` ya da içeren bir `Variant` değişken uzunlukta bir dize en az 4 bayt belirtilen kayıt uzunluğundan daha kısa olduğundan emin olun `Len` yan tümcesi `FileOpen` deyimi.</span><span class="sxs-lookup"><span data-stu-id="27325-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27325-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="27325-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>  
 <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
