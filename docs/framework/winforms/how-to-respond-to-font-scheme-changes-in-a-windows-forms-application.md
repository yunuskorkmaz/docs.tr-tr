---
title: "Nasıl yapılır: Bir Windows Forms Uygulamasında Yazı Tipi Şeması Değişikliklerine Yanıt Verme"
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
helpviewer_keywords: Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3b2e53df114c491e99e13940ae47a4119bd8da46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>Nasıl yapılır: Bir Windows Forms Uygulamasında Yazı Tipi Şeması Değişikliklerine Yanıt Verme
Windows işletim sistemlerinde, bir kullanıcı daha büyük veya küçük görünür varsayılan yazı tipi yapmak için sistem genelinde yazı tipi ayarlarını değiştirebilirsiniz. Bu yazı tipi ayarlarını değiştirme ekranlarını üzerindeki metin okumak büyük türü gerektirir ve görme engelli kullanıcılar için kritik öneme sahiptir. Bu değişiklikleri artırarak veya yazı tipi düzenini değiştiğinde form ve içerdiği tüm metin boyutunu azaltarak tepki vermek için Windows Forms uygulaması ayarlayabilirsiniz. Formunuz yazı tipi boyutlarını değişiklikleri dinamik olarak sağlamak istiyorsanız, kod ekleyebilirsiniz.  
  
 Genellikle, Windows Forms tarafından kullanılan varsayılan yazı tipi tarafından döndürülen yazı tipidir <xref:Microsoft.Win32> ad alanı çağrısına `GetStockObject(DEFAULT_GUI_FONT)`. Bu çağrı tarafından döndürülen yazı tipi yalnızca ekran çözünürlüğü değiştiğinde değişir. Aşağıdaki yordamda gösterildiği gibi kodunuz için varsayılan yazı tipi değiştirmelisiniz <xref:System.Drawing.SystemFonts.IconTitleFont%2A> yazı tipi boyutunu değişikliklere yanıt.  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>Masaüstü yazı tipi kullanın ve yazı tipi şeması değişikliklerine yanıt vermek için  
  
1.  Formunuz oluşturun ve istediğiniz denetimleri ekleyin. Daha fazla bilgi için bkz: [nasıl yapılır: komut satırından bir Windows Forms uygulaması oluşturma](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md) ve [Windows Forms'ta kullanılacak denetimler](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).  
  
2.  Bir başvuru ekleyin <xref:Microsoft.Win32> kodunuz için ad alanı.  
  
     [!code-csharp[WinFormsAutoScaling#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  Oluşturucuya formunuzu gerekli olay işleyicilerini bağlanmanıza ve form için kullanılan varsayılan yazı tipini değiştirmek için aşağıdaki kodu ekleyin.  
  
     [!code-csharp[WinFormsAutoScaling#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  Uygulama için bir işleyici <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> otomatik olarak ölçeklendirme forma neden olan olay olduğunda <xref:Microsoft.Win32.UserPreferenceCategory.Window> kategori değişiklikleri.  
  
     [!code-csharp[WinFormsAutoScaling#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  Son olarak, uygulama için bir işleyici <xref:System.Windows.Forms.Form.FormClosing> ayırır olay <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> olay işleyicisi.  
  
> [!IMPORTANT]
>  Bu kod dahil etmek için hata bellek sızıntısı uygulamanıza neden olur.  
  
 [!code-csharp[WinFormsAutoScaling#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
 [!code-vb[WinFormsAutoScaling#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
1.  Derleme ve kodu çalıştırın.  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>El ile Windows XP'de yazı tipi düzenini değiştirmek için  
  
1.  Windows Forms uygulamanızı çalışırken, Windows Masaüstü sağ tıklatın ve seçin **özellikleri** kısayol menüsünden.  
  
2.  İçinde **görüntü özellikleri** iletişim kutusu, tıklatın **Görünüm** sekmesi.  
  
3.  Gelen **yazı tipi boyutu** aşağı açılan liste kutusunda, yeni bir yazı tipi boyutu seçin.  
  
     Form şimdi de masaüstü yazı tipi düzeni değiştiğinde çalışmaya tepki verdiğini olduğunu fark edeceksiniz. Kullanıcı değiştiğinde arasında **Normal**, **büyük yazı tipleri**, ve **ekstra büyük yazı tipleri**, form yazı tipini değiştirir ve doğru şekilde ölçeklendirir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[WinFormsAutoScaling#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 Bu kod örneğinde constructer yapılan bir çağrı içerir `InitializeComponent`, hangi Visual Studio'da yeni bir Windows Forms projesi oluşturduğunuzda tanımlanır. Bu kod satırı, komut satırında, uygulamanızın oluşturuluyorsa kaldırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>  
 [Windows Forms'ta otomatik ölçeklendirme](../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)
