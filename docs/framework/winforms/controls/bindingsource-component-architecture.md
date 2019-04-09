---
title: BindingSource Bileşeni Mimarisi
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: 81559444b6e3da2861e48bdc637ae01d246c0758
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165353"
---
# <a name="bindingsource-component-architecture"></a>BindingSource Bileşeni Mimarisi
İle <xref:System.Windows.Forms.BindingSource> bileşeni, Evrensel bağlayabilirsiniz tüm Windows Formları denetimleri için veri kaynakları.  
  
 <xref:System.Windows.Forms.BindingSource> Bileşeni denetimlerini bir veri kaynağına bağlama işlemini basitleştirir ve geleneksel veri bağlama aşağıdaki avantajları sunar:  
  
-   İş nesneler için tasarım zamanı bağlamayı etkinleştirir.  
  
-   Kapsülleyen <xref:System.Windows.Forms.CurrencyManager> işlevsellik ve kullanıma sunan <xref:System.Windows.Forms.CurrencyManager> tasarım zamanında olayları.  
  
-   Destekleyen liste oluşturma basitleştirir <xref:System.ComponentModel.IBindingList> değişikliği bildirimi listesi yerel olarak desteklemeyen veri kaynakları listesinde değişiklik bildirimi sağlayarak arabirimi.  
  
-   Bir genişletilebilirlik noktası sağlar <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType> yöntemi.  
  
-   Veri kaynağı ve denetim arasında bir yöneltme düzeyi sağlar. Veri kaynağı çalışma zamanında değiştirebiliyorsa, bu yöneltme önemlidir.  
  
-   Diğer ilgili verileri Windows Forms dentimleriyle özellikle birlikte çalışır <xref:System.Windows.Forms.BindingNavigator> ve <xref:System.Windows.Forms.DataGridView> kontrol eder.  
  
 Bu nedenlerle, <xref:System.Windows.Forms.BindingSource> bileşenidir, Windows Forms denetimleri veri kaynaklarına bağlamak için tercih edilen yoludur.  
  
## <a name="bindingsource-features"></a>BindingSource özellikleri  
 <xref:System.Windows.Forms.BindingSource> Bileşen verilere denetimler bağlama için çeşitli özellikler sunar. Bu özellikleri ile neredeyse bulunmanıza kodlama ile çoğu veri bağlama senaryoları uygulayabilirsiniz.  
  
 <xref:System.Windows.Forms.BindingSource> Bileşen gerçekleştirir Bu birçok farklı türde veri kaynaklarına erişmek için tutarlı bir arabirim sağlayarak. Başka bir deyişle, bağlama herhangi bir tür için aynı yordamı kullanın. Örneğin, iliştirebilirsiniz <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliğini bir <xref:System.Data.DataSet> veya bir iş nesnesi için ve her iki durumda, aynı özellikleri, yöntemleri ve olayları veri kaynağını değiştirmek için kullanın.  
  
 Tarafından sağlanan tutarlı arabirimi <xref:System.Windows.Forms.BindingSource> bileşen denetimlere veri bağlama işlemini büyük ölçüde basitleştirir. Veri kaynağı türler değişikliği bildirimi, <xref:System.Windows.Forms.BindingSource> bileşen denetim ve veri kaynağı arasındaki değişiklikleri otomatik olarak iletişim kurar. Değişiklik bildirimi sağlamayan veri kaynağı türleri için değişiklik bildirimleri yükseltmek sağlayan olaylar sağlanır. Aşağıdaki liste tarafından desteklenen özellikler gösterir <xref:System.Windows.Forms.BindingSource> bileşeni:  
  
-   Yöneltme.  
  
-   Para birimi yönetimi.  
  
-   Veri kaynağı olarak bir listesi.  
  
-   <xref:System.Windows.Forms.BindingSource> olarak bir <xref:System.ComponentModel.IBindingList>.  
  
-   Özel öğe oluşturma.  
  
-   İşlem öğe oluşturma.  
  
-   <xref:System.Collections.IEnumerable> destekler.  
  
-   Tasarım zamanı desteği.  
  
-   Statik <xref:System.Windows.Forms.ListBindingHelper> yöntemleri.  
  
-   Sıralama ve filtreleme ile <xref:System.ComponentModel.IBindingListView> arabirimi.  
  
-   İle tümleştirme <xref:System.Windows.Forms.BindingNavigator>.  
  
### <a name="indirection"></a>Yöneltme  
 <xref:System.Windows.Forms.BindingSource> Bileşeni, Denetim ve veri kaynağı arasında bir yöneltme düzeyi sağlar. Bir denetimi doğrudan bir veri kaynağına bağlama yerine denetime bağlamak bir <xref:System.Windows.Forms.BindingSource>, ve veri kaynağına ekleme <xref:System.Windows.Forms.BindingSource> bileşenin <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliği.  
  
 Bu yöneltme düzeyi ile veri kaynağı denetimi bağlama sıfırlamadan değiştirebilirsiniz. Bu, aşağıdaki özellikleri sağlar:  
  
