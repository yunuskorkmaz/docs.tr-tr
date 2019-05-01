---
title: 'Nasıl yapılır: Standart bir Denetimde Klavye Girdisini Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyboard input [Windows Forms], modifying
- modifying keyboard input
- Windows Forms, modifying keyboard input
- keyboards [Windows Forms], keyboard input
ms.assetid: 626d3712-d866-4988-bcda-a2d5b36ec0ba
ms.openlocfilehash: 81d33234670fb8ae5445cc86a79f5c3b6a647a03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802342"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a>Nasıl yapılır: Standart bir Denetimde Klavye Girdisini Değiştirme
Windows Forms, kullanma ve klavye girdisini değiştirme olanağı sağlar. Bir anahtarı kullanan bir yöntem veya olay işleyicisi içindeki bir anahtar diğer yöntemleri ve olayları daha fazla ileti kuyruğu aşağı anahtar değerini alıyor musunuz böylece işlemeye ifade eder. Bir anahtar değiştirme yöntemlerini ve olay işleyicileri daha fazla ileti kuyruğu aşağı farklı bir anahtar değeri alması için bunları bir anahtarın değerini değiştirmek için ifade eder. Bu konu aşağıdaki görevlerin nasıl gerçekleştirileceğini gösterir.  
  
### <a name="to-consume-a-key"></a>Bir anahtar kullanmak için  
  
- İçinde bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyicisini <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> özelliği <xref:System.Windows.Forms.KeyPressEventArgs> sınıfının `true`.  
  
     -veya-  
  
     İçinde bir <xref:System.Windows.Forms.Control.KeyDown> olay işleyicisini <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> özelliği <xref:System.Windows.Forms.KeyEventArgs> sınıfının `true`.  
  
    > [!NOTE]
    >  Ayarı <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> özelliğinde <xref:System.Windows.Forms.Control.KeyDown> olay işleyicisi engellemez <xref:System.Windows.Forms.Control.KeyPress> ve <xref:System.Windows.Forms.Control.KeyUp> için geçerli bir tuş vuruşu gerçekleştirilen gelen olayları. Kullanım <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> bu amaç için özellik.  
  
     Aşağıdaki örnek, kitabından bir `switch` inceler deyimi <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> özelliği <xref:System.Windows.Forms.KeyPressEventArgs> tarafından alınan bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyicisi. Bu kod, 'A' ve 'bir' karakter anahtarları kullanır.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a>Bir standart karakter anahtarı değiştirmek için  
  
- İçinde bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyicisini <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> özelliği <xref:System.Windows.Forms.KeyPressEventArgs> yeni karakter anahtar değerine sınıfı.  
  
     Aşağıdaki örnek, kitabından bir `switch` değiştirir 'A', ' B' deyimi ve 'a', ' b'. Unutmayın <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> özelliği <xref:System.Windows.Forms.KeyPressEventArgs> parametrenin ayarlanmış `false`, böylece yeni bir anahtar değeri diğer yöntemler ve olaylar ileti sırasına yayılır.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a>Karakter olmayan bir anahtarı değiştirmek için  
  
- Geçersiz bir <xref:System.Windows.Forms.Control> Windows iletileri işleyen yöntem WM_KEYDOWN veya WM_SYSKEYDOWN ileti algılayın ve ayarlama <xref:System.Windows.Forms.Message.WParam%2A> özelliği <xref:System.Windows.Forms.Message> parametresi <xref:System.Windows.Forms.Keys> yeni karakter olmayan anahtar gösteren bir değer.  
  
     Aşağıdaki kod örneğinde nasıl geçersiz kılınacağını gösterir <xref:System.Windows.Forms.Control.PreProcessMessage%2A> yöntemi F9 F1 anahtarlarıyla algılamak ve tüm F3 tuşuna F1 değiştirmek için bir denetim. Daha fazla bilgi için <xref:System.Windows.Forms.Control> klavye iletileri izlemesine kılabilirsiniz yöntemlerini [bir Windows Forms uygulamasında kullanıcı girişi](user-input-in-a-windows-forms-application.md) ve [nasıl klavye girişi çalışır](how-keyboard-input-works.md).  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, önceki bölümlerde kod örnekleri için tam uygulamasıdır. Öğesinden türetilen özel bir denetim uygulamanın kullandığı <xref:System.Windows.Forms.TextBox> kullanma ve klavye girdisini değiştirme sınıfı.  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Sistem, System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir Windows Forms Uygulamasında Klavye Girdisi](keyboard-input-in-a-windows-forms-application.md)
- [Bir Windows Forms Uygulamasında Kullanıcı Girdisi](user-input-in-a-windows-forms-application.md)
- [Klavye Girdisi Nasıl Çalışır](how-keyboard-input-works.md)
