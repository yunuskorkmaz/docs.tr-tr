---
title: BindingSource Bileşeni Mimarisi
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: 54a23ba899ceb05701fe3580aefbb723c6b3f0fd
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364410"
---
# <a name="bindingsource-component-architecture"></a>BindingSource Bileşeni Mimarisi
<xref:System.Windows.Forms.BindingSource> Bileşeniyle, tüm Windows Forms denetimlerini veri kaynaklarına evrensel olarak bağlayabilirsiniz.  
  
 <xref:System.Windows.Forms.BindingSource> Bileşen bir veri kaynağına denetim bağlama sürecini basitleştirir ve geleneksel veri bağlama üzerinde aşağıdaki avantajları sağlar:  
  
- İş nesnelerine tasarım zamanı bağlamayı sağlar.  
  
- İşlevselliği <xref:System.Windows.Forms.CurrencyManager> kapsüller ve olayları <xref:System.Windows.Forms.CurrencyManager> tasarım zamanında kullanıma sunar.  
  
- Liste değişikliği bildirimini yerel olarak desteklemeyen veri <xref:System.ComponentModel.IBindingList> kaynakları için liste değişiklik bildirimi sağlayarak arabirimi destekleyen bir liste oluşturmayı basitleştirir.  
  
- <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType> Yöntemi için bir genişletilebilirlik noktası sağlar.  
  
- Veri kaynağı ile denetim arasında bir yöneltme düzeyi sağlar. Veri kaynağı çalışma zamanında değişebilir bu yöneltme önemlidir.  
  
- , Özellikle <xref:System.Windows.Forms.BindingNavigator> <xref:System.Windows.Forms.DataGridView> ve denetimleri gibi verilerle ilgili diğer Windows Forms denetimleriyle birlikte çalışır.  
  
 Bu nedenlerden dolayı <xref:System.Windows.Forms.BindingSource> bileşen, Windows Forms denetimlerinizi veri kaynaklarına bağlamak için tercih edilen yoldur.  
  
## <a name="bindingsource-features"></a>BindingSource özellikleri  
 Bileşen <xref:System.Windows.Forms.BindingSource> , denetimleri verilere bağlamak için çeşitli özellikler sağlar. Bu özelliklerle, en çok veri bağlama senaryolarını, sizin bölüminizdeki neredeyse hiçbir kodlamaya sahip olacak şekilde uygulayabilirsiniz.  
  
 Bu <xref:System.Windows.Forms.BindingSource> bileşen, birçok farklı türdeki veri kaynağına erişmek için tutarlı bir arabirim sağlayarak bunu gerçekleştirir. Bu, herhangi bir türe bağlamak için aynı yordamı kullandığınız anlamına gelir. Örneğin, <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliğini bir <xref:System.Data.DataSet> veya bir iş nesnesine ekleyebilirsiniz ve her iki durumda da veri kaynağını işlemek için aynı özellik, yöntem ve olay kümesini kullanırsınız.  
  
 <xref:System.Windows.Forms.BindingSource> Bileşen tarafından sunulan tutarlı arabirim, verileri denetimlere bağlama sürecini büyük ölçüde basitleştirir. Değişiklik bildirimi sağlayan veri kaynağı türleri için, <xref:System.Windows.Forms.BindingSource> bileşen denetim ve veri kaynağı arasındaki değişikliklere otomatik olarak iletişim kurar. Değişiklik bildirimi sağlamayan veri kaynağı türleri için, değişiklik bildirimleri yükseltmenize izin veren olaylar sağlanır. Aşağıdaki listede <xref:System.Windows.Forms.BindingSource> bileşen tarafından desteklenen özellikler gösterilmektedir:  
  
- Yöneltme.  
  
- Para birimi yönetimi.  
  
- Liste olarak veri kaynağı.  
  
- <xref:System.Windows.Forms.BindingSource>olarak bir <xref:System.ComponentModel.IBindingList>.  
  
- Özel öğe oluşturma.  
  
- İşlem öğesi oluşturma.  
  
- <xref:System.Collections.IEnumerable>support.  
  
- Tasarım zamanı desteği.  
  
- Statik <xref:System.Windows.Forms.ListBindingHelper> Yöntemler.  
  
- <xref:System.ComponentModel.IBindingListView> Arabirimiyle sıralama ve filtreleme.  
  
- İle <xref:System.Windows.Forms.BindingNavigator>tümleştirme.  
  
### <a name="indirection"></a>Yöneltme  
 Bileşen <xref:System.Windows.Forms.BindingSource> , bir denetim ve veri kaynağı arasında bir yöneltme düzeyi sağlar. Bir denetimi doğrudan bir veri kaynağına bağlamak yerine, denetimi bir <xref:System.Windows.Forms.BindingSource>öğesine bağlarsınız ve veri kaynağını <xref:System.Windows.Forms.BindingSource> bileşenin <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliğine iliştirolursunuz.  
  
 Bu yöneltme düzeyiyle veri kaynağını denetim bağlamasını sıfırlamadan değiştirebilirsiniz. Bu size aşağıdaki olanakları sağlar:  
  