-   İliştirebilirsiniz <xref:System.Windows.Forms.BindingSource> geçerli denetim bağlamalarını korurken farklı veri kaynaklarına.  
  
-   Veri kaynağındaki öğeleri değiştirmek ve ilişkili denetimler bildirir. Daha fazla bilgi için [nasıl yapılır: BindingSource ile Windows Forms denetiminde veri kaynağı güncelleştirmelerini yansıtma](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md).  
  
-   Bağlayabileceğiniz bir <xref:System.Type> bellekte bir nesne yerine. Daha fazla bilgi için [nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama](how-to-bind-a-windows-forms-control-to-a-type.md). Ardından, bir nesneye çalışma zamanında bağlayabilirsiniz.  
  
### <a name="currency-management"></a>Para birimi yönetimi  
 <xref:System.Windows.Forms.BindingSource> Bileşenini uygulayan <xref:System.Windows.Forms.ICurrencyManagerProvider> para birimi yönetimini işlemek için arabirim. İle <xref:System.Windows.Forms.ICurrencyManagerProvider> arabirimi da erişebilirsiniz için para birimi Yöneticisi için bir <xref:System.Windows.Forms.BindingSource>, başka bir para birimi Yöneticisi yanı sıra <xref:System.Windows.Forms.BindingSource> aynı bağlı <xref:System.Windows.Forms.BindingSource.DataMember%2A>.  
  
 <xref:System.Windows.Forms.BindingSource> Bileşeni kapsülleyen <xref:System.Windows.Forms.CurrencyManager> işlevsellik ve kullanıma sunan en yaygın <xref:System.Windows.Forms.CurrencyManager> özellikler ve olaylar. Aşağıdaki tabloda, para birimi yönetimiyle ilgili üyelerin bazılarını açıklar.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> özellik  
 İle ilişkili para birimi Yöneticisi alır <xref:System.Windows.Forms.BindingSource>.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A> yöntemi  
 Varsa başka <xref:System.Windows.Forms.BindingSource> belirtilen veri üyesine bağlıysa, kendi para birimi Yöneticisi alır.  
  
 <xref:System.Windows.Forms.BindingSource.Current%2A> özellik  
 Veri kaynağının geçerli öğeyi alır.  
  
 <xref:System.Windows.Forms.BindingSource.Position%2A> özellik  
 Alır veya ayarlar temel listesi geçerli konumu.  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> yöntemi  
 Bekleyen değişiklikler temel alınan veri kaynağına uygular.  
  
 <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> yöntemi  
 Geçerli düzenleme işlemi iptal eder.  
  
### <a name="data-source-as-a-list"></a>Veri kaynağı olarak bir liste  
 <xref:System.Windows.Forms.BindingSource> Bileşenini uygulayan <xref:System.ComponentModel.IBindingListView> ve <xref:System.ComponentModel.ITypedList> arabirimleri. Bu uygulama ile kullanabileceğiniz <xref:System.Windows.Forms.BindingSource> bileşene bir veri kaynağı olarak herhangi bir dış depolama olmadan.  
  
 Zaman <xref:System.Windows.Forms.BindingSource> bileşen bir veri kaynağına bağlı, veri kaynağı olarak bir listesini sunar.  
  
 <xref:System.Windows.Forms.BindingSource.DataSource%2A> Özelliği, çeşitli veri kaynakları için ayarlanabilir. Bunlar, türleri, nesneleri ve türlerinin bir listesini içerir. Sonuçta elde edilen veri kaynağı bir listesi sunulur. Aşağıdaki tabloda, genel veri kaynakları ve elde edilen listesi değerlendirme bazıları gösterilmektedir.  
  
