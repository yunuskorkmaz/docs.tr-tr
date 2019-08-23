---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ile Çok Bölmeli bir Kullanıcı Arabirimi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- user interface [Windows Forms], multipane
- SplitContainer control [Windows Forms], using the designer
- multipane user interface
ms.assetid: c3f9294d-a26c-4198-9242-f237f55f7573
ms.openlocfilehash: 97888a77dfc731be591d5f0284e87f45ef7dc437
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930174"
---
# <a name="how-to-create-a-multipane-user-interface-with-windows-forms-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ile Çok Bölmeli bir Kullanıcı Arabirimi Oluşturma
Aşağıdaki yordamda, Microsoft Outlook 'ta kullanılan bir **klasör** listesi, **Iletiler** bölmesi ve **Önizleme** bölmesi ile benzer bir çoklu bölmeli Kullanıcı arabirimi oluşturacaksınız. Bu düzenleme, formla birlikte yerleştirme denetimleri aracılığıyla oyda elde edilir.

 Bir denetimi yuvadığınızda, üst kapsayıcının bir denetimin hangi kenarının ' a ekleneceğini belirlersiniz. Bu nedenle, <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini olarak <xref:System.Windows.Forms.DockStyle.Right>ayarlarsanız, denetimin sağ kenarı üst denetiminin sağ kenarına yerleştirilir. Ayrıca, denetimin yerleşik kenarı kapsayıcı denetimiyle eşleşecek şekilde yeniden boyutlandırılır. <xref:System.Windows.Forms.SplitContainer.Dock%2A> Özelliğin nasıl çalıştığı hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms](how-to-dock-controls-on-windows-forms.md)denetimleri yerleştirme.

 Bu yordam, <xref:System.Windows.Forms.SplitContainer> uygulamanın Microsoft Outlook 'u taklit etmek için işlev ekleme üzerine değil, formdaki ve diğer denetimlerin düzenlenmesi üzerine odaklanır.

 Bu Kullanıcı arabirimini oluşturmak için, tüm denetimleri sol bölmede bir <xref:System.Windows.Forms.SplitContainer> <xref:System.Windows.Forms.TreeView> denetim içeren bir denetimin içine yerleştirebilirsiniz. <xref:System.Windows.Forms.SplitContainer> Denetimin sağ paneli bir <xref:System.Windows.Forms.ListView> <xref:System.Windows.Forms.SplitContainer> denetimin<xref:System.Windows.Forms.RichTextBox> üzerinde denetime sahip ikinci bir denetim içerir. Bu <xref:System.Windows.Forms.SplitContainer> denetimler formdaki diğer denetimlerin bağımsız yeniden boyutlandırılmasını etkinleştirir. Kendi özel kullanıcı arabirimlerini daha fazla yapmak için bu yordamın tekniklerini uyarlayabilirsiniz.

## <a name="to-create-an-outlook-style-user-interface-at-design-time"></a>Tasarım zamanında Outlook stili bir kullanıcı arabirimi oluşturmak için

1. Yeni bir Windows uygulaması projesi oluşturma (**Dosya** > **Yeni** > **Proje** > **görseli C#**  veya **Visual Basic** > **Klasik** Masaüstü >  **Windows Forms uygulama**).

2. <xref:System.Windows.Forms.SplitContainer> **Araç kutusundan** bir denetimi forma sürükleyin. **Özellikler** penceresinde, <xref:System.Windows.Forms.SplitContainer.Dock%2A> özelliğini olarak <xref:System.Windows.Forms.DockStyle.Fill>ayarlayın.

3. **Araç kutusu** ' ndan denetimin sol paneline <xref:System.Windows.Forms.SplitContainer> bir <xref:System.Windows.Forms.TreeView> denetim sürükleyin. **Özellikler** penceresinde, aşağı oka tıklandığında gösterilen <xref:System.Windows.Forms.SplitContainer.Dock%2A> değer düzenleyicisinde <xref:System.Windows.Forms.DockStyle.Left> sol panele tıklayarak özelliğini olarak ayarlayın.

4. <xref:System.Windows.Forms.SplitContainer> **Araç kutusundan**başka bir denetim sürükleyin; formunuza eklediğiniz <xref:System.Windows.Forms.SplitContainer> denetimin sağ paneline koyun. **Özellikler** penceresinde <xref:System.Windows.Forms.SplitContainer.Dock%2A> , <xref:System.Windows.Forms.DockStyle.Fill> özelliğinive<xref:System.Windows.Forms.Orientation.Horizontal>özelliğiniolarakayarlayın. <xref:System.Windows.Forms.SplitContainer.Orientation%2A>

5. <xref:System.Windows.Forms.ListView> **Araç kutusundan** bir denetimi formunuza eklediğiniz ikinci <xref:System.Windows.Forms.SplitContainer> denetimin üst paneline sürükleyin. Denetiminin özelliğini olarak<xref:System.Windows.Forms.DockStyle.Fill>ayarlayın. <xref:System.Windows.Forms.SplitContainer.Dock%2A> <xref:System.Windows.Forms.ListView>

6. <xref:System.Windows.Forms.RichTextBox> **Araç kutusundan** bir denetimi ikinci <xref:System.Windows.Forms.SplitContainer> denetimin alt paneline sürükleyin. Denetiminin özelliğini olarak<xref:System.Windows.Forms.DockStyle.Fill>ayarlayın. <xref:System.Windows.Forms.SplitContainer.Dock%2A> <xref:System.Windows.Forms.RichTextBox>

     Bu noktada, uygulamayı çalıştırmak için F5 tuşuna basarsanız, form Microsoft Outlook 'a benzer şekilde üç bölümden oluşan bir kullanıcı arabirimi görüntüler.

    > [!NOTE]
    > Fare işaretçisini <xref:System.Windows.Forms.SplitContainer> denetimlerin içindeki bölümlendiricileri üzerine getirdiğinizde, iç boyutları yeniden boyutlandırabilirsiniz.

Uygulama geliştirmede bu noktada, gelişmiş bir kullanıcı arabirimi oluşturduysanız. Bir sonraki adım, <xref:System.Windows.Forms.TreeView> denetimin ve <xref:System.Windows.Forms.ListView> denetimlerin bir tür veri kaynağına bağlanarak uygulamanın kendisini programlamaya devam eder. Denetimleri verilere bağlama hakkında daha fazla bilgi için bkz. [veri bağlama ve Windows Forms](../data-binding-and-windows-forms.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer Denetimi](splitcontainer-control-windows-forms.md)
