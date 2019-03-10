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
ms.openlocfilehash: 886558eb33ffbbec65917f15f4da16673518dce9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723965"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a>Nasıl yapılır: Windows Forms denetimlerinde kullanıcı girdi olaylarını işleme
Bu örnek, çoğu klavye, fare, odak ve bir Windows Forms denetiminde oluşabilecek doğrulama olayların nasıl ele alınacağını gösterir. Adlı metin kutusunda `TextBoxInput` odaklı ve her olay hakkında bilgiler adlı metin kutusuna yazılan olayları alır `TextBoxOutput` olaylar oluştuğunda sırada. Uygulama onay kutularını, rapora hangi olayları filtrelemek için kullanılan bir dizi de içerir.  
  
## <a name="example"></a>Örnek  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Forms'ta Kullanıcı Girdisi](user-input-in-windows-forms.md)