|DataSource özelliği|Liste sonuçlarından|  
|-------------------------|------------------|  
|Bir null başvuru (`Nothing` Visual Basic)|Boş bir <xref:System.ComponentModel.IBindingList> nesne. Bir öğe ekleme listeye eklenen öğe türünü ayarlar.|  
|Bir null başvuru (`Nothing` Visual Basic'te) ile <xref:System.Windows.Forms.BindingSource.DataMember%2A> ayarlayın|Desteklenmeyen; başlatır <xref:System.ArgumentException>.|  
|Olmayan listesi türü veya "T" türündeki nesne|Boş bir <xref:System.ComponentModel.IBindingList> "T" türü.|  
|Dizi örneği|Bir <xref:System.ComponentModel.IBindingList> dizi öğeleri içeren.|  
|<xref:System.Collections.IEnumerable> örnek|Bir <xref:System.ComponentModel.IBindingList> içeren <xref:System.Collections.IEnumerable> öğeleri|  
|"T" türünü içeren örnek listesi|Bir <xref:System.ComponentModel.IBindingList> örnek türü "T" içeren.|  
  
 Ayrıca, <xref:System.Windows.Forms.BindingSource.DataSource%2A> gibi diğer liste türlerine ayarlanabilir <xref:System.ComponentModel.IListSource> ve <xref:System.ComponentModel.ITypedList>ve <xref:System.Windows.Forms.BindingSource> bunları uygun şekilde işler. Bu durumda, listede yer alan türü varsayılan bir oluşturucuya sahip olmalıdır.  
  
### <a name="bindingsource-as-an-ibindinglist"></a>IBindingList olarak BindingSource  
 <xref:System.Windows.Forms.BindingSource> Bileşeni üyelere erişme ve temel alınan verileri olarak yönlendirmek için bir <xref:System.ComponentModel.IBindingList>. Aşağıdaki tabloda bu üyelerin bazılarını açıklar.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.List%2A> özellik|' In değerlendirmesinden gelen sonuçları listesi alır <xref:System.Windows.Forms.BindingSource.DataSource%2A> veya <xref:System.Windows.Forms.BindingSource.DataMember%2A> özellikleri.|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A> yöntemi|Yeni bir öğe temel alınan listesine ekler. Uygulayan veri kaynaklarına uygulanır <xref:System.ComponentModel.IBindingList> arabirim ve öğeleri eklemeye izin ver (diğer bir deyişle, <xref:System.Windows.Forms.BindingSource.AllowNew%2A> özelliği `true`).|  
  
### <a name="custom-item-creation"></a>Özel öğesi oluşturma  
 İşleyebilirsiniz <xref:System.Windows.Forms.BindingSource.AddingNew> kendi öğe oluşturma mantığını sağlamak için olay. <xref:System.Windows.Forms.BindingSource.AddingNew> Gerçekleştiğinde yeni bir nesne için eklenmeden önce <xref:System.Windows.Forms.BindingSource>. Sonra bu olay tetiklenir <xref:System.Windows.Forms.BindingSource.AddNew%2A> yöntemi çağrılır, ancak temel alınan listesine yeni öğe eklenmesi. Bu olay işleme tarafından özel öğesi oluşturma davranışını türetme olmadan sağlayabilirsiniz <xref:System.Windows.Forms.BindingSource> sınıfı. Daha fazla bilgi için [nasıl yapılır: Windows Forms BindingSource ile öğe eklemeyi özelleştirme](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md).  
  
### <a name="transactional-item-creation"></a>İşlem öğesi oluşturma  
 <xref:System.Windows.Forms.BindingSource> Bileşenini uygulayan <xref:System.ComponentModel.ICancelAddNew> arabirimi, işlem bir öğe oluşturmanıza olanak tanır. Yeni bir öğe için bir çağrı kullanılarak ayrıştırmanın oluşturulduktan sonra <xref:System.Windows.Forms.BindingSource.AddNew%2A>, ayrıca kaydedilmiş veya aşağıdaki yollarla geri alındı:  
  
-   <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> Yöntemi açıkça eklenmeyi bekliyor işleyin.  
  
-   Ekleme, kaldırma veya taşıma, gibi başka bir toplama işlemi gerçekleştirmek, örtük olarak eklenmeyi bekliyor işleme.  
  
-   <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A> Yöntemi geri eklenmeyi bekliyor, metodu zaten kaydedilmemiş.  
  
### <a name="ienumerable-support"></a>IEnumerable desteği  
 <xref:System.Windows.Forms.BindingSource> Bileşeni sağlayan denetimlerini bağlama <xref:System.Collections.IEnumerable> veri kaynakları. Bu bileşen için bir veri kaynağı gibi bağlayabilirsiniz bir <xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>.  
  
 Olduğunda bir <xref:System.Collections.IEnumerable> veri kaynağı için atandığı <xref:System.Windows.Forms.BindingSource> bileşeni <xref:System.Windows.Forms.BindingSource> oluşturur bir <xref:System.ComponentModel.IBindingList> ve içeriğini ekler <xref:System.Collections.IEnumerable> listesine veri kaynağı.  
  
### <a name="design-time-support"></a>Tasarım zamanı desteği  
 Tasarım zamanında bir Fabrika sınıfından oluşturulan nesneler veya bir Web hizmeti tarafından döndürülen nesne gibi bazı nesne türleri oluşturulamaz. Denetimlerinizi adlarınıza bağlayabileceğiniz bellekte bir nesne olsa denetimleri tasarım zamanında, bu tür için bağlama bazen gerekebilir. Örneğin, sütun başlıklarını etiketlemek ihtiyacınız olabilir bir <xref:System.Windows.Forms.DataGridView> denetimi ile özel türün genel özelliklerin adları.  
  
 Bu senaryoyu desteklemek için <xref:System.Windows.Forms.BindingSource> bileşeni bağlamayı destekleyen bir <xref:System.Type>. Atadığınızda bir <xref:System.Type> için <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliği <xref:System.Windows.Forms.BindingSource> bileşeni oluşturur boş <xref:System.ComponentModel.BindingList%601> , <xref:System.Type> öğeleri. Daha sonra bağlamak üzere herhangi bir denetim <xref:System.Windows.Forms.BindingSource> bileşen uyarılmak varlığını özelliklerini veya şema türünüz için tasarım zamanında ya da çalışma zamanında. Daha fazla bilgi için [nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama](how-to-bind-a-windows-forms-control-to-a-type.md).  
  
### <a name="static-listbindinghelper-methods"></a>Statik ListBindingHelper yöntemleri  
 <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>, <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType>, Ve <xref:System.Windows.Forms.BindingSource> listesinden bir liste oluşturmak için tüm paylaşım ortak mantığını türleri bir `DataSource` / `DataMember` çifti. Ayrıca, bu sık kullanılan mantıksal genel kullanım için tarafından denetim yazarlar ve diğer üçüncü taraflara aşağıdaki sunulan `static` yöntemleri:  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>biçimindeki telefon numarasıdır.  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>Sıralama ve filtreleme ile IBindingListView arabirimi  
 <xref:System.Windows.Forms.BindingSource> Bileşenini uygulayan <xref:System.ComponentModel.IBindingListView> genişleten arabirimi <xref:System.ComponentModel.IBindingList> arabirimi. <xref:System.ComponentModel.IBindingList> Tek sütun sıralama sunar ve <xref:System.ComponentModel.IBindingListView> teklifler Gelişmiş sıralama ve filtreleme. İle <xref:System.ComponentModel.IBindingListView>sıralayabilir ve filtre öğeleri aynı zamanda veri kaynağı, veri kaynağında, bu arabirimlerinden birini uygular. <xref:System.Windows.Forms.BindingSource> Bileşen, bu üyenin bir başvuru uygulaması sağlamaz. Bunun yerine, aramalar temel alınan listesine iletilir.  
  
 Aşağıdaki tabloda, sıralama ve filtreleme için kullandığınız özellikler açıklanmaktadır.  
  
|Üye|Açıklama|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A> özellik|Veri kaynağı ise bir <xref:System.ComponentModel.IBindingListView>hangi satırların görüntülenen filtrelemek için kullanılan ifade ayarlar veya alır.|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A> özellik|Veri kaynağı ise bir <xref:System.ComponentModel.IBindingList>sıralama ve sipariş bilgilerini sıralama için kullanılan sütun adını ayarlar veya alır.<br /><br /> -veya-<br /><br /> Veri kaynağı ise bir <xref:System.ComponentModel.IBindingListView> ve sıralama, Gelişmiş destekler, sıralama ve sıralama için kullanılan birden fazla sütun adlarını alır|  
  
### <a name="integration-with-bindingnavigator"></a>BindingNavigator ile tümleştirme  
 Kullanabileceğiniz <xref:System.Windows.Forms.BindingSource> herhangi bir Windows Forms denetimini bir veri kaynağına bağlamak için bileşen ancak <xref:System.Windows.Forms.BindingNavigator> denetimi ile özel olarak çalışacak şekilde tasarlanmıştır <xref:System.Windows.Forms.BindingSource> bileşeni. <xref:System.Windows.Forms.BindingNavigator> Denetim denetlemek için bir kullanıcı arabirimi sağlar <xref:System.Windows.Forms.BindingSource> bileşenin geçerli öğesi. Varsayılan olarak, <xref:System.Windows.Forms.BindingNavigator> denetim üzerinde karşılık gelen gezinme yöntemlerine düğmeler sağlar <xref:System.Windows.Forms.BindingSource> bileşeni. Daha fazla bilgi için [nasıl yapılır: Windows Forms BindingNavigator denetimi ile verilerde gezinme](how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [BindingSource Bileşenine Genel Bakış](bindingsource-component-overview.md)
- [BindingNavigator Denetimi](bindingnavigator-control-windows-forms.md)
- [Windows Forms Veri Bağlama](../windows-forms-data-binding.md)
- [Windows Forms'ta Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
- [Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Nasıl yapılır: BindingSource ile Windows Forms Denetiminde Veri Kaynağı Güncelleştirmelerini Yansıtma](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)
