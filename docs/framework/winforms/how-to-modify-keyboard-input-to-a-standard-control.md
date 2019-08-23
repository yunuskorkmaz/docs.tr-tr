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
ms.openlocfilehash: 1aa22501eb3d15b30be4ea4918473cf5a48cfe94
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964284"
---
# <a name="how-to-modify-keyboard-input-to-a-standard-control"></a>Nasıl yapılır: Standart bir Denetimde Klavye Girdisini Değiştirme
Windows Forms klavye girişini kullanma ve değiştirme olanağı sağlar. Bir anahtarı kullanmak, bir yöntem veya olay işleyicisi içinde bir anahtarın işlenmesine, böylece ileti sırasının daha sonra gelen diğer yöntemlerin ve olayların anahtar değerini almamasını sağlar. Bir anahtarı değiştirmek, bir anahtarın değerini değiştirmek ve bu sayede ileti sırasının daha sonra gelen Yöntem ve olay işleyicilerinin farklı bir anahtar değeri alması anlamına gelir. Bu konu, bu görevlerin nasıl gerçekleştirileceğini gösterir.  
  
### <a name="to-consume-a-key"></a>Bir anahtarı kullanmak için  
  
- Bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyicisinde, <xref:System.Windows.Forms.KeyPressEventArgs> sınıfının <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> özelliğini olarak `true`ayarlayın.  
  
     -veya-  
  
     Bir <xref:System.Windows.Forms.Control.KeyDown> olay işleyicisinde, <xref:System.Windows.Forms.KeyEventArgs> sınıfının <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> özelliğini olarak `true`ayarlayın.  
  
    > [!NOTE]
    > Olay işleyicisindeki <xref:System.Windows.Forms.Control.KeyPress> özelliği ayarlamak, ve <xref:System.Windows.Forms.Control.KeyUp> olaylarının geçerli tuş vuruşu için oluşmasını engellemez. <xref:System.Windows.Forms.KeyEventArgs.Handled%2A> <xref:System.Windows.Forms.Control.KeyDown> Bu amaçla <xref:System.Windows.Forms.KeyEventArgs.SuppressKeyPress%2A> özelliğini kullanın.  
  
     Aşağıdaki örnek `switch` , bir <xref:System.Windows.Forms.KeyPressEventArgs> <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> olay<xref:System.Windows.Forms.Control.KeyPress> işleyicisi tarafından alınan özelliğinin özelliğini incelediği bir deyimin alıntısıdır. Bu kod ' A ' ve ' a ' karakter anahtarlarını kullanır.  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#6)]  
  
### <a name="to-modify-a-standard-character-key"></a>Standart bir karakter anahtarını değiştirmek için  
  
- Bir <xref:System.Windows.Forms.Control.KeyPress> olay işleyicisinde, <xref:System.Windows.Forms.KeyPressEventArgs> sınıfının <xref:System.Windows.Forms.KeyPressEventArgs.KeyChar%2A> özelliğini yeni karakter anahtarının değerine ayarlayın.  
  
     Aşağıdaki örnek ' a ' ile ' b `switch` ' ve ' b ' ile değiştiren bir deyimden alıntıdır. Parametresinin özelliğinin, yeni anahtar değerinin ileti sırasındaki diğer yöntemlere `false`ve olaylara yayılması için olarak ayarlandığını unutmayın. <xref:System.Windows.Forms.KeyPressEventArgs.Handled%2A> <xref:System.Windows.Forms.KeyPressEventArgs>  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#7)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#7)]  
  
### <a name="to-modify-a-noncharacter-key"></a>Karakter olmayan bir anahtarı değiştirmek için  
  
- Windows iletilerini <xref:System.Windows.Forms.Control> işleyen, wm_keydown veya wm_syskeydown iletisini algılayan bir yöntemi geçersiz kılın ve <xref:System.Windows.Forms.Message> parametrenin <xref:System.Windows.Forms.Message.WParam%2A> <xref:System.Windows.Forms.Keys> özelliğini yeni olmayan karakter anahtarını temsil eden değere ayarlayın.  
  
     Aşağıdaki kod örneği, bir denetimin <xref:System.Windows.Forms.Control.PreProcessMessage%2A> yönteminin F1 ile F9 arası bir şekilde algılanması ve tüm F3 tuşuna basarak F1 'e basmanız için nasıl geçersiz kılınacağını göstermektedir. Klavye iletilerini kesmeye yönelik <xref:System.Windows.Forms.Control> geçersiz kılabileceğiniz yöntemler hakkında daha fazla bilgi için, bkz. [Windows Forms uygulamasında kullanıcı girişi](user-input-in-a-windows-forms-application.md) ve [klavye girişinin nasıl çalıştığı](how-keyboard-input-works.md).  
  
     [!code-csharp[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#12)]
     [!code-vb[System.Windows.Forms.KeyBoardInput#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, önceki bölümlerdeki kod örnekleri için tüm uygulamadır. Uygulama, klavye girişini kullanmak ve değiştirmek için <xref:System.Windows.Forms.TextBox> sınıfından türetilmiş özel bir denetim kullanır.  
  
 [!code-csharp[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInput#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInput/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bir Windows Forms Uygulamasında Klavye Girdisi](keyboard-input-in-a-windows-forms-application.md)
- [Bir Windows Forms Uygulamasında Kullanıcı Girdisi](user-input-in-a-windows-forms-application.md)
- [Klavye Girdisi Nasıl Çalışır](how-keyboard-input-works.md)
