---
title: BindingSource Bileşenine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- controls [Windows Forms], binding to data
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: be838caf-fcb0-4b68-827f-58b2c04b747f
ms.openlocfilehash: 2237ba71487afc132f9164243a664b277397ccfa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939119"
---
# <a name="bindingsource-component-overview"></a>BindingSource Bileşenine Genel Bakış
<xref:System.Windows.Forms.BindingSource> Bileşen denetimleri temel alınan veri kaynağına bağlama işlemini basitleştirmek üzere tasarlanmıştır. <xref:System.Windows.Forms.BindingSource> Bileşen bir conduit hem bağlamak diğer denetimler için bir veri kaynağı olarak görev yapar. Bu, temel alınan veri listesine komutları geçirme sırasında veri bağlantısının formunuzun bir Özet sağlar. Bileşen işlevlerinin veri kaynağı olarak ayrıca, verileri doğrudan, ekleyebilirsiniz.  
  
## <a name="bindingsource-component-as-an-intermediary"></a>Bir aracı olarak BindingSource bileşeni  
 <xref:System.Windows.Forms.BindingSource> Bileşen bazılarını veya tümünü form üzerinde denetimleri için veri kaynağı olarak davranır. Visual Studio'da <xref:System.Windows.Forms.BindingSource> yoluyla bir denetime bağlı `DataBindings` erişilebilir özelliği **özellikleri** penceresi. Ayrıca bkz: [nasıl yapılır: BindingSource bileşeniyle Tasarımcı kullanarak Windows Forms denetimleri bağlama](bind-wf-controls-with-the-bindingsource.md).  
  
 Bağlayabilirsiniz <xref:System.Windows.Forms.BindingSource> ister bir nesne veya temel bir koleksiyonu tek bir özellik gibi her iki basit veri kaynakları bileşeni <xref:System.Collections.ArrayList>ve bir veritabanı tablosu gibi karmaşık veri kaynakları. <xref:System.Windows.Forms.BindingSource> Bileşen bağlama ve para birimi yönetimi hizmetleri sağlayan bir aracı görev yapar. Tasarım zamanı veya çalışma zamanı, adlarınıza bağlayabileceğiniz bir <xref:System.Windows.Forms.BindingSource> ayarlayarak bir karmaşık veri kaynağına bileşen kendi <xref:System.Windows.Forms.BindingSource.DataSource%2A> ve <xref:System.Windows.Forms.BindingSource.DataMember%2A> veritabanı ve tablo, Özellikler sırasıyla. Aşağıdaki çizimde yeri gösterir <xref:System.Windows.Forms.BindingSource> bileşen mevcut veri bağlama mimarisine uygun.  
  
 ![Kaynak ve veri bağlama mimarisine bağlama](./media/net-bindsrcdatabindarch.gif "NET_BindSrcDataBindArch")  
  
