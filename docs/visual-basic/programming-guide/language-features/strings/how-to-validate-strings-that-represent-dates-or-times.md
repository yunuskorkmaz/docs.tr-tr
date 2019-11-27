---
title: 'Nasıl yapılır: Tarihleri veya Saatleri Temsil Eden Dizeleri Doğrulama'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 34af6dffeb0d05eaeed38354f8007554b60e91b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344351"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="43434-102">Nasıl yapılır: Tarihleri veya Saatleri Temsil Eden Dizeleri Doğrulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43434-102">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>
<span data-ttu-id="43434-103">Aşağıdaki kod örneği bir dizenin geçerli bir tarih veya saati temsil edip etmediğini belirten `Boolean` bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="43434-103">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43434-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="43434-104">Example</span></span>  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="43434-105">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="43434-105">Compiling the Code</span></span>  
 <span data-ttu-id="43434-106">`("01/01/03")` ve `"9:30 PM"`, doğrulamak istediğiniz tarih ve saat ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="43434-106">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="43434-107">Dizeyi, bir `String` değişkeni ile veya `InputBox`gibi bir dize döndüren bir yöntemle değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43434-107">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="43434-108">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="43434-108">Robust Programming</span></span>  
 <span data-ttu-id="43434-109">`String` bir `DateTime` değişkenine dönüştürmeyi denemeden önce dizeyi doğrulamak için bu yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="43434-109">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="43434-110">İlk olarak tarihi veya saati denetleyerek, çalışma zamanında bir özel durum oluşturmaktan kaçınabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43434-110">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43434-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43434-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="43434-112">Visual Basic dizeleri doğrulanıyor</span><span class="sxs-lookup"><span data-stu-id="43434-112">Validating Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
