---
title: 'Nasıl yapılır: Tarihleri veya Saatleri Temsil Eden Dizeleri Doğrulama (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: 411c8517783421b2472c3e4aa77287f8252f179b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647868"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Nasıl yapılır: Tarihleri veya Saatleri Temsil Eden Dizeleri Doğrulama (Visual Basic)
Aşağıdaki örnek kod bir `Boolean` bir dizenin geçerli bir tarih veya saat temsil edip etmediğini gösteren değer.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbcnRegEx#2](../../../../visual-basic/programming-guide/language-features/strings/codesnippet/VisualBasic/how-to-validate-strings-that-represent-dates-or-times_1.vb)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Değiştir `("01/01/03")` ve `"9:30 PM"` doğrulamak istediğiniz saat ve tarihi ile. İle başka bir sabit kodlanmış dize dizesiyle değiştirin bir `String` değişkenine veya farklı bir yöntemle bir dize gibi döndüren `InputBox`.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Dönüştürülecek denemeden önce bir dizeyi doğrulamak için bu yöntemi kullanın `String` için bir `DateTime` değişkeni. Tarih veya saat önce denetleyerek, çalışma zamanında bir özel durum oluşturmak önleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Information.IsDate%2A>  
 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>  
 [Visual Basic'de dizeleri doğrulama](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
