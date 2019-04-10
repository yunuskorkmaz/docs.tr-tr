---
title: Veri Bağlama ile İlgili Arabirimler
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], data-binding interfaces
- INotifyPropertyChanged interface
- IBindingListView interface
- IList interface [Windows Forms], Windows Forms data binding
- IBindingList interface [Windows Forms], Windows Forms data binding
- interfaces [Windows Forms], Windows Forms data binding
- IEditableObject interface [Windows Forms], Windows Forms data binding
- data binding [Windows Forms], interfaces
- IDataErrorInfo interface [Windows Forms], Windows Forms data binding
ms.assetid: 14e49a2e-3e46-47ca-b491-70d546333277
ms.openlocfilehash: ffda85b2704212ea5323117447e0cfe17ffb33db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226978"
---
# <a name="interfaces-related-to-data-binding"></a>Veri Bağlama ile İlgili Arabirimler
İle [!INCLUDE[vstecado](../../../includes/vstecado-md.md)], uygulamanızı ve birlikte çalıştığınız veri bağlama gereksinimlerine uyacak şekilde birçok farklı veri yapılarını oluşturabilirsiniz. Kendi sınıflarınızı sağlayan veya tüketen Windows Forms verilerinde oluşturmak isteyebilirsiniz. Bu nesneler, temel veri bağlamanın dışında veri için yapılan değişikliklerin yapılandırılmış bir geri alma için tasarım zamanı desteği, hata denetimi, değişiklik bildirimi veya hatta destek sağlamaya işlevselliği ve karmaşıklığı, çeşitli izin düzeyleriyle sunabilir.  
  
## <a name="consumers-of-data-binding-interfaces"></a>Veri bağlama arabirimleri tüketicilerinin  
 Aşağıdaki bölümlerde iki grup arabirimi nesnelerin açıklanmaktadır. İlk Grup veri kaynaklarında veri kaynağı yazarları tarafından uygulanan arabirimler listelenmiştir. Bu arabirimler, çoğu Windows Forms denetimleri durumları veya bileşenleri olan veri kaynağı tüketicileri tarafından kullanılması için tasarlanmıştır. İkinci grup bileşen yazarları tarafından kullanılmak üzere tasarlanmış arabirimleri listeler. Bileşen yazarları, Windows Forms veri bağlama altyapısı tarafından kullanılması için veri bağlamayı destekleyen bir bileşeni oluştururken bu arabirimler kullanın. Bu arabirim içinde veri bağlamayı etkinleştirmek için bir formla ilişkili sınıfları uygulayabilir; her durumda, verilerle etkileşimi sağlayan bir arabirimi uygulayan bir sınıf sunar. Visual Studio hızlı uygulama geliştirme (RAD) veri tasarım deneyimini Araçları zaten bu işlevselliği yararlanın.  
  
### <a name="interfaces-for-implementation-by-data-source-authors"></a>Uygulama veri kaynağı yazarlar tarafından arabirimleri  
 Windows Forms denetimleri tarafından kullanılması için aşağıdaki arabirimlerinden tasarlanmıştır:  
  
-   <xref:System.Collections.IList> arabirim  
  
     Uygulayan bir sınıf <xref:System.Collections.IList> arabirimi olabilir bir <xref:System.Array>, <xref:System.Collections.ArrayList>, veya <xref:System.Collections.CollectionBase>. Bu öğe türü dizinli listeleridir <xref:System.Object>. Bu listeler, dizinin ilk öğesi türü belirlediğinden homojen türleri içermesi gerekir. <xref:System.Collections.IList> yalnızca çalışma zamanında bağlama için kullanılabilir hale gelir.  
  
    > [!NOTE]
    >  Windows Forms ile bağlama için iş nesnelerin bir listesini oluşturmak istiyorsanız, kullanmayı düşünmelisiniz <xref:System.ComponentModel.BindingList%601>. <xref:System.ComponentModel.BindingList%601> İki yönlü Windows Forms veri bağlama için gerekli birincil arabirimlerini uygular genişletilebilir bir sınıftır.  
  