> [!NOTE]
>  Tasarım zamanında, bir veritabanı tablosu boş bir form üzerine veri penceresinden sürükleme gibi bazı eylemler oluşturacak <xref:System.Windows.Forms.BindingSource> bileşeni, temel alınan veri kaynağına bağlama ve tümü tek bir işlemde veri kullanan denetimler ekleme. Ayrıca bkz: [Visual Studio'da verilere Windows Forms bağlama denetimleri](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio).  
  
## <a name="bindingsource-component-as-a-data-source"></a>Veri kaynağı olarak BindingSource bileşeni  
 Öğeler ekleme başlatırsanız <xref:System.Windows.Forms.BindingSource> bağlanmasını listesini ilk belirtmeden bileşeni, bileşen liste stilini veri kaynağı gibi davranır ve bu eklenen öğeleri kabul.  
  
 Ayrıca, özel "AddNew" işlevi yoluyla sağlamak için kod yazabilirsiniz <xref:System.Windows.Forms.BindingSource.AddingNew> olan olay arandığında <xref:System.Windows.Forms.BindingSource.AddNew%2A> yöntemi listeye eklenen öğe önce çağrılır. Daha fazla bilgi için [BindingSource bileşeni mimarisi](bindingsource-component-architecture.md).  
  
## <a name="navigation"></a>Gezinti  
 Formdaki verileri gitmek için gereken kullanıcılar için <xref:System.Windows.Forms.BindingNavigator> bileşeni gidin ve ile koordinasyon halinde veri düzenleme sağlar bir <xref:System.Windows.Forms.BindingSource> bileşeni. Daha fazla bilgi için [BindingNavigator denetimine](bindingnavigator-control-windows-forms.md).  
  
## <a name="data-manipulation"></a>Veri işleme  
 : <xref:System.Windows.Forms.BindingSource> Görevi gören bir <xref:System.Windows.Forms.CurrencyManager> tüm bağlamaları ve can için bu nedenle, veri kaynağıyla ilgili para birimi ve konum bilgilerine erişim sağlar. Üyeleri aşağıdaki tabloda gösterilmektedir <xref:System.Windows.Forms.BindingSource> erişme ve temel alınan verileri yönlendirmek için bileşen sağlar.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Current%2A> Özelliği|Veri kaynağının geçerli öğeyi alır.|  
|<xref:System.Windows.Forms.BindingSource.Position%2A> Özelliği|Alır veya ayarlar temel listesi geçerli konumu.|  
|<xref:System.Windows.Forms.BindingSource.List%2A> Özelliği|Değerlendirme listesinde alır <xref:System.Windows.Forms.BindingSource.DataSource%2A> ve <xref:System.Windows.Forms.BindingSource.DataMember%2A> değerlendirme. Varsa <xref:System.Windows.Forms.BindingSource.DataMember%2A> ayarlı değil, tarafından belirtilen bir liste döndürür <xref:System.Windows.Forms.BindingSource.DataSource%2A>.|  
|<xref:System.Windows.Forms.BindingSource.Insert%2A> Yöntemi|Belirtilen dizindeki listedeki bir öğe ekler.|  
|<xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> Yöntemi|Geçerli öğeyi listeden kaldırır.|  
|<xref:System.Windows.Forms.BindingSource.EndEdit%2A> Yöntemi|Bekleyen değişiklikler temel alınan veri kaynağına uygular.|  
|<xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Yöntemi|Geçerli düzenleme işlemi iptal eder.|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A> Yöntemi|Yeni bir öğe temel alınan listesine ekler. Veri kaynağı uygulayan <xref:System.ComponentModel.IBindingList> ve bir öğe döndürür <xref:System.Windows.Forms.BindingSource.AddingNew> olayı, bu öğe ekler. Aksi takdirde isteği listenin geçirilir <xref:System.ComponentModel.IBindingList.AddNew%2A> yöntemi. Arka plandaki liste değilse bir <xref:System.ComponentModel.IBindingList>, öğenin kendi ortak varsayılan oluşturucusu otomatik olarak oluşturulur.|  
  
## <a name="sorting-and-filtering"></a>Sıralama ve Filtreleme  
 Genellikle, bir veri kaynağı sıralı veya filtrelenmiş görünümü ile çalışması gerekir. Üyeleri aşağıdaki tabloda gösterilmektedir <xref:System.Windows.Forms.BindingSource> bileşen veri kaynağı sağlar.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A> Özelliği|Veri kaynağı ise bir <xref:System.ComponentModel.IBindingList>sıralama ve sipariş bilgilerini sıralama için kullanılan sütun adını ayarlar veya alır. Veri kaynağı ise bir <xref:System.ComponentModel.IBindingListView> ve sıralama, Gelişmiş destekler, sıralama ve sipariş bilgilerini sıralama için kullanılan birden fazla sütun adlarını alır|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A> Özelliği|Veri kaynağı ise bir <xref:System.ComponentModel.IBindingListView>hangi satırların görüntülenen filtrelemek için kullanılan ifade ayarlar veya alır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [BindingSource Bileşeni Mimarisi](bindingsource-component-architecture.md)
- [BindingSource Bileşeni](bindingsource-component.md)
- [BindingNavigator Denetimi](bindingnavigator-control-windows-forms.md)
- [Windows Forms Veri Bağlama](../windows-forms-data-binding.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
