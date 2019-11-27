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
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Nasıl yapılır: Tarihleri veya Saatleri Temsil Eden Dizeleri Doğrulama (Visual Basic)
Aşağıdaki kod örneği bir dizenin geçerli bir tarih veya saati temsil edip etmediğini belirten `Boolean` bir değer ayarlar.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 `("01/01/03")` ve `"9:30 PM"`, doğrulamak istediğiniz tarih ve saat ile değiştirin. Dizeyi, bir `String` değişkeni ile veya `InputBox`gibi bir dize döndüren bir yöntemle değiştirebilirsiniz.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 `String` bir `DateTime` değişkenine dönüştürmeyi denemeden önce dizeyi doğrulamak için bu yöntemi kullanın. İlk olarak tarihi veya saati denetleyerek, çalışma zamanında bir özel durum oluşturmaktan kaçınabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Visual Basic dizeleri doğrulanıyor](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