-   <xref:System.ComponentModel.IBindingList> arabirim  
  
     Uygulayan bir sınıf <xref:System.ComponentModel.IBindingList> arabirimi daha yüksek veri bağlama işlevselliği sağlar. Bu uygulama, temel sıralama yetenekleri ve ne zaman değişiklik listesi öğeleri için değişiklik bildirimi sunar (örneğin, müşterilerin listesindeki üçüncü öğe bir değişiklik adres alanına sahiptir), liste değiştiğinde yanı sıra (örneğin, Listedeki öğe sayısını artırır veya azaltır). Değişiklik bildirimi, birden çok denetim aynı verilere bağlı olmasını planladığınız ve diğer ilişkili denetimler yayılması denetimlerden birini yapılan veri değişikliklerini istiyorsanız önemlidir.  
  
    > [!NOTE]
    >  Değişiklik bildirimi için etkin <xref:System.ComponentModel.IBindingList> aracılığıyla arabirim <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A> özelliği, `true`, başlatır bir <xref:System.ComponentModel.IBindingList.ListChanged> değiştirilmiş liste veya listeden bir öğeyi gösteren olay değiştirildi.  
  
     Değişiklik türü tarafından açıklanan <xref:System.ComponentModel.ListChangedType> özelliği <xref:System.ComponentModel.ListChangedEventArgs> parametresi. Bu nedenle, veri modelinin her güncelleştirildiğinde, aynı veri kaynağına bağlı diğer denetimler gibi tüm bağımlı görünümleri de güncelleştirilir. Listede yer alan nesneleri ancak liste gönderebilirsiniz, böylece bunlar değiştiğinde uyarı listesi gerekir <xref:System.ComponentModel.IBindingList.ListChanged> olay.  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BindingList%601> Genel bir uygulamasını sağlar <xref:System.ComponentModel.IBindingList> arabirimi.  
  
-   <xref:System.ComponentModel.IBindingListView> arabirim  
  
     Uygulayan bir sınıf <xref:System.ComponentModel.IBindingListView> arabirimi uygulaması tüm işlevleri sağlayan <xref:System.ComponentModel.IBindingList>de olarak filtreleme ve gelişmiş işlevleri sıralama. Bu uygulama, dize tabanlı filtreleme ve özellik tanımlayıcısı yön çiftiyle sütunlu sıralama sunar.  
  
-   <xref:System.ComponentModel.IEditableObject> arabirim  
  
     Uygulayan bir sınıf <xref:System.ComponentModel.IEditableObject> bir nesne, o nesnenin kalıcı değişiklikler denetlemek arabirim sağlar. Bu uygulama, ortaya koymaktadır <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, ve <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> etkinleştirmeniz nesneye yapılan değişiklikleri geri almak yöntemleri. İşlevleriyle ilgili kısa bir açıklaması verilmiştir <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, ve <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> yöntemleri ve başka bir olası verilerde yapılan değişiklikleri geri etkinleştirmek için birlikte nasıl çalışır:  
  
    -   <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> Yöntemi, bir nesne üzerinde bir düzenleme başlangıcını bildirir. Bu arabirimi uygulayan bir nesne sonra herhangi bir güncelleştirme depolamanız gerekir <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> güncelleştirmeleri atılabilir şekilde yöntemi çağrısı, <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> yöntemi çağrılır. Windows Forms bağlama verilerinde çağırabilirsiniz <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> birden çok kez tek bir kapsamında işlem düzenleme (örneğin, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>). Uygulamaları <xref:System.ComponentModel.IEditableObject> olup izlenmesi <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> zaten çağrıldı ve yapılan sonraki çağrılar Yoksay <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>. Bu yöntem, birden çok kez çağrılabilir çünkü kendisine yapılan sonraki çağrılar dönüşlü önemlidir; diğer bir deyişle, sonraki <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> çağrıları yapıldı veya kaydedilmiş olan veri güncelleştirmeleri yok edilemez ilk <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> çağırın.  
  
    -   <xref:System.ComponentModel.IEditableObject.EndEdit%2A> Yöntemi bu yana herhangi bir değişiklik gönderim <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> nesne şu anda düzenleme modunda ise temel alınan nesnede çağrıldı.  
  
    -   <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> Yöntemi nesneye yapılan tüm değişiklikleri çıkarır.  
  
     Nasıl hakkında daha fazla bilgi için <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, ve <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> yöntemleri çalışma, bkz [verileri yeniden veritabanına kaydetme](/visualstudio/data-tools/save-data-back-to-the-database).  
  
     Bu işlem veri işlevleri kavramı tarafından kullanılan <xref:System.Windows.Forms.DataGridView> denetimi.  
  
