---
title: 'Nasıl yapılır: Tarihleri veya saatleri temsil eden dizeleri doğrulama (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: f24ff05e48327c21c02eb92b07db17266f743a80
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024618"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="62f68-102">Nasıl yapılır: Tarihleri veya saatleri temsil eden dizeleri doğrulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62f68-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="62f68-103">Aşağıdaki örnek kod bir `Boolean` bir dizenin geçerli bir tarih veya saat temsil edip etmediğini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="62f68-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62f68-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="62f68-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="62f68-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="62f68-105">Compiling the Code</span></span>  
 <span data-ttu-id="62f68-106">Değiştirin `("01/01/03")` ve `"9:30 PM"` istediğiniz doğrulamak için saat ve tarihi ile.</span><span class="sxs-lookup"><span data-stu-id="62f68-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="62f68-107">İle başka bir sabit kodlanmış dize dizesiyle değiştirin bir `String` değişkenine veya bir yöntemle bir dize gibi döndürür `InputBox`.</span><span class="sxs-lookup"><span data-stu-id="62f68-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="62f68-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="62f68-108">Robust Programming</span></span>  
 <span data-ttu-id="62f68-109">Dönüştürülecek denemeden önce bir dizeyi doğrulamak için bu yöntemi kullanın `String` için bir `DateTime` değişkeni.</span><span class="sxs-lookup"><span data-stu-id="62f68-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="62f68-110">Tarih veya saat önce denetleyerek, çalışma zamanında bir özel durum oluşturma önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62f68-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f68-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62f68-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="62f68-112">Visual Basic'de dizeleri doğrulama</span><span class="sxs-lookup"><span data-stu-id="62f68-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
