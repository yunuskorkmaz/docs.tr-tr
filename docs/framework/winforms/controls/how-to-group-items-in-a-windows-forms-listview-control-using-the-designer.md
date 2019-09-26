---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimindeki Öğeleri Gruplandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: b63bcd9e5e357db350cc2987e09af84eb58bdcff
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "69039408"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms ListView Denetimindeki Öğeleri Gruplandırma

<xref:System.Windows.Forms.ListView> Denetimin gruplandırma özelliği, gruplar içindeki ilgili öğe kümelerini görüntülemenizi sağlar. Bu gruplar, grup başlıklarını içeren yatay grup üst bilgilerine göre ekranda ayrılır. Öğeleri alfabetik olarak <xref:System.Windows.Forms.ListView> , tarihe göre veya diğer mantıksal gruplandırmalara göre gruplandırarak büyük listeleri daha kolay gezinmek için grupları kullanabilirsiniz. Aşağıdaki görüntüde bazı gruplanmış öğeler gösterilmektedir:

![Tek ve hatta gruplara ayrılmış sayılar.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

Aşağıdaki yordam, bir <xref:System.Windows.Forms.ListView> denetim içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz [. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.

Gruplamayı etkinleştirmek için önce tasarımcıda veya program aracılığıyla bir veya daha <xref:System.Windows.Forms.ListViewGroup> fazla nesne oluşturmanız gerekir. Bir grup tanımlandıktan sonra, ona öğe atayabilirsiniz.

> [!NOTE]
> <xref:System.Windows.Forms.ListView>gruplar yalnızca [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanız <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi çağırdığında kullanılabilir. Önceki işletim sistemlerinde, gruplarla ilgili herhangi bir kodun etkisi yoktur ve gruplar görünmez. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.

## <a name="to-add-or-remove-groups-in-the-designer"></a>Tasarımcıda grup eklemek veya kaldırmak için

1. **Özellikler** penceresinde](./media/visual-studio-ellipsis-button.png)![, özelliğin<xref:System.Windows.Forms.ListView.Groups%2A> yanındaki Visual Studio 'nun Özellikler penceresi (... **) üç nokta (.** ..) düğmesine tıklayın.

     **ListViewGroup koleksiyonu Düzenleyicisi** görünür.

2. Bir grup eklemek için **Ekle** düğmesine tıklayın. Daha sonra, <xref:System.Windows.Forms.ListViewGroup.Header%2A> ve <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> özellikleri gibi yeni grubun özelliklerini ayarlayabilirsiniz. Bir grubu kaldırmak için, seçin ve **Kaldır** düğmesine tıklayın.

## <a name="to-assign-items-to-groups-in-the-designer"></a>Tasarımcı 'daki gruplara öğe atamak için

1. **Özellikler** penceresinde](./media/visual-studio-ellipsis-button.png)![, özelliğin<xref:System.Windows.Forms.ListView.Items%2A> yanındaki Visual Studio 'nun Özellikler penceresi (... **) üç nokta (.** ..) düğmesine tıklayın.

     **ListViewItem koleksiyonu Düzenleyicisi** görünür.

2. Yeni bir öğe eklemek için **Ekle** düğmesine tıklayın. Ardından, <xref:System.Windows.Forms.ListViewItem.Text%2A> ve <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> özellikleri gibi yeni öğenin özelliklerini ayarlayabilirsiniz.

3. <xref:System.Windows.Forms.ListViewItem.Group%2A> Özelliği seçin ve açılan listeden bir grup seçin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [ListView Denetimi](listview-control-windows-forms.md)
- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView denetimiyle öğe ekleme ve kaldırma](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
