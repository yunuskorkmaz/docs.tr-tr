---
description: 'Daha fazla bilgi edinin: Hatalı kayıt uzunluğu'
title: Hatalı kayıt uzunluğu
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 820597a3c4e157894aadb280ae141098cae7eed4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797061"
---
# <a name="bad-record-length"></a><span data-ttu-id="89064-103">Hatalı kayıt uzunluğu</span><span class="sxs-lookup"><span data-stu-id="89064-103">Bad record length</span></span>

<span data-ttu-id="89064-104">Bu hatanın olası nedenleri arasında:</span><span class="sxs-lookup"><span data-stu-id="89064-104">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="89064-105">,, Veya ifadesinde belirtilen bir kayıt değişkeninin uzunluğu `FileGet` , `FileGetObject` `FilePut` `FilePutObject` karşılık gelen bildirimde belirtilen uzunluktan farklı `FileOpen` .</span><span class="sxs-lookup"><span data-stu-id="89064-105">The length of a record variable specified in a `FileGet`, `FileGetObject`, `FilePut` or `FilePutObject` statement differs from the length specified in the corresponding `FileOpen` statement.</span></span>  
  
- <span data-ttu-id="89064-106">Or deyimindeki değişken veya `FilePut` `FilePutObject` değişken uzunluklu bir dize içeriyor.</span><span class="sxs-lookup"><span data-stu-id="89064-106">The variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string.</span></span>  
  
- <span data-ttu-id="89064-107">Veya içindeki değişkeni `FilePut` `FilePutObject` bir tür ya da içerir `Variant` .</span><span class="sxs-lookup"><span data-stu-id="89064-107">The variable in a `FilePut` or `FilePutObject` is or includes a `Variant` type.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="89064-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="89064-108">To correct this error</span></span>  
  
1. <span data-ttu-id="89064-109">Kayıt değişkeninin türünü tanımlayan Kullanıcı tanımlı türdeki sabit uzunluklu değişkenlerin değerlerinin toplamının `FileOpen` deyimin yan tümcesinde belirtilen değerle aynı olduğundan emin olun `Len` .</span><span class="sxs-lookup"><span data-stu-id="89064-109">Make sure the sum of the sizes of fixed-length variables in the user-defined type defining the record variable's type is the same as the value stated in the `FileOpen` statement's `Len` clause.</span></span>  
  
2. <span data-ttu-id="89064-110">`FilePut`Or deyimindeki değişken veya `FilePutObject` bir değişken uzunluklu dize içeriyorsa, değişken uzunluklu dizenin, `Len` deyimin yan tümcesinde belirtilen kayıt uzunluğundan en az 2 karakter daha kısa olduğundan emin olun `FileOpen` .</span><span class="sxs-lookup"><span data-stu-id="89064-110">If the variable in a `FilePut` or `FilePutObject` statement is or includes a variable-length string, make sure the variable-length string is at least 2 characters shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
3. <span data-ttu-id="89064-111">Ya da ' deki değişken `FilePut` veya `FilePutObject` içeriyorsa, `Variant` değişken uzunluklu dizenin en az 4 bayt olduğundan `Len` deyimin yan tümcesinde belirtilen kayıt uzunluğundan daha kısa olduğundan emin olun `FileOpen` .</span><span class="sxs-lookup"><span data-stu-id="89064-111">If the variable in a `FilePut` or `FilePutObject` is or includes a `Variant` make sure the variable-length string is at least 4 bytes shorter than the record length specified in the `Len` clause of the `FileOpen` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89064-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89064-112">See also</span></span>

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
