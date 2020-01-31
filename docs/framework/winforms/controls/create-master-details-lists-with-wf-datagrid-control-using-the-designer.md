---
title: Tasarımcı kullanarak DataGrid denetimiyle ana Ayrıntılar listeleri oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: 0dea3dd88a8c6c2aceb894789ace8ef3b5c83632
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743390"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları DataGrid Denetimi ile Ana-Ayrıntılar Listeleri Oluşturma

> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 <xref:System.Data.DataSet>, bir dizi ilişkili tablo içeriyorsa, verileri bir ana ayrıntı biçiminde göstermek için iki <xref:System.Windows.Forms.DataGrid> denetimi kullanabilirsiniz. Bir <xref:System.Windows.Forms.DataGrid> ana kılavuz olarak, ikincisi ise ayrıntılar kılavuzu olacak şekilde belirlenir. Ana listede bir giriş seçtiğinizde, ilgili alt girdilerin hepsi Ayrıntılar listesinde gösterilir. Örneğin, <xref:System.Data.DataSet> bir müşteriler tablosu ve ilgili siparişler tablosu içeriyorsa, müşteriler tablosunu ana kılavuz ve siparişler tablosunun ayrıntılar kılavuzu olacak şekilde belirtirsiniz. Ana kılavuzdan bir müşteri seçildiğinde, Siparişler tablosunda bu müşteriyle ilişkili tüm siparişler Ayrıntılar kılavuzunda görüntülenir.

 Aşağıdaki yordam, bir **Windows uygulama** projesi (**Dosya** > **Yeni** > **projesi** > **görsel C#**  veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulaması**) gerektirir.

## <a name="to-create-a-master-details-list-in-the-designer"></a>Tasarımcıda ana ayrıntılar listesi oluşturmak için

1. Forma iki <xref:System.Windows.Forms.DataGrid> denetimi ekleyin. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md). Visual Studio 2005 ' de, <xref:System.Windows.Forms.DataGrid> denetimi **araç kutusunda** varsayılan olarak değildir. Daha fazla bilgi için bkz. [nasıl yapılır: araç kutusuna öğe ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

    > [!NOTE]
    > Aşağıdaki adımlar, tasarım zamanı veri bağlama için **veri kaynakları** penceresini kullanan Visual Studio 2005 için geçerli değildir. Daha fazla bilgi için bkz. [Visual Studio 'da verileri denetimlere bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) ve [nasıl yapılır: Windows Forms uygulamasında ilgili verileri görüntüleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120)).

2. **Sunucu Gezgini** iki veya daha fazla tabloyu forma sürükleyin.

3. Veri menüsünde **veri** **kümesi oluştur**' u seçin.

4. XML tasarımcısını kullanarak tablolar arasındaki ilişkileri ayarlayın. Ayrıntılar için MSDN 'de "nasıl yapılır: XML şemalarda ve veri kümelerinde bire çok Ilişkiler oluşturma" konusuna bakın.

5. **Dosya** menüsünden **Tümünü Kaydet** ' i seçerek ilişkileri kaydedin.

6. Ana Kılavuzu atamak istediğiniz <xref:System.Windows.Forms.DataGrid> denetimini şu şekilde yapılandırın:

    1. <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliğindeki aşağı açılan listeden <xref:System.Data.DataSet> seçin.

    2. <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliğindeki açılan listeden ana tabloyu (örneğin, "müşteriler") seçin.

7. Ayrıntılar kılavuzunu atamak istediğiniz <xref:System.Windows.Forms.DataGrid> denetimini şu şekilde yapılandırın:

    1. <xref:System.Windows.Forms.DataGrid.DataSource%2A> özelliğindeki aşağı açılan listeden <xref:System.Data.DataSet> seçin.

    2. <xref:System.Windows.Forms.DataGrid.DataMember%2A> özelliğindeki açılan listeden ana ve ayrıntı tabloları arasında ilişkiyi (örneğin, "Customers. CustOrd") seçin. İlişkiyi görmek için, açılan listede ana tablonun yanındaki artı ( **+** ) işaretine tıklayarak düğümü genişletin.

## <a name="see-also"></a>Ayrıca bkz.

- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [DataGrid Denetimine Genel Bakış](datagrid-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