-   <xref:System.ComponentModel.ICancelAddNew> arabirim  
  
     Uygulayan bir sınıf <xref:System.ComponentModel.ICancelAddNew> genellikle arabirimi uygulayan <xref:System.ComponentModel.IBindingList> arabirim ve veri kaynağı ile yapılan bir toplama geri sağlar <xref:System.ComponentModel.IBindingList.AddNew%2A> yöntemi. Uygular, veri kaynağı, <xref:System.ComponentModel.IBindingList> arabirimi, sahip olmanız gereken Ayrıca, uygulama <xref:System.ComponentModel.ICancelAddNew> arabirimi.  
  
-   <xref:System.ComponentModel.IDataErrorInfo> arabirim  
  
     Uygulayan bir sınıf <xref:System.ComponentModel.IDataErrorInfo> nesneleri bağlı denetimler için özel hata bilgileri sunmak arabirim sağlar:  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Error%2A> Özelliği genel hata iletisi metni döndürür (örneğin, "bir hata oluştu").  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Item%2A> Özelliği sütundan belirli hata iletisiyle bir dize döndürür (örneğin, "değer `State` sütun geçersiz").  
  
-   <xref:System.Collections.IEnumerable> arabirim  
  
     Uygulayan bir sınıf <xref:System.Collections.IEnumerable> arabirimi tarafından tüketilen genellikle [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]. Bu arabirim için Windows Forms desteği aracılığıyla, yalnızca <xref:System.Windows.Forms.BindingSource> bileşeni.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource> Bileşeni tüm kopyalar <xref:System.Collections.IEnumerable> bağlama amacıyla için ayrı bir liste öğeleri.  
  
-   <xref:System.ComponentModel.ITypedList> arabirim  
  
     Uygulayan bir koleksiyonları sınıf <xref:System.ComponentModel.ITypedList> arabirimi sırasını ve bağımlı denetimi için kullanıma sunulan özellikler kümesini denetleme olanağı sağlar.  
  
    > [!NOTE]
    >  Uyguladığınızda <xref:System.ComponentModel.ITypedList.GetItemProperties%2A> yöntemi ve <xref:System.ComponentModel.PropertyDescriptor> dizisi null değil, son giriş dizideki öğelerin başka bir listesini liste özelliği tanımlayan özellik tanımlayıcı olacaktır.  
  
-   <xref:System.ComponentModel.ICustomTypeDescriptor> arabirim  
  
     Uygulayan bir sınıf <xref:System.ComponentModel.ICustomTypeDescriptor> arabirimi kendisiyle ilgili dinamik bilgiler sağlar. Bu arabirim benzer <xref:System.ComponentModel.ITypedList> ancak listeleri yerine nesneler için kullanılır. Bu arabirim tarafından kullanılan <xref:System.Data.DataRowView> temel alınan satırları şemasını planlamak için. Basit bir uygulaması <xref:System.ComponentModel.ICustomTypeDescriptor> tarafından sağlanan <xref:System.ComponentModel.CustomTypeDescriptor> sınıfı.  
  
    > [!NOTE]
    >  Tasarım zamanı bağlamayı desteklemek için uygulayan türleri <xref:System.ComponentModel.ICustomTypeDescriptor>, türü de uygulamalıdır <xref:System.ComponentModel.IComponent> ve formdaki bir örnek olarak mevcut.  
  
-   <xref:System.ComponentModel.IListSource> arabirim  
  
     Uygulayan bir sınıf <xref:System.ComponentModel.IListSource> arabirimi liste tabanlı bağlama listesinde olmayan nesneler üzerinde sağlar. <xref:System.ComponentModel.IListSource.GetList%2A> Yöntemi <xref:System.ComponentModel.IListSource> öğesinden devralmayan bir nesneden bağlanabilir listesini döndürmek için kullanılan <xref:System.Collections.IList>. <xref:System.ComponentModel.IListSource> tarafından kullanılan <xref:System.Data.DataSet> sınıfı.  
  
-   <xref:System.ComponentModel.IRaiseItemChangedEvents> arabirim  
  
     Uygulayan bir sınıf <xref:System.ComponentModel.IRaiseItemChangedEvents> arabirimi ayrıca uygulayan bir listedir bağlanabilir <xref:System.ComponentModel.IBindingList> arabirimi. Bu arabirim türüne harekete geçirirse göstermek için kullanılan <xref:System.ComponentModel.IBindingList.ListChanged> türünde olayları <xref:System.ComponentModel.ListChangedType.ItemChanged> aracılığıyla kendi <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A> özelliği.  
  
    > [!NOTE]
    >  Uygulamalıdır <xref:System.ComponentModel.IRaiseItemChangedEvents> veri kaynağınızı daha önce açıklanan listesi olay dönüştürme özelliğini sağlar ve ile etkileşim kurma <xref:System.Windows.Forms.BindingSource> bileşeni. Aksi takdirde, <xref:System.Windows.Forms.BindingSource> daha yavaş performans listesi olay dönüştürme özelliğini de gerçekleştirir.  
  
