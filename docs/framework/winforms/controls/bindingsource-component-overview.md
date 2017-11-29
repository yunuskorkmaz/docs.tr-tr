---
title: "BindingSource Bileşenine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, data binding
- controls [Windows Forms], binding to data
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: be838caf-fcb0-4b68-827f-58b2c04b747f
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cf46a3d5207f3414bc8abd5fd7bdb904e91f07d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="bindingsource-component-overview"></a>BindingSource Bileşenine Genel Bakış
<xref:System.Windows.Forms.BindingSource> Bileşen denetimleri için temel bir veri kaynağına bağlama işlemini basitleştirmek için tasarlanmıştır. <xref:System.Windows.Forms.BindingSource> Bileşen bir conduit ve bağlamak diğer denetimler için bir veri kaynağı olarak davranır. Temel alınan veri listesine komutları geçirme sırasında formun veri bağlantısı için bir Özet sağlar. Böylece bir veri kaynağı olarak bileşen işlevleri Ayrıca, veri doğrudan bu onu ekleyebilirsiniz.  
  
## <a name="bindingsource-component-as-an-intermediary"></a>Bir aracı gibi BindingSource bileşeni  
 <xref:System.Windows.Forms.BindingSource> Bileşen bazılarını veya tümünü form üzerinde denetimleri için veri kaynağı olarak davranır. Visual Studio'da <xref:System.Windows.Forms.BindingSource> yoluyla bir denetime bağlı `DataBindings` erişilebilir özelliği **özellikleri** penceresi. Ayrıca bkz. [nasıl yapılır: Windows Formları denetimlerini BindingSource bileşenini kullanarak Tasarımcısı ile bağlama](../../../../docs/framework/winforms/controls/bind-wf-controls-with-the-bindingsource.md).  
  
 Bağlayabilirsiniz <xref:System.Windows.Forms.BindingSource> hem basit veri kaynaklarına bileşen bir nesne veya temel koleksiyonu tek bir özellikte ister gibi <xref:System.Collections.ArrayList>ve bir veritabanı tablosu gibi karmaşık veri kaynakları. <xref:System.Windows.Forms.BindingSource> Bileşen bağlama ve para birimi yönetim hizmetleri sağlayan bir aracı gibi davranır. Tasarım zamanı veya çalışma zamanında, bağlayabileceğiniz bir <xref:System.Windows.Forms.BindingSource> bileşen ayarlayarak karmaşık veri kaynağı için kendi <xref:System.Windows.Forms.BindingSource.DataSource%2A> ve <xref:System.Windows.Forms.BindingSource.DataMember%2A> veritabanı ve tablo, Özellikler sırasıyla. Where aşağıdaki çizimde gösterilmektedir <xref:System.Windows.Forms.BindingSource> bileşen mevcut veri bağlama mimariye uygun.  
  
 ![Kaynak ve veri bağlama mimarisine bağlama](../../../../docs/framework/winforms/controls/media/net-bindsrcdatabindarch.gif "NET_BindSrcDataBindArch")  
  
