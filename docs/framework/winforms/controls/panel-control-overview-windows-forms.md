---
title: Panel Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- Panel
helpviewer_keywords:
- grouping controls [Windows Forms], Panel control
- Panel control [Windows Forms], about Panel control
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
ms.openlocfilehash: 3ea86e898e8a3e1ca90ba8e0a6240414702a1a73
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744310"
---
# <a name="panel-control-overview-windows-forms"></a>Panel Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Panel> denetimleri, diğer denetimler için tanımlanabilir bir gruplandırma sağlamak üzere kullanılır. Genellikle, bir formu işleve göre bölümlere ayırmak için paneller kullanırsınız. Örneğin, hangi fazla gece kullanım taşıyıcısı kullanılacak posta seçeneklerini belirten bir sipariş formunuz olabilir. Bir paneldeki tüm seçenekleri gruplandırmak, kullanıcıya bir mantıksal görsel ipucu verir. Tasarım zamanında tüm denetimler kolayca taşınabilir — <xref:System.Windows.Forms.Panel> denetimini taşıdığınızda, içerdiği tüm denetimler de taşınır. Bir panelde gruplanmış denetimlere <xref:System.Windows.Forms.Control.Controls%2A> özelliği aracılığıyla erişilebilir. Bu özellik bir <xref:System.Windows.Forms.Control> örnekleri koleksiyonu döndürür, bu nedenle genellikle bu şekilde bir denetimi bu şekilde belirli bir türe atamalısınız.  
  
## <a name="panel-versus-groupbox"></a>Panel ve GroupBox  
 <xref:System.Windows.Forms.Panel> denetimi <xref:System.Windows.Forms.GroupBox> denetimine benzerdir; ancak yalnızca <xref:System.Windows.Forms.Panel> denetimi kaydırma çubuklarına sahip olabilir ve yalnızca <xref:System.Windows.Forms.GroupBox> denetimi bir başlık görüntüler.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Kaydırma çubuklarını göstermek için <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> özelliğini `true`olarak ayarlayın. Ayrıca, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>ve <xref:System.Windows.Forms.Panel.BorderStyle%2A> özelliklerini ayarlayarak panelin görünümünü özelleştirebilirsiniz. <xref:System.Windows.Forms.Control.BackColor%2A> ve <xref:System.Windows.Forms.Control.BackgroundImage%2A> özellikleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: bölmenin arka planını ayarlama](how-to-set-the-background-of-a-windows-forms-panel.md). <xref:System.Windows.Forms.Panel.BorderStyle%2A> özelliği, panelin görünür kenarlık (<xref:System.Windows.Forms.BorderStyle.None>), düz çizgi (<xref:System.Windows.Forms.BorderStyle.FixedSingle>) veya gölgeli çizgi (<xref:System.Windows.Forms.BorderStyle.Fixed3D>) olmadan ana hatlarıyla birleştirilmeyeceğini belirler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Panel>
- [GroupBox Denetimi](groupbox-control-windows-forms.md)
- [Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panel Denetimi ile Denetimleri Gruplandırma](group-controls-with-wf-panel-control-using-the-designer.md)
- [Nasıl yapılır: Tasarımcı Kullanarak Windows Forms Panelinin Arka Planını Ayarlama](how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)
