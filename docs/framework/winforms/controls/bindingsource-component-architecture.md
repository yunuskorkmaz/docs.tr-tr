---
title: BindingSource Bileşeni Mimarisi
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: b0334bd7a0bc5ff46c43fd7ee549422d98c35efe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="bindingsource-component-architecture"></a>BindingSource Bileşeni Mimarisi
İle <xref:System.Windows.Forms.BindingSource> bileşeni, Evrensel bağlayabilirsiniz tüm Windows Forms denetimleri için veri kaynakları.  
  
 <xref:System.Windows.Forms.BindingSource> Bileşeni denetimleri bir veri kaynağına bağlama işlemini basitleştirir ve geleneksel veri bağlama aşağıdaki avantajları sunar:  
  
-   İş nesneler için tasarım zamanı bağlamayı sağlar.  
  
-   Yalıtan <xref:System.Windows.Forms.CurrencyManager> işlevselliği ve çıkarır <xref:System.Windows.Forms.CurrencyManager> tasarım zamanında olaylar.  
  
-   Destekleyen liste oluşturma basitleştirir <xref:System.ComponentModel.IBindingList> değişikliği bildirimi listesi yerel olarak desteklemeyen veri kaynakları listesi değişiklik bildirimi sağlayarak arabirimi.  
  
-   İçin genişletilebilirlik noktasıdır <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType> yöntemi.  
  
-   Veri kaynağı ile denetimi arasında yöneltme düzeyi sağlar. Veri kaynağı çalışma zamanında değişebilir, bu yöneltme önemlidir.  
  
-   Diğer ilgili verileri Windows Forms denetimleri ile özellikle birlikte çalışır <xref:System.Windows.Forms.BindingNavigator> ve <xref:System.Windows.Forms.DataGridView> kontrol eder.  
  
 Bu nedenlerle, <xref:System.Windows.Forms.BindingSource> Windows Forms denetimleri veri kaynaklarına bağlamak için tercih edilen yol bir bileşendir.  
  
## <a name="bindingsource-features"></a>BindingSource özellikleri  
 <xref:System.Windows.Forms.BindingSource> Bileşeni verilere denetimler bağlama için çeşitli özellikler sağlar. Bu özellikleri ile neredeyse hiçbir bölümü'kodlama ile çoğu veri bağlama senaryoları uygulayabilirsiniz.  
  
 <xref:System.Windows.Forms.BindingSource> Bileşen gerçekleştirir Bu birçok farklı türde veri kaynaklarına erişmek için tutarlı bir arayüz sağlar. Başka bir deyişle, bağlama herhangi bir tür için aynı yordamı kullanın. Örneğin, iliştirebilirsiniz <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliğine bir <xref:System.Data.DataSet> ya da bir iş nesnesi için ve her iki durumda da, özellikleri, yöntemleri ve olayları aynı kümesini veri kaynağı değiştirmek için kullanın.  
  
 Tarafından sağlanan tutarlı arabirim <xref:System.Windows.Forms.BindingSource> bileşen denetimlere veri bağlama işlemini büyük ölçüde basitleştirir. Bildirim, sağlayan veri kaynağı türlerini değiştirmek için <xref:System.Windows.Forms.BindingSource> bileşen denetim ve veri kaynağı arasındaki değişiklikleri otomatik olarak iletişim kurar. Değişiklik bildirimi sağlamaz, veri kaynağı türleri için değişiklik bildirimleri Yükselt imkan sağlayan olayları sağlanır. Aşağıdaki listede tarafından desteklenen özellikler gösterilmektedir <xref:System.Windows.Forms.BindingSource> bileşen:  
  
-   Yöneltme.  
  
-   Para birimi yönetimi.  
  
-   Veri kaynağı olarak bir listesi.  
  
-   <xref:System.Windows.Forms.BindingSource> farklı bir <xref:System.ComponentModel.IBindingList>.  
  
-   Özel öğesi oluşturma.  
  
-   İşlem öğesi oluşturma.  
  
-   <xref:System.Collections.IEnumerable> destekler.  
  
-   Tasarım zamanı desteği.  
  
-   Statik <xref:System.Windows.Forms.ListBindingHelper> yöntemleri.  
  
-   Sıralama ve filtreleme ile <xref:System.ComponentModel.IBindingListView> arabirimi.  
  
-   İle tümleştirme <xref:System.Windows.Forms.BindingNavigator>.  
  
