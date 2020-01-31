---
title: "Nasıl yapılır: ToolStripTextBox'nu bir ToolStrip'nin Kalan Genişliğini Kaplayacak Şekilde Genişletme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: c60cc2a377f08a73159f25b2ab5f2812d41f0c10
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742845"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a>Nasıl Yapılır: ToolStripTextBox'nu bir ToolStrip'nin Kalan Genişliğini Kaplayacak Şekilde Genişletme (Windows Forms)
Bir <xref:System.Windows.Forms.ToolStrip> denetiminin <xref:System.Windows.Forms.ToolStrip.Stretch%2A> özelliğini `true`olarak ayarladığınızda denetim, kapsayıcısını uçtan uca doldurur ve kapsayıcısı yeniden boyutlandırdığında yeniden boyutlandırılır. Bu yapılandırmada, denetimdeki bir öğeyi (<xref:System.Windows.Forms.ToolStripTextBox>gibi), kullanılabilir alanı dolduracak ve denetimin yeniden boyutlandırılıp boyutlandırılacağını anlamak için yararlı bulabilirsiniz. Bu uzatma, örneğin Microsoft® Internet Explorer 'da adres çubuğuna benzer görünüm ve davranış elde etmek istiyorsanız yararlı olur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, `ToolStripSpringTextBox`çağrılan <xref:System.Windows.Forms.ToolStripTextBox> türetilmiş bir sınıf sağlar. Bu sınıf, diğer tüm öğelerin Birleşik genişliği çıkarılmasıyla sonra üst <xref:System.Windows.Forms.ToolStrip> denetiminin kullanılabilir genişliğini hesaplamak için <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> yöntemini geçersiz kılar. Bu kod örneği Ayrıca yeni davranışı göstermek için bir <xref:System.Windows.Forms.Form> sınıfı ve bir `Program` sınıfı sağlar.  
  
 [!code-csharp[ToolStripSpringTextBox#00](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- System, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [ToolStrip Denetim, Mimarisi](toolstrip-control-architecture.md)
- [Nasıl yapılır: Bir StatusStrip içinde Spring Özelliğini Etkileşimli Kullanma](how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
