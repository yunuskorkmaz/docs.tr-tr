---
title: 'Nasıl yapılır: Klavye Girdisini Form Düzeyinde İşleme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8fa1a7cb7dbddc541445e5bee798261a682036b0
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a>Nasıl yapılır: Klavye Girdisini Form Düzeyinde İşleme
Windows Forms Denetim iletileri düşmeden önce klavye iletileri form düzeyinde işleme yeteneği sağlar. Bu konu, bu görevin nasıl gerçekleştirileceğini gösterir.  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a>Form düzeyinde bir klavye ileti işleme  
  
-   İşlemek <xref:System.Windows.Forms.Control.KeyPress> veya <xref:System.Windows.Forms.Control.KeyDown> başlangıç formu ve kümesi olay <xref:System.Windows.Forms.Form.KeyPreview%2A> forma özelliğinin `true` böylece form üzerinde herhangi bir denetim düşmeden önce klavye iletileri form tarafından alınır. Aşağıdaki kod örneği tanıtıcıları <xref:System.Windows.Forms.Control.KeyPress> tüm sayı tuşları algılama ve '1', '4' ve '7' tüketen olay.  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, yukarıdaki örnek için tüm uygulamasıdır. Uygulama içeren bir <xref:System.Windows.Forms.TextBox> odağı taşımanızı sağlayan birkaç diğer denetimlerle birlikte <xref:System.Windows.Forms.TextBox>. <xref:System.Windows.Forms.Control.KeyPress> Ana olay <xref:System.Windows.Forms.Form> '1', '4' ve '7' tüketir ve <xref:System.Windows.Forms.Control.KeyPress> olayı <xref:System.Windows.Forms.TextBox> kalan anahtarları görüntülenirken '2', '5' ve '8' kullanır. Karşılaştırma <xref:System.Windows.Forms.MessageBox> numara anahtar biraz bastığınızda çıktı <xref:System.Windows.Forms.TextBox> ile odaklanmış <xref:System.Windows.Forms.MessageBox> odak diğer denetimleri birinde olsa da bir numara tuşuna bastığınızda çıktı.  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir Windows Forms Uygulamasında Klavye Girdisi](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)
