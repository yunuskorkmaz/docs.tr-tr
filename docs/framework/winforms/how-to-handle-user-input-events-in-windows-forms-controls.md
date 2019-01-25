---
title: 'Nasıl yapılır: Windows Forms denetimlerinde kullanıcı girdi olaylarını işleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: ae4a6f7087c82be6531a91980e2fee0108298a46
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738715"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a>Nasıl yapılır: Windows Forms denetimlerinde kullanıcı girdi olaylarını işleme
Bu örnek, çoğu klavye, fare, odak ve bir Windows Forms denetiminde oluşabilecek doğrulama olayların nasıl ele alınacağını gösterir. Adlı metin kutusunda `TextBoxInput` odaklı ve her olay hakkında bilgiler adlı metin kutusuna yazılan olayları alır `TextBoxOutput` olaylar oluştuğunda sırada. Uygulama onay kutularını, rapora hangi olayları filtrelemek için kullanılan bir dizi de içerir.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  Ayrıca bkz: [nasıl yapılır: Derleme ve Visual Studio kullanarak tam bir Windows Formları kod örneği çalıştırma](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Forms'ta Kullanıcı Girdisi](../../../docs/framework/winforms/user-input-in-windows-forms.md)
