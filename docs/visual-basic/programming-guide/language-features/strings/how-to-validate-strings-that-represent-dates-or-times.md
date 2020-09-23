---
title: 'Nasıl yapılır: Tarihleri veya Saatleri Temsil Eden Dizeleri Doğrulama'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], validating
- String data type [Visual Basic], validation
ms.assetid: ae7d4b29-3436-4032-bdbf-4650eb1c8e19
ms.openlocfilehash: f3654894e274404410179dab04422e20f6040440
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072606"
---
# <a name="how-to-validate-strings-that-represent-dates-or-times-visual-basic"></a>Nasıl yapılır: Tarihleri veya Saatleri Temsil Eden Dizeleri Doğrulama (Visual Basic)

Aşağıdaki kod örneği `Boolean` bir dizenin geçerli bir tarih veya saati temsil ettiğini belirten bir değer belirler.  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbVbcnRegEx#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#2)]  
  
## <a name="compile-the-code"></a>Kodu derle  

 `("01/01/03")`Ve ' i `"9:30 PM"` doğrulamak istediğiniz tarih ve saat ile değiştirin. Dizeyi, bir değişkenle veya bir dize döndüren bir yöntemle (gibi) bir sabit kodlanmış dize ile değiştirebilirsiniz `String` `InputBox` .  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 Öğesini bir değişkene dönüştürmeyi denemeden önce dizeyi doğrulamak için bu yöntemi kullanın `String` `DateTime` . İlk olarak tarihi veya saati denetleyerek, çalışma zamanında bir özel durum oluşturmaktan kaçınabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Information.IsDate%2A>
- <xref:Microsoft.VisualBasic.Interaction.InputBox%2A>
- [Visual Basic'de Dizeleri Doğrulama](validating-strings.md)
