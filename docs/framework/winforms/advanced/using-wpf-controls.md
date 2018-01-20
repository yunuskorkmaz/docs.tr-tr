---
title: WPF Denetimlerini Kullanma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e616019d53648058d51a3d0df457b1380aaf3b1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="using-wpf-controls"></a>WPF Denetimlerini Kullanma
Windows Forms tabanlı uygulamalarda Windows Presentation Foundation (WPF) denetimleri kullanabilirsiniz. Bu iki farklı görünüm teknolojileri olsa da, bunlar sorunsuz onunla birlikte çalışamaz.  
  
 Windows Form Tasarımcısı Windows Presentation Foundation denetimleri barındırma bir görsel tasarım ortamı sağlar. WPF denetimi adlı bir özel Windows Formları denetimi tarafından barındırılan <xref:System.Windows.Forms.Integration.ElementHost>. Bu denetim formun düzende katılmak ve klavye ve fare iletileri almak için WPF denetimi sağlar. Tasarım zamanında düzenleyebilirsiniz <xref:System.Windows.Forms.Integration.ElementHost> herhangi bir Windows Forms denetimi olarak denetleme.  
  
 WPF tabanlı uygulamalarınızda Windows Forms denetimleri de kullanabilirsiniz. Daha fazla bilgi için bkz: [WPF Tasarımcısı](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Tasarım Zamanında bir ElementHost Denetimini Kopyalayıp Yapıştırma](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 Bir Windows formunda Windows Presentation Foundation denetimi kopyalama gösterilmektedir.  
  
 [İzlenecek yol: Windows Forms'ta Tasarım Zamanında WPF İçeriğini Düzenleme](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 Windows Forms düzeni özellikleri sabitleme ve dayama çizgileri, gibi Windows Presentation Foundation denetimlerini düzenlemek için nasıl kullanılacağını gösterir.  
  
 [İzlenecek yol: Tasarım Zamanında Barındırılan bir WPF Öğesinin Özelliklerini Değiştirme](../../../../docs/framework/winforms/advanced/walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time.md)  
 Windows Form Tasarımcısı arasında iş akışı gösterir ve [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] WPF denetimleri özelliklerini değiştirmek için.  
  
 [İzlenecek yol: Windows Forms’ta Tasarım Zamanında Yeni bir WPF İçeriği Oluşturma](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 Windows Forms tabanlı uygulamalarınızda kullanım için bir Windows Presentation Foundation denetimini oluşturulacağını gösterir.  
  
 [İzlenecek yol: Bir ElementHost Denetimini Ayrı Windows Forms’a Kopyalama ve Yapıştırma](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 Bir Windows Presentation Foundation denetimi bir Windows formundan kopyalama gösterilmektedir.  
  
 [İzlenecek yol: Windows Forms’ta Tasarım Zamanında WPF İçeriği Atama](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 Windows Presentation Foundation denetim türlerini formunuzda görüntülemek istediğinizi seçmek gösterilmiştir.  
  
 [İzlenecek yol: WPF İçeriği için Stil Oluşturma](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 Windows Form Tasarımcısı arasında iş akışı gösterir ve [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] stilleri Windows Presentation Foundation denetimlerine uygulama için.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 Windows Forms tabanlı uygulamalarda ana bilgisayar Windows Presentation Foundation denetimleri için kullanabileceğiniz bir sınıfı tanımlar.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 Windows Presentation Foundation tabanlı uygulamanızda ana bilgisayar Windows Forms denetimleri için kullanabileceğiniz bir sınıfı tanımlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Geçiş ve Birlikte Çalışabilirlik](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 Windows Presentation Foundation ve Windows Forms teknolojileri arasında birlikte çalışabilirlik açıklar.  
  
 [WPF Tasarımcısı](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 Windows Presentation Foundation denetimlerinde tasarım açıklar [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].
