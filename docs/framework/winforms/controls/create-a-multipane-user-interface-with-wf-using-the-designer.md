---
title: Tasarımcıyı kullanarak çok Bölbir Kullanıcı arabirimi oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: 6b41d538f1cd1633cec51c89e27adf3c5b47f9a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737282"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ile Çok Bölmeli bir Kullanıcı Arabirimi Oluşturma
Aşağıdaki yordamda, Microsoft Outlook 'ta kullanılan bir **klasör** listesi, **Iletiler** bölmesi ve **Önizleme** bölmesi ile benzer bir çoklu bölmeli Kullanıcı arabirimi oluşturacaksınız. Bu düzenleme, formla birlikte yerleştirme denetimleri aracılığıyla oyda elde edilir.

 Bir denetimi yuvadığınızda, üst kapsayıcının bir denetimin hangi kenarının ' a ekleneceğini belirlersiniz. Bu nedenle, <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Right>olarak ayarlarsanız, denetimin sağ kenarı üst denetiminin sağ kenarına yerleştirilir. Ayrıca, denetimin yerleşik kenarı kapsayıcı denetimiyle eşleşecek şekilde yeniden boyutlandırılır. <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğinin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [nasıl yapılır: denetimleri yerleştirme Windows Forms](how-to-dock-controls-on-windows-forms.md).

 Bu yordam, uygulamanın Microsoft Outlook 'U taklit etmek için işlev ekleme üzerine değil, <xref:System.Windows.Forms.SplitContainer> ve formdaki diğer denetimleri düzenleme konusunda odaklanır.

 Bu Kullanıcı arabirimini oluşturmak için, tüm denetimleri sol bölmedeki bir <xref:System.Windows.Forms.TreeView> denetimi içeren bir <xref:System.Windows.Forms.SplitContainer> denetimine yerleştirebilirsiniz. <xref:System.Windows.Forms.SplitContainer> denetiminin sağ paneli, bir <xref:System.Windows.Forms.RichTextBox> denetiminin üzerinde <xref:System.Windows.Forms.ListView> denetimine sahip ikinci bir <xref:System.Windows.Forms.SplitContainer> denetimi içerir. Bu <xref:System.Windows.Forms.SplitContainer> denetimleri, formdaki diğer denetimlerin bağımsız yeniden boyutlandırılmasını etkinleştirir. Kendi özel kullanıcı arabirimlerini daha fazla yapmak için bu yordamın tekniklerini uyarlayabilirsiniz.

## <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Tasarım zamanında Outlook stili bir kullanıcı arabirimi oluşturmak için

1. Yeni bir Windows uygulaması projesi oluşturun (**Dosya** > **Yeni** > **projesi** > **Visual C#**  veya **Visual Basic** > **Klasik Masaüstü** > Windows Forms **uygulaması**).

2. **Araç kutusundan** bir <xref:System.Windows.Forms.SplitContainer> denetimini forma sürükleyin. **Özellikler** penceresinde <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>olarak ayarlayın.

3. **Araç kutusundan** bir <xref:System.Windows.Forms.TreeView> denetimini <xref:System.Windows.Forms.SplitContainer> denetiminin sol bölmesine sürükleyin. **Özellikler** penceresinde, aşağı oka tıklandığında gösterilen değer düzenleyicisinde sol panele tıklayarak <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Left> olarak ayarlayın.

4. **Araç kutusundan**başka bir <xref:System.Windows.Forms.SplitContainer> denetimini sürükleyin; formunuza eklediğiniz <xref:System.Windows.Forms.SplitContainer> denetimin sağ paneline yerleştirin. **Özellikler** penceresinde, <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill> ve <xref:System.Windows.Forms.SplitContainer.Orientation%2A> özelliğini <xref:System.Windows.Forms.Orientation.Horizontal>olarak ayarlayın.

5. **Araç kutusundan** bir <xref:System.Windows.Forms.ListView> denetimini formunuza eklediğiniz ikinci <xref:System.Windows.Forms.SplitContainer> denetiminin üst paneline sürükleyin. <xref:System.Windows.Forms.ListView> denetiminin <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>olarak ayarlayın.

6. **Araç kutusundan** bir <xref:System.Windows.Forms.RichTextBox> denetimini ikinci <xref:System.Windows.Forms.SplitContainer> denetiminin alt paneline sürükleyin. <xref:System.Windows.Forms.RichTextBox> denetiminin <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini <xref:System.Windows.Forms.DockStyle.Fill>olarak ayarlayın.

     Bu noktada, uygulamayı çalıştırmak için F5 tuşuna basarsanız, form Microsoft Outlook 'a benzer şekilde üç bölümden oluşan bir kullanıcı arabirimi görüntüler.

    > [!NOTE]
    > Fare işaretçisini <xref:System.Windows.Forms.SplitContainer> denetimleri içindeki bölümlendiricileri üzerine getirdiğinizde, iç boyutları yeniden boyutlandırabilirsiniz.

Uygulama geliştirmede bu noktada, gelişmiş bir kullanıcı arabirimi oluşturduysanız. Bir sonraki adım, <xref:System.Windows.Forms.TreeView> denetimini ve <xref:System.Windows.Forms.ListView> denetimlerini bir tür veri kaynağına bağlayarak uygulamanın kendisini programlamaya devam eder. Denetimleri verilere bağlama hakkında daha fazla bilgi için bkz. [veri bağlama ve Windows Forms](../data-binding-and-windows-forms.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer Denetimi](splitcontainer-control-windows-forms.md)
