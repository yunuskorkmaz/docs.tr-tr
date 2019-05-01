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
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Nasıl yapılır: Tarihleri veya saatleri temsil eden dizeleri doğrulama (Visual Basic)
Aşağıdaki örnek kod bir `Boolean` bir dizenin geçerli bir tarih veya saat temsil edip etmediğini belirten değer.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Değiştirin `("01/01/03")` ve `"9:30 PM"` istediğiniz doğrulamak için saat ve tarihi ile. İle başka bir sabit kodlanmış dize dizesiyle değiştirin bir `String` değişkenine veya bir yöntemle bir dize gibi döndürür `InputBox`.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Dönüştürülecek denemeden önce bir dizeyi doğrulamak için bu yöntemi kullanın `String` için bir `DateTime` değişkeni. Tarih veya saat önce denetleyerek, çalışma zamanında bir özel durum oluşturma önleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Visual Basic'de dizeleri doğrulama](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