- Geçerli denetim bağlamalarını korurken <xref:System.Windows.Forms.BindingSource> , öğesini farklı veri kaynaklarına iliştirebilirsiniz.  
  
- Veri kaynağındaki öğeleri değiştirebilir ve bağlantılı denetimlere bildirimde bulabilirsiniz. Daha fazla bilgi için [nasıl yapılır: BindingSource](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)Ile Windows Forms denetimindeki veri kaynağı güncelleştirmelerini yansıtır.  
  
- Bellekteki bir <xref:System.Type> nesne yerine öğesine bağlayabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Bir Windows Forms denetimini bir türe](how-to-bind-a-windows-forms-control-to-a-type.md)bağlayın. Daha sonra çalışma zamanında bir nesneye bağlanabilirsiniz.  
  
### <a name="currency-management"></a>Para birimi yönetimi  
 Bileşen, sizin için <xref:System.Windows.Forms.ICurrencyManagerProvider> para birimi yönetimini işlemek üzere arabirimini uygular. <xref:System.Windows.Forms.BindingSource> Arabirimi ile, <xref:System.Windows.Forms.BindingSource> aynı <xref:System.Windows.Forms.BindingSource> zamandabirdiğeriiçinparabirimiyöneticisininyanısırabiriçinparabirimiyöneticisinedaerişebilirsiniz.<xref:System.Windows.Forms.BindingSource.DataMember%2A> <xref:System.Windows.Forms.ICurrencyManagerProvider>  
  
 Bileşen işlevleri Kapsüller <xref:System.Windows.Forms.CurrencyManager> ve en sık kullanılan <xref:System.Windows.Forms.CurrencyManager> özellikleri ve olayları gösterir. <xref:System.Windows.Forms.BindingSource> Aşağıdaki tabloda, para birimi yönetimiyle ilgili bazı Üyeler açıklanmaktadır.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>özelliði  
 İle ilişkili para birimi yöneticisini alır <xref:System.Windows.Forms.BindingSource>.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A>yöntemidir  
 Belirtilen veri üyesine bir <xref:System.Windows.Forms.BindingSource> tane daha varsa, bu, para birimi yöneticisini alır.  
  
 <xref:System.Windows.Forms.BindingSource.Current%2A>özelliði  
 Veri kaynağının geçerli öğesini alır.  
  
 <xref:System.Windows.Forms.BindingSource.Position%2A>özelliði  
 Temel alınan listedeki geçerli konumu alır veya ayarlar.  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A>yöntemidir  
 Temel alınan veri kaynağına bekleyen değişiklikleri uygular.  
  
 <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>yöntemidir  
 Geçerli düzenleme işlemini iptal eder.  
  
### <a name="data-source-as-a-list"></a>Liste olarak veri kaynağı  
 <xref:System.Windows.Forms.BindingSource> Bileşeni <xref:System.ComponentModel.IBindingListView> ve arabirimlerini<xref:System.ComponentModel.ITypedList> uygular. Bu uygulamayla, <xref:System.Windows.Forms.BindingSource> bileşeni herhangi bir dış depolama olmadan bir veri kaynağı olarak kullanabilirsiniz.  
  
 <xref:System.Windows.Forms.BindingSource> Bileşen bir veri kaynağına eklendiğinde, veri kaynağını bir liste olarak kullanıma sunar.  
  
 Özelliği <xref:System.Windows.Forms.BindingSource.DataSource%2A> , çeşitli veri kaynaklarına ayarlanabilir. Bunlar türleri, nesneleri ve tür listelerini içerir. Elde edilen veri kaynağı bir liste olarak gösterilir. Aşağıdaki tabloda bazı ortak veri kaynakları ve elde edilen liste değerlendirmesi gösterilmektedir.  
  
|DataSource özelliği|Liste sonuçları|  
|-------------------------|------------------|  
|Null başvurusu (`Nothing` Visual Basic)|Nesnelerden oluşan <xref:System.ComponentModel.IBindingList> boş bir nesne. Öğe eklendiğinde liste eklenen öğenin türüne ayarlanır.|  
|Küme ile`Nothing` <xref:System.Windows.Forms.BindingSource.DataMember%2A> null başvuru (Visual Basic)|Desteklenmiyor; yükseltir <xref:System.ArgumentException>.|  
|"T" türünde liste olmayan tür veya nesne|"T <xref:System.ComponentModel.IBindingList> " türünde boş.|  
|Dizi örneği|Dizi <xref:System.ComponentModel.IBindingList> öğelerini içeren bir.|  
|<xref:System.Collections.IEnumerable>Instance|Öğeleri<xref:System.Collections.IEnumerable> içeren bir <xref:System.ComponentModel.IBindingList>|  
|"T" türünü içeren liste örneği|"T" türünü içeren örnek.<xref:System.ComponentModel.IBindingList>|  
  
 Ayrıca, <xref:System.ComponentModel.IListSource> <xref:System.Windows.Forms.BindingSource> ve gibidiğerlistetürlerineayarlanabilirvebunlarıuygunşekildeişleymeyecektir.<xref:System.ComponentModel.ITypedList> <xref:System.Windows.Forms.BindingSource.DataSource%2A> Bu durumda, listede yer alan türün parametresiz bir oluşturucusu olmalıdır.  
  