### <a name="indirection"></a>Yöneltme  
 <xref:System.Windows.Forms.BindingSource> Bileşen düzeyde bir denetim ve veri kaynağı arasında yönlendirme sağlar. Bir denetim doğrudan veri kaynağına bağlama yerine denetimi bağlamak bir <xref:System.Windows.Forms.BindingSource>, ve veri kaynağına attach <xref:System.Windows.Forms.BindingSource> bileşenin <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliği.  
  
 Bu yöneltme düzeyi ile veri kaynağı denetimi bağlama sıfırlamadan değiştirebilirsiniz. Bu, aşağıdaki özellikleri sunar:  
  
-   Ekleyebilir miyim <xref:System.Windows.Forms.BindingSource> geçerli denetimi bağlamaları korurken farklı veri kaynakları için.  
  
-   Veri kaynağındaki öğeleri değiştirmek ve ilişkili denetimler bilgilendirin. Daha fazla bilgi için bkz: [nasıl yapılır: BindingSource ile Windows Forms denetiminde veri kaynağı güncelleştirmeleri yansıtmak](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md).  
  
-   Bağlayabileceğiniz bir <xref:System.Type> yerine bellekte bir nesne. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms denetimini bir türe bağlama](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md). Ardından, çalışma zamanında bir nesneye bağlayabilirsiniz.  
  
### <a name="currency-management"></a>Para birimi yönetimi  
 <xref:System.Windows.Forms.BindingSource> Bileşenini uygulayan <xref:System.Windows.Forms.ICurrencyManagerProvider> para birimi yönetimini işlemek için arabirim. İle <xref:System.Windows.Forms.ICurrencyManagerProvider> arabirimi da erişebilirsiniz para birimi yöneticisine bir <xref:System.Windows.Forms.BindingSource>, başka bir para birimi yöneticisini yanı sıra <xref:System.Windows.Forms.BindingSource> aynı bağlı <xref:System.Windows.Forms.BindingSource.DataMember%2A>.  
  
 <xref:System.Windows.Forms.BindingSource> Bileşen yalıtır <xref:System.Windows.Forms.CurrencyManager> işlevselliği ve düzenlemenizi sağlayan en yaygın <xref:System.Windows.Forms.CurrencyManager> özellikleri ve olayları. Aşağıdaki tabloda para birimi yönetimiyle ilgili üyeleri bazıları açıklanmaktadır.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> Özelliği  
 İle ilişkili para birimi Yöneticisi alır <xref:System.Windows.Forms.BindingSource>.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A> Yöntemi  
 Varsa başka <xref:System.Windows.Forms.BindingSource> için belirtilen veri üyesi bağlıysa, kendi para birimi Yöneticisi alır.  
  
 <xref:System.Windows.Forms.BindingSource.Current%2A> Özelliği  
 Veri kaynağı geçerli öğesini alır.  
  
 <xref:System.Windows.Forms.BindingSource.Position%2A> Özelliği  
 Alır veya arka plandaki listesinde geçerli konumunu ayarlar.  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> Yöntemi  
 Bekleyen değişiklikler, temel alınan veri kaynağı için geçerlidir.  
  
 <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> Yöntemi  
 Geçerli düzenleme işlemi iptal eder.  
  
### <a name="data-source-as-a-list"></a>Veri kaynağı bir liste olarak  
 <xref:System.Windows.Forms.BindingSource> Bileşenini uygulayan <xref:System.ComponentModel.IBindingListView> ve <xref:System.ComponentModel.ITypedList> arabirimleri. Bu uygulama ile kullandığınız <xref:System.Windows.Forms.BindingSource> bileşene bir veri kaynağı olarak herhangi bir harici depolama olmadan.  
  
 Zaman <xref:System.Windows.Forms.BindingSource> bileşen bir veri kaynağına eklenen, veri kaynağı bir liste olarak kullanıma sunar.  
  
 <xref:System.Windows.Forms.BindingSource.DataSource%2A> Özelliği çeşitli veri kaynakları için ayarlanabilir. Bunlar, türleri, nesneleri ve türleri listesini içerir. Sonuçta elde edilen veri kaynağı bir liste olarak sunulur. Aşağıdaki tabloda bazı genel veri kaynakları ve sonuçta elde edilen listesi değerlendirme gösterir.  
  
