---
title: Windows Forms uygulamasındaki yazı tipi şeması değişikliklerine yanıt verme
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: e3b96139a7cfd4b268d81b1da58229527e2beb87
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739234"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>Nasıl yapılır: Bir Windows Forms Uygulamasında Yazı Tipi Şeması Değişikliklerine Yanıt Verme
Windows işletim sistemlerinde, bir Kullanıcı, varsayılan yazı tipinin daha büyük veya küçük görünmesini sağlamak için sistem genelindeki yazı tipi ayarlarını değiştirebilir. Bu yazı tipi ayarlarının değiştirilmesi, görme engelli kullanıcılar için kritiktir ve ekranlarındaki metni okumak için daha büyük bir tür gerektirir. Windows Forms uygulamanızı, form boyutunu artırarak veya azaltarak ve yazı tipi şeması her değiştiğinde içerilen tüm metinler için bu değişikliklere tepki verecek şekilde ayarlayabilirsiniz. Formunuzun yazı tipi boyutlarında değişiklikleri dinamik olarak sığbilmesini istiyorsanız formunuza kod ekleyebilirsiniz.  
  
 Genellikle, Windows Forms tarafından kullanılan varsayılan yazı tipi, `GetStockObject(DEFAULT_GUI_FONT)`<xref:Microsoft.Win32> ad alanı çağrısının döndürdüğü yazı tipidir. Bu çağrının döndürdüğü yazı tipi yalnızca ekran çözünürlüğü değiştiğinde değişir. Aşağıdaki yordamda gösterildiği gibi, yazı tipi boyutundaki değişikliklere yanıt vermek için kodunuzun varsayılan yazı tipini <xref:System.Drawing.SystemFonts.IconTitleFont%2A> değiştirmesi gerekir.  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>Masaüstü yazı tipini kullanmak ve yazı tipi şeması değişikliklerine yanıt vermek için  
  
1. Formunuzu oluşturun ve istediğiniz denetimleri ekleyin. Daha fazla bilgi için, bkz. [nasıl yapılır: komut satırından Windows Forms uygulama oluşturma](how-to-create-a-windows-forms-application-from-the-command-line.md) ve [Windows Forms kullanılacak denetimler](./controls/controls-to-use-on-windows-forms.md).  
  
2. Kodunuza <xref:Microsoft.Win32> ad alanına bir başvuru ekleyin.  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3. Aşağıdaki kodu, gerekli olay işleyicilerini bağlamak ve form için kullanılan varsayılan yazı tipini değiştirmek için formunuzun oluşturucusuna ekleyin.  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4. <xref:Microsoft.Win32.UserPreferenceCategory.Window> kategorisi değiştiğinde formun otomatik olarak ölçeklendirilmesine neden olan <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> olayı için bir işleyici uygulayın.  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5. Son olarak, <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> olay işleyicisini ayırır <xref:System.Windows.Forms.Form.FormClosing> olayı için bir işleyici uygulayın.  
  
     > [!IMPORTANT]
     > Bu kodun dahil edilmemesi, uygulamanızın belleği sızdırmasına neden olur.  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6. Kodu derleyin ve çalıştırın.  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>Windows XP 'de yazı tipi düzenini el ile değiştirmek için  
  
1. Windows Forms uygulamanız çalışırken, Windows masaüstüne sağ tıklayıp kısayol menüsünden **Özellikler** ' i seçin.  
  
2. **Görüntü özellikleri** Iletişim kutusunda **Görünüm** sekmesine tıklayın.  
  
3. **Yazı tipi boyutu** aşağı açılan liste kutusundan yeni bir yazı tipi boyutu seçin.  
  
     Formun artık Masaüstü yazı tipi düzeninde çalışma zamanı değişikliklerine tepki verdiğini fark edeceksiniz. Kullanıcı **normal**, **büyük yazı tipleri**ve çok **büyük yazı tipleri**arasında değişiklik yaparken, form yazı tipini değiştirir ve doğru şekilde ölçeklendirir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 Bu kod örnekteki Oluşturucu, Visual Studio 'da yeni bir Windows Forms projesi oluşturduğunuzda tanımlanan `InitializeComponent`için bir çağrı içerir. Uygulamanızı komut satırında oluşturuyorsanız bu kod satırını kaldırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [Windows Forms'ta Otomatik Ölçeklendirme](automatic-scaling-in-windows-forms.md)
