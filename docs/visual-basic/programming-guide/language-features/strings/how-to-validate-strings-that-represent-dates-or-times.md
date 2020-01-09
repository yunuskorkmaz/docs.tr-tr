---
title: 'Nasıl yapılır: Tarihleri veya Saatleri Temsil Eden Dizeleri Doğrulama'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 5321e7a85c45ddb6ce17433bd25ce9ca2165f0a3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348409"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Nasıl yapılır: Tarihleri veya Saatleri Temsil Eden Dizeleri Doğrulama (Visual Basic)
Aşağıdaki kod örneği bir dizenin geçerli bir tarih veya saati temsil edip etmediğini belirten `Boolean` bir değer ayarlar.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a>Kod derleme  
 `("01/01/03")` ve `"9:30 PM"`, doğrulamak istediğiniz tarih ve saat ile değiştirin. Dizeyi, bir `String` değişkeni ile veya `InputBox`gibi bir dize döndüren bir yöntemle değiştirebilirsiniz.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 `String` bir `DateTime` değişkenine dönüştürmeyi denemeden önce dizeyi doğrulamak için bu yöntemi kullanın. İlk olarak tarihi veya saati denetleyerek, çalışma zamanında bir özel durum oluşturmaktan kaçınabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Visual Basic dizeleri doğrulanıyor](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