|DataSource özelliği|Liste sonuçları|  
|-------------------------|------------------|  
|Bir null başvuru (`Nothing` Visual Basic)|Boş bir <xref:System.ComponentModel.IBindingList> nesne. Bir öğe ekleme listesi eklenen öğenin türünü ayarlar.|  
|Bir null başvuru (`Nothing` Visual Basic'te) ile <xref:System.Windows.Forms.BindingSource.DataMember%2A> ayarlayın|Desteklenmeyen; başlatır <xref:System.ArgumentException>.|  
|Olmayan liste türü veya nesne türü "T"|Boş bir <xref:System.ComponentModel.IBindingList> "T" türü.|  
|Array örneği|Bir <xref:System.ComponentModel.IBindingList> dizi öğeleri içeren.|  
|<xref:System.Collections.IEnumerable> Örneği|Bir <xref:System.ComponentModel.IBindingList> içeren <xref:System.Collections.IEnumerable> öğeleri|  
|"T" türünü içeren örnek listesi|Bir <xref:System.ComponentModel.IBindingList> türü "T" içeren örneği.|  
  
 Ayrıca, <xref:System.Windows.Forms.BindingSource.DataSource%2A> diğer liste türleri gibi ayarlanabilir <xref:System.ComponentModel.IListSource> ve <xref:System.ComponentModel.ITypedList>ve <xref:System.Windows.Forms.BindingSource> bunları uygun şekilde işler. Bu durumda, listede yer alan türü varsayılan bir oluşturucusu olmalıdır.  
  
### <a name="bindingsource-as-an-ibindinglist"></a>BindingSource IBindingList olarak  
 <xref:System.Windows.Forms.BindingSource> Bileşeni erişmek ve temel alınan veri olarak düzenleme üyeleri sağlar bir <xref:System.ComponentModel.IBindingList>. Aşağıdaki tabloda bu üyelerin bazıları açıklanmaktadır.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.List%2A> Özelliği|Değerlendirmesi sonuçları listeyi alır <xref:System.Windows.Forms.BindingSource.DataSource%2A> veya <xref:System.Windows.Forms.BindingSource.DataMember%2A> özellikleri.|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A> Yöntemi|Yeni bir öğe altta yatan listeye ekler. Uygulayan veri kaynaklarına uygulanır <xref:System.ComponentModel.IBindingList> arabirim ve öğeleri eklemeye izin ver (diğer bir deyişle, <xref:System.Windows.Forms.BindingSource.AllowNew%2A> özelliği ayarlanmış `true`).|  
  
### <a name="custom-item-creation"></a>Özel öğesi oluşturma  
 İşleyebilir <xref:System.Windows.Forms.BindingSource.AddingNew> olay kendi öğesi oluşturma mantığı sağlar. <xref:System.Windows.Forms.BindingSource.AddingNew> Olaylarının yeni bir nesne için eklenmeden önce <xref:System.Windows.Forms.BindingSource>. Sonra bu olay tetiklenir <xref:System.Windows.Forms.BindingSource.AddNew%2A> yöntemi çağrılır, ancak yeni öğe altta yatan listeye eklenmeden önce. Bu olay işleyerek, özel öğesi oluşturma davranışı türetme olmadan sağlayabilirsiniz <xref:System.Windows.Forms.BindingSource> sınıfı. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms BindingSource ile öğe eklemeyi özelleştirme](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md).  
  
### <a name="transactional-item-creation"></a>İşlem öğesi oluşturma  
 <xref:System.Windows.Forms.BindingSource> Bileşenini uygulayan <xref:System.ComponentModel.ICancelAddNew> işlem öğesi oluşturmanıza olanak tanıyan arabirimi. Yeni bir öğe, geçici olarak yapılan bir çağrı kullanılarak oluşturulduktan sonra <xref:System.Windows.Forms.BindingSource.AddNew%2A>, ek yürütülmeli veya geri aşağıdaki yollarla:  
  
-   <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> Yöntemi açıkça bekleyen eklenmesi Yürüt.  
  
-   Bir ekleme, kaldırma veya taşıma gibi başka bir toplama işlemi gerçekleştiren örtük olarak bekleyen eklenmesi yürütme.  
  
-   <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A> Yöntemi geri alacaktır bekleyen toplama yöntemi zaten kaydedilmemiş durumunda.  
  
### <a name="ienumerable-support"></a>IEnumerable desteği  
 <xref:System.Windows.Forms.BindingSource> Bileşen sağlar denetimleri bağlama <xref:System.Collections.IEnumerable> veri kaynakları. Bu bileşen ile bir veri kaynağına gibi bağlayabilirsiniz bir <xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>.  
  
 Zaman bir <xref:System.Collections.IEnumerable> veri kaynağı atanması <xref:System.Windows.Forms.BindingSource> bileşeni <xref:System.Windows.Forms.BindingSource> oluşturur bir <xref:System.ComponentModel.IBindingList> ve içeriğini ekler <xref:System.Collections.IEnumerable> listesine veri kaynağı.  
  
