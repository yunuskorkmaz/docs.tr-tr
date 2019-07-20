---
title: BindingSource Bileşenine Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- controls [Windows Forms], binding to data
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: be838caf-fcb0-4b68-827f-58b2c04b747f
ms.openlocfilehash: 9c9c9fb574b9f3e687b2d8d5c4606bfb66ebfa64
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364455"
---
# <a name="bindingsource-component-overview"></a>BindingSource Bileşenine Genel Bakış
<xref:System.Windows.Forms.BindingSource> Bileşen, denetimleri temel alınan bir veri kaynağına bağlama işlemini basitleştirmek için tasarlanmıştır. <xref:System.Windows.Forms.BindingSource> Bileşen hem bir iletken hem de diğer denetimlerin bağlanacağı bir veri kaynağı olarak davranır. Temel alınan veri listesine geçiş yaparken formunuzun veri bağlantısının bir soyutlamasını sağlar. Ayrıca, doğrudan buna veri ekleyebilirsiniz, böylece bileşen bir veri kaynağı olarak çalışır.  
  
## <a name="bindingsource-component-as-an-intermediary"></a>Aracı olarak BindingSource bileşeni  
 <xref:System.Windows.Forms.BindingSource> Bileşen, formdaki denetimlerin bazıları veya tümü için veri kaynağı olarak davranır. Visual Studio <xref:System.Windows.Forms.BindingSource> 'da, **Özellikler** penceresinden erişilebilen `DataBindings` özelliği aracılığıyla bir denetime bağlanabilir. Ayrıca bkz [. nasıl yapılır: Tasarımcıyı](bind-wf-controls-with-the-bindingsource.md)kullanarak BindingSource bileşeniyle Windows Forms denetimleri bağlayın.  
  
 <xref:System.Windows.Forms.BindingSource> Bileşeni, bir nesnenin tek bir özelliği ya da gibi <xref:System.Collections.ArrayList>bir temel koleksiyon ve veritabanı tablosu gibi karmaşık veri kaynakları gibi basit veri kaynaklarına bağlayabilirsiniz. Bileşen <xref:System.Windows.Forms.BindingSource> , bağlama ve para birimi yönetim hizmetleri sağlayan bir aracı gibi davranır. Tasarım zamanında veya çalışma zamanında,, <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.DataSource%2A> ve <xref:System.Windows.Forms.BindingSource.DataMember%2A> özelliklerini sırasıyla veritabanı ve tablo olarak ayarlayarak karmaşık bir veri kaynağına bir bileşeni bağlayabilirsiniz. Aşağıdaki çizimde, <xref:System.Windows.Forms.BindingSource> bileşenin var olan veri bağlama mimarisine hangi noktada uyduğunu gösterilmektedir.  
  
 ![Bağlama kaynağı ve veri bağlama mimarisi](./media/net-bindsrcdatabindarch.gif "NET_BindSrcDataBindArch")  
  
