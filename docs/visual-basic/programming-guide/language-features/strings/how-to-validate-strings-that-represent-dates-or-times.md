---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: tarihleri veya saatleri temsil eden dizeleri doğrulama (Visual Basic)'
title: 'Nasıl yapılır: Tarihleri veya Saatleri Temsil Eden Dizeleri Doğrulama'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 4e9255717d1711d8e9839c218a78b359549d9eef
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100424273"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a><span data-ttu-id="b00fc-103">Nasıl yapılır: Tarihleri veya Saatleri Temsil Eden Dizeleri Doğrulama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b00fc-103">How to: Validate Strings That Represent Dates or Times (Visual Basic)</span></span>

<span data-ttu-id="b00fc-104">Aşağıdaki kod örneği `Boolean` bir dizenin geçerli bir tarih veya saati temsil ettiğini belirten bir değer belirler.</span><span class="sxs-lookup"><span data-stu-id="b00fc-104">The following code example sets a `Boolean` value that indicates whether a string represents a valid date or time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b00fc-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b00fc-105">Example</span></span>  

 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="b00fc-106">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="b00fc-106">Compile the code</span></span>  

 <span data-ttu-id="b00fc-107">`("01/01/03")`Ve ' i `"9:30 PM"` doğrulamak istediğiniz tarih ve saat ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b00fc-107">Replace `("01/01/03")` and `"9:30 PM"` with the date and time you want to validate.</span></span> <span data-ttu-id="b00fc-108">Dizeyi, bir değişkenle veya bir dize döndüren bir yöntemle (gibi) bir sabit kodlanmış dize ile değiştirebilirsiniz `String` `InputBox` .</span><span class="sxs-lookup"><span data-stu-id="b00fc-108">You can replace the string with another hard-coded string, with a `String` variable, or with a method that returns a string, such as `InputBox`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b00fc-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="b00fc-109">Robust Programming</span></span>  

 <span data-ttu-id="b00fc-110">Öğesini bir değişkene dönüştürmeyi denemeden önce dizeyi doğrulamak için bu yöntemi kullanın `String` `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="b00fc-110">Use this method to validate the string before trying to convert the `String` to a `DateTime` variable.</span></span> <span data-ttu-id="b00fc-111">İlk olarak tarihi veya saati denetleyerek, çalışma zamanında bir özel durum oluşturmaktan kaçınabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b00fc-111">By checking the date or time first, you can avoid generating an exception at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b00fc-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b00fc-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [<span data-ttu-id="b00fc-113">Visual Basic'de Dizeleri Doğrulama</span><span class="sxs-lookup"><span data-stu-id="b00fc-113">Validating Strings in Visual Basic</span></span>](validating-strings.md)
