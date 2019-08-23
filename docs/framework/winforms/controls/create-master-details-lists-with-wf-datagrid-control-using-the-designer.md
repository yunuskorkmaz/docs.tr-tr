---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimi ile Ana-Ayrıntılar Listeleri Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: 3962b671176ad158b338889140181834e05bbeee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929721"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimi ile Ana-Ayrıntılar Listeleri Oluşturma

> [!NOTE]
> Denetim yerini alır ve <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGrid> denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView> Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 Bir dizi ilişkili tablo <xref:System.Windows.Forms.DataGrid> içeriyorsa,verilerianaayrıntıbiçimindegöstermekiçinikidenetimkullanabilirsiniz.<xref:System.Data.DataSet> Biri <xref:System.Windows.Forms.DataGrid> ana kılavuz olarak, ikincisi ise ayrıntılar kılavuzu olacak şekilde belirlenir. Ana listede bir giriş seçtiğinizde, ilgili alt girdilerin hepsi Ayrıntılar listesinde gösterilir. Örneğin, <xref:System.Data.DataSet> bir müşteriler tablosu ve ilgili siparişler tablosu içeriyorsa, müşteriler tablosunu ana kılavuz ve Siparişler tablosu olarak ayrıntılar kılavuzu olacak şekilde belirtirsiniz. Ana kılavuzdan bir müşteri seçildiğinde, Siparişler tablosunda bu müşteriyle ilişkili tüm siparişler Ayrıntılar kılavuzunda görüntülenir.

 Aşağıdaki yordam bir **Windows uygulaması** projesi gerektirir (**Dosya** > **Yeni** > **Proje** > **görseli C#**  veya **Visual Basic**  >   **Klasik Masaüstü** > **Windows Forms uygulaması**).

## <a name="to-create-a-master-details-list-in-the-designer"></a>Tasarımcıda ana ayrıntılar listesi oluşturmak için

1. Forma iki <xref:System.Windows.Forms.DataGrid> denetim ekleyin. Daha fazla bilgi için [nasıl yapılır: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin. Visual Studio 2005 ' de, <xref:System.Windows.Forms.DataGrid> denetim **araç kutusunda** varsayılan olarak değildir. Daha fazla bilgi için [nasıl yapılır: Araç kutusuna](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))öğe ekleyin.

    > [!NOTE]
    > Aşağıdaki adımlar, tasarım zamanı veri bağlama için **veri kaynakları** penceresini kullanan Visual Studio 2005 için geçerli değildir. Daha fazla bilgi için bkz. [Visual Studio 'da verileri denetimlere bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) ve [nasıl yapılır: Windows Forms bir uygulamada](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))ilgili verileri görüntüleme.

2. **Sunucu Gezgini** iki veya daha fazla tabloyu forma sürükleyin.

3. Veri menüsünde **veri** **kümesi oluştur**' u seçin.

4. XML tasarımcısını kullanarak tablolar arasındaki ilişkileri ayarlayın. Ayrıntılar için bkz. "nasıl yapılır: MSDN 'de XML şemalarda ve veri kümelerinde bire çok Ilişkiler oluşturun.

5. **Dosya** menüsünden **Tümünü Kaydet** ' i seçerek ilişkileri kaydedin.

6. Ana kılavuzunu atamak istediğiniz denetimişuşekildeyapılandırın:<xref:System.Windows.Forms.DataGrid>

    1. Özelliğindekiaçılan<xref:System.Windows.Forms.DataGrid.DataSource%2A> listeden öğesini seçin. <xref:System.Data.DataSet>

    2. <xref:System.Windows.Forms.DataGrid.DataMember%2A> Özelliğindeki açılan listeden ana tabloyu (örneğin, "müşteriler") seçin.

7. Ayrıntılar kılavuzunu atamak istediğiniz denetimişuşekildeyapılandırın:<xref:System.Windows.Forms.DataGrid>

    1. Özelliğindekiaçılan<xref:System.Windows.Forms.DataGrid.DataSource%2A> listeden öğesini seçin. <xref:System.Data.DataSet>

    2. <xref:System.Windows.Forms.DataGrid.DataMember%2A> Özelliğindeki açılan listeden ana ve ayrıntı tabloları arasındaki ilişkiyi (örneğin, "Customers. CustOrd") seçin. İlişkiyi görmek için, açılan listede ana tablonun yanındaki artı ( **+** ) işaretine tıklayarak düğümü genişletin.

## <a name="see-also"></a>Ayrıca bkz.

- [DataGrid Denetimi](datagrid-control-windows-forms.md)
- [DataGrid Denetimine Genel Bakış](datagrid-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms DataGrid denetimini bir veri kaynağına bağlama](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