> [!NOTE]
>  Tasarım zamanında, bir veritabanı tablosunun bir veri penceresinden boş bir form üzerine sürüklenmesi gibi bazı eylemler, <xref:System.Windows.Forms.BindingSource> bileşeni oluşturur, temel alınan veri kaynağına bağlar ve tek bir işlemde veri kullanan denetimleri ekler. Ayrıca bkz. [Visual Studio 'da verilere Windows Forms denetimleri bağlama](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio).  
  
## <a name="bindingsource-component-as-a-data-source"></a>Veri kaynağı olarak BindingSource bileşeni  
 Önce bağlanacak bir liste belirtmeden <xref:System.Windows.Forms.BindingSource> bileşen eklemeye başlayabilirsiniz, bileşen bir liste stili veri kaynağı gibi davranır ve bu eklenen öğeleri kabul eder.  
  
 Ayrıca, <xref:System.Windows.Forms.BindingSource.AddingNew> olaya eklenen öğeden önce <xref:System.Windows.Forms.BindingSource.AddNew%2A> yöntemi çağrıldığında oluşturulan olay aracılığıyla özel "AddNew" işlevselliği sağlamak için kod yazabilirsiniz. Daha fazla bilgi için bkz. [BindingSource bileşen mimarisi](bindingsource-component-architecture.md).  
  
## <a name="navigation"></a>Gezinti  
 Bir form <xref:System.Windows.Forms.BindingNavigator> üzerinde verilerde gezinmeniz gereken kullanıcılar için bileşen, bir <xref:System.Windows.Forms.BindingSource> bileşenle koordine halinde verileri gezinmenizi ve değiştirmenizi sağlar. Daha fazla bilgi için [BindingNavigator denetimine](bindingnavigator-control-windows-forms.md).  
  
## <a name="data-manipulation"></a>Veri Işleme  
 : <xref:System.Windows.Forms.BindingSource> Tüm bağlamaları için bir <xref:System.Windows.Forms.CurrencyManager> olarak davranır ve bu nedenle veri kaynağıyla ilgili para birimi ve konum bilgilerine erişim sağlar. Aşağıdaki tabloda, <xref:System.Windows.Forms.BindingSource> bileşenin temel verilere erişmek ve onları işlemek için sağladığı Üyeler gösterilmektedir.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Current%2A>özelliði|Veri kaynağının geçerli öğesini alır.|  
|<xref:System.Windows.Forms.BindingSource.Position%2A>özelliði|Temel alınan listedeki geçerli konumu alır veya ayarlar.|  
|<xref:System.Windows.Forms.BindingSource.List%2A>özelliði|<xref:System.Windows.Forms.BindingSource.DataSource%2A> Ve<xref:System.Windows.Forms.BindingSource.DataMember%2A> değerlendirmesinin değerlendirmesi olan listeyi alır. Ayarlanmamışsa, tarafından <xref:System.Windows.Forms.BindingSource.DataSource%2A>belirtilen listeyi döndürür. <xref:System.Windows.Forms.BindingSource.DataMember%2A>|  
|<xref:System.Windows.Forms.BindingSource.Insert%2A>yöntemidir|Belirtilen dizindeki listeye bir öğe ekler.|  
|<xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A>yöntemidir|Geçerli öğeyi listeden kaldırır.|  
|<xref:System.Windows.Forms.BindingSource.EndEdit%2A>yöntemidir|Temel alınan veri kaynağına bekleyen değişiklikleri uygular.|  
|<xref:System.Windows.Forms.BindingSource.CancelEdit%2A>yöntemidir|Geçerli düzenleme işlemini iptal eder.|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A>yöntemidir|Temel alınan listeye yeni bir öğe ekler. Veri kaynağı, <xref:System.Windows.Forms.BindingSource.AddingNew> olaydan bir <xref:System.ComponentModel.IBindingList> öğe uygularsa ve döndürürse, bu öğeyi ekler. Aksi takdirde, istek listenin <xref:System.ComponentModel.IBindingList.AddNew%2A> yöntemine geçirilir. Temel alınan liste bir <xref:System.ComponentModel.IBindingList>değilse, öğe genel parametresiz oluşturucusu aracılığıyla otomatik olarak oluşturulur.|  
  
## <a name="sorting-and-filtering"></a>Sıralama ve Filtreleme  
 Genellikle, veri kaynağının sıralı veya filtrelenmiş görünümüyle çalışmanız gerekir. Aşağıdaki tabloda, <xref:System.Windows.Forms.BindingSource> bileşen veri kaynağının sağladığı Üyeler gösterilmektedir.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A>özelliði|Veri kaynağı bir <xref:System.ComponentModel.IBindingList>ise, sıralama ve sıralama bilgileri için kullanılan bir sütun adı alır veya ayarlar. Veri kaynağı bir <xref:System.ComponentModel.IBindingListView> ise ve gelişmiş sıralamayı destekliyorsa, sıralama ve sıralama bilgileri için kullanılan birden çok sütun adı alır|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A>özelliði|Veri kaynağı bir <xref:System.ComponentModel.IBindingListView>ise, hangi satırların görüntülendiğini filtrelemek için kullanılan ifadeyi alır veya ayarlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [BindingSource Bileşeni Mimarisi](bindingsource-component-architecture.md)
- [BindingSource Bileşeni](bindingsource-component.md)
- [BindingNavigator Denetimi](bindingnavigator-control-windows-forms.md)
- [Windows Forms Veri Bağlama](../windows-forms-data-binding.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
