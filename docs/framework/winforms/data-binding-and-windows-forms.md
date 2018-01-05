---
title: "Veri Bağlama ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f2a4d023600456adf1e14b801ee6c24fd0a2348c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="data-binding-and-windows-forms"></a>Veri Bağlama ve Windows Forms
Windows Forms'ta yalnızca geleneksel veri kaynaklarına bağlayabilirsiniz, ancak Ayrıca verileri içeren neredeyse her yapısına. Çalışma zamanında hesaplamak, bir dosyadan okunan veya diğer denetimlerin değerleri türetilen değerleri dizisi bağlayabilirsiniz.  
  
 Ayrıca, herhangi bir denetim herhangi bir özelliği veri kaynağına bağlayabilirsiniz. Geleneksel Veri bağlamada, genellikle görüntü özelliği bağlamak — Örneğin, <xref:System.Windows.Forms.Control.Text%2A> özelliği bir <xref:System.Windows.Forms.TextBox> denetim — veri kaynağı. İle [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], ayrıca diğer özellikleri de bağlama aracılığıyla ayarlama seçeneğiniz vardır. Bağlama, aşağıdaki görevleri gerçekleştirmek için kullanabilirsiniz:  
  
-   Grafiği bir görüntü denetiminin ayarlama.  
  
-   Bir veya daha fazla denetim arka plan rengini ayarlama.  
  
-   Denetimleri boyutunu ayarlama.  
  
 Esas olarak, veri bağlama, herhangi bir çalışma zamanı erişilebilir özelliği, bir form üzerinde herhangi bir denetimi ayarı bir otomatik yoludur.  
  
## <a name="types-of-data-binding"></a>Veri bağlama türleri  
 Windows Forms veri bağlama iki tür avantajlarından alabilir: basit bağlama ve karmaşık bağlama. Her farklı avantajlar sunar.  
  
|Veri bağlama türü|Açıklama|  
|--------------------------|-----------------|  
|Basit veri bağlama|Tek bir veri öğesi, bir veri kümesi tablo sütununda bir değer gibi bağlamak için bir denetim yeteneği. Bu tür denetimler için tipik bağlama olduğu gibi bir <xref:System.Windows.Forms.TextBox> denetim veya <xref:System.Windows.Forms.Label> genellikle yalnızca tek bir değer görüntüler denetimleri denetimi. Aslında, denetim üzerinde herhangi bir özelliği bir veritabanı alanına bağlanabilir. Bu özellik için kapsamlı destek [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].<br /><br /> Daha fazla bilgi için bkz.:<br /><br /> -   [Veri bağlama ile ilgili arabirimler](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)<br />-   [Nasıl yapılır: Windows formlarında verilerde gezinme](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)<br />-   [Nasıl yapılır: bir Windows formunda basit bağlantılı denetim oluşturma](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)|  
|Karmaşık veri bağlama|Birden fazla veri öğesi, genellikle birden fazla kayıt bir veritabanında bağlamak için bir denetim yeteneği. Karmaşık bağlama, liste tabanlı bağlama olarak da adlandırılır. Karmaşık bağlama destekleyen denetimleri örnekleri <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.ListBox>, ve <xref:System.Windows.Forms.ComboBox> kontrol eder. Karmaşık veri bağlama örneği için bkz: [nasıl yapılır: Windows Forms ComboBox veya ListBox denetimini verilere bağlama](../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md).|  
  
## <a name="bindingsource-component"></a>BindingSource Bileşeni  
 Veri bağlama işlemini basitleştirmek için Windows Forms veri kaynağına bağlama sağlar <xref:System.Windows.Forms.BindingSource> bileşeni ve bağ denetimlere <xref:System.Windows.Forms.BindingSource>. Kullanabileceğiniz <xref:System.Windows.Forms.BindingSource> basit veya karmaşık bağlama senaryolarda. Her iki durumda da <xref:System.Windows.Forms.BindingSource> bildirim para birimi yönetimi ve diğer hizmetleri sağlayan ilişkili denetimler ve veri kaynağı arasında aracı görevi görür değiştirin.  
  
