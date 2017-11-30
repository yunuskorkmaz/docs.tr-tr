---
title: "Nasıl yapılır: Tarihleri veya Saatleri Temsil Eden Dizeleri Doğrulama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ed3201ef2bbef97eebbafa5ef128ca015adac013
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="cc5dc-102">Nasıl yapılır: Tarihleri veya Saatleri Temsil Eden Dizeleri Doğrulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc5dc-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="cc5dc-103">Aşağıdaki örnek kod bir `Boolean` bir dizenin geçerli bir tarih veya saat temsil edip etmediğini gösteren değer.</span><span class="sxs-lookup"><span data-stu-id="cc5dc-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc5dc-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc5dc-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cc5dc-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="cc5dc-105">Compiling the Code</span></span>  
 <span data-ttu-id="cc5dc-106">Değiştir `("01/01/03")` ve `"9:30 PM"` doğrulamak istediğiniz saat ve tarihi ile.</span><span class="sxs-lookup"><span data-stu-id="cc5dc-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="cc5dc-107">İle başka bir sabit kodlanmış dize dizesiyle değiştirin bir `String` değişkenine veya farklı bir yöntemle bir dize gibi döndüren `InputBox`.</span><span class="sxs-lookup"><span data-stu-id="cc5dc-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="cc5dc-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="cc5dc-108">Robust Programming</span></span>  
 <span data-ttu-id="cc5dc-109">Dönüştürülecek denemeden önce bir dizeyi doğrulamak için bu yöntemi kullanın `String` için bir `DateTime` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="cc5dc-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="cc5dc-110">Tarih veya saat önce denetleyerek, çalışma zamanında bir özel durum oluşturmak önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cc5dc-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc5dc-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc5dc-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>  
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>  
 [<span data-ttu-id="cc5dc-112">Visual Basic'de dizeleri doğrulama</span><span class="sxs-lookup"><span data-stu-id="cc5dc-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
