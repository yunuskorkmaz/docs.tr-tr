---
title: 'Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimine Veri Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
ms.openlocfilehash: 609878416be26786ce865168c996c78e18b1897f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917883"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGridView Denetimine Veri Bağlama
Tasarımcı kullanarak veritabanları, iş nesneleri veya Web <xref:System.Windows.Forms.DataGridView> hizmetleri gibi çeşitli farklı variclarınızın veri kaynaklarına bir denetim bağlayabilirsiniz. Tasarımcıyı kullanarak denetimi bir veri kaynağına bağladığınızda, denetim otomatik olarak veri kaynağını temsil eden bir <xref:System.Windows.Forms.BindingSource> bileşene bağlanır. Ayrıca, veri kaynağı tarafından belirtilen şema bilgilerini eşleştirmek için, sütunlarda otomatik olarak sütunlar oluşturulur.

 Sütunlar oluşturulduktan sonra gereksinimlerinizi karşılayacak şekilde değişiklik yapabilirsiniz. Örneğin, görüntüleme konusunda İlgilendiğiniz sütunları kaldırabilir veya gizleyebilirsiniz, sütunları yeniden düzenleyebilir veya sütun türlerini değiştirebilirsiniz. Sütunları değiştirme hakkında daha fazla bilgi için Ayrıca bkz. bölümünde listelenen konulara bakın.

 Ayrıca, ana/ayrıntı <xref:System.Windows.Forms.DataGridView> ilişkileri oluşturmak için ilgili tablolara birden fazla denetim bağlayabilirsiniz. Bu yapılandırmada, bir denetim üst tablo görüntüler ve başka bir denetim, yalnızca üst tablodaki geçerli satırla ilişkili bir alt tablodaki satırları görüntüler. Daha fazla bilgi için [nasıl yapılır: Windows Forms bir uygulamada](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))ilgili verileri görüntüleme.

 Aşağıdaki yordam, bir ana/ayrıntı ilişkisi için <xref:System.Windows.Forms.DataGridView> denetim veya iki denetim içeren bir form içeren bir **Windows uygulama** projesi gerektirir. Böyle bir projeyi başlatma hakkında daha fazla bilgi için [bkz. nasıl yapılır: Windows Forms bir uygulama projesi](/visualstudio/ide/step-1-create-a-windows-forms-application-project) oluşturun ve [şunları yapın: Windows Forms](how-to-add-controls-to-windows-forms.md)denetimleri ekleyin.

## <a name="to-bind-the-control-to-a-data-source"></a>Denetimi bir veri kaynağına bağlamak için

1. <xref:System.Windows.Forms.DataGridView> Denetimin sağ üst köşesindeki akıllı etiket simgesine (![akıllı etiket karakter](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) tıklayın.

2. **Veri kaynağı seç** seçeneğinin açılır okuna tıklayın.

3. Projenizde zaten bir veri kaynağı yoksa, **proje veri kaynağı Ekle** ' ye tıklayın ve sihirbazın gösterdiği adımları izleyin.

     Daha fazla bilgi için bkz. [veri kaynağı Yapılandırma Sihirbazı](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/w4dd7z6t(v=vs.120)). Yeni veri kaynağınız, **veri kaynağı seç** açılır penceresinde görünür. Yeni veri kaynağınız tek bir veritabanı tablosu gibi yalnızca bir üye içeriyorsa denetim otomatik olarak bu üyeye bağlanır. Aksi halde, bir sonraki adıma devam edin.

4. Henüz genişletilmemişse **diğer veri kaynaklarını** ve **proje veri kaynakları** düğümlerini genişletin ve sonra denetimin bağlanacağı veri kaynağını seçin.

5. Veri kaynağınız birden fazla üye içeriyorsa (örneğin, birden çok tablo içeren bir <xref:System.Data.DataSet?displayProperty=nameWithType> oluşturduysanız), veri kaynağını genişletin ve sonra bağlanacak belirli üyeyi seçin.

6. Ana/ayrıntı ilişkisi oluşturmak için, ikinci <xref:System.Windows.Forms.DataGridView> bir <xref:System.Windows.Forms.BindingSource> denetim için **veri kaynağı seç** açılır penceresinde, üst tablo için oluşturulan öğesini genişletin ve gösterilen listeden ilgili alt tabloyu seçin.

    > [!NOTE]
    > Projenizde bir veri kaynağı zaten varsa, veri **kaynakları** penceresini bir veri formu oluşturmak için de kullanabilirsiniz. Daha fazla bilgi için bkz. [veri kaynakları penceresi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120)).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- [Nasıl yapılır: Bir veritabanındaki verilere bağlanma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))
- [Nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView denetiminde sütun ekleme ve kaldırma](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView Denetimindeki sütunların sırasını değiştirme](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGridView sütununun türünü değiştirme](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)
- [Nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView Denetimindeki sütunları dondurma](freeze-columns-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView Denetimindeki sütunları gizleme](hide-columns-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Tasarımcı kullanarak sütunları Windows Forms DataGridView denetiminde Salt okunabilir hale getirme](make-columns-read-only-in-the-datagrid-using-the-designer.md)
- [Nasıl yapılır: Windows Forms uygulama projesi oluşturma](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Nasıl yapılır: Windows Forms denetim ekleme](how-to-add-controls-to-windows-forms.md)
- [Veri kaynakları penceresi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
- [Nasıl yapılır: Windows Forms uygulamasında Ilgili verileri görüntüleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))