-   <xref:System.ComponentModel.ISupportInitialize> arabirim  
  
     Uygulayan bir bileşen <xref:System.ComponentModel.ISupportInitialize> arabirimi özellikleri ayarlama ve ortak bağımlı özellikler başlatma için batch iyileştirmeleri avantajları alır. <xref:System.ComponentModel.ISupportInitialize> İki yöntem içerir:  
  
    -   <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> Bu nesne başlatmayı başlangıç bildirir.  
  
    -   <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> Bu nesne başlatmayı tamamlıyor bildirir.  
  
-   <xref:System.ComponentModel.ISupportInitializeNotification> arabirim  
  
     Uygulayan bir bileşen <xref:System.ComponentModel.ISupportInitializeNotification> arabirimini de uygular <xref:System.ComponentModel.ISupportInitialize> arabirimi. Bu arabirim, diğer bildirim sağlar <xref:System.ComponentModel.ISupportInitialize> bileşenleri bu başlatma işlemi tamamlandı. <xref:System.ComponentModel.ISupportInitializeNotification> Arabirimi iki üyeleri içerir:  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A> döndürür bir `boolean` bileşeni başlatılıp başlatılmadığını gösteren bir değer.  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> Gerçekleşir, <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> çağrılır.  
  
-   <xref:System.ComponentModel.INotifyPropertyChanged> arabirim  
  
     Bu arabirimi uygulayan bir sınıf özellik değerleri değiştiğinde bir olay başlatır bir türdür. Bu arabirim, bir denetimin her bir özellik için bir değişiklik olayı yaşama düzeni değiştirmek için tasarlanmıştır. Kullanıldığında bir <xref:System.ComponentModel.BindingList%601>, bir iş nesnesi uygulamalıdır <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi ve BindingList\`1 tarafından dönüştürülür <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> olayları <xref:System.ComponentModel.BindingList%601.ListChanged> türünde olayları <xref:System.ComponentModel.ListChangedType.ItemChanged>.  
  
    > [!NOTE]
    >  Değişiklik için bildirim ilişkili istemci ve veri arasında bir bağ oluşmasına kaynak, bağlı veri kaynağı türü ya da uygulama <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi (tercih edilen) veya sağlayabilir *propertyName* `Changed` olayları ilişkili tür, ancak her ikisini birden yapın olmamalıdır.  
  
### <a name="interfaces-for-implementation-by-component-authors"></a>Uygulama bileşen yazarları tarafından arabirimleri  
 Aşağıdaki arabirimlerinden Windows Forms veri bağlama altyapısı tarafından kullanımı için tasarlanmıştır:  
  
-   <xref:System.Windows.Forms.IBindableComponent> arabirim  
  
     Bu arabirimi uygulayan bir sınıf veri bağlamayı destekleyen bir denetim olmayan bileşenidir. Bu sınıf veri bağlamalar ve bağlama bağlamını bileşeninin döndürür <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> ve <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> bu arabirimin özellikleri.  
  
    > [!NOTE]
    >  Bileşeniniz öğesinden devralıyorsa <xref:System.Windows.Forms.Control>, uygulama gerekmez <xref:System.Windows.Forms.IBindableComponent> arabirimi.  
  
-   <xref:System.Windows.Forms.ICurrencyManagerProvider> arabirim  
  
     Uygulayan bir sınıf <xref:System.Windows.Forms.ICurrencyManagerProvider> arabirimidir kendi sağlayan bir bileşen <xref:System.Windows.Forms.CurrencyManager> bu belirli bir bileşen ile ilişkili bağlamaları yönetileceği. Özel erişim <xref:System.Windows.Forms.CurrencyManager> tarafından sağlanan <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> özelliği.  
  
    > [!NOTE]
    >  Öğesinden devralınan bir sınıf <xref:System.Windows.Forms.Control> bağlamaları ile otomatik olarak yönetir, <xref:System.Windows.Forms.Control.BindingContext%2A> özelliği, gerektiği uygulamak bunu çalışmaları <xref:System.Windows.Forms.ICurrencyManagerProvider> oldukça nadir rastlanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Bağlama ve Windows Forms](data-binding-and-windows-forms.md)
- [Nasıl yapılır: Windows Forms’ta Basit Bağlantılı Denetim Oluşturma](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
