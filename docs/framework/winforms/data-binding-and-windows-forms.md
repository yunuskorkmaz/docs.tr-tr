---
title: Veri Bağlama
description: Çalışma zamanında hesaplacağınız, bir dosyadan okunan veya Windows Forms diğer denetimlerin değerlerinden türeten bir dizi değere bağlamayı öğrenin.
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
ms.openlocfilehash: 78e8a3287c565cfa7dae56b68c0eb57f48c30ea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619669"
---
# <a name="data-binding-and-windows-forms"></a>Veri Bağlama ve Windows Forms
Windows Forms ' de, yalnızca geleneksel veri kaynaklarına değil, verileri içeren bir yapıya de bağlanabilirsiniz. Çalışma zamanında hesaplacağınız, bir dosyadan okunan veya diğer denetimlerin değerlerinden türeten bir değerler dizisine bağlayabilirsiniz.  
  
 Ayrıca, herhangi bir denetimin herhangi bir özelliğini veri kaynağına bağlayabilirsiniz. Geleneksel veri bağlamasında, genellikle görüntüleme özelliğini — Örneğin, <xref:System.Windows.Forms.Control.Text%2A> bir <xref:System.Windows.Forms.TextBox> denetimin özelliğini — veri kaynağına bağlarsınız. .NET Framework, diğer özellikleri de bağlama aracılığıyla ayarlama seçeneğiniz de vardır. Aşağıdaki görevleri gerçekleştirmek için bağlamayı kullanabilirsiniz:  
  
- Görüntü denetiminin grafiğini ayarlama.  
  
- Bir veya daha fazla denetimin arka plan rengini ayarlama.  
  
- Denetimlerin boyutunu ayarlama.  
  
 Esas olarak, veri bağlama, form üzerinde herhangi bir denetimin çalışma zamanı erişilebilir özelliğini ayarlamanın otomatik bir yoludur.  
  
## <a name="types-of-data-binding"></a>Veri bağlama türleri  
 Windows Forms, iki tür veri bağlama özelliğinden yararlanabilir: basit bağlama ve karmaşık bağlama. Her biri farklı avantajlar sunar.  
  
|Veri bağlamanın türü|Açıklama|  
|--------------------------|-----------------|  
|Basit veri bağlama|Bir denetimin veri kümesi tablosundaki bir sütundaki değer gibi tek bir veri öğesine bağlanması özelliği. Bu, <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.Label> genellikle yalnızca tek bir değeri görüntüleyen denetimler olan denetim veya denetim gibi denetimler için tipik bağlama türüdür. Aslında, bir denetimdeki herhangi bir özellik, veritabanındaki bir alana bağlanabilir. Visual Studio 'da bu özellik için kapsamlı destek vardır.<br /><br /> Daha fazla bilgi için bkz.<br /><br /> -   [Veri bağlama ile Ilgili arabirimler](interfaces-related-to-data-binding.md)<br />-   [Nasıl yapılır: Windows Forms verilerde gezinme](how-to-navigate-data-in-windows-forms.md)<br />-   [Nasıl yapılır: bir Windows formunda basit bağlantılı denetim oluşturma](how-to-create-a-simple-bound-control-on-a-windows-form.md)|  
|Karmaşık veri bağlama|Bir denetimin birden fazla veri öğesine bağlanması, genellikle bir veritabanında birden çok kayıt olması. Karmaşık bağlama da liste tabanlı bağlama olarak adlandırılır. Karmaşık bağlamayı destekleyen denetimlerin örnekleri <xref:System.Windows.Forms.DataGridView> , <xref:System.Windows.Forms.ListBox> , ve <xref:System.Windows.Forms.ComboBox> denetimleridir. Karmaşık veri bağlama örneği için bkz. [nasıl yapılır: Windows Forms ComboBox veya ListBox denetimini verilere bağlama](./controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md).|  
  