### <a name="bindingsource-as-an-ibindinglist"></a>IBindingList olarak BindingSource  
 Bileşeni <xref:System.Windows.Forms.BindingSource> , temel alınan verilere erişmek ve bu verileri <xref:System.ComponentModel.IBindingList>işlemek için Üyeler sağlar. Aşağıdaki tabloda bu üyelerin bazıları açıklanmaktadır.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.List%2A>özelliði|<xref:System.Windows.Forms.BindingSource.DataSource%2A> Veya<xref:System.Windows.Forms.BindingSource.DataMember%2A> özelliklerinin değerlendirmesinden elde edilen listeyi alır.|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A>yöntemidir|Temel alınan listeye yeni bir öğe ekler. <xref:System.ComponentModel.IBindingList> Arabirimi uygulayan ve öğe eklemeye izin veren veri kaynakları için geçerlidir (yani <xref:System.Windows.Forms.BindingSource.AllowNew%2A> , özelliği olarak `true`ayarlanır).|  
  
### <a name="custom-item-creation"></a>Özel öğe oluşturma  
 Kendi öğe oluşturma mantığınızı sağlamak için <xref:System.Windows.Forms.BindingSource.AddingNew> olayı işleyebilirsiniz. <xref:System.Windows.Forms.BindingSource.AddingNew> Olayı ,<xref:System.Windows.Forms.BindingSource>öğesine yeni bir nesne eklenmeden önce oluşur. Bu olay, <xref:System.Windows.Forms.BindingSource.AddNew%2A> yöntemi çağrıldıktan sonra, ancak yeni öğe temel alınan listeye eklenmeden önce tetiklenir. Bu olayı işleyerek, <xref:System.Windows.Forms.BindingSource> sınıftan türemeksizin özel öğe oluşturma davranışı sağlayabilirsiniz. Daha fazla bilgi için [nasıl yapılır: Windows Forms BindingSource](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)ile öğe eklemeyi özelleştirin.  
  
### <a name="transactional-item-creation"></a>İşlem öğesi oluşturma  
 Bileşen, işlem öğesi <xref:System.ComponentModel.ICancelAddNew> oluşturmaya izin veren arabirimini uygular. <xref:System.Windows.Forms.BindingSource> Yeni bir öğe çağrısı <xref:System.Windows.Forms.BindingSource.AddNew%2A>kullanılarak geçici olarak oluşturulduktan sonra, ekleme işlemi aşağıdaki yollarla uygulanabilir veya geri döndürülebilir:  
  
- <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> Yöntemi, bekleyen ekleme işlemi açıkça uygulanır.  
  
- Ekleme, kaldırma veya taşıma gibi başka bir koleksiyon işlemi gerçekleştirmek, bekleyen ekleme işlemini örtülü olarak işlemeye çalışır.  
  
- Yöntem henüz yürütülmemiş ise Yöntem,bekleyeneklemeyigerialacak.<xref:System.ComponentModel.ICancelAddNew.CancelNew%2A>  
  
### <a name="ienumerable-support"></a>IEnumerable desteği  
 Bileşen <xref:System.Windows.Forms.BindingSource> , <xref:System.Collections.IEnumerable> veri kaynaklarına denetim bağlamayı sağlar. Bu bileşenle, gibi bir <xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>veri kaynağına bağlanabilirsiniz.  
  
 <xref:System.Windows.Forms.BindingSource> Bileşene <xref:System.Collections.IEnumerable> birveri<xref:System.ComponentModel.IBindingList> kaynağı atandığında, bir <xref:System.Collections.IEnumerable> oluşturur ve veri kaynağının içeriğini listeye ekler. <xref:System.Windows.Forms.BindingSource>  
  
