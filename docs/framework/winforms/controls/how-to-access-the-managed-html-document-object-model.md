---
title: 'Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modeline Erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- HTML DOM [Windows Forms], accessing
- managed HTML DOM [Windows Forms], accessing
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
ms.openlocfilehash: 175a29322fe2af13992e267b3fc3308b70212272
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-the-managed-html-document-object-model"></a>Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modeline Erişme
Yönetilen HTML belgesi nesne modeli (DOM) uygulamaları iki türden erişebilirsiniz:  
  
-   Yönetilen barındırılan bir Windows Forms uygulaması (.exe) <xref:System.Windows.Forms.WebBrowser> denetim. Bu iki teknolojiler birbirine, ile tamamlar <xref:System.Windows.Forms.WebBrowser> denetimi kullanıcı ve belgenin mantıksal yapısını temsil eden HTML DOM sayfanın görüntüleme.  
  
-   Windows Forms <xref:System.Windows.Forms.UserControl> Internet Explorer içinde barındırılan. Sayfayı temsil eden HTML DOM erişebilir, <xref:System.Windows.Forms.UserControl> belgenin yapısını değiştirin ya da diğer birçok olasılıklar arasında kalıcı iletişim kutuları açma amacıyla barındırılır.  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a>Bir Windows Forms uygulamasından DOM erişmek için  
  
1.  Konak bir <xref:System.Windows.Forms.WebBrowser> Windows Forms uygulamanızdaki denetlemek ve izlemek <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> olay. Denetimleri barındırma ve olaylar için izleme ile ilgili ayrıntılar için bkz: [olayları](../../../../docs/standard/events/index.md).  
  
2.  Alma <xref:System.Windows.Forms.HtmlDocument> erişerek geçerli sayfa için <xref:System.Windows.Forms.WebBrowser.Document%2A> özelliği <xref:System.Windows.Forms.WebBrowser> denetim.  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a>Internet Explorer'da barındırılan bir UserControl DOM erişmek için  
  
1.  Kendi özel türetilen sınıfı oluşturmak <xref:System.Windows.Forms.UserControl> sınıfı. Daha fazla bilgi için bkz: [nasıl yapılır: bileşik denetimler Yazar](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md).  
  
2.  Aşağıdaki kodu için yük olay işleyicisi içinde yerleştirin, <xref:System.Windows.Forms.UserControl>:  
  
 [!code-csharp[AccessHTMLDOMControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a>Güçlü Programlama  
  
1.  DOM aracılığıyla kullanırken <xref:System.Windows.Forms.WebBrowser> denetimi, her zaman beklemesi gereken kadar <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> olayı meydana erişmeyi denemeden önce <xref:System.Windows.Forms.WebBrowser.Document%2A> özelliği <xref:System.Windows.Forms.WebBrowser> denetim. <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> Tüm belgeyi yüklendikten sonra olayı oluşturulur; daha önce DOM kullanırsanız, bir çalışma zamanı özel uygulamanızda neden risk.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
  
1.  Uygulamanızı veya <xref:System.Windows.Forms.UserControl> yönetilen HTML DOM erişmek için tam güven gerektirir Windows Forms uygulaması kullanarak dağıtıyorsanız [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], izin yükseltme veya güvenilir uygulama dağıtımı kullanarak tam güven isteyebilir; bkz [ClickOnce uygulamalarının güvenliğini sağlama](/visualstudio/deployment/securing-clickonce-applications) Ayrıntılar için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen HTML Belgesi Nesne Modelini Kullanma](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