### <a name="design-time-support"></a>Tasarım zamanı desteği  
 Tasarım zamanında bir Fabrika sınıftan oluşturulan nesneler veya bir Web hizmeti tarafından döndürülen nesne gibi bazı nesne türleri oluşturulamaz. Denetimlerinizin bağlamak bellekte nesne olsa bazen denetimleri bu tür için tasarım zamanında bağlamak olabilir. Örneğin, sütun başlıklarını etiket yapmanız gerekebilir bir <xref:System.Windows.Forms.DataGridView> özel tür ortak özellik adlarını denetimiyle.  
  
 Bu senaryoyu desteklemek için <xref:System.Windows.Forms.BindingSource> bileşen bağlamayı destekler bir <xref:System.Type>. Atadığınızda bir <xref:System.Type> için <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliği, <xref:System.Windows.Forms.BindingSource> bileşeni oluşturur boş bir <xref:System.ComponentModel.BindingList%601> , <xref:System.Type> öğeleri. Daha sonra bağlamak üzere herhangi bir denetim <xref:System.Windows.Forms.BindingSource> bileşen uyarılmak özelliklerini veya şema türünüze varlığını Tasarım zamanında veya çalışma zamanında. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms denetimini bir türe bağlama](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md).  
  
### <a name="static-listbindinghelper-methods"></a>Statik ListBindingHelper yöntemleri  
 <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>, <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType>, Ve <xref:System.Windows.Forms.BindingSource> listeden oluşturmak için tüm paylaşım ortak mantığı türleri bir `DataSource` / `DataMember` çifti. Ayrıca, bu ortak mantığı genel olarak kullanılmak üzere Denetim yazarlar ve diğer üçüncü tarafların aşağıdaki açığa `static` yöntemleri:  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>Sıralama ve filtreleme IBindingListView arabirimi  
 <xref:System.Windows.Forms.BindingSource> Bileşenini uygulayan <xref:System.ComponentModel.IBindingListView> genişletir arabirimi <xref:System.ComponentModel.IBindingList> arabirimi. <xref:System.ComponentModel.IBindingList> Tek sütun sıralama sunar ve <xref:System.ComponentModel.IBindingListView> teklifleri Gelişmiş sıralama ve filtreleme. İle <xref:System.ComponentModel.IBindingListView>, sıralayabilir ve ayrıca veri kaynağı, veri kaynağındaki filtre öğeleri bu arabirimlerinden biri, uygular. <xref:System.Windows.Forms.BindingSource> Bileşen bu üyeleri başvuru uyarlamasını sağlamaz. Bunun yerine, çağrıları altta yatan listeye iletilir.  
  
 Aşağıdaki tabloda, sıralama ve filtreleme için kullandığınız özellikler açıklanmaktadır.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A> Özelliği|Veri kaynağı ise bir <xref:System.ComponentModel.IBindingListView>, alır veya ayarlar hangi satırların görüntülenen filtre uygulamak için kullanılan ifade.|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A> Özelliği|Veri kaynağı ise bir <xref:System.ComponentModel.IBindingList>, alır veya ayarlar sıralama ve sıralama sipariş bilgilerini için kullanılan bir sütun adı.<br /><br /> -veya-<br /><br /> Veri kaynağı ise bir <xref:System.ComponentModel.IBindingListView> ve sıralama, Gelişmiş destekler, sıralama ve sıralama için kullanılan birden fazla sütun adlarını alır|  
  
### <a name="integration-with-bindingnavigator"></a>BindingNavigator ile tümleştirme  
 Kullanabileceğiniz <xref:System.Windows.Forms.BindingSource> herhangi bir Windows Forms denetimini bir veri kaynağına bağlanmak için bileşen ancak <xref:System.Windows.Forms.BindingNavigator> denetimi, özel olarak çalışmak üzere tasarlanmıştır <xref:System.Windows.Forms.BindingSource> bileşeni. <xref:System.Windows.Forms.BindingNavigator> Denetimi denetlemek için bir kullanıcı arabirimi sağlar <xref:System.Windows.Forms.BindingSource> bileşenin geçerli öğe. Varsayılan olarak, <xref:System.Windows.Forms.BindingNavigator> denetimi gezinti yöntemlerini üzerinde karşılık gelen düğmeler sağlar <xref:System.Windows.Forms.BindingSource> bileşeni. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms BindingNavigator denetimi ile veri gidin](../../../../docs/framework/winforms/controls/how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [BindingSource Bileşenine Genel Bakış](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 [BindingNavigator Denetimi](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Windows Forms Veri Bağlama](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [Nasıl yapılır: BindingSource ile Windows Forms Denetiminde Veri Kaynağı Güncelleştirmelerini Yansıtma](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)
