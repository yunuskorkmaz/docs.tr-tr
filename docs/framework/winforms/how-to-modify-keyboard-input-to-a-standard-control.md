---
title: "Nasıl yapılır: Standart bir Denetimde Klavye Girdisini Değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d9ff0689671d7d6ff73d158533091330c4fd598
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a>Nasıl yapılır: Standart bir Denetimde Klavye Girdisini Değiştirme
Windows Forms kullanabilir ve klavye girişini değiştirme olanağı sağlar. Bir anahtarı kullanan diğer yöntemleri ve daha fazla ileti sırası aşağı olayları anahtar değeri almazsınız böylece anahtarı yöntemi veya olay işleyicisi içinde işlemeye başvuruyor. Bir anahtar değiştirme yöntemleri ve olay işleyicileri daha fazla ileti sırası aşağı farklı bir anahtar değer alması için bunları bir anahtarın değerini değiştirmek için ifade eder. Bu konu, bu görevlerin nasıl gerçekleştirileceğini gösterir.  
  
### <a name="to-consume-a-key"></a>Bir anahtarı kullanmak için  
  
-   İçinde bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyici ayarlamayı <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> özelliği <xref:System.Windows.Forms.KeyPressEventArgs> sınıfının `true`.  
  
     veya  
  
     İçinde bir <xref:System.Windows.Forms.Control.KeyDown> olay işleyici ayarlamayı <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> özelliği <xref:System.Windows.Forms.KeyEventArgs> sınıfının `true`.  
  
    > [!NOTE]
    >  Ayarı <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> özelliğinde <xref:System.Windows.Forms.Control.KeyDown> olay işleyicisi engellemez <xref:System.Windows.Forms.Control.KeyPress> ve <xref:System.Windows.Forms.Control.KeyUp> için geçerli tuş vuruşu gerçekleştirilen gelen olayları. Kullanım <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> özelliği bu amaç için.  
  
     Aşağıdaki örnek yapılan bir alıntı olan bir `switch` inceler deyimi <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> özelliği <xref:System.Windows.Forms.KeyPressEventArgs> tarafından alınan bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyicisi. Bu kod 'A' ve 'bir' karakteri anahtarları kullanır.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a>Bir standart karakter anahtarı değiştirmek için  
  
-   İçinde bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyici ayarlamayı <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> özelliği <xref:System.Windows.Forms.KeyPressEventArgs> değeri bir sınıfa yeni karakter anahtar.  
  
     Aşağıdaki örnek yapılan bir alıntı olan bir `switch` 'Bir' ' B' değiştirir deyimi ve 'b' 'bir'. Unutmayın <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> özelliği <xref:System.Windows.Forms.KeyPressEventArgs> parametrenin ayarlanmış `false`, böylece yeni anahtar değeri diğer yöntemleri ve ileti sırasındaki olay yayılır.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a>Noncharacter anahtarı değiştirmek için  
  
-   Geçersiz bir <xref:System.Windows.Forms.Control> Windows iletilerini işleme yöntemi WM_KEYDOWN veya WM_SYSKEYDOWN iletisi algılamak ve ayarlama <xref:System.Windows.Forms.Message.WParam%2A> özelliği <xref:System.Windows.Forms.Message> parametresi <xref:System.Windows.Forms.Keys> yeni noncharacter anahtarını temsil eden bir değer.  
  
     Aşağıdaki kod örneğinde nasıl geçersiz kılınacağı gösterilmektedir <xref:System.Windows.Forms.Control.PreProcessMessage%2A> F9 anahtarlarıyla F1 algılamak ve tüm F3 tuşuna F1 değiştirmek için bir denetim yöntemi. Daha fazla bilgi için <xref:System.Windows.Forms.Control> klavye iletileri izlemesine kılabilirsiniz yöntemlerini görmek [bir Windows Forms uygulamasında kullanıcı girişi](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md) ve [nasıl klavye girişi çalışır](../../../docs/framework/winforms/how-keyboard-input-works.md).  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, önceki bölümlerde kod örnekleri için tam uygulamasıdır. Türetilen özel bir denetim uygulamanın kullandığı <xref:System.Windows.Forms.TextBox> kullanabilir ve klavye girdisini değiştirmek için sınıf.  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bir Windows Forms Uygulamasında Klavye Girdisi](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [Bir Windows Forms Uygulamasında Kullanıcı Girdisi](../../../docs/framework/winforms/user-input-in-a-windows-forms-application.md)  
 [Klavye Girdisi Nasıl Çalışır](../../../docs/framework/winforms/how-keyboard-input-works.md)
