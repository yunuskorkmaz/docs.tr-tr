---
title: 'Nasıl yapılır: Klavye Girdisini Form Düzeyinde İşleme'
description: İletiler bir denetime ulaşmadan önce, form düzeyinde Windows Forms klavye girişini nasıl işleyeceğinizi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
ms.openlocfilehash: 6f0695b6f665a613e0e4e001a4f9bbfc09dd45ed
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904162"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a>Nasıl yapılır: Klavye Girdisini Form Düzeyinde İşleme
Windows Forms, iletiler bir denetime ulaşmadan önce klavye iletilerini form düzeyinde işleme yeteneği sağlar. Bu konu, bu görevin nasıl gerçekleştirileceğini gösterir.  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a>Bir klavye iletisini form düzeyinde işlemek için  
  
- <xref:System.Windows.Forms.Control.KeyPress> <xref:System.Windows.Forms.Control.KeyDown> Başlangıç formunun veya olayını işleyin ve form özelliğini, form <xref:System.Windows.Forms.Form.KeyPreview%2A> `true` üzerinde herhangi bir denetime erişmeden önce form tarafından alınan klavye iletilerini olarak ayarlayın. Aşağıdaki kod örneği, <xref:System.Windows.Forms.Control.KeyPress> Tüm sayı anahtarlarını algılayarak ve ' 1 ', ' 4 ' ve ' 7 ' kullanan olayı işler.  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, yukarıdaki örnek için tüm uygulamadır. Uygulama <xref:System.Windows.Forms.TextBox> , odağı içinden taşımanızı sağlayan diğer birçok denetim ile birlikte içerir <xref:System.Windows.Forms.TextBox> . <xref:System.Windows.Forms.Control.KeyPress>Ana <xref:System.Windows.Forms.Form> ' 1 ', ' 4 ' ve ' 7 ' kullanımını ve <xref:System.Windows.Forms.Control.KeyPress> <xref:System.Windows.Forms.TextBox> geri kalan anahtarları görüntülerken ' 2 ', ' 5 ' ve ' 8 ' kullanımını tüketen olay. <xref:System.Windows.Forms.MessageBox>Bir sayı tuşuna bastığınızda çıktıyı karşılaştırın, ancak <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.MessageBox> odak diğer denetimlerden birinde olduğunda bir sayı tuşuna bastığınızda çıkış ile odak edilir.  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir Windows Forms Uygulamasında Klavye Girdisi](keyboard-input-in-a-windows-forms-application.md)
