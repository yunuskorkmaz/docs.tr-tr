---
title: Veri Bağlama ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- data [Windows Forms], data binding
- reports [Windows Forms], Windows Forms
- lookup tables [Windows Forms], data binding
- data [Windows Forms], complex data binding
- data binding [Windows Forms], Windows Forms
- data [Windows Forms], simple data binding
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: 419aac5e-819b-4aad-88b0-73a2f8c0bd27
ms.openlocfilehash: 3d420e5cb4d9e7f2ad6f8136b8dd33f5901326d2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095496"
---
# <a name="data-binding-and-windows-forms"></a>Veri Bağlama ve Windows Forms
Windows Forms'ta yalnızca geleneksel veri kaynaklarına da bağlayabilirsiniz, ancak Ayrıca verileri içeren neredeyse her yapı için. Çalışma zamanında hesaplamak, bir dosyadan okunan veya diğer denetimlerin değerleri türetilen değerler dizisi bağlayabilirsiniz.  
  
 Ayrıca, herhangi bir denetime herhangi bir özelliği veri kaynağına da bağlayabilirsiniz. Geleneksel veri bağlamasında, genellikle görüntü özelliği bağlamak — Örneğin, <xref:System.Windows.Forms.Control.Text%2A> özelliği bir <xref:System.Windows.Forms.TextBox> denetim — veri kaynağı. İle [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], ayrıca diğer özelliklerini de bağlama aracılığıyla ayarlama seçeneğiniz de vardır. Bağlama, aşağıdaki görevleri gerçekleştirmek için kullanabilirsiniz:  
  
-   Grafiği bir görüntü denetiminin ayarlanıyor.  
  
-   Bir veya daha fazla denetim arka plan rengini ayarlama.  
  
-   Denetimleri boyutunu ayarlama.  
  
 Esas olarak, veri bağlama herhangi bir çalışma zamanı erişilebilir özelliği herhangi bir form denetiminin ayarlanmasından otomatik bir yolu var.  
  
## <a name="types-of-data-binding"></a>Veri bağlama türü  
 Windows Forms veri bağlama iki tür bir avantajlarından faydalanabilirsiniz: basit bağlama ve karmaşık bağlama. Her farklı avantajlar sunar.  
  
|Veri bağlama türü|Açıklama|  
|--------------------------|-----------------|  
|Basit veri bağlama|Bir veri kümesi tablodaki bir sütundaki bir değer gibi bir tek veri öğesine bağlamak için bir denetim yeteneğidir. Bu tür denetimler için tipik bağlantı olduğu gibi bir <xref:System.Windows.Forms.TextBox> denetim veya <xref:System.Windows.Forms.Label> genellikle yalnızca tek bir değer görüntüler denetimleri denetimi. Aslında, bir denetim üzerinde herhangi bir özelliği bir veritabanında bir alana bağlı olabilir. Visual Studio'da bu özellik için kapsamlı desteği yoktur.<br /><br /> Daha fazla bilgi için bkz.:<br /><br /> -   [Veri bağlama ile ilgili arabirimler](interfaces-related-to-data-binding.md)<br />-   [Nasıl Yapılır: Windows Forms'ta verilerde gezinme](how-to-navigate-data-in-windows-forms.md)<br />-   [Nasıl Yapılır: Bir Windows formunda basit bağlantılı denetim oluşturma](how-to-create-a-simple-bound-control-on-a-windows-form.md)|  
|Karmaşık veri bağlama|Birden fazla veri öğesi, genellikle birden fazla kayıtla bir veritabanında bağlamak için bir denetim yeteneğidir. Karmaşık bağlama, liste tabanlı bağlama olarak da adlandırılır. Karmaşık bağlamayı destekleyen denetimleri örnekler <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.ListBox>, ve <xref:System.Windows.Forms.ComboBox> kontrol eder. Karmaşık veri bağlama bir örnek için bkz [nasıl yapılır: Bir Windows Forms ComboBox veya ListBox denetimini verilere bağlama](./controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md).|  
  
