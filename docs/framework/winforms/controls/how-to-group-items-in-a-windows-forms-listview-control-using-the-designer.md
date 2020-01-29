---
title: Tasarımcıyı kullanarak ListView denetimindeki öğeleri gruplandırma
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- grouping
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
ms.openlocfilehash: 935d8d75517e1028e686ca229f6ada656f58b01e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736675"
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları ListView Denetimindeki Öğeleri Gruplandırma

<xref:System.Windows.Forms.ListView> denetiminin gruplandırma özelliği, gruplar içindeki ilgili öğe kümelerini görüntülemenizi sağlar. Bu gruplar, grup başlıklarını içeren yatay grup üst bilgilerine göre ekranda ayrılır. Öğeleri alfabetik olarak, tarihe göre veya diğer mantıksal gruplandırmalara göre gruplandırarak büyük listeleri daha kolay gezinmek için <xref:System.Windows.Forms.ListView> gruplarını kullanabilirsiniz. Aşağıdaki görüntüde bazı gruplanmış öğeler gösterilmektedir:

![Tek ve hatta gruplara ayrılmış sayılar.](./media/how-to-group-items-in-a-windows-forms-listview-control-using-the-designer/odd-even-list-view-groups.gif)

Aşağıdaki yordam, bir <xref:System.Windows.Forms.ListView> denetimi içeren bir form ile **Windows uygulama** projesi gerektirir. Böyle bir projeyi ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma Windows Forms uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) ve [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md).

Gruplamayı etkinleştirmek için önce tasarımcıda veya program aracılığıyla bir veya daha fazla <xref:System.Windows.Forms.ListViewGroup> nesnesi oluşturmanız gerekir. Bir grup tanımlandıktan sonra, ona öğe atayabilirsiniz.

## <a name="to-add-or-remove-groups-in-the-designer"></a>Tasarımcıda grup eklemek veya kaldırmak için

1. **Özellikler** penceresinde, <xref:System.Windows.Forms.ListView.Groups%2A> özelliğinin yanındaki Visual Studio 'nun Özellikler penceresi](./media/visual-studio-ellipsis-button.png)) düğmesine **üç nokta**![(...) düğmesini tıklatın.

     **ListViewGroup koleksiyonu Düzenleyicisi** görünür.

2. Bir grup eklemek için **Ekle** düğmesine tıklayın. Daha sonra, <xref:System.Windows.Forms.ListViewGroup.Header%2A> ve <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A> özellikleri gibi yeni grubun özelliklerini ayarlayabilirsiniz. Bir grubu kaldırmak için, seçin ve **Kaldır** düğmesine tıklayın.

## <a name="to-assign-items-to-groups-in-the-designer"></a>Tasarımcı 'daki gruplara öğe atamak için

1. **Özellikler** penceresinde, <xref:System.Windows.Forms.ListView.Items%2A> özelliğinin yanındaki Visual Studio 'nun Özellikler penceresi](./media/visual-studio-ellipsis-button.png)) düğmesine **üç nokta**![(...) düğmesini tıklatın.

     **ListViewItem koleksiyonu Düzenleyicisi** görünür.

2. Yeni bir öğe eklemek için **Ekle** düğmesine tıklayın. Daha sonra, <xref:System.Windows.Forms.ListViewItem.Text%2A> ve <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> özellikleri gibi yeni öğenin özelliklerini ayarlayabilirsiniz.

3. <xref:System.Windows.Forms.ListViewItem.Group%2A> özelliğini seçin ve açılan listeden bir grup seçin.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.Groups%2A>
- <xref:System.Windows.Forms.ListViewGroup>
- [ListView Denetimi](listview-control-windows-forms.md)
- [ListView Denetimine Genel Bakış](listview-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
