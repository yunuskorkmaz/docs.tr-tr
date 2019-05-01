---
title: Hatalı kayıt uzunluğu
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 1bc75303bcc2f46e54c06e89347da28997e59786
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935258"
---
# <a name="bad-record-length"></a><span data-ttu-id="84855-102">Hatalı kayıt uzunluğu</span><span class="sxs-lookup"><span data-stu-id="84855-102">Bad record length</span></span>
<span data-ttu-id="84855-103">Bu hatanın olası nedenleri arasında:</span><span class="sxs-lookup"><span data-stu-id="84855-103">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="84855-104">Belirtilen bir kayıt değişken uzunluğu bir `FileGet`, `FileGetObject`, `FilePut` veya `FilePutObject` deyimi, ilgili belirtilen uzunluğu farklıdır `FileOpen` deyimi.</span><span class="sxs-lookup"><span data-stu-id="84855-104">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
- <span data-ttu-id="84855-105">Değişkeninde bir `FilePut` veya `FilePutObject` deyimi olduğundan veya değişken uzunluklu bir dize içerir.</span><span class="sxs-lookup"><span data-stu-id="84855-105">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
- <span data-ttu-id="84855-106">Değişkeninde bir `FilePut` veya `FilePutObject` içerir ya da bir `Variant` türü.</span><span class="sxs-lookup"><span data-stu-id="84855-106">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="84855-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="84855-107">To correct this error</span></span>  
  
1. <span data-ttu-id="84855-108">Kayıt değişkenin türünü tanımlayan kullanıcı tanımlı tür, sabit uzunluklu değişkenlerin boyutlarının toplamı olduğundan, aynı, değeri bölümünde belirtildiği emin `FileOpen` deyimin `Len` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="84855-108">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2. <span data-ttu-id="84855-109">Varsa değişkeninde bir `FilePut` veya `FilePutObject` deyimi olduğunu veya bir değişken uzunluklu dize içeren, değişken uzunluklu dize en az 2 karakter belirtilen kayıt uzunluğu daha kısa olduğundan emin olun `Len` yan tümcesi `FileOpen` deyimi.</span><span class="sxs-lookup"><span data-stu-id="84855-109">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3. <span data-ttu-id="84855-110">Varsa değişkeninde bir `FilePut` veya `FilePutObject` içerir ya da bir `Variant` değişken uzunluklu dize en az 4 bayt belirtilen kayıt uzunluğu daha kısa olduğundan emin olun `Len` yan tümcesi `FileOpen` deyimi.</span><span class="sxs-lookup"><span data-stu-id="84855-110">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84855-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84855-111">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