## <a name="bindingsource-component"></a>BindingSource Bileşeni  
 Veri bağlama işlemini basitleştirmek için Windows Forms bir veri kaynağına bağlama sayesinde <xref:System.Windows.Forms.BindingSource> bileşeni ve bağlama denetimlerini <xref:System.Windows.Forms.BindingSource>. Kullanabileceğiniz <xref:System.Windows.Forms.BindingSource> basit veya karmaşık bağlama senaryolarda. Her iki durumda da <xref:System.Windows.Forms.BindingSource> bildirim para birimi yönetimi ve diğer hizmetleri sağlama bağlama denetimleri ve veri kaynağı arasında aracı görevi görür değiştirin.  
  
## <a name="common-scenarios-that-employ-data-binding"></a>Veri bağlama Görevlendirmek yaygın senaryoları  
 Neredeyse tüm ticari bir uygulamaya, bir tür ya da başka veri kaynaklarından veri bağlama aracılığıyla genellikle okunan bilgileri kullanır. Aşağıdaki listede, birkaç veri bağlama verilerini sunumu ve düzenleme iletişim yöntemi olarak kullanan en yaygın senaryolar gösterilmektedir.  
  
|Senaryo|Açıklama|  
|--------------|-----------------|  
|Raporlama|Raporları görüntülemek ve verilerinizi yazdırılan belgede özetlemek esnek bir yol sağlar. Seçili içerikleri ekranına veya yazıcı için bir veri kaynağının yazdıran bir rapor oluşturmak için çok yaygındır. Sık kullanılan raporlar listeleri, faturaları ve özetleri içerir. Öğeleri genellikle her bir liste öğesi altında düzenlenmiş alt öğeleri ile listeleri, sütunlara biçimlendirilir ancak verileri en uygun Düzen seçmeniz gerekir.|  
|Veri girişi|Bir ortak ilgili verileri büyük miktarlarda girin veya kullanıcıların bilgi istemek için bir veri giriş formunu yoludur. Kullanıcılar, bilgileri girin veya metin kutuları, seçenek düğmeleri, açılan listeleri ve onay kutularını kullanarak seçim. Bilgileri sonra gönderilen ve yapısını girmiş bilgiyi temel alan bir veritabanında depolanır.|  
|Ana/ayrıntı ilişkisi|Ana/ayrıntılı uygulama ilgili verilere baktığımızda bir biçimidir. Özellikle, iki tablo veri bağlamayı bir ilişkisi vardır: Klasik iş örneği, "Müşteri" tablosu ve onlara bağlama müşteriler ve bunların ilgili Siparişler arasında bir ilişki ile "Siparişler" bir tablo. İki Windows Forms ile ana/ayrıntılı uygulama oluşturma hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridView> denetimlerini, [nasıl yapılır: İki Windows Forms DataGridView denetimi kullanarak ana/ayrıntı formu oluşturma](./controls/create-a-master-detail-form-using-two-datagridviews.md)|  
|Arama tablosu|Başka bir ortak veri sunu/işleme tablosu aramasında bir senaryodur. Genellikle, daha büyük bir veri görünen bir parçası olarak bir <xref:System.Windows.Forms.ComboBox> denetimi görüntülemek ve veri işlemek için kullanılır. İçinde görüntülenen verileri anahtardır <xref:System.Windows.Forms.ComboBox> denetimidir veritabanına yazılan veriler farklı. Örneğin, bir <xref:System.Windows.Forms.ComboBox> öğeleri görüntüleyen bir denetimi Market kullanılabilir, büyük olasılıkla ürünlerin (ekmek, sütlü, örneğin sucuklu) adlarını görmek istediğiniz. Ancak, veritabanı içinde ve veritabanı normalleştirmesi için bilgi alma kolaylaştırmak için büyük olasılıkla bilgi belirli bir sırada belirli öğeler için öğesi numaraları saklayacağından (#501, #603 vb.). Bu nedenle, Market öğesinde "kolay adı" arasında örtük bir bağlantı yoktur <xref:System.Windows.Forms.ComboBox> formunuza ve bir sırada mevcut olan ilgili öğe numarası üzerinde denetim. Bu tablo arama olduğu. Daha fazla bilgi için [nasıl yapılır: Windows Forms BindingSource bileşeniyle arama tablosu oluşturma](./controls/how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component.md).|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Binding>
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
- [Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama](./controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [BindingSource Bileşeni](./controls/bindingsource-component.md)