### <a name="design-time-support"></a>Tasarım zamanı desteği  
 Bir fabrika sınıfından oluşturulan nesneler veya bir Web hizmeti tarafından döndürülen nesneler gibi tasarım zamanında bazı nesne türleri oluşturulamaz. Denetimlerinizin bağlayabileceği bellekte hiç nesne olmasa bile, bazı durumlarda denetimlerinizi bu türlere tasarım zamanında bağlamanız gerekebilir. Örneğin, bir <xref:System.Windows.Forms.DataGridView> denetimin sütun üstbilgilerini özel türün ortak özelliklerinin adlarıyla etiketlemenize gerek vardır.  
  
 Bu senaryoyu desteklemek için <xref:System.Windows.Forms.BindingSource> bileşen bir ' a <xref:System.Type>bağlamayı destekler. Özelliğine<xref:System.Windows.Forms.BindingSource.DataSource%2A> bir <xref:System.Type> atadığınızda <xref:System.ComponentModel.BindingList%601> , <xref:System.Windows.Forms.BindingSource> bileşen bir öğe<xref:System.Type> boş oluşturur. Daha sonra <xref:System.Windows.Forms.BindingSource> bileşene daha sonra bağlanan denetimler, tasarım zamanında veya çalışma zamanında, yazdığınız özelliklerin veya şemanın varlığı ile ilgili olarak uyarılacaktır. Daha fazla bilgi için [nasıl yapılır: Bir Windows Forms denetimini bir türe](how-to-bind-a-windows-forms-control-to-a-type.md)bağlayın.  
  
### <a name="static-listbindinghelper-methods"></a>Statik ListBindingHelper yöntemleri  
 <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>, Vetürleri<xref:System.Windows.Forms.BindingSource> bir çiftin/ listesini oluşturmak için tüm ortak mantığı paylaşır. `DataSource` <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType> `DataMember` Ayrıca, bu ortak mantık aşağıdaki `static` yöntemlerde denetim yazarları ve diğer üçüncü taraflar tarafından kullanıma açıktır:  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>IBindingListView arabirimiyle sıralama ve filtreleme  
 Bileşen arabirimini <xref:System.ComponentModel.IBindingListView> genişleten<xref:System.ComponentModel.IBindingList>arabiriminiuygular. <xref:System.Windows.Forms.BindingSource> Tek sütunlu sıralama <xref:System.ComponentModel.IBindingListView> ve gelişmiş sıralama ve filtreleme olanakları sunar. <xref:System.ComponentModel.IBindingList> İle <xref:System.ComponentModel.IBindingListView>veri kaynağı bu arabirimlerden birini de uygularsa, veri kaynağındaki öğeleri sıralayabilir ve filtreleyebilirsiniz. <xref:System.Windows.Forms.BindingSource> Bileşen bu üyelerin başvuru uygulamasını sağlamıyor. Bunun yerine, çağrılar temel alınan listeye iletilir.  
  
 Aşağıdaki tabloda, sıralama ve filtreleme için kullandığınız özellikler açıklanmaktadır.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A>özelliði|Veri kaynağı bir <xref:System.ComponentModel.IBindingListView>ise, hangi satırların görüntülendiğini filtrelemek için kullanılan ifadeyi alır veya ayarlar.|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A>özelliði|Veri kaynağı bir <xref:System.ComponentModel.IBindingList>ise, sıralama ve sıralama bilgileri için kullanılan bir sütun adı alır veya ayarlar.<br /><br /> -veya-<br /><br /> Veri kaynağı bir <xref:System.ComponentModel.IBindingListView> ise ve gelişmiş sıralamayı destekliyorsa, sıralama ve sıralama düzeni için kullanılan birden çok sütun adı alır|  
  
### <a name="integration-with-bindingnavigator"></a>BindingNavigator ile tümleştirme  
 <xref:System.Windows.Forms.BindingSource> Bileşeni, herhangi bir Windows Forms denetimini bir veri kaynağına bağlamak için kullanabilirsiniz, <xref:System.Windows.Forms.BindingNavigator> ancak denetim <xref:System.Windows.Forms.BindingSource> özellikle bileşenle çalışmak üzere tasarlanmıştır. Denetim <xref:System.Windows.Forms.BindingNavigator> , <xref:System.Windows.Forms.BindingSource> bileşenin geçerli öğesini denetlemek için bir kullanıcı arabirimi sağlar. Varsayılan <xref:System.Windows.Forms.BindingNavigator> olarak denetim, <xref:System.Windows.Forms.BindingSource> bileşendeki gezinti yöntemlerine karşılık gelen düğmeleri sağlar. Daha fazla bilgi için [nasıl yapılır: Windows Forms BindingNavigator denetimiyle](how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md)verileri gezin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [BindingSource Bileşenine Genel Bakış](bindingsource-component-overview.md)
- [BindingNavigator Denetimi](bindingnavigator-control-windows-forms.md)
- [Windows Forms Veri Bağlama](../windows-forms-data-binding.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [Nasıl yapılır: Windows Forms denetimini bir türe bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Nasıl yapılır: BindingSource ile Windows Forms denetimindeki veri kaynağı güncelleştirmelerini yansıtma](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)