> [!NOTE]
>  Tasarım zamanında bir veritabanı tablosu boş bir form verileri penceresinden sürükleme gibi bazı eylemler oluşturacak <xref:System.Windows.Forms.BindingSource> bileşeni, temel alınan veri kaynağına bağlama ve tümünü tek bir işlemde veri algılayan denetimleri ekleyin. Ayrıca bkz. [bağlamak Windows Forms denetimleri Visual Studio'da verilere](/visualstudio/data-tools/bind-windows-forms-controls-to-data-in-visual-studio).  
  
## <a name="bindingsource-component-as-a-data-source"></a>Veri kaynağı olarak BindingSource bileşeni  
 Öğeler ekleme başlatırsanız <xref:System.Windows.Forms.BindingSource> bağlı olmasını listesini ilk belirtmeden bileşeni, bileşen bir liste stili veri kaynağı gibi davranır ve bu eklenen öğeler kabul.  
  
 Ayrıca, özel "AddNew" işlevselliği yoluyla sağlamak üzere kod yazabilirsiniz <xref:System.Windows.Forms.BindingSource.AddingNew> olan olay zaman yükseltilmiş <xref:System.Windows.Forms.BindingSource.AddNew%2A> yöntemi Listeye eklenmekte olan öğeyi önce çağrılır. Daha fazla bilgi için bkz: [BindingSource bileşeni mimarisi](../../../../docs/framework/winforms/controls/bindingsource-component-architecture.md).  
  
## <a name="navigation"></a>Gezinme  
 Bir form üzerinde veri gitmek için olması gereken kullanıcılar için <xref:System.Windows.Forms.BindingNavigator> bileşen sağlar gidin ve birlikte verileri işlemek için bir <xref:System.Windows.Forms.BindingSource> bileşeni. Daha fazla bilgi için bkz: [BindingNavigator denetimi](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md).  
  
## <a name="data-manipulation"></a>Veri Yönetimi  
 : <xref:System.Windows.Forms.BindingSource> Görevi gören bir <xref:System.Windows.Forms.CurrencyManager> tüm bağlamalar ve can bu nedenle, para birimi ve konum bilgilerini veri kaynağıyla ilgili erişim sağlar. Üyeleri, aşağıdaki tabloda gösterilmektedir <xref:System.Windows.Forms.BindingSource> erişme ve temel alınan veri düzenleme için bileşen sağlar.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Current%2A>özelliği|Veri kaynağı geçerli öğesini alır.|  
|<xref:System.Windows.Forms.BindingSource.Position%2A>özelliği|Alır veya arka plandaki listesinde geçerli konumunu ayarlar.|  
|<xref:System.Windows.Forms.BindingSource.List%2A>özelliği|Değerlendirmesi listesinde alır <xref:System.Windows.Forms.BindingSource.DataSource%2A> ve <xref:System.Windows.Forms.BindingSource.DataMember%2A> değerlendirme. Varsa <xref:System.Windows.Forms.BindingSource.DataMember%2A> ayarlı değildir, tarafından belirtilen listesini döndürür <xref:System.Windows.Forms.BindingSource.DataSource%2A>.|  
|<xref:System.Windows.Forms.BindingSource.Insert%2A>yöntemi|Belirtilen dizindeki listedeki bir öğe ekler.|  
|<xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A>yöntemi|Geçerli öğeyi listeden kaldırır.|  
|<xref:System.Windows.Forms.BindingSource.EndEdit%2A>yöntemi|Bekleyen değişiklikler, temel alınan veri kaynağı için geçerlidir.|  
|<xref:System.Windows.Forms.BindingSource.CancelEdit%2A>yöntemi|Geçerli düzenleme işlemi iptal eder.|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A>yöntemi|Yeni bir öğe altta yatan listeye ekler. Implements veri kaynağı, <xref:System.ComponentModel.IBindingList> ve bir öğeyi döndürür <xref:System.Windows.Forms.BindingSource.AddingNew> olay, bu öğe ekler. Aksi takdirde, istek listesine ait geçirilir <xref:System.ComponentModel.IBindingList.AddNew%2A> yöntemi. Alttaki listede değilse, bir <xref:System.ComponentModel.IBindingList>, öğesi kendi ortak varsayılan oluşturucu kullanılarak otomatik olarak oluşturulur.|  
  
## <a name="sorting-and-filtering"></a>Sıralama ve filtreleme  
 Genellikle, bir veri kaynağı sıralı veya filtrelenmiş görünüm ile çalışması gerekir. Üyeleri, aşağıdaki tabloda gösterilmektedir <xref:System.Windows.Forms.BindingSource> bileşen veri kaynağı sağlar.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A>özelliği|Veri kaynağı ise bir <xref:System.ComponentModel.IBindingList>, alır veya ayarlar sıralama ve sıralama sipariş bilgilerini için kullanılan bir sütun adı. Veri kaynağı ise bir <xref:System.ComponentModel.IBindingListView> ve sıralama, Gelişmiş destekler, sıralama ve sıralama sipariş bilgilerini için kullanılan birden fazla sütun adlarını alır|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A>özelliği|Veri kaynağı ise bir <xref:System.ComponentModel.IBindingListView>, alır veya ayarlar hangi satırların görüntülenen filtre uygulamak için kullanılan ifade.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [BindingSource bileşeni mimarisi](../../../../docs/framework/winforms/controls/bindingsource-component-architecture.md)  
 [BindingSource bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [BindingNavigator denetimi](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Windows Forms veri bağlama](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Windows Forms'ta kullanılacak denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