## <a name="bindingsource-component"></a>BindingSource Bileşeni  
 Windows Forms veri bağlamayı basitleştirmek için, bir veri kaynağını <xref:System.Windows.Forms.BindingSource> bileşene bağlamanıza ve sonra denetimleri öğesine bağlamanıza olanak sağlar <xref:System.Windows.Forms.BindingSource> . <xref:System.Windows.Forms.BindingSource>Basit veya karmaşık bağlama senaryolarında ' i kullanabilirsiniz. Her iki durumda da, <xref:System.Windows.Forms.BindingSource> değişiklik bildirimi para birimi yönetimi ve diğer hizmetler sağlayan veri kaynağı ve bağlantılı denetimler arasında bir aracı işlevi görür.  
  
## <a name="common-scenarios-that-employ-data-binding"></a>Veri bağlama kullanan yaygın senaryolar  
 Neredeyse her ticari uygulama, genellikle veri bağlama aracılığıyla tek bir türdeki veya başka bir veri kaynağından okunan bilgileri kullanır. Aşağıdaki listede veri sunumu ve düzenlemesi yöntemi olarak veri bağlamayı kullanan en yaygın senaryolardan bazıları gösterilmektedir.  
  
|Senaryo|Açıklama|  
|--------------|-----------------|  
|Raporlama|Raporlar, verileri yazdırılmış bir belgede görüntüleyip özetlemeniz için esnek bir yol sağlar. Bir veri kaynağının seçili içeriğini ekrana ya da bir yazıcıya yazdıran bir rapor oluşturmak çok yaygındır. Ortak raporlarda listeler, faturalar ve özetler bulunur. Öğeler genellikle her liste öğesi altında düzenlenmiş alt öğelerle birlikte liste sütunları halinde biçimlendirilir, ancak verilere en uygun düzeni seçmeniz gerekir.|  
|Veri girişi|Büyük miktarlarda ilgili verileri girmek veya kullanıcılara bilgi istemek için bir veri girişi formu aracılığıyla kullanılan yaygın bir yoldur. Kullanıcılar, metin kutuları, seçenek düğmeleri, açılan listeler ve onay kutularını kullanarak bilgi girebilir veya seçim yapabilir. Daha sonra bilgiler, bir veritabanında gönderilir ve depolanır ve bu, yapısı girilen bilgileri temel alır.|  
|Ana/ayrıntı ilişkisi|Ana/ayrıntı uygulaması, ilgili verilere bakmaya yönelik bir biçimdir. Özellikle, bir ilişkiye bağlanan iki veri tablosu vardır — klasik iş örneğinde, müşterileri ve ilgili siparişlerini bağlayan aralarında ilişki içeren bir "müşteriler" tablosu ve "Siparişler" tablosu. İki Windows Forms denetimi ile ana/ayrıntı uygulaması oluşturma hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridView> , bkz [. nasıl yapılır: Iki Windows Forms DataGridView denetimi kullanarak ana/ayrıntı formu oluşturma](./controls/create-a-master-detail-form-using-two-datagridviews.md)|  
|Arama tablosu|Diğer bir yaygın veri sunumu/işleme senaryosu tablo aramadır. Genellikle, daha büyük bir veri görüntüleme kapsamında <xref:System.Windows.Forms.ComboBox> verileri göstermek ve işlemek için bir denetim kullanılır. Anahtar, denetimde görüntülenen verilerin <xref:System.Windows.Forms.ComboBox> veritabanına yazılan verilerden farklı olduğu anahtardır. Örneğin, <xref:System.Windows.Forms.ComboBox> bir Market Mağazası 'nda bulunan öğeleri görüntüleyen bir denetiminiz varsa, büyük olasılıkla ürünlerin (ekten, mılg, yumurlar) adlarını görmek istersiniz. Ancak, veritabanı içinde bilgi alımını kolaylaştırmak ve veritabanı normalleştirmesi için, büyük olasılıkla belirli bir sıra için bilgileri öğe numarası (#501, #603 vb.) olarak depoladığınızda. Bu nedenle, formunuzdaki denetimindeki Market öğesinin "kolay adı" <xref:System.Windows.Forms.ComboBox> ve bir siparişte bulunan ilgili öğe numarası arasında örtülü bir bağlantı vardır. Bu, bir tablo aramasının özünü. Daha fazla bilgi için bkz. [nasıl yapılır: Windows Forms BindingSource bileşeniyle arama tablosu oluşturma](./controls/how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component.md).|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Binding>
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
- [Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama](./controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [BindingSource Bileşeni](./controls/bindingsource-component.md)