## <a name="common-scenarios-that-employ-data-binding"></a>Veri bağlama uygulamadığınız yaygın senaryolar  
 Ticari neredeyse her uygulama, bir tür ya da başka veri kaynaklarından veri bağlama aracılığıyla genellikle okunan bilgileri kullanır. Aşağıdaki liste, veri bağlama yöntemini veri sunumu ve işleme olarak kullanan en yaygın senaryolar bazılarını gösterir.  
  
|Senaryo|Açıklama|  
|--------------|-----------------|  
|Raporlama|Raporları görüntülemek ve verilerinizi yazdırılan belgede özetlemek esnek bir yol sağlar. Seçili veri kaynağı ekranına ya da bir yazıcıya içeriğini yazdırır bir rapor oluşturmak için çok yaygındır. Sık kullanılan raporları listeler, faturalar ve özetleri içerir. Öğeler alt öğelerin her liste öğesi altında düzenlenmiştir ile genellikle listeleri sütunlara biçimlendirilir ancak veri uygun düzenini seçmeniz gerekir.|  
|Veri girdisi|Genel bir büyük miktarlarda ilgili veri girin veya kullanıcıların bilgi istemek için veri girişi formu yoludur. Kullanıcılar, bilgileri girin veya metin kutuları, seçenek düğmeleri, açılan listeleri ve onay kutularını kullanarak seçenekleri seçin. Bilgileri sonra gönderildi ve, yapısı girilen bilgilere dayalı bir veritabanında depolanır.|  
|Ana/ayrıntı ilişkisi|Ana/ayrıntı uygulama ilgili veri aramak için bir biçimidir. Özellikle, bunları bağlanma ilişkisi veri iki tablo vardır: Klasik iş örneği, "Müşteriler" tablosu ve bunları bağlama müşteriler ve bunların ilgili Siparişler arasında bir ilişki "Siparişleri" bir tabloyla. İki Windows Forms ile ana/ayrıntı uygulama oluşturma hakkında daha fazla bilgi için <xref:System.Windows.Forms.DataGridView> denetimleri bkz [nasıl yapılır: bir ana öğe/ayrıntı formu kullanarak iki Windows Forms DataGridView denetimi oluşturma](../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)|  
|Arama tablosu|Başka bir ortak veri sunu/işleme tablo arama senaryodur. Genellikle, daha büyük bir veri görünen bir parçası olarak bir <xref:System.Windows.Forms.ComboBox> denetimi görüntülemek ve verileri işlemek için kullanılır. İçinde görüntülenen verileri anahtarıdır <xref:System.Windows.Forms.ComboBox> denetimidir veritabanına yazılan veriler farklı. Örneğin, bir <xref:System.Windows.Forms.ComboBox> öğeleri görüntüleme denetim Market kullanılabilir, büyük olasılıkla (ekmek sütlü, Yumurta) ürünlerin adlarını görmek istediğiniz. Ancak, bilgi alma veritabanındaki ve veritabanı normalleştirmesi için kolaylaştırmak için büyük olasılıkla verilen siparişi belirli öğelere ilişkin bilgileri öğesi sayı olarak saklayacağından (#501, #603 ve benzeri). Bu nedenle, Market öğesi "kolay adı" arasında örtük bir bağlantısı vardır <xref:System.Windows.Forms.ComboBox> denetim formunuz ve bir sırada mevcut ilgili öğe sayısı. Bu tablo arama olduğu. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Formları BindingSource bileşeniyle arama tablosu oluşturma](../../../docs/framework/winforms/controls/how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component.md).|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Binding>  
 [Windows Forms Veri Bağlama](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama](../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [BindingSource Bileşeni](../../../docs/framework/winforms/controls/bindingsource-component.md)
